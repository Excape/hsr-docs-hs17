# Eclipse Architecture and Patterns

## Überblick
- Wurde zuerst als Framework für IDEs entwickelt
- Dann mit dem Ziel, eine Software-Plattform für allgemeine Desktop-Applikationen zu sein
- Fast alles ist als Plugin implementiert - auch der Workbench (das GUI)

## SWT / JFace
- Plattformunabhängig, aber Teil des GUIs ist aber plattform-spezifisch
- SWT selbst entwickelt
    - Dünne Abstraktionsschicht über das GUI des Betriebssystems
- JFace baut auf SWT auf und bildet die konkreten und komplexeren GUI-Komponenten

## OSGi
- Open Services Gateway initiative
- Komponenten- und Service-Modell für Java + Dependency Management
- Komponenten können gebündelt werden und dynamisch starten / stoppen
- ähnlich zu Java 9 Modularisierung
- Standard, der von Eclipse implementiert wird (mit Equinox)

## Eclipse Plug-ins
- Eclipse Plugins sind OSGi bundles
- Plugins können nicht ohne Neustart installiert werden, weil OSGi Services nicht benutzt werden
- Jedes Plugin hat eigenen Class loader, womit mehrere Plugins auch unterschiedliche Versionen einer dependency benutzen können
- Plugins werden erst geladen, wenn es benötigt wird
    - Eclipse kann statische XML-Files durchsuchen, ohne dafür Java Code zu laden

### Extension Points
- Bsp: Plugin möchte sich in ein Menü einhängen
    - Menü bietet einen Extension Point an
    - Plugin implementiert Interface des Extension Points
- Plugins können selbst EPs zur Verfügung stellen
- Wird definiert in `plugin.xml`

## Eclipse Core Patterns
- Viele Singletons - Unit testing unmöglich, ohne eigene Instanz zu starten
- Proxy Pattern: Handler für eine Ressource anbieten, als Abstraktion auf das OS
    - Wird auch genutzt für Plugin Lazy Loading
    - Plugin wird erst geladen, wenn der Proxy die "action" bekommt
- Pluggable Adapter: Komplexe Komponenten in JFace
- Observer z.B. auf Ressourcen
- Strategy: Ein Teil eines Controls kann verschiedene Arten von Layouts (=Strategies) haben
- Command: JFace Action, z.B. bei einem Klick auf ein Menü

## Refactoring Language Toolkit (LTK)
- Sprach-unabhängige API für Refactorings
- Template Method, um Skeleton vorzugeben und bestimmte Schritte an Unterklassen weiter zu geben
- Am Endes des Refactorings wird ein `Change` Objekt erstellt, das vom Eclipse auf die Files angewendet wird
- Ein Change kann aus mehreren Komponenten bestehen -> **Composite Pattern**
- Refactorings können aus der History exportiert werden, dafür werden sie serialisiert -> **Memento Pattern**
- Refactorings arbeiten mit dem AST
- Um AST zu traversieren -> **Visitor Pattern**
    - Traversierung ist in den Knoten selbst, nur die benötigten Methoden werden implementiert