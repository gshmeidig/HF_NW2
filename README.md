## HF – NW2 GNS3 Labor 1

## Vorgehen

<p>Allgemeines Vorgehen, von Edge1 rückwerts verscuht IP und Hostname Ping</p> 

## Core1

<p>Vieleicht Flasch</p>

                ip dns set servers=8.8.8.8,8.8.4.4 allow-remote-requests=yes max-udp-packet-size=4096 query-server-timeout=2.000 query-total-timeout=10.000 cache-size=2048 cache-max-ttl=7d

## R1

<p>Ping funktioniert nicht. Routing erstellt</p>

                 ip route/add dst-address=0.0.0.0/0 gateway=10.103.64.5


## R2

<p>Port em0 Ip Angepasst, auf 10.103.64.10/30</p>

<p>Port em1 Ip Angepasst, auf 10.103.8.1/21 mit DHCP Aktiv von 10.103.8.2 - 10.103.15.254</p>




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

<p>Vorgenommene Konfiguration überprüfen</p>

                show ip interface brief

![Bild R3_showipinterfacebrief](Bilder/R3_showipinterfacebrief.png)

<p>IP Route erfasse</p>

                ip route 0.0.0.0 0.0.0.0 10.103.64.13

<p>alte IP Route erfasse</p>

                no ip route 0.0.0.0 0.0.0.0 10.100.64.13

copy
## Analyse SW1

### Vlan zu fehlenden Ports hinzufügen

<p>Dies wurde für die Ports g3/0, g3/1, g3/2 angepasst</p>


                R1# configure terminal
                R1(config)# interface g3/1
                R1(config-if)# switchport mode access
                R1(config-if)# switchport access vlan 10
                R1(config-if)# exit
                R1(config)# write memory

## Analyse SW2

### Vlan zu fehlenden Ports hinzufügen

<p>Dies wurde für die Ports g3/3, g3/1, g3/2 angepasst</p>


                R1# configure terminal
                R1(config)# interface g3/1
                R1(config-if)# switchport mode access
                R1(config-if)# switchport access vlan 10
                R1(config-if)# exit
                R1(config)# write memory

### Interface Starten

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

<p>Vorgenommene Konfiguration überprüfen</p>

![Bild SW2_showipinterfacebrief](Bilder/SW2_showipinterfacebrief.png)

<p>Geänderte Configuration speichern, damit nicht bei einem Neustart alles neu konfiguriert werden muss </p>

                copy running-config startup-config

## Analyse SW3

### Spanning Tree Deaktivierung

<p>In Admin Modus wechseln: </p>

                en
                
<p>In die Konfig wechseln: </p>

                conf t
                
<p>In jeweiligen Port wechseln (wir haben spanning tree bei den Ports g3/0 - g3/3 deaktiviert): </p>

                g3/1
                
<p>Spanning-Tree Deaktivieren: </p>

                no spanning-tree portfast edge

<p> </p>




## Analyse SW4

### Vlan zu fehlenden Ports hinzufügen

<p>Dies wurde für die Ports g3/3, g3/1, g3/2 angepasst</p>


                R1# configure terminal
                R1(config)# interface g3/1
                R1(config-if)# switchport mode access
                R1(config-if)# switchport access vlan 10
                R1(config-if)# exit
                R1(config)# write memory

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

<p>Interface 3/1 auswählen</p>

                interface g3/1

<p>Port Starten</p>

                no shut

<p>Interface 3/2 auswählen</p>

                interface g3/2

<p>Port Starten</p>

                no shut

<p>Interface 3/3 auswählen</p>

                interface g3/3

<p>Port Starten</p>

                no shut
                
<p>Vorgenommene Konfiguration überprüfen</p>

![Bild SW4_showipinterfacebrief](Bilder/SW4_showipinterfacebrief.png)

<p>Geänderte Configuration speichern, damit nicht bei einem Neustart alles neu konfiguriert werden muss </p>

                copy running-config startup-config
