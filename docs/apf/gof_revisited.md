# GoF Revisited
## Repetition
### Observer
Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

### Strategy
Define a family of algorithms, encapsulate each one, and make them interchangeable. Strategy lets the algorithm vary independently from clients that use it.

### Template Method
Define the skeleton of an algorithm in an operation, deferring some steps to subclasses. Template Method lets subclasses redefine certain steps of an algorithm without changing the algorithm's structure.

### Abstract Factory
Provide an interface for creating families of related or dependent objects without specifying their concrete classes.

### Prototype
Eine konkrete Instanz wird gecloned (statt mit Factory) für eine neue Instanz. So können gleiche Instanzen schnell erstellt werden, ohne sie jedes Mal neu zu instanzieren

### Composite
Compose objects into tree structures to represent part-whole hierarchies. Composite lets clients treat individual objects and compositions of objects uniformly.

- Transparent Composite: Oberklasse (Graphic) hat `add(Graphic)` methode
    - Problem: abgeleitete Klassen haben diese dann auch, können sie aber nicht brauchen!

### Decorator
Attach additional responsibilities to an object dynamically. Decorators provide a flexible alternative
to subclassing for extending functionality.

- Andere Intention als Composite: Man möchte weitere Funktionalität einführen, nicht einen Baum aufbauen. Es ist eine "Kette" von Funktionalität

### Facade
Provide a unified interface to a set of interfaces in a subsystem. Facade defines a higher-level interface that makes the subsystem easier to use

## Lesser Known Patterns
### Mediator
- Kommunikation unter Objekten sicherstellen, ohne dass die Objekte selbst Referenzen untereinander haben
- Mediator ist oft Observer, die beteiligten Objekte Observables
    - z.B. in `update()` die Updates von einem Colleague einem anderen Colleague übergeben
- Gut testbar, wenn sauber: Colleagues-Mocks dem Mediator übergeben
- Nachteil: Mediator ist SPOF,  kann sehr gross und unstrukturiert werden

### Memento
- Ein Zustand eines Objektes auslagern, damit er später wiederhergestellt werden kann, ohne die Kapselung zu verletzen
- z.B. Savegames
- Der Zustand vom Originator wird in das Memento kopiert
- Beim Widerherstellen schreibt der Originator der Zustand vom Memento zu sich selber
- Vorteil: Originator muss nicht seine Internals heraus geben
- Nachteile:
    - Braucht jedes Mal eine vollständige Kopie
    - Viel Speicherplatz benötigt

### Command
- Ein Command kann herumgereicht werden ("was gibt es auszuführen")
- Command wird von einem Invoker ausgeführt (`execute()`)
- Command kann z.B. geloggt oder scheduled (verzögert) werden
- Nachteil: Viele kleine Command-Klassen bei grossem Design, wird zersaust
- Quasi ein Function pointer, der herum gereicht wird

### Command Processor
- Wie Command, aber mit Undo / Redo
- z.B. Commands in Stack speichern als History
- Der Processor verwaltet die History
- Command Processor gibt auch vor, wer die Commands ausführt, dürfen nicht mehr "beliebig" herum geschoben werden!

### Visitor
- Problem: Klassenhierarchie braucht neue Methode, ohne die Klasse zu verändern
- Beispiel Filesystem Serialisierung: Oberklasse `FSObj` hat Methode `accept(visitor)`. Die Unterklassen "konsumieren" den Visitor
    - Der Visitor ist entweder ein `XmlVisitor` oder `JSONVisitor`
    - Unterklassen rufen im `accept()` visitor mit Referenz auf sich selbst auf (z.B. in File: `visitor.visitFile(this)`)
- Nachteile: 
    - Die beiden Hierarchien sind gekoppelt, für neue Elemente müssen beide Hierarchien angepasst werden beide Hierarchien angepasst werden
    - Gefahr von Code duplication, weil die Logik aufgebrochen wird

### Flyweight
- Ausgangslange: Viele Objekte, die alle "gleich" sind, aber in einer Art (z.B. Position) unterschiedlich sind
- Interner State ist immer gleich, externer State kann sich ändern
- Ziel: Memory-sparend abbilden
- Die `Flyweight`-Klasse ist z.B. ein Baum
- `FlyweightManager`verwaltet die Objekte
    - Vom Flyweight gibt es nur eine Instanz, gehalten vom Manager 
- Der interne (intrinsic) State ist für alle Objekte gleich (immutable Flyweights)
- Der externe State wird vom Client direkt dem konkreten Flyweight gegeben (und wird dort nicht gespeichert!)
