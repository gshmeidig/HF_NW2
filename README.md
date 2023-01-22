## HF – NW2 GNS3 Labor 1

## Analyse SW2

<p> Status der Switch-Ports abrufen um zu schauen welche Ports den Status "Down" haben.</p>
                show ip interface brief
![Bild SW2_showipinterfacebrief](Bilder/SW2_showipinterfacebrief.png)

<p>In Admin Modus wechseln</p>
                en

<p>Konfiguration aufrufen und mit "t" den Terminal-Modus auswählen.</p>
                conf t

<p>Interfaces 3/0 auswählen</p>
                interface g3/0

<p>Port Starten</p>
                no shut
