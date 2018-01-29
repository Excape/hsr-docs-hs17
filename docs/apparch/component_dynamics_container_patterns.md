# Component Dynamics & Container Patterns
- INSIEME nach 12 Jahren und 100 Mio. abgebrochen

## Component Dynamics
- Candidate Components sind logische Komponenten der Architektur, die ähnliche Verantwortlichkeiten zusammen fassen
- Implementation Components sind aus dem Development Viewpoint, dies sind die konkreten Implementation mit deren Interfaces
- Bei der Architektur geht es auch um den Fluss, d.h. um das Verhalten des Systems, nicht nur deren Struktur

- *Component Interaction Diagrams* sind UML Sequenzdiagramme, die das Zusammenspiel zwischen mehreren Komponenten zeigen
- 
## Container Patterns

### Plugin
- z.B. Eclipse, Browser
- Funktionen werden durch Konfiguration (ohne Neukompilieren) hinzugefügt

### Inversion of Control
- Frameworks steuern den Fluss selber, Komponenten werden  vom Framework aufgerufen
- Problem: Wie wird definiert, wie Frameworks die Komponenten finden kann?
    - -> Dependency Injection
