# Reflection - Self-aware Software
## Für was
- Mocking/Test-Frameworks
- Remote Systems
- Annotations
- OR-Mapper / z.B. EF
- Exception Handling (& stack trace)
- Debugging
- Plugin-Systeme
- Linker / dynamisch (.so, .dll)
- Dynamic Polymorphism

## Reflection Pattern
- Im Base Level sind die normalen Objekte des Programms
- Im Meta Level sind die Informationen über die Base level objekte, als Meta-Objects
    - `class`-Objekt in Java ist meta object
- MOP (Metaobject Protocol) ist ein interface für die meta objects
    - z.B. `Object.getClass()`
- Introspection: In Base Level Objects hinein "schauen"
- `eval` z.B. verändert Base Level Objects (intercession)

## Type Object Pattern
- Meta-Object, das calls weiterleitet an ein konkretes Objekt, das von aussen gesetzt wird
- Konfiguration wird von extern, z.B. mit config-file eingespiesen
    - Nachteil: Keine inhärente Type-Safety mehr

## Property List
- a.k.a Dictionary, Map
- Problem: z.B. variable Anzahl Parameter übergeben (klassisch `...varargs`)
- Lösung: Property List übergeben
- Nachteile: 
    - Nicht "type-safe"
    - Es können beliebig viele Elemente in der Property List sein
    - Attribut-Namen werden nicht von Compiler geprüft
    - Memory Management (Garbage Collection?)

## Anything
- Rekursive Struktur von Anything-Objekten
    - Jedes Element ist entweder "etwas" oder eine Liste von "etwas" (oder dictionary)
- Heute "JSON"
- Meist für Konfigurationen verwendet
- "Anything" in "Anything" mit Composite-Pattern
    - Achtung: Unterschied Composite / Decorator ist nur Assoziation zu Base-Klasse!
r
## Extension Interface
- Quasi Plugin-Pattern
- _Component Factory_ instanziiert und verwaltet die Komponenten
- Client fragt _Component Factory_ nach bestimmter Komponenten und bekommt ein Interface zurück
- z.B. Eclipse: Client benötigt C++ Editor
- Braucht Reflection, um zur Laufzeit die entsprechenden Komponenten zu finden

## Zusammenfassung
- Reflection braucht immer overhead durch Runtime
- Behindert Optimierung (JIT)
- Kontrollfluss kann komplex sein
- Kann sehr nützlich sein für sich entwickelnde Systeme
- Korrektheit ist nicht mehr nachweisbar