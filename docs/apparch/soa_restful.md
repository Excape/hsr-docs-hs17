# Service-Oriented Architectures / Restful HTTP

## Application Styles
- Ziel: Komponenten miteinander integrieren
- 4+1-Viewpoint _Process_
    - Im Sinne von OS-Prozessen
- Nach Fowler: Komponente ist lokal, Service ist eine Remote-Komponenten, der über ein Interface angesprochen wird

### Service Layer Pattern
- Zwischen Domain- und UI-Layer einen Service-Layer einschieben, um komplexe Domain-Modelle vom Presentation-Layer zu verstecken
- Verantwortlichkeiten z.B. für Exception Handling, Access Control, Logging

# DTO Pattern
- Daten-Objekt ohne Businesslogik
- Kann z.B. Methoden wie `toXML()` haben

### SOA
- "Begriff überladen"
- Grundsätzlich ein Set von Services, das von einem Business angeboten wird
- Auch ein Set von Architektur-Patterns
- Deployment Models wie mit Docker, Container, etc.

#### Loose Kopplung
1. Zeitliche Entkopplung: Client und Server müssen nicht zur gleichen Zeit aktiv sein (ohne Datenverlust) - Message Queueing
2. Adress-Transparenz/-Autonomie: "Location-Transparency"
    - z.B. man gibt URI statt MAC-Adresse ein
3. Plattform-Autonomie: Man weiss z.B. nicht, in welcher Sprache die andere Komponente (Client/Server) geschrieben ist
    - Gegenbeispiel: Java RMI
4. Format-Autonomie: Client und Server müssen sich nicht auf ein Datenmodell einigen
    - Siehe Pattern "Enterprise Service Bus", Anti-Corruption Layer

## REST
- Representational State Transfer
- REST ist ein Architekturstil, definiert über Constraints (Einschränkungen)
- Ursprünglich völlig Stateless (Server merkt sich nicht, was er vom Client schon erhalten hat)
    - D.h z.B. ohne Cookies
    - Dadurch sehr einfach verteilbar
    - "AS" (Application State) in HATEOS

### REST Majurity Model
- Ziel: Level 3 (HATEOS) -> Restful HTTP
- Nicht jedes HTTP-API erfüllt die REST-Kriterien!
- Wichtigste Eigenschaft: Resources
    - Haben jeweils genau eine URI
- HTTP-Verben: NUR HTTP-Verben auf Ressourcen aufrufen
    - Ist nicht mehr Platform-Neutral!
    - HTTP ist einzige reale "Implementation" von REST

### HatEoAS
- Hypertext as the Engine of Application State
- Custom Media Types
    - z.B. `application/json`
- Media Types tragen den Application State (Engine)
- Links identifizieren den Application State
    - Was sind die nächsten gültigen Operationen?
- Bringt viel Flexibilität, aber auch Unsicherheit
    - Kontrollfluss wird abgegeben an Endpoint
    - Dadurch oft nicht verwendet in Application Integration

!!! info "Asynchrone Calls"
    z.B. eine Ressource "Process" machen, über die der Status einer Operation (State) abgefragt werden kann

