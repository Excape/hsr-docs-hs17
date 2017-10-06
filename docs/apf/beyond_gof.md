# Beyond GoF
## Enumerator
- Probleme mit Iterator
    - Collections dürfen nie während Iteration verändert werden
    - Umgehung davon aufwändig, gibt enges coupling zwischen Iterator und Collection
- GoF hat externer Iterator ("klassisch") und interner Iterator (= Enumerator) vermischt
- Enumerator ist Inversion des Iterators
- Collection hat selbst eine Methode, die ein Kommando entgegen nimmt
    - z.B. `c.forEach(i => foo(i))`
- Iteration ist direkt in der Collection, dadurch hat es mehr Kontrolle, z.B. bei Änderungen während der Iteratation, oder mit Locking
- Ohne Lambdas das Command-Pattern verwenden

### Distribution
- Problem bei Remote Calls, wenn für jedes Element ein eigener Call auf das Remote-system gemacht werden muss
- Lösung: `Batch Method` Pattern
    - Mehrere Elemente auf einmal schicken

## State Pattern
- GoF-Beschreibung ist sehr allgemein, besserer Name wäre "Objects for States"
- Häufig overkill, oft ist auch ein primitives "Flag-based" State Management ausreichend
- Konkrete States müssen für `StateChange` etwas zurückgeben, das den nächsten State identifiziert, z.B. den Typ (In State-machine Hashtable für die einzelnen konkreten States verwenden)
    - n.b. das GoF-Sate Pattern definiert keinen solchen Mechanismus zum State-Switch
- Was, wenn ein konkreter State Daten der State-machine verändern muss?
    - Holder von Daten, der dem konkreten State übergeben wird, z.B. `increment(timeHolder)` bei Uhr

### Methods for States
- Alle Methoden (Implementation), die vorher in den States waren, kommen direkt in die State-Machine
- Methoden, die zum selben State gehören, werden in Function-Pointer-Lists zusammengefasst
- Eine dynamische Struktur (z.B. Structs) wird mit Methoden abgefüllt, je eine Struktur pro State
- Vorteil: Übersichtlicher für kleine Anwendungsfälle
- Nachteil: Grosse Klasse, viele Methoden

### Collections for States
- Jeder State ist eine Collection in der State Machine
- In den Collections können auch weitere State Machines sein
- bei jedem State change werden die Objekte in andere Collections verschoben
- Logik der State machine ist in einem "Workpiece"
- Simpelste Variante

## Frameworks
- Frameworks bieten "Hooks" für Erweiterungen
- Im Gegensatz zu einer Library steuert ein Framework den Kontrollfluss
- Arbeiten mit Callbacks, Inversion of control
- Application Frameworks sind oft over-engineered
