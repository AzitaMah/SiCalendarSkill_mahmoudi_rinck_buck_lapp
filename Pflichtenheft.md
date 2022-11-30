Gruppe: SI-WS2022_Buck_Rinck_Mahmoudi_Lapp

# Pflichtenheft

## Einleitung
Im Auftrag des Kunden Prof. Dr. Christian Becker-Asano werden diverse Aufgaben mittels dem Sprachassistenten MyCroft umgesetzt. 
MyCroft ist eine open source Software, die als virtueller Assistent agiert und durch Spracheingaben gesteuert wird.
Als Hardware wird ein Raspberry-Pi verwendet, welcher für die Sprachausgabe an einen Lautsprecher angeschlossen ist.
Zudem ist er mit einer Webcam verbunden, welcher als Mikrofon dient.
Unter den Aufgabenbereich fällt die Implementierung eines Kalender-Skills. 
Dieser besitzt die Fähigkeit, alle Termine eines bestimmten Tages, sowie den nächsten Termin nach Anfrage auszugeben.
Des Weiteren werden Zusatzaufgaben umgesetzt. 
Diese bestehen darin einen neuen Termin anzulegen, umzubenennen und einen bestehenden Termin nach einer Sicherheitsbestätigung des Nutzers zu löschen.
Diese Zusatzaufgaben sollen alle über Sprachkommandos realisiert werden.


## Auftrag

Das Projekt wird im Rahmen Speech Interaction bei Prof. Dr. Christian Becker-Asano durchgeführt.


## Funktionale Anforderungen

- MyCroft soll auf Nachfrage den nächsten Termin ausgeben.
- MyCroft soll auf Nachfrage alle Termine am nachgefragten Tag ausgeben.
- Durch ein Sprachkommando soll ein neuer Termin angelegt, sowie umbenannt werden können.
- Ein bestehender Termin soll nach einer Sicherheitsbestätigung durch Sprachaufforderung gelöscht werden können.
- Bei fehlerhaften Anfragen soll dem Nutzer ein entsprechendes Feedback gegeben werden. 

## Nicht-funktionale Anforderungen
- Laufzeit -> MyCroft soll in kürzester Zeit den Skill ausführen
- MyCroft reagiert auf verschiedene Abwandlungen der Spracheingabe für bessere Interaktion
- Datenschutz -> man kann nicht über Spracheingabe auf Kalender von anderen Personen zugreifen
- Die Bedienung des Programms soll simple und verständlich gestaltet werden.
- Das Programm soll do entwickelt werden, dass es änderbar und somit wartbar ist. 
- Netzwerkanschluss


## Ausgeschlossene Funktionalität ("future work")

- Aus Sicherheitsgründen sollte der Besitzer des Kalenders nur mit seiner Stimme Veränderungen im Kalender vornehmen dürfen und Termine abfragen dürfen.  


## Zeit- und Personalplanung

### Zeitplanung

November:
- MyCroft nutzen über den Computerbildschirm, um verschiedene vorgegebene Funktionen auszuprobieren. (check)
- IP-Adresse ohne das Raspberry Pi am Computer Bildschirm anzuschließen herausfinden. (check)
- Am Ende des Monats soll eine Verbindung über SSH mit dem raspberryPi aufgebaut werden können. (check)
- MyCroft nutzen über SSH Verbindung mit Laptop. 
- Ein Template für einen eigenen Skills in MyCroft erstellen und das Raspberry Pi mit git verbinden.

Dezember
- mit dem Programmieren eines eigenen Kalender-Skill anfangen.
  - Nach dem nächsten Termin fragen können.
  - Alle Termine eines bestimmten Tages abfragen.
- wenn zeitlich machbar mit der Bonusaufgabe anfangen.

Januar:
- Bonusaufgabe fertigstellen.
  - Einen neuen Termin per Sprachkommando anlegen.
  - Einen bestehenden Termin per Sprachkommando umbenennen.
  - Einen bestehenden Termin per Sprachkommando nach Sicherheitsbestätigung durch den Nutzer löschen.

Abgabe 24.01.23


### Personalplanung
 
Für die genaue Aufteilung der Rollen müssen vorerst alle Punkte im November abgeschlossen sein.
Zu Beginn arbeiten alle Mitglieder zusammen, damit jeder weiß wie man das Raspberry Pi benutzt und eine spätere Aufgabenverteilung möglich ist. 

(spätere) Rollenverteilung: 
- Anna:
- Alex:
- Azita:
- Julia:
