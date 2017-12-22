# Flyweight Boxing & Singleton Assassination

## Flyweight
- "Most state can be made extrinsic": Wenn Zustand ausgelagert wird, sind die Flyweights leer, dadurch bringt es nicht viel
- Factory ist eigentlich der Manager der Flyweights
- `UnsharedConcreteFlgyweight` ist verwirrend und gehört eigentlich nicht zum Pattern
- Flyweight zeigt eigentlich mehrere Patterns
    - Factory Method als Teil eines Managers
    - Immutable Value
    - Pooling

!!! info
    Factory Method wird oft als Hook in einem Template Method Pattern verwendet


!!! todo
    Manager Design Pattern (Selbststudium) lesen


!!! info
    Value objects in Java: `final` fields über Konstruktor setzen. Achtung vor Referenzen, `final` ist nicht transitiv wie in C++!

### Consequences
- Laufzeitkosten, vor allem heute relevant, da eigentlich alles gecached werden kann und nicht von einem zentralen Pool geholt werden muss
- Dafür spart es Speicherplatz

## Pattern Kombinationen
- Template Method -> Factory Method
- Composite -> Chain or Responsibility

## Singleton
- Shared Resource, die nicht immutable ist -> Problem!
- Kann *maximal* einmal instanziiert werden, also auch gar nicht (zur Optimierung)
- Singleton vererben: Superklasse muss Subklasse kennen, damit die Instanz erstellt werden kann
    - Gibt zirkuläre Abhängigkeit!
- GoF-Buch beschreibt keine Nachteile!
- Double-Checked-Locking: Zuerst ohne Lock checken, ob die Instanz existiert, und erst dann wird gelockt (mit 2. Check)
- Monostate Pattern
    - Es gibt nur einen State über alle Instanzen
    - Klasse wird mit `static` fields geschrieben, die von non-static-methoden zugegriffen werden
- Alternative: Parameterize from above, bzw. Dependency Injection

!!! quote
    "How do you provide global variables in languages without global variables? Don't. Your programs will thank you for taking the time to think about design instead." - Kent Beck

