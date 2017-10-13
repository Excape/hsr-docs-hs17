# On the Value of Values
- In C++ werden Objekte kopiert bei Parameterübergabe (ausser es werden Referenzen übergeben mit `&`)

## Definition M. Jackson
- Events ist ein "Individuum", das zu einer bestimmten Zeit passiert
    - z.B. Mausklick, Absenden einer Bestellung
- Entities sind Indivduen, die über eine Zeit lang existieren und Properties haben, die sich ändern können
    - Bestellung, Datei, Profil, ...
- Values sind "unantastbare" Individuen, die sich nicht verändern
    - z.B. Zahlen, Farben, Zeichen, Koordinate

## Definition Kevin Henney
- Entities müssen unterschieden werden könnnen
- Service: Objekte, die durch das Verhalten bestimmt sind (und nicht durch den Zustand)
    - z.B. `System.out`, Connection-Services
- Value: Objekte sind durch Inhalt bestimmt, sie haben *keine relevante Identität*
    - z.B. Point, String, Integer
- Task: Im Gegensatz zum Service haben sie eine Identität und einen Zustand
    - z.B. Runnables, Threads

## Values in Programming
- Pure Functions können auch als values angesehen werden
- Einfach übers Netzwerk zu übertragen, weil sowieso nur Values übertragen werden können
- Der Wert ist das wichtige, nicht die Identität
 
### OO-Example
- ISBN als Typ modellieren, sonst muss das Format immer geparsed und geprüft werden
- So kann sich Format auch mal ändern

## Value Objects
- Ziel: Primitive Daten sinnvoll mit z.B. Einheiten repräsentieren
- z.B. Datum
### Java 
- Equals und Hashcode überschreiben!
- Aufpassen bei State-changes: Objekt klonen, damit nicht externe Referenzen gesetzt werden
    - Alternative: Klasse immutable machen

### Mutable Companion
- z.B. `StringBuilder`
- Builder, der values zusammen baut
- 
