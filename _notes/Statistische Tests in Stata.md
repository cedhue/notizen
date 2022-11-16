---
title: Statistische Tests in Stata
tags: permanent/rough
aliases: []
---

Verschiedene Typen von t-Tests

- Einstichproben-t-Test (single sample t-test)
	- so lässt sich testen, ob sich der Mittelwert von einem theoretisch bedeutsamen Wert unterscheidet
	- Beispiel: Entspricht das durchschnittliche Alter einem bestimmten Erwartungswert?

- Zweistichproben-t-Test für abhängige Stichproben (paired / dependent t-test)
	- für verschiedene Messungen der gleichen Beobachtungseinheit, z. B. Vorher-Nachher-Vergleiche
	- Beispiel: Wird ein Kanzlerkandidat nach dem TV-Duell anders bewertet als davor? (Zeitvergleiche mit der gleichen Stichprobe)

- Zweistichproben-t-Test für unabhängige Stichproden (independent group t-test)
	- für Messungen unterschiedlicher Beobachtungseinheiten bzgl. der gleichen Variablen, z. B. Gruppenvergleiche
	- Unterschiedliche Stichproben
	- Hier muss auf die Varianz geachtet werden.

## Ein-Stichproben-t-Tests

	ttest lire_cdu == 0

Formulierung der Null-Hypothese in diesem Fall: 

Nullhypothese: Arithmetisches Mittel der Grundgesamtheit = dem angegebenen Wert

Wenn die Nullhypothese sich bestätigt, dann ist die geringe Abweichung in der Stichprobe rein zufällig (kein substanstieller Befund)

Verschiedene Alternativhypothesen (Ha)

Ha: mean < 0 (linksseitiger Test)
Ha: mean != 0 (zweiseitiger Test -> für ungerichtete Alternativhypothesen)
Ha: mean > 0 (rechtsseitiger Test)

Wenn p-Wert ≤ 0,05 kann die Nullhypothese zugunsten der Alternativhypothese verworfen werden

### Beispiel: Wird die CDU als Partei der Mitte eingeschätzt?

Die CDU hatte lange den Slogan "Die Mitte". Allerdings ist das arithmetische Mittel in der Stichprobe für die Variable `lire_cdu = 0.38`, das heißt die Befragten der Stichprobe schätzen die CDU nicht genau in der Mitte, sondern ein kleines bisschen weiter rechts ein. 

Nun stellt sich die Frage, ob diese Abweichung nur zufällig entsteht (also in der Grundgesamtheit so nicht wiederzufinden wäre) oder ob davon ausgegangen werden kann, dass die Abweichung auch in der Grundgesamtheit wiederzufinden ist.

Dazu wird die Nullhypothese H0 aufgestellt, dass das arithmetische Mittel der Links-Rechts-Einschätzung der CDU in der Grundgesamtheit = 0 ist und ein entsprechender t-Test mit dem Befehl `ttest lire_cdu == 0`

## t-Test für abhängige Stichproben

Wird häufig für die Panel- oder Experimentaldaten eingesetzt (Befragungen über einen Zeitraum, zum Beispiel vor oder nach einer Wahl oder vor oder nach der Gabe eines Medikaments). In diesem Fall sind die Variablen abhängig voneinander, da sie zum Beispiel die gleiche Person betreffen.

Mit dem t-Test kann getestet werden, ob beide Messungen im Durschnitt identisch sind. Wenn die Differenz der beiden Variablen sich von 0 unterscheidet, dann würde auf beiden Variablen ein nicht nur zufällig unterschiedliches Antwortverhalten vorliegen.

Lässt sich auch innerhalb einer Stichprobe anwenden, um die Konsistenz des Antwortverhaltens zwischen zwei Variablen zu untersuchen, für die ein ähnliches Antwortverhalten logisch erscheint.

### Beispiel: Einschätzung der Parteien und ihrer Spitzenkandidat\*innen

**These:** Die Wahrnehmung der Spitzenkandidat\*innen einer Partei ist teilweise unabhängig davon, wie deren Partei wahrgenommen wird. Es sind also auch persönliche Eigenschaften der Kandidat\*innen relevant.

Entsprechend wäre die Nullhypothese: Einstellungen bzgl. der Parteien und der Kandidat\*innen sind identisch, die Bewertung der letzten ist nur eine Projektion der Parteipräferenz

	*T-Test für die Bewertung der Partei "Die Linke" und deren Spitzenkandidatin*
	ttest skalo_lin == skalo_wagenknecht

Die Differenz im arithmetischen Mittel der beiden Variablen ist hier leicht negativ, das heißt dass der Wert der zweiten Variable für das arithmetische Mittel größer ist, als der der zweiten Variable. In diesem Fall bedeutet dass, dass die Kandidatin etwas beliebter ist, als ihre Partei.

In diesem Fall ist die Hypothese ungerichtet formuliert. Für `Ha: mean(diff) !=0` ist `P = 0.000`, das heißt, die Abweichungen sind in der Stichprobe mit sehr hoher Wahrscheinlichkeit nicht ganz zufällig.

## t-Test für unabhängige Stichproben

Bei dieser Art von Test werden Unterschiede in der selben Variable zwischen verschiedenen Subgruppen getestet.

### Beispiel: Gibt es einen Ost-West-Unterschied in der Bewertung der Partei "Die Linke"?

**These:** Die Linke hat in Ostdeutschland wesentlich bessere Wahlergebnisse, daher liegt die Vermutung nahe, dass diese in Ostdeutschland beliebter ist.

Bevor der t-Test durchgeführt wird, werden Unterschiede in den Standardabweichungen der beiden Gruppen untersucht. Wenn die Antworten in einer Gruppe stärker streuen, als die Antworten in der anderen Gruppe, könnte dies die Ergebnisse des t-Tests verfälschen.

	sdtest skalo_lin , by (ostwest2)

Nullhypothese: Quotient der Standardabweichungen ist 1, das heißt die Standardabweichungen sind in beiden Gruppen gleich und es gibt kein Problem für den t-Test.

	H0 = sd(Ostdeutschland / sd(Westdeutschland = 1

Wenn die p-Werte < 0,05 sind, sind die Abweichungen signifikant. Da das nicht der Fall ist, kann der t-Test normal durchgeführt werden:

	ttest skalo_lin , by(ostwest2)

Wären die Abweichungen im vorherigen Test signifkigant gewesen, lässt sich ein "stabilerer" Test durchführen, der diese Abweichungen berücksichtigt:

	ttest skalo_lin, by (ostwest2) unequal

Die Nullhypothese ist hier wieder, dass die durchschnittliche Bewertung der Partei sich in beiden Gruppen nicht unterscheidet, also dass die Differenz der arithmetischen Mittel der beiden Gruppen gleich null ist.

Da unsere These war, dass ostdeutsche Wähler\*innen die Linke besser einstufen, ist der rechtsseitige Test relevant. Da `p` für diesen `> 0,05` ist, ist dieser Unterschied keine zufällige Abweichung innerhalb der Stichprobe, sondern lässt sich auch (mit sehr hoher Wahrscheinlichkeit) in der Grundgesamtheit wiederfinden.


---
### Referenzen
### Relevant
### Tags
Stata