## HF – NW2 GNS3 Labor 1

## Analyse R3

<p>Status der Interfaces abrufen</p>

                show ip interface brief

![Bild R3_showipinterfacebrief_errors](Bilder/R3_showipinterfacebrief_errors.png)

<p>In Admin Modus wechseln mit:</p>

                en

<p>Konfiguration aufrufen und mit "t" den Terminal-Modus auswählen.</p>

                conf t

<p>Interface 0/0 auswählen</p>

                interface g0/0

<p>IP Adresse des Interfaces angepasst</p>

                ip address 10.103.64.14 255.255.255.252

<p>Vorgeneommene Konfiguration überprüfen</p>

                show ip interface brief

![Bild R3_showipinterfacebrief](Bilder/R3_showipinterfacebrief.png)

## Analyse SW1

## Analyse SW2

<p>Status der Switch-Ports abrufen um zu schauen welche Ports den Status "Down" haben.</p>

                show ip interface brief

![Bild SW2_showipinterfacebrief_errors](Bilder/SW2_showipinterfacebrief_errors.png)

<p>In Admin Modus wechseln mit:</p>

                en

<p>Konfiguration aufrufen und mit "t" den Terminal-Modus auswählen.</p>

                conf t

<p>Interface 3/0 auswählen</p>

                interface g3/0

<p>Port Starten</p>

                no shut

<p>Vorgeneommene Konfiguration überprüfen</p>

![Bild SW2_showipinterfacebrief](Bilder/SW2_showipinterfacebrief.png)

## Analyse SW3

## Analyse SW4

<p> Status der Switch-Ports abrufen um zu schauen welche Ports den Status "Down" haben.</p>

                show ip interface brief

![Bild SW2_showipinterfacebrief_errors](Bilder/SW4_showipinterfacebrief_errors.png)

<p>In Admin Modus wechseln mit:</p>

                en

<p>Konfiguration aufrufen und mit "t" den Terminal-Modus auswählen.</p>

                conf t

<p>Interface 3/0 auswählen</p>

                interface g3/0

<p>Port Starten</p>

                no shut

<p>Vorgeneommene Konfiguration überprüfen</p>

![Bild SW4_showipinterfacebrief](Bilder/SW4_showipinterfacebrief.png)