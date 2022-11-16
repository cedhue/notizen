---
title: 
tags: permanent/rough
aliases: []
---

## Chi-Quadrat und Cramers V
Zusammenhangsmaße für nominal skalierte Variablen

Chi-Quadrat basiert auf dem Vergleich von beobachteten und erwarteten Häufigkeiten

	tab zweistimme ostwest2 , exp chi

Mit `exp` lässt sich die erwartete Häufigkeit anzeigen, wenn die beiden Variabeln statistisch unabhängig wären, mit `chi` lässt Chi-Quadrat berechnen

Je größer die Abweichung, desto größer ist auch Chi-Quadrat.

Berechnung von Chi-Quadrat ?


Freiheitszahl

P Wert = Wahrscheinlichkeit, dass wir den beobachteten oder einen noch extremeren Chi-Quadrat-Wert erhalten, wenn die Nullhypothese gilt

Nullhypothese = es besteht kein Zusammenhang

Cramers V

Berechnung: sqr(Chi-Quadrat-Wert/ Chi-Quadrat-Wert für maximale Verteilung)

	tab zweistimme ostwest2, exp 

Faustregel

< 0,2 schwach
0,2 - 0,4 mittlerer
\> 0,4 starker Zusammenhang

## Gamma und Tau-b

Zusammenhangsmaße für ordinalskalierte Daten

Logik des Paarvergleichs, Anzahl von konkordanten und diskordante Paarvergleiche bzw. ties.

	tab wahlbeteiligung bildung, gamma tau

## Pearson's r und Kovarianz

Zusammenhangsmaße für metrisch skalierte Variablen

Streng genommen nicht metrisch, sondern ordinalskalierte Variablen, allerdings werden sie ab einer zehnstufigen Skala als metrisch betrachtet.

	* Berechnung des Korrelationskoeffizienten mit zwei oder mehr Variablen:
	corr skalo_lin skalo_spd 

	* Anzeige der Kovarianzen für jedes Variablenpaar
	corr skalo_lin skalo_spd , covariance

## Signifikanztests

	pwcorr skalo_lin skalo_spd , sig

Die Option `sig` für "significance" zeigt die t-Werte an. 
Wichtiger Unterschied zu `correlate`: Hier werden alle jeweils verfügbaren Fälle mit einbezogen (inkl. missings)

Listwise-Deletion mit `listwise`

Mit der Option ‚sig‘ berechnet der Befehl pwcorr den p-Wert für einen statistischen Test mit folgender Nullhypothese:


---
### Referenzen
### Relevant
### Tags
Stata


