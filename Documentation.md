Gruppe: SI-WS2022_Buck_Rinck_Mahmoudi_Lapp

# Documentation 

## Aufgabenstellung
Aufgabe ist es, mittels des Sprachassistenten Mycroft einen Kalender Skill umzusetzten, mit welchem man dazu in der Lage ist, Kalendereinträge zu erstellen, zu ändern und zu löschen. 
Der Skill besteht darin, einen neuen Termin anzulegen, alle Termine eines Tages, sowie den nächsten Termin auszugeben. Zudem einen Termin umzubenennen und einen Termin zu löschen. Für das Löschen des Termins wird eine Sicherheitsbestätigung benötigt, bevor der Kalendereintrag gelöscht werden kann. Dabei müssen gewisse Anforderungen beachtet werden. Beispielsweise die richtige Umwandlung eines Datums, wie 01.02.2022 in first of february twothousendtwentytwo, und umgekehrt.
Des Weiteren wurde ein Pflichten- und Lastenheft angelegt, welches die zu erfüllenden Anforderungen an dieses Projekt enthält. Ebenso enthalten sind ausgeschlossene Fuktionalitäten.
Außerdem müssen in dem Programm die Google Coding Styles zu mindestestens 50% erfüllt werden.
Zusätzlich haben wir versucht unseren Code recht übersichtlich zu halten, indem wir Code, welcher mehrmals genutzt wird, in einzelne Methoden auszulagern. Die Methoden und Variablen wurden mit eindeutigen Namen benannt. 

## Vorgehensweise

Zu Beginn ist das Pflichtenheft angelegt worden, um das Vorgehen und die zu erfüllenden Aufgaben zu strukturieren.
Es wurden genauen Befehle, welche durch den Skill möglich sind definiert, ebenso wie funktionale und nicht funktionale Anforderungen. Darüber hinaus haben ist darin festgelegt, welche Funktionalitäten ausgeschlossen sind. Des weiteren wurde eine genauere Implementierung der Zeitzonen angelegt. Das bedeutet, es werden nur Termine nach der Zeit angelegt und ausgegeben, die der aktuellen Zeitzone zugehörig sind. Zudem wird nicht unterschieden, mit welcher Stimme ein Befehl mitgegeben wird und ob die Person tatsächlicher Inhaber des Kalenders ist.
Im Anschluss wurde der Skill, sowie das GitHub Repository angelegt. Nachdem eine Verbindung zu dem CalendarSkill bestand, wurden die einzelnen Befehle implementieren. Bei aufkommenden Fehlern haben wir, mit Hilfe der skills.log nach der Ursache gesucht und diese behoben.
Als alle Befehle fehlerfrei funktionierten, haben wir den Code überarbeitet, sodass dieser den Google Coding Styles entspricht.

## Mycroft Skill anlegen

Zuerst muss der Befehl ```pip install msk``` und danach ```msk create``` ins Terminal von dem Rasberry PI eingegeben werden, um einen neuen Skill zu erstellen. Falls man GitHub als Version Control System nutzen möchte, muss dann der eigene GitHub Benutzername eingegeben werden. Zudem muss der gewünschte Name für den Skill gewählt werden. Die Erstellung eines Skills kann man nochmal genauer unter diesem Link finden https://mycroft-ai.gitbook.io/docs/mycroft-technologies/mycroft-skills-kit. <br>
Optional können bereits beispielhafte Befehle eingegeben werden, auf welche Mycroft reagieren soll. Ebenso kann ein personalisiertes Icon für den Skill erstellt werden.<br>
Wenn das gemacht ist, müssen die Kategorien ausgewählt werden, in die der Skill fällt. Zudem muss eine Lizenz gewählt werden, um fortfahren zu können.<br>
Daraufhin kann man automatisch ein GitHub Repository anlegen lassen. Hierfür muss man in dem erstellten Repository einen Access Token generieren lassen. Dieser muss in der Kommandozeile eingegeben werden.(repo token)
### GitHub und Skill erstellt
Um eine SSH Verbindung herzustellen wird die IP-Adresse des Rasberry Pi benötigt. Diese lässt sich herausfinden über den Befehl `ifconfig` herausfinden. Man kann nun in die Kommandozeile oder in Visual Studio Code `pi@ip-adresse` eingeben und die Verbindung zum Rasberry Pi wird nach der Eingabe des korrekten Passworts aufgebaut. 

## Erläuterung des Konzepts der Implementierung des Kalenderskills 

### Erklärung Methoden

Um die Verbindung zwischen unserem Skill und einem Kalender zu schaffen, haben wir die caldav library genutzt, welche unter folgenden Link zu finden ist https://github.com/python-caldav/caldav. Die hier erkläreten Methoden führen die mit Hilfe von caldav die nötigen Aktionen zur Veränderung und Abfrage von Kalendereinträgen durch. Die Methoden werden in den entsprechenden Handler Methoden aufgrufen und die nötigen Informationen aus der Spracheingabe werden mitgegeben. 

