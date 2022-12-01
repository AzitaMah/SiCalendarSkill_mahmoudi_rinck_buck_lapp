Gruppe: SI-WS2022_Buck_Rinck_Mahmoudi_Lapp

# Pflichtenheft

## Einleitung
Im Auftrag des Kunden Prof. Dr. Christian Becker-Asano werden diverse Aufgaben mittels dem Sprachassistenten MyCroft umgesetzt. 
MyCroft ist eine open source Software, die als virtueller Assistent agiert und durch Spracheingaben gesteuert wird.
Als Hardware wird ein Raspberry-Pi verwendet, welcher für die Sprachausgabe an einen Lautsprecher angeschlossen ist.
Zudem ist er mit einer Webcam verbunden, welche als Mikrofon dient.
Unter den Aufgabenbereich fällt die Implementierung eines Kalender-Skills. 
Dieser besitzt die Fähigkeit, alle Termine eines bestimmten Tages, sowie den nächsten Termin nach Anfrage auszugeben.
Des Weiteren werden Zusatzaufgaben umgesetzt. 
Diese bestehen darin über ein Sprachkommando einen neuen Termin anzulegen, umzubenennen und einen bestehenden Termin nach einer Sicherheitsbestätigung des Nutzers zu löschen.


## Auftrag

Das Projekt wird im Rahmen Speech Interaction bei Prof. Dr. Christian Becker-Asano durchgeführt.


## Funktionale Anforderungen

- MyCroft soll auf Nachfrage den nächsten Termin ausgeben.
- MyCroft soll auf Nachfrage alle Termine am nachgefragten Tag ausgeben.
- Durch ein Sprachkommando soll ein neuer Termin angelegt, sowie umbenannt werden können.
- Ein bestehender Termin soll nach einer Sicherheitsbestätigung durch Sprachaufforderung gelöscht werden können.
- Bei fehlerhaften Anfragen soll dem Nutzer ein entsprechendes Feedback gegeben werden. 

## Nicht-funktionale Anforderungen
- Laufzeit: MyCroft soll in kürzester Zeit den Skill ausführen
- MyCroft reagiert auf verschiedene Abwandlungen der Spracheingabe für bessere Interaktion
- Datenschutz: Man kann nicht über Spracheingabe auf den Kalender von anderen Personen zugreifen
- Die Bedienung des Programms soll simple und verständlich gestaltet werden.
- Das Programm soll so entwickelt werden, dass es änderbar und somit wartbar ist. 
- Netzwerkanschluss


## Ausgeschlossene Funktionalität ("future work")

- Aus Sicherheitsgründen sollte der Besitzer des Kalenders nur mit seiner Stimme Veränderungen im Kalender vornehmen dürfen und Termine abfragen dürfen.  


## Zeit- und Personalplanung

### Zeitplanung

November:
- MyCroft über den Computerbildschirm nutzen, um verschiedene vorgegebene Funktionen auszuprobieren. (check)
- IP-Adresse herausfinden ohne den Raspberry-Pi am Computer Bildschirm anzuschließen. (check)
- Am Ende des Monats soll eine Verbindung über SSH mit dem Raspberry-Pi aufgebaut werden können. (check)
- MyCroft über SSH Verbindung mit dem Laptop nutzen. 
- Ein Template für einen eigenen Skill in MyCroft erstellen und den Raspberry-Pi mit GitHub verbinden.

Dezember
- Mit dem Programmieren eines eigenen Kalender-Skills anfangen.
  - Nach dem nächsten Termin fragen können.
  - Alle Termine eines bestimmten Tages abfragen.
- Wenn zeitlich realisierbar mit der Bonusaufgabe anfangen.

Januar:
- Bonusaufgabe fertigstellen.
  - Einen neuen Termin per Sprachkommando anlegen.
  - Einen bestehenden Termin per Sprachkommando umbenennen.
  - Einen bestehenden Termin per Sprachkommando nach Sicherheitsbestätigung durch den Nutzer löschen.

Abgabe 24.01.23


### Personalplanung
 
Für die genaue Aufteilung der Rollen müssen vorerst alle Punkte im November abgeschlossen sein.
Zu Beginn arbeiten alle Mitglieder zusammen, damit jeder weiß wie man den Raspberry-Pi benutzt und eine spätere Aufgabenverteilung möglich ist. 

(spätere) Rollenverteilung: 
- Anna:
- Alex:
- Azita:
- Julia:
