Gruppe: SI-WS2022_Buck_Rinck_Mahmoudi_Lapp

# Pflichtenheft

## Einleitung
Im Auftrag des Kunden Prof. Dr. Christian Becker-Asano werden diverse Aufgaben mittels dem Sprachassistenten MyCroft umgesetzt. 
MyCroft ist eine Open Source Software, die als virtueller Assistent agiert und durch Spracheingaben gesteuert wird.
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
- MyCroft soll auf Nachfrage alle Termine am gewünschten Tag ausgeben.
- Durch ein Sprachkommando soll ein neuer Termin angelegt, sowie umbenannt werden können.
- Ein bestehender Termin soll nach einer Sicherheitsbestätigung durch Sprachaufforderung gelöscht werden können.
- Bei fehlerhaften Anfragen soll dem Nutzer ein entsprechendes Feedback gegeben werden. 

### Beispielhafte Anfragen:


**How to enter a date**
{day} of {month} in {year}: first of March in two thousand twenty three

**How to enter a time**
{time} o'clock: teen

**Nächster Termin:**
- U: What's my next appointment? 
- M: Your next appointment is {name} and will take place on the {day} {month} of {year} and starts at {time}

**Termine an bestimmtem Tag**
- U: What are my appointments on the {day} {month} of {year} ? 
- M: You don't have any appointments on this day. 
- M: You have the following appointments on this date
     {name} starting at {start_time} and ending at {end_time}
     {name} all day long

**Neuen Termin anlegen**
- U: Create an appointment on the {day} {month} of {year} named {name} starting at {start_time} and ending at {end_time}
- M: I created a new appointment called "name" on the {day} {month} of {year} starting at {start_time}

**Bestehenden Termin umbenennen**
- U: rename my meeting on the {day} {month} of {year} called {old_name} to {new_name}
- M: I changed the name of your appointment on the {day} {month} of {year} called {old_name} to {new_name}

**Termin löschen**
- U: delete my meeting on the {day} {month} of {year} named {name}
- M: Do you really want to delete the appointment {name} on the {day} {month} of {year} ? To confirm type yes or no.
- U: Yes
- M: I deleted your appointment on the {day} {month} of {year} called {name}

**Fehlerhafte Anfrage**
- U: "wrong request"
- M: I didn't understand that. Please repeat your request.
User versucht nicht bestehenden Termin zu löschen:
- M: I can't delete the appointment {name} on the {day} {month} of {year}

Anmerkungen zu den Anfragen:
- Das Jahr muss beim Abfragen, Angeben oder Erstellen eines Termins, immer mitgeteilt werden.
- Beim Erstellen eines Termines kann nur die Stunde angegeben werden. Eine zusätzliche Minutenangabe ist nicht möglich.
- Termine, die in der Vergangenheit liegen, können gelöscht werden. Es können Termine an jedem beliebigen Datum angelegt oder umbenannt werden, da keine entsprechenden Begrenzungen implementiert wurden.  
- Für Ganztagestermine wird die Uhrzeit des Termins auf 0:00 bis 24:00 festgelegt. Wird nach dem nächsten Termin gefragt, und an dem Tag befinden sich ein normaler und ein Ganztagestermin, wird daher der Ganztagestermin ausgegeben.
- Mit tzlocal.get_localzone() fragt das Programm automatisch die lokale Zeitzone ab. Wenn ein Termin angelegt wird, wird er anhand der aktuellen Zeitzone angelegt.




## Nicht-funktionale Anforderungen
- Laufzeit: MyCroft soll in kürzester Zeit den Skill ausführen
- MyCroft reagiert auf verschiedene Abwandlungen der Spracheingabe für bessere Interaktion
- Datenschutz: Man kann nicht über Spracheingabe auf den Kalender von anderen Personen zugreifen
- Die Bedienung des Programms soll simple und verständlich gestaltet werden.
- Das Programm soll so entwickelt werden, dass es änderbar und somit wartbar ist. 
- Netzwerkanschluss


## Ausgeschlossene Funktionalität ("future work")

Aus Sicherheitsgründen sollte der Besitzer des Kalenders nur mit seiner eigenen Stimme Veränderungen im Kalender vornehmen dürfen und Termine abfragen dürfen. Dadurch soll vermieden werden, dass fremde Person durch rein sprachliche Kommandos Zugriff auf den Kalender haben. 
Der Nutzer kann somit zum einen über die Webseite von NextCloud seine Termine steuern, aber auch über die Stimme, welche vorher authentifiziert werden muss. 
Zudem ist die Erstellung eines Termins nur für die Zeitzone gedacht, in der sich der Nutzer aktuell befindet. Falls ein Nutzer einen Termin erstellen möchte, der nicht in seiner Zeitzone stattfindet, wird die Zeit nach der aktuellen Zeitzone angegeben.
Weiterhin soll die Möglichkeit bestehen, Termine nicht nur zur vollen Stunde anzulegen. Uhrzeiten wie 10:30 sollen bei der Terminerstellung ebenfalls möglich sein.

Die Google Coding Guidlines wurden mit Pylint kontrolliert und angewendet. Der Code wird momentan von Pylint mit einem Score 9,18/10 bewertet.


## Zeit- und Personalplanung

### Zeitplanung

November:
- MyCroft über den Computerbildschirm nutzen, um verschiedene vorgegebene Funktionen auszuprobieren. 
- IP-Adresse herausfinden ohne den Raspberry-Pi am Computer Bildschirm anzuschließen. 
- Am Ende des Monats soll eine Verbindung über SSH mit dem Raspberry-Pi aufgebaut werden können. 
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
  - Google Coding Styles umsetzen

Abgabe 24.01.23


### Personalplanung
 
Zu Beginn haben wir alle zusammen gearbeitet, damit jeder wusste wie man den Raspberry-Pi benutzt. Jeder hat einen eigenen Skill implemetiert. Zum Schluss haben wir gemeinsam die Google Coding Styles umgesetzt.

Rollenverteilung:

Pflichtenheft, Dokumentation: Alle
- Anna: "Create new appointment" & "delete appointment"
- Alex: "Next appointment" & "appointment on a specific date", Sprachausgabe von Nummer (1) zu Wort(first), Umsetzung Google Coding Styles
- Azita: "Delete appointment", beispielhafte Termine erstellt
- Julia: Implementierung Verbindungsaufbau zu NextCloud Kalender, "rename appointment", Spracheingabe von Wort(first) zu Nummer (1)
