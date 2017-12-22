# Patterns for Parallel Programming

## Hardware Architektur
- Pentium konnte Berechnungen parallel auf floating-point unit und integer unit ausführen
- Intel i / xeon CPU's haben Vector Registers, um Vektoren im einen Schritt zu berechnen

!!! info
    <https://godbolt.org/> als Compiler Explorer

## Decomposing Strategy
- Ziel: Ein Problem in kleinere zerteilen, um diese zu parallelisieren
- Ansatz *Task decomposition*: Problem in Tasks zerlegen
    - z.B. unabhängige Requests verarbeiten
- Ansatz *Data decomposition*: Daten zerlegen
    - z.B. in Physik, Raum in kleine unabhängige Teile zu teilen
- Beide Ansätze können kombiniert eingesetzt werden
- Schwierigkeit: Abhängigkeiten (die nicht offensichtlich sind)
- loop-splitting: Unabhängige Iterationen parallelisieren

## Koordination
- linear Abhängige Tasks: Pipes and Filters
- "ungeordnete" Abhängigkeiten: Event-based coordination, analog Thread Pools