# Strategic DDD

## Tactic DDD update
- Aggregates können auch Events austauschen (Message Queue System)

## Aggregate Best Practices
- Aggregates kommunizieren asynchron (mit MQ) miteinander
- Aggregates sollen separat deploybar sein
- Keine verteilten Transaktionen

## Bounded Context
- "Beschränkter" Context (Boundary)
- Meist ein Subsystem oder die Arbeit eines Teams
- Innerhalb der Boundary soll z.B. "ubiquitous" language gelten
- Grenzen sind eindeutig und explizit definiert

## Subdomain Pattern
- Die ganze Problemdomäne aufteilen in Subdomains
    - Funktionale Anforderungen aufteilen
- SE2: Partitioning vom Domain Model
- Die Lösungsdomäne (design-level domain model) in bounded Contexts aufzuteilen
- Unterschied zum Bound Context: BC ist im Solution Space, Subdomains im Problem Space
- In "idealer" Welt Mappen Subdomains und BCs 1:1
    - Realität eher n:m, eine Subdomain kann z.B. in mehreren BC vorkommen

## Context Map Pattern
- Technik, um Bounded Contexts zu verbinden und die Beziehungen dazwischen zu verbinden
- Den Beziehung einen Typ zuweisen
    - Die Typen unterscheiden sich in Sachen Einfluss (coupling) und (a)symmetrie
- *conformist*: Ein BC "folgt" einem Anderen, hat keinen Einfluss auf das Interface des anderen BC
- *partnership*: Einigung, gemeinsame Aggregates zwischen BCs
- *shared kernel*: Gemeinsamer Kernel (z.B. library) - enge Kopplung
- *Open Host Service*: z.B. Offene API mit Doku, kann von jedem anderen BC verwendet werden
- *Customer/Supplier*: Customer kann Interface auch beeinflussen
- *Anti Corruption Layer*: Adapter implementieren, um sich vor Änderungen des Interfaces zu schützen

!!! info
    Context-Map Aufgabe (oder ähnliche) kommt oft in Prüfung!

