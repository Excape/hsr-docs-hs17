# State and Event Management / Service Granularity

- Problem bei Microservices: Ein Service kann nur auf eigenen Daten operieren. Was, wenn globale Transaktion ausgeführt werden muss?

## Statelessness
- *Session state* und *resource state* sind Unterbegriffe von *application state*
- *session state* ist auf dem Presentation layer, nicht interessant für domain layer, z.B. Page flow auf website
- *resource state* ist auf Business Ebene, die Resources sind REST-Ressourcen, z.B. Entities
- REST erlaubt streng genommen gar keine Cookies
- Server Session State ist unpopulär wegen schlechter Skalierbarkeit, besser gleich Session in Datenbank speichern (z.B. Redis)
    - So ist Session natürlich auch einfacher zu archivieren und auszuwerten. Bei REST ist das viel schwieriger (möglicher Grund für Verbreitung)

## Event Sourcing
- Bei leerem application state anfangen und change logs verwenden (ähnlich Git)
- Alle Änderungen gehen über Events
- Es werden Checkpoints gesetzt in der "Kette" der Events
- Erlaubt komplette Audit Logs, oder z.B. Messaging zwischen Aggregates in DDD
- Coupling:
    - Events sind time- und reference-decoupled
    - Platform-decoupling mit XML / JSON
    - Format-coupling: Empfänger und Sender müssen sich auf Datenformat einigen

## Command Query Responsibility Segregation (CQRS)
- Domain Model auseinander ziehen
- Eines ist auf Reads und eines auf Writes optimiert
- Nützlich, wenn grosse Imbalance zwischen Read und Write 
- Read-Cache für schnelles Lesen
- Schreib-Operationen werden eventually consistent in den Read Storage übertragen
- Gut, wenn Performance wichtiger als Korrektheit ist
- Schwierig, konsistent zu halten

## Service Granularity
- Master Data Separation: Lang-lebende Objekte werden abgekapselt
- Loose Kopplung zwischen grösseren Services ist einfacher als zwischen vielen kleinen Services
- Business Granularität: "Gib den Status der Bestellung" (fein granular)
- Technische Granularität: Beeinflusst Performance und Skalierbarkeit, z.B. Anzahl Operationen im System
- Bsp: "Tweets der letzten 30 Minuten" ist auf Business-Ebene feingranular, auf technischer Ebene sind das aber viele Daten, also grob granular

