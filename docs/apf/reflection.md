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
- MOP (Metaobject protocal) ist ein interface für die meta objects
    - z.B. `Object.getClass()`
- Introspection: In Base Level Objects hinein "schauen"
- `eval` z.B. verändert Base Level Objects (intercession)

## Type Object Pattern
- Meta-Object, das calls weiterleitet an ein konkretes Objekt, das von aussen gesetzt wird
- Konfiguration wird von extern, z.B. mit config-file eingespiesen
    - Nachteil: Keine inhärente Type-Safety mehr
