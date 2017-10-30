# Tactic DDD & Architecturally Evident Coding Style
## Recap
- `SpringDIAssember` ist ein erfundener Name, steht für Dependency Injection Komponente von Spring

## Domain Model Pattern (PoEAA)
- Bei Fowler nur sehr knapp definiert, mehr in DDD

## Business Layer Logic
- Verschiedene Arten von Business-Logik: Berechnungen, CRUD, Checks, Reporting, etc.

## Tactic Domain Driven Design
- "Zoom-in" auf Domain-Model
- Strategie: Langfristig, Taktik: Kurzfristige Entscheidungen, um Ziele zu erreichen
- Modifiziertes Layer-Modell
    - *Interfaces*: quasi Presentation Layer
    - *Application*: Business Logik
    - *Infrastructure*: Data Access, quer zu den anderen Schichten! Gehört eigentlich eher unter Domain
- Ubiquitous Language: Sprache von DDD soll "allgegenwärtig" und einheitlich in der Applikation sein
- Best Practice: An Aggregate-Grenzen nur Objekt-Ids überbgeben, keine Referenzen (Entkopplung)

### DDD Patterns
- Einteilung von _Entities_, _Services_ und _value objects_ (siehe APF)
    - Klassen mit lediglich "Do-er" Methoden (stateless) sind _services_
- Aggregate Pattern: Entities und Value Objects in _Aggregates_ gruppieren
    - Analog SE1/SE2: Partitionieren
    - Jedes Aggregate hat eine _root Entity_, die Zugriff zu anderen Entities bietet und Business Rules (Invariants, Pre-- und Post-conditions) überprüft
    - Aggregate selbst ist keine Klasse, nur ein package!
- Pro aggregate und root entity eine _Factory_ implementieren
- Eine _Repository_-Klasse pro Aggregate für alle Entities definieren, die abgerufen werden sollen (per id)
    - z.B. `find()`, `store()`

## Architecturally Evident Coding Styles (AECS)
- Architektur soll im Code nicht "verloren" gehen
- Startup-Code soll zentralisiert sein (und klar benannt)
- In DDD: "Intention Revealing Interfaces"
- 2-3 Wörter pro Name
- Starke Verben verwenden (nicht "set", "change")