Um die Verbindung mit einem Kalender herzustellen, haben wir die `connect()` Methode implementiert. Der return-Wert ermöglicht später den Zugriff auf den Kalender.

```python
def connect(self):
        client = caldav.DAVClient(url=self.url, username=self.username, password=self.password)
        principal = client.principal()
        return principal
```

Da wir für mehrere Methoden die verschiedenen Termine eines Kalenders nutzen, haben wir eine Methode implementiert, welche alle Termine eines Kalenders zurückgibt.

```python
def get_all_appointments(self):
        principal = self.connect()
        calendars = principal.calendars()
        all_events = calendars[1].events()
        return all_events
```

Um das nächste Event ausgeben zu können, müssen zunächst alle Events des Kalenders ermittelt werden, auch die aktuelle Zeit und das aktuelle Datum müssen gegeben sein. Nun kann man alle Events durchgehen und die relevanten Informationen (Name, Startzeit und Datum, Endzeit) für die Ausgabe in eine neue Liste speichern, aber nur von den Events welche in der Zukunft liegen. Zum Schluss sortieren wir die Liste, sodass das nächste Event an erster Stelle der Liste steht. Auch beachtet diese Methode, dass es womöglich keinen nächsten Termin gibt. 

```python
def get_next_appointment(self):
        all_events = self.get_all_appointments()
        all_appointments = []
        tz = get_local_timezone()
        current_time = tz.localize(datetime.today())
        if len(all_events) == 0:
            return "No events"
        for e in all_events:
            start_time = e.vobject_instance.vevent.dtstart.value
            end_time = e.vobject_instance.vevent.dtend.value
            name = e.vobject_instance.vevent.summary.value
            if not isinstance(start_time, datetime):  # Termin geht den ganzen Tag
                start_time = datetime.combine(start_time, datetime.min.time())
                start_time = tz.localize(start_time)
                if start_time >= current_time:  # nur Termin die in der Zukunft liegen
                    all_appointments.append({'name': name, 'start': start_time, 'all_day': True})
            else:
                if start_time >= current_time:  # nur Termin die in der Zukunft liegen
                    all_appointments.append({'name': name, 'start': start_time, 'end': end_time, 'all_day': False})
        if len(all_appointments) == 0:
            return "No events in the future"
        sorted_appointments = sorted(all_appointments, key=lambda t: t['start'])
        return sorted_appointments[0]
```


Um alle Events an einem gegebenen Datum auszugeben, werden nun wieder alle Events des Kalenders durchgegangen und die Events an dem gegebenen Datum in eine neue Liste hinzugefügt und zurückgegeben. So kann nicht nur ein Event an dem Tag ausgegeben werden, sondern eben alle an dem gegebenen Tag.

```python
def get_all_appointments_on_a_specific_date(self, day, month, year):
        all_events = self.get_all_appointments()
        year, month, day = convert_word_date_to_number_date(day, month, year)
        tz = get_local_timezone()
        new_date = str(tz.localize(datetime(year, month, day))).split(" ")
        appointments = []
        for e in all_events:
            actual_date = str(e.vobject_instance.vevent.dtstart.value).split(" ")
            if actual_date[0] == new_date[0]:
                if len(actual_date) == 1:
                    appointments.append(
                        {'name': e.vobject_instance.vevent.summary.value, 'all_day': True})
                else:
                    appointments.append(
                        {'name': e.vobject_instance.vevent.summary.value,
                         'start': e.vobject_instance.vevent.dtstart.value,
                         'end': e.vobject_instance.vevent.dtend.value, 'all_day': False})
        return appointments
```

Die unten gezeigte Methode kann einen bestehenden Termin, welcher mit Namen und Datum eingegeben werden muss umbennenen.
Es werden wieder alle Events nach einem Event durchsucht, welches den entsprechenden Namen und Datum hat. Wenn kein solches Event vorhanden ist, wird dies dem Nutzer entsprechend mitgeteilt

```python
def rename_appointment(self, old_name, new_name, day, month, year):
        all_events = self.get_all_appointments()
        year, month, day = convert_word_date_to_number_date(day, month, year)
        tz = get_local_timezone()
        new_date = str(tz.localize(datetime(year, month, day))).split(" ")
        for e in all_events:
            actual_date = str(e.vobject_instance.vevent.dtstart.value).split(" ")
            if str(e.vobject_instance.vevent.summary.value) == old_name and actual_date[0] == new_date[0]:
                e.vobject_instance.vevent.summary.value = new_name
                e.save()
                return True
        return False
```

Um einen neuen Termin zu erstellen, gibt der Nutzer ein Datum, Startzeit, Endzeit und den gewünschten Namen ein. Wenn der Nutzer einen Ganztagestermin erstellt, muss keine Startzeit und Endzeit mitgegeben werden, sondern gesagt werden, dass es sich um einen Ganztagestermin handelt. 

