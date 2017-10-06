# Solution Strategy
Tipps für Solution Strategy: <http://docs.arc42.org/keywords/#solution-strategy>

## Architectural Synthesis
- Scope abstecken mit funktionalen Komponenten und externen Interfaces
- Wichtige Entscheidungen zur Architektur (Tiers, Frameworks)
- "Twin Peaks Model": Requirements und Design (Architektur) werden "gleichzeitig" ausgearbeitet (iterativ und inkrementell)

## Layer-Pattern
- Im Layer-Pattern gibt es keine Layer-"Sprünge"!
- Layers sind logisch und geben nicht die physikalische Verteilung (tiers) vor
- "Enterprise Resources" = "Domain Entities"
- Business Rule: Anforderungen, z.B. "Kundenanfragen werden in x Min beantwortet"

## Client-Server Cuts
- Layer-Pattern zwei mal angewendet: Logisch (logical Viewpoint) und Aufteilung auf phyiskalische Tiers (deployment viewpoint)
- Layer können als ganzes auf Tiers aufgeteilt werden, oder Layer können auch "geschnitten" werden
- Tiers und Layers werden oft missverständlich verwendet, am besten immer nachfragen
- Fliessende Layers: Ist z.B. Eingabevalidierung im Presentation-Layer, oder allein / zusätzlich noch in Business Logic?
    - z.B. auf beiden Layern testen und mit Tests "synchronisieren"

## C4 Models
- **Context**: System ist black-box, welche Schnittstellen kommunizieren damit?
    - Dazu gehören andere Systeme und auch User mit Use Cases
- **Container**: Gibt eine Übersicht der Architektur (solution strateby)
    - High-Level Technology choices
- **Components**: Logische Komponenten und Kommunikation innerhalb eines Containers (mehr in nächster Vorlesung)
- **Classes** (or Code): Klassendiagramm oder Code selbst
