# Essensklingel mit Home Assistant und ESPhome
## Was ist der Anlass?
Mein Büro ist ein gutes Stück von der Küche und Wohnzimmer entfernt und durch mehrere Türen abgetrennt. Ist das Essen fertig oder man braucht meine Hilfe musste man vorher durch das ganze Haus schreien und selbst das ist nicht immer erfolgreich.
Dann kam mir die Idee eines Tasters den man in der Küche drückt und daraufhin sich mein Smarthome bei mir bemerkbar macht. Der Fake Alarm ist für die Zeiten wo es kein Essen gibt, aber man trotzdem nach mir rufen würde. Dieser ist bei mir limitiert auf zweimal pro Tag!
Ich habe am gleichen Microcontroller auch noch ein Helligkeitssensor und einen Bewegungssensor die zu der Beleuchtung der Küche gehören. Auf die gehe ich hier aber nicht weiter ein.
## Ablauf der Automation
### Essensklingel (Einmal drücken):
1. Einmal Taster drücken
2. Lichter flashen
3. Ansage "Essen ist fertig" über Google Home Minis
4. Smartphone und Tablet Benachrichtigung "Essen ist fertig!"
 ### Fake Alarm (Zweimal drücken):
1. Zweimal Taster drücken
6. Abfrage ob Counter < 2 wenn nicht Abbruch
7. Lichter flashen
8. Ansage "Fake Alarm" über Google Home Minis
9. Smartphone und Tablet Benachrichtigung "Fake Alarm!
10. Counter wird um eins erhöht

## Was wird vorausgesetzt?
- Home Assistant Server
- Wemos D1 Mini
- Wemos D1 Mini Button Modul
- Smarte Lampen
- Google Home (Mini) (s)
- Basics im Umgang mit Home Assistant
	- Automatisierungen
	- Skripte
	- Helfer
	- Integrationen
- ESPhome Addon in HA installiert
- Man muss ESP8266 Microcontroller mit ESPhome flashen können
- Eventuell Lötkenntnisse

## Welche Technik wird verwendet?

- Als Kopf/Server läuft bei mir Home Assistant OS
- Der Taster ist ein Wemos D1 mini mit dem Button Modul und 3D gedrucktem Case von Thingiverse
- mit Home Assistant kompatible Lampen (bei mir Philips Hue)
- Google Home Minis zur Sprachausgabe
- Smartphone und Tablet für Benachrichtigung

## Hardware vorbereiten
1. Wemos D1 Mini mit Aufsteckmodul verbinden
2. Wemos D1 Mini mit ESPhome Software flashen um später OTA zu nutzen
3. Wemos D1 Mini in Case einbauen
![Wemos in Küche](https://github.com/FelixLenz-Code/Essensklingel-HA/blob/main/Bilder/Wemos%20in%20der%20Kueche.jpg?raw=true)

## Software vorbereiten (Entitys und Geräte Namen müssen eventuell geändert werden)
1. [Skripte](https://github.com/FelixLenz-Code/Essensklingel-HA/tree/main/Skripte) in HA importieren (Essensklingel & Fake Alarm)
2. Fake Alarm Zähler ([Counter bei Helfern in HA](https://www.home-assistant.io/integrations/counter/)) erstellen
![Fake Alarm Counter](https://github.com/FelixLenz-Code/Essensklingel-HA/blob/main/Bilder/Fake%20Counter%20Einstellungen.PNG?raw=true)
4. [Wemos config](https://github.com/FelixLenz-Code/Essensklingel-HA/blob/main/Wemos%20config/Kueche%20Wemos.yaml) in ESPhome integrieren und flashen
5. [Automatisierung zum Rücksetzen des Counters](https://github.com/FelixLenz-Code/Essensklingel-HA/blob/main/Automationen/Fake%20Alarm%20Counter%20taeglich%20zur%C3%BCcksetzen.yaml) importieren


## Fazit
Hoffentlich sollte diese coole Automation bei euch laufen. Wenn nicht schreibt mich hier gerne an oder kommentiert unter dem dazugehörigen Video (Link/Video folgt noch)!

LG Felix
