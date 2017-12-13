# Enterprise Service Bus (Guest Lecture)

## Motivation
- Viele Services (ERP, CRM, etc.)
- Integration, um zwischen den Services kommunizieren zu können
- Verschiedene Protokolle / Datenformate der Systeme
- Punkt-zu-Punkt-Verbindungen erzeugen starke Kopplung der Systeme

## Definitionen
- "An enterprise service bus (ESB) is a software architecture model used for designing and implementing the interaction and communication between interacting software applications in service-oriented architecture (SOA).“
- Architektur-Pattern und Produktkategorie
- Implementation von Anti Corruption Layer (ACL)

## Lösung
- Für jede Technologie einen Adapter
- Verarbeitungsflow wird innerhalb ESB definiert
- Wenn Technologie an einer Schnittstelle ändert, muss nur der Adapter ausgetauscht werden
- Wenn ein kanonisches Datenmodell existiert (für die ganze Firma), muss lediglich jedes andere Datenmodell darin übersetzt werden. Sonst muss für jede Verbindung zwischen zwei Protokolle übersetzt werden

### Versionierung
- ESB kann Funktionalität zur Verfügung stellen, um zwischen verschiedenen Versionen zu übersetzen

## XQuery
- Mapping zwischen zwei Datenformaten
- Code oder über grafische Tools