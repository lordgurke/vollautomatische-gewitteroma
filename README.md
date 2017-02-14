# vollautomatische-gewitteroma
Die vollautomatische Gewitteroma auf Asterisk-Basis, die rangeht wenn mir jemand am Telefon was verkaufen will

## Einleitung
Die vollautomatische Gewitteroma basiert auf einem relativ simplen Asterisk-Macro (getestet unter Version 1.8 und 11),  
welches mithilfe von "WaitForNoise" und "WaitForSilence" [1] herausfindet wann ein Callcenter-Agent auf die Gewitteroma
einredet oder auf eine Antwort wartet. Wenn ausreichend Stille erkannt wird, wird per Zufallsgenerator ein Schnipsel der
Gewitteroma eingespielt, dann wieder mit WaitForNoise darauf gewartet dass der Callcenter-Agent darauf reagiert.


## Tipps
Die ersten drei Einspieler sollten (wie im Beispielcode) hardcoded zwei Mal "Hallo?!" und darauf folgend ein "Ja..." sein.
Das liegt daran, dass das erste "Hallo" meistens garnicht beim Anrufer ankommt, da dieser erst zugeschaltet wird nachdem
sich jemand am Telefon gemeldet hat. Die Anrufer rechnen quasi damit, dass jemand in die Leitung hineinruft.
Das "Ja" an dritter Stelle ist notwendig, weil dann *immer* entweder gefragt wird "Spreche ich mit..." oder "Hören Sie mich?".
Wird darauf nicht mit "Ja" geantwortet legen die Anrufer auf und es ist nicht so lustig ;-)


## Bekannte Probleme
Wenn der Anrufer sehr leise und das Callcenter sehr laut ist kann die ohnehin schwer hörgeschädigte Gewitteroma
mit aller Magie der Asterisk-Funktionen den Lärm nicht von der Stimme des Anrufers unterscheiden. Das führt dann
zu interessanten Fehlern, weil "WaitForSilence" dann in den angegebenen Timeout läuft.
Gleiches passiert auch, wenn der Anrufer minutenlang am Stück auf die arme Oma einzureden versucht.


## Wo sind die Audiodateien?
Die habe ich erstmal nicht mit ins Repository eingepflegt, da die Urheberrechtsfrage zur Verteilung etwas unklar ist.
Im Zweifel kann man sich aber selbst hinsetzen, sich die benötigten Schnipsel zusammensuchen und z.B. mit Audacity
zurechtschneiden und die Hintergrundgeräusche über die Rauschentfernung wegbekommen.
Man kann auch andere Snippets benutzen - wichtig ist bloß, dass der Eindruck für den Anrufer entsteht dass er in irgendeiner
Weise mit jemandem interagiert. Bei einer schwerhörigen Omma ist das nicht so ein Problem, anders wäre es z.B.
beim "Kleinen Nils" den ich bereits erwägte einzubauen. Da kann man halt nicht per Zufall irgendeine Antwort geben,
die müsste dann zur Frage des Callcenter-Menschen passen. Andererseits... So eine Frage nach "Verstehe ich nicht"
und "Was heißt denn das?" wäre ja schon durchaus einen Versuch wert... :-)


## Links
[1] https://wiki.asterisk.org/wiki/display/AST/Asterisk+11+Application_WaitForNoise
