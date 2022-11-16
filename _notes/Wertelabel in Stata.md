---
title: Wertelabel in Stata
tags: permanent/rough
aliases: []
---

Stata arbeitet bei seinen Berechnungen immer mit den numerischen Ausprägungen einer Variable. Diesen Ausprägungen lassen sich zum besseren Verständnis Wertelabel zuordnen. Das gleiche Wertelabel kann auch mehreren Variablen zugeordnet werden.

## Befehle für die Arbeit mit Wertelabeln

| Befehl | Erklärung |
| --- | --- |
| `tab VAR , nolabel` | Anzeige der Zahlencodes ohne Label |
| `lable variable VAR "Name der Variable"` | ganze Variable labeln |
| `label define` | Label für Ausprägungen einer Variable erstellen |
| `codebook [VAR]`| Übersicht über alle oder eine bestimmte Variable anzeigen. Zeigt Name, Label, numerische Ausprägungen und dazugehörige Label einer Variable an. |
| `labelbook [VAR]`| Übersicht über alle oder ein bestimmtes Wertelabel anzeigen |


## Beispiel

    * Definiert ein Label "Demokratiezufriedenheit" für verschiedene numerische Werte
    label define Demokratiezufriedenheit 1 "Sehr zufrieden" 2 "zufrieden" [...]
    * Weist das Label "Demokratiezufriedenheit" der Variable "demzuf" zu
    label value demzuf Demokratiezufriedenheit

---
### Referenzen
### Relevant
### Tags
Stata
