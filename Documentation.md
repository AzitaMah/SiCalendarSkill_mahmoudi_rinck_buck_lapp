Gruppe: SI-WS2022_Buck_Rinck_Mahmoudi_Lapp

# Documentation 

## Aufgabenstellung
Aufgabe ist es, mittels des Sprachassistenten Mycroft einen Kalender Skill umzusetzten, mit welchem man dazu in der Lage ist, Kalendereinträge zu erstellen ändern und löschen. 
Der Skill besteht darin, einen neuen Termin anzulegen, alle Termine eines Tages, sowie den nächsten Termin auszugeben. Zudem einen Termin umzubenennen und einen Termin zu löschen. Für das Löschen des Termins wird eine Sicherheitsbestätigung benötigt, bevor der Kalendereintrag gelöscht werden kann. Dabei müssen gewisse Anforderungen beachtet werden. Beispielsweise die richtige Umwandlung eines Datums, wie 01.02.2022 in first of february twothousendtwentytwo, und umgekehrt.
Des Weiteren wurde ein Pflichten- und Lastenheft angelegt, welches die zu erfüllenden Anforderungen an dieses Projekt enthält. Ebenso enthalten sind ausgeschlossene Fuktionalitäten.
(die Regelung für Termineinrichtungen in einer neuen Zeitzone ist beispielsweise darin definiert.)
Außerdem müssen in dem Programm die Google Coding Styles zu mindestestens 50% erfüllt werden.

-clean code

## Vorgehensweise
Zu Beginn haben wir das Pflichtenheft angelegt, um somit das Vorgehen und die zu erfüllenden Aufgaben zu strukturieren.
Es wurden die genauen Befehle, welche durch den Skill möglich sind definiert, ebenso wie funktionale und nicht funktionale Anforderungen. Darüber hinaus haben wir festgelegt, welche Funktionalitäten wir ausschließen. Dazu gehört eine genauere Implementierung der Zeitzonen. Das bedeutet, es werden Termine nur nach der Zeit angelegt und ausgegeben, die nach der aktuellen Zeitzone gilt. Zudem wird nicht unterschieden, mit welcher Stimme ein Befehl gegeben wird und ob die Person tatsächlicher Inhaber des Kalenders ist.
Im Anschluss haben wir den Skill, sowie das GitHub Repository angelegt. Nachdem eine Verbindung zu dem CalendarSkill bestand, haben wir angefangen, die einzelnen Befehle zu implementieren. Bei aufkommenden Fehlern haben wir, mit Hilfe der skills.log nach der Ursache gesucht und diese behoben.
Als alle Befehle fehlerfrei funktionierten, haben wir den Code überarbeitet, sodass dieser den Google Coding Styles entspricht.

## Mycroft Skill anlegen

## Eingesetzte Google Coding Styles