```python
def create_new_appointment(self, name, day, month, year, start_time, end_time):
        principal = self.connect()
        calendars = principal.calendars()
        calendar_si = calendars[1]
        tz = get_local_timezone()
        year, month, day = convert_word_date_to_number_date(day, month, year)
        h_start, mi_start = convert_word_time_to_number_date(start_time)
        h_end, mi_end = convert_word_time_to_number_date(end_time)
        start_time_date = tz.localize(datetime(year, month, day, h_start, mi_start))
        end_time_date = tz.localize(datetime(year, month, day, h_end, mi_end))
        calendar_si.save_event(dtstart=start_time_date, dtend=end_time_date, summary=name)
```

Nach der Konfirmation, das der Nutzer den gegebenen Termin wirklich löschen möchte, wird dies durch die untern angegebende Methode durchgeführt. Auch hier muss der Nutzer einen Namen und ein Datum bei der Eingabe des Befehls angeben um den entsprechenden Termin löschen zu können. Auch hier werden alle Events durchgegagen und das Event mit dem gegebenen Namen und Datum rausgesucht. 

```python
def delete_appointment_by_name_and_time(self, name, day, month, year):
        all_events = self.get_all_appointments()
        year, month, day = convert_word_date_to_number_date(day, month, year)
        tz = get_local_timezone()
        new_date = str(tz.localize(datetime(year, month, day))).split(" ")
        for e in all_events:
            actual_date = str(e.vobject_instance.vevent.dtstart.value).split(" ")
            if e.vobject_instance.vevent.summary.value == name and actual_date[0] == new_date[0]:
                e.delete()
                return True
        return False
```

### Dialog Dateien

Die Dialog Dateien befinden sich in dem Ordner `/locale/en-us`. Diese Dateien werden genutzt um den Nutzer entsprechende Antworten auf eine Spracheingabe zu geben. <br>
Beispiel Inhalt einer Dialog Datei (`get_next_appointment`): <br>
Your next appointment is {name} {date} <br>
Um der Ausgabe entsprechenden {name} {date} mitzuteilen, wird die unten gezeigte Funktion in der `__init__.py` genutzt. 
```python
self.speak_dialog('get_next_appointment',
                        {'name': name,
                        'date': date})
```


### Intent Dateien

Die Intent Dateien befinden sich auch in dem Ordner `/locale/en-us`. Die gespeicherten Sätze in den Intent Dateien, sind die Sätze mit denen ein Nutzer das System nutzen kann. {name} kann über `message.data.get('name'` in der `__init__.py` genutzt werden. <br>
Beispiel Inhalt einer Intent Datei: <br>
delete my appointment {day} {month} of {year} named {name} <br>


### __init__.py

In der `__init__.py` Datei befinden sich nicht nur die oben besprochenen Methoden, sondern auch die entsprechenden Hanlder Methoden. Die Handler Methoden verknüpfen die Dialog Dateien, Intent Dateien und die entsprechenden Methoden miteinander.  <br>

Zum Beispiel die Handle Methode von get_next_appointment(). 
Mit `@intent_file_handler` wird die entsprechende Intent Datei ausgewählt. In der Methode wird die `get_next_appointment()` Methode ausgegeben und anhand des return Werts der Methode die passende Dialog Datei ausgewählt. Wenn der nächste Termin den ganzen Tag geht wird der Inhalt der `get_next_appointment_all_day.dialog` Datei ausgegeben. 

```python
@intent_file_handler('get_next_appointment.intent')
def handle_get_next_appointment(self, message):
    appointment = self.get_next_appointment()
    if not appointment['all_day']:
        self.speak_dialog('get_next_appointment',
                              {'day': date_d,
                               'month': date_m,
                               'year': date_y_num,
                               'time': start_time,
                               'name': name})
    else:
        self.speak_dialog('get_next_appointment_all_day',
                              {'day': date_d,
                               'month': date_m,
                               'year': date_y_num,
                               'name': name})
```

### Zeitkonvertierung

Um die eingegebenen Daten und Zeiten in ein Datum zu konvertieren, implementierten wir `convert_word_date_to_number_date()` und `convert_word_time_to_number_date()`. 

<br> <br>
`convert_word_date_to_number_date()` wandelt ein Datum von first March of two thousand twenty three zu 1.3.2023 um 
```python
def convert_word_date_to_number_date(day, month, year):
    day_number = day_to_num(day.lower())
    month_number = month_to_num(month.lower())
    year_number = w2n.word_to_num(year)
    return year_number, month_number, day_number
```

`convert_word_time_to_number_date()` wandelt fifteen thirty zu 15:30 oder ten zu 10 um

```python
def convert_word_time_to_number_date(given_time):
    if given_time.find(" ") != -1:
        hour, minutes = given_time.split(" ")
        minutes_number = w2n.word_to_num(minutes)
        hour_number = w2n.word_to_num(hour)
    else:
        minutes_number = 0
        hour_number = w2n.word_to_num(given_time)
    return hour_number, minutes_number
```


