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

### Beispielhafte Anfragen:
**Nächster Termin:**
- U: Was ist mein nächster Termin? 
- M: Dein nächster Termin ist am "dd.mm.yyyy" und lautet "xy".

**Termine an bestimmtem Tag**
- U: Welche Termine habe ich am "dd.mm."? 
- M: An diesem Tag hast du keine Termine. 
- M: Dein Termin am "dd.mm." lautet "xy"

**Neuen Termin anlegen**
- U: Ich möchte am "dd.mm.yyyy" einen neuen Termin anlegen.
- M: Okay. Wie lautet dein Termin? 
- U: "Termin Name"
- M: Ist es ein Ganztagestermin?
- U: Nein.
- M: Wann beginnt der Termin?
- U: "hh:mm"
- M: Wann endet der Termin?
- U: "hh:mm"
- M: Ich habe einen Termin am "dd.mm." hinzugefügt von "Beginn" bis "Ende" mit dem Namen "Termin Name".

**Bestehenden Termin umbenennen**
- U: Ich möchte am "dd.mm." den Termin umbennenen.
- M: Okay. Wie soll der Termin heißen?

**Termin löschen**
- U: Termin am "dd.mm." löschen.
- M: Soll der Termin am "dd.mm." sicher gelöscht werden?
- U: Ja
- M: Der Termin wurde gelöscht.

**Fehlerhafte Anfrage**
- U: "fehlerhafte Anfrage"
- M: Das habe ich nicht verstanden. Kannst du es bitte wiederholen?
User versucht nicht bestehenden Termin zu löschen:
- M: es tut mir leid, aber am "dd.mm" besteht zur Zeit kein Termin, der gelöscht werden kann.

Anmerkungen zu den Anfragen:
- Wenn kein Jahr genannt wird, geht man vom aktuellen Jahr aus.
- Termine aus der Vergangenheit können gelöscht werden. Es können aber keine Termine in der Vergangenheit angelegt werden oder umbenannt werden. 
- Ganztagestermine werden so behandelt, dass die Uhrzeit des Termins auf 0:00 bis 24:00 festgelegt ist. Wenn die nächsten Termine also am nächsten Tag sind und einmal ein Ganztagestermin und ein Termin um 10:00 stattfinden, wird der Ganztagestermin als nächster ausgegeben.
-  Mit tzlocal.get_localzone() fragt das Programm automatisch die Lokale Zeitzone ab und passt den Kalender an die Lokale Zeitzone an. Wenn man nun einen Termin in Japan anlegt nach japanischer Zeit aber zum Zeitpunkt des Termins sich in Deutschland befindet, wird dieser Termin bei Abfrage automatisch zur entsprechenden deutschen Uhrzeit ausgegeben.




## Nicht-funktionale Anforderungen
- Laufzeit: MyCroft soll in kürzester Zeit den Skill ausführen
- MyCroft reagiert auf verschiedene Abwandlungen der Spracheingabe für bessere Interaktion
- Datenschutz: Man kann nicht über Spracheingabe auf den Kalender von anderen Personen zugreifen
- Die Bedienung des Programms soll simple und verständlich gestaltet werden.
- Das Programm soll so entwickelt werden, dass es änderbar und somit wartbar ist. 
- Netzwerkanschluss


## Ausgeschlossene Funktionalität ("future work")

Aus Sicherheitsgründen sollte der Besitzer des Kalenders nur mit seiner eigenen Stimme Veränderungen im Kalender vornehmen dürfen und Termine abfragen dürfen. 
Dadurch soll vermieden werden, dass fremde Person durch rein sprachliche Kommandos Zugriff auf den Kalender haben. 
Der Nutzer kann somit zum einen über die Webseite von NextCloud seine Termine steuern, aber auch über die Stimme, welche vorher authentifiziert werden muss.


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

Abgabe 24.01.23


### Personalplanung
 
Für die genaue Aufteilung der Rollen müssen vorerst alle Punkte im November abgeschlossen sein.
Zu Beginn arbeiten alle Mitglieder zusammen, damit jeder weiß wie man den Raspberry-Pi benutzt und eine spätere Aufgabenverteilung möglich ist. 

(spätere) Rollenverteilung: 
- Anna:
- Alex:
- Azita:
- Julia:
