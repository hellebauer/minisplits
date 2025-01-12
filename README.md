Anbei eine HA Automation fuer meine Mitsubishi SRK/SRC  bzgl. Taktvermeidung. Funktioniert auch wahrscheinlich fuer Daikin, usw. 
Leider war es nicht moeglich Kommentare im YAML einzufuegen, weil HA diese sofort wieder entfernt..... 


Dieses Script ist ein Spin-off von [friedolin1](https://akkudoktor.net/u/friedolin1) .   Damit dieses Script funktioniert brauchst Du einen externen Raumtemperatursensor, welcher in HA sichtbar ist. Dieser sollte so im Raum plaziert sein dass er nicht von der Minisplit angeblasen wird.

* Passe Script folgendermassen an:
-Ersetzte [Gerät] mit deiner Klimaanlage (z.B. climate.ac_kueche) 
-Ersetzte [Solltemperaturregler] mit deinem Temperaturregler (z.B. input_number.solltemp_kueche)
-Ersetzte [Boolean] mit einem Helfer (z.B. input_boolean.boolkuechewarzuwarm)
-Ersetzte [RaumTemperaturSensor] mit deinem TemperaturSensor (z.B. sensor.zigbeekueche)

Beachte: Beim Ersetzen verschwinden die eckigen Klammern [  ] der Platzhalter.

* Die Klimaanlage wird nur hoch/runtergeregelt. Ein-/Ausschalten, Fan-Speeds, Eco-modes werden im Script nicht veraendert
* Wenn Raumtemperatur < Solltemperaturregler , dann wird SolltemperaturKlima=KlimaanlagenInnentemperatur gesetzt . Meine Klima heizt hiermit etwas flotter.
* Wenn Raumtemperatur > Solltemperaturregler  , dann wird (SolltemperaturKlima = KlimaanlagenInnentemperatur -2Grad)  gesetzt .  Meine Klima heizt dann mit kleinstmoeglicher Leistung (immer knapp vorm 'Abschalten'  ... man kann auch mal -2.2 oder -2.3 Grad probieren)
*  Wenn (Raumtemperatur > Solltemperaturregler +1.2Grad), dann wird SolltemperaturKlima=16 Grad gesetzt (niedriger geht nicht bei Mitsubishi). Die Klimaanlage regelt dann auf 'Fast 0' runter bis die Raumtemperatur wieder unter den Solltemperaturregler sinkt.

Die SolltemperaturKlima kann hierbei auch mal auf 25 / 26 Grad hochgehen, aber die Raumtemperatur (gemessen vom externen Temperatursensor), bleibt im Bereich  Solltemperaturregler (+1.2Grad)  
