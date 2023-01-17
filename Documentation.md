Gruppe: SI-WS2022_Buck_Rinck_Mahmoudi_Lapp

# Documentation 

## Aufgabenstellung
Aufgabe ist es, mittels des Sprachassistenten Mycroft einen Kalender Skill umzusetzten, mit welchem man dazu in der Lage ist, Kalendereinträge zu erstellen ändern und löschen. 
Der Skill besteht darin, einen neuen Termin anzulegen, alle Termine eines Tages, sowie den nächsten Termin auszugeben. Zudem einen Termin umzubenennen und einen Termin zu löschen. Für das Löschen des Termins wird eine Sicherheitsbestätigung benötigt, bevor der Kalendereintrag gelöscht werden kann. Dabei müssen gewisse Anforderungen beachtet werden. Beispielsweise die richtige Umwandlung eines Datums, wie 01.02.2022 in first of february twothousendtwentytwo, und umgekehrt.
Des Weiteren wurde ein Pflichten- und Lastenheft angelegt, welches die zu erfüllenden Anforderungen an dieses Projekt enthält. Ebenso enthalten sind ausgeschlossene Fuktionalitäten.
Außerdem müssen in dem Programm die Google Coding Styles zu mindestestens 50% erfüllt werden.

-clean code

## Vorgehensweise

Zu Beginn ist das Pflichtenheft angelegt worden, um das Vorgehen und die zu erfüllenden Aufgaben zu strukturieren.
Es wurden genauen Befehle, welche durch den Skill möglich sind definiert, ebenso wie funktionale und nicht funktionale Anforderungen. Darüber hinaus haben ist darin festgelegt, welche Funktionalitäten ausgeschlossen sind. Des weiteren wurde eine genauere Implementierung der Zeitzonen implementiert. Das bedeutet, es werden nur Termine nach der Zeit angelegt und ausgegeben, die der aktuellen Zeitzone zugehörig sind. Zudem wird nicht unterschieden, mit welcher Stimme ein Befehl mitgegeben wird und ob die Person tatsächlicher Inhaber des Kalenders ist.
Im Anschluss wurde der Skill, sowie das GitHub Repository angelegt. Nachdem eine Verbindung zu dem CalendarSkill bestand, wurden die einzelnen Befehle implementieren. Bei aufkommenden Fehlern haben wir, mit Hilfe der skills.log nach der Ursache gesucht und diese behoben.
Als alle Befehle fehlerfrei funktionierten, haben wir den Code überarbeitet, sodass dieser den Google Coding Styles entspricht.

## Mycroft Skill anlegen

Zuerst muss der Befehl ```pip install msk``` und danach ```msk create``` eingegeben werden. Falls man GitHub als Version Control System nutzen möchte, muss dann der eigene GitHub Benutzername eingegeben werden. Zudem muss der gewünschte Name für den Skill gewählt werden.<br>
Optional können bereits beispielhafte Befehle eingegeben werden, auf welche Mycroft reagieren soll. Ebenso kann ein personalisiertes Icon für den Skill erstellt werden.<br>
Wenn das gemacht ist, müssen die Kategorien ausgewählt werden, in die der Skill fällt. Zudem muss eine Lizenz gewählt werden, um fortfahren zu können.<br>
Daraufhin kann man automatisch ein GitHub Repository anlegen lassen. Hierfür muss man in dem erstellten Repository einen Access Token generieren lassen. Dieser muss in der Kommandozeile eingegeben werden.(repo token)
### GitHub und Skill erstellt
Um eine SSH Verbindung herzustellen wird die IP-Adresse des Rasperry Pi benötigt. Diese lässt sich herausfinden über den Befehl ```ifconfig``` herausfinden.


## Eingesetzte Google Coding Styles
