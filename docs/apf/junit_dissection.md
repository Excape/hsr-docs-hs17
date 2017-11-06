# Testing Framework Dissection
## JUnit Design
- Command-Pattern für Tests
- Jeder `TestCase` implementiert das Command-Interface `Test`
- `TestCase` hat `run()` als Template-Method
    - Besteht aus setup, run und teardown als "hooks"
- TDD Exkurs: `ZOMBIES`
    - "Zero, One, Many, Behavior Interface, Exceptional Behavior, Simple Scenario / Simple Solution"
- Resultate sammeln mit `Collecting Parameter`
- Factory Method kommt oft in Template Method vor
- Exceptions werden in TestResult gesammelt
- Für jede Test-Methode wird mit Reflection ein Adapter zum TestCase erstellt
- Viele Test-Cases werden in einer suite gruppiert und mit `Composite` ineinander verschachtelt

### Extending JUnit
- Mit Decorator z.B. Timing implementieren

## JUTLAND

!!! todo
    Kevlin Henney's JAOOO Presentation

- Mehr als Design-Übung gemacht
- `Tester` ist "Nanokernel" (Micro-Kernel)
- Policies definieren Tests
- Test-Listeners reagieren auf Resultate

## FIT
- Framework for Integrated Test (von Cunningham)
- Deklarativ: Was muss Programm können?
- HTML-Tabellen als Input, die Tests spezifizieren
- Sehr schlank mit nur 3 Klassen