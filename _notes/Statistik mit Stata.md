---
title: Statistik mit Stata
tags: permanent/rough
aliases: [Stata]
---

## Typische Arbeitsschritte

- [[Daten einlesen in Stata|Daten einlesen]]
- [[Wertelabel in Stata|Wertelabel]]
- [[Variablen in Stata generieren und umkodieren|Variablen generieren und umkodieren]]
- [[Zusammenhangsmaße in Stata]]
- [[Statistische Tests in Stata|Statistische Tests]]
- [[Lineare Regression in Stata]]


## Befehlsreferenz

Grundlegende Form für einen Befehl:

	'Befehl' 'Variable' , 'ergänzende Optionen'

| Befehl        | Beschreibung | Beispiel |
| ------------- | ------------ | ------- |
| `use`  | Datensatz einlesen | `use "PFAD"` |
| `clear` | Arbeitsspeicher leeren. Kann auch an den `use`-Befehl angehängt werden. | `use "PFAD", clear` |
| `tab` | Erstellt (Kreuz)tabelle einer oder mehrer Variablen | `tab var 1` |
| `help` | Hilfefunktion | `help recode` |
| `lookfor` | Sucht nach passenden Variablen im Datensatz | `lookfor links-rechts` |
| `search` | | |
| `gen`, `generate` | Generiert eine neue Variable |


### Shortcuts

| Shortcut | Beschreibung |
| -------- | ------------ |
| `Strg+D`    | Do-File ausführen. Wenn nur einzelne Bereiche ausgewählt sind, werden nur diese ausgeführt |


## Kommentare

- in einer einzelnen Zeile: `* Kommentar` 
- nach einem Befehl: `// Kommentar` 
- für mehrzeilige Kommentare: `/* Kommentar */` 


## Kreuztabellen

## If-Bedingungen
### Relationale Operatoren
- gleich: `==`
- ungleich: `!=`
- größer als: `>` (≠ größer gleich)
- größer gleich: `>=`
- kleiner als: `<`
- kleiner gleich: `>=`

### Logische Operatoren
- und: `&`
- oder: `|`

### Arithmetische Operatoren
- Addition
- Subtraktion
- Multiplikation
- Division
- Potenzen  `^`
- Wurzel `sqrt(WERT)`

Beispiel: `tab q11ba if q11ba > 0`



## Aufbereitung von Daten

= Vorbereitung der Variablen, die verwendet werden sollen

Schritte um Variable anzupassen:

    * Erstellen einer neuen Variable aus einer bestehenden Variable
    gen zweistimme = q11ba
    * Ausschließen eines Bereichs (markiert durch den "/")
    recode zweitstimme (-99/-83 = .) 

---
### Referenzen
### Relevant
### Tags
Stata








