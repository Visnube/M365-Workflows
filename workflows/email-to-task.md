# E-Mail zu Task Automatisierung

**Mails mit Aufgaben/Deadlines werden automatisch als Aufgaben gespeichert und als Teams-Reminder angezeigt.**

## Anleitung

1. **Trigger:** Neue E-Mail im Posteingang (mit Schlüsselwort im Betreff, z. B. "Task", "Deadline", "Fällig")
2. **Aktion:** Aufgabe/Deadline aus Mailtext extrahieren
3. **Duplikate prüfen:** Gibt es den Task schon? → Nur neue Aufgaben übernehmen
4. **Speichern:** Aufgabe an Excel/Planner/To Do senden
5. **Teams-Reminder:** Reminder an dich (Chat/Kanal)

---

1️⃣ Trigger: Outlook – „When a new email arrives“
Filter: Betreff enthält „Task“, „Deadline“, „Fällig“

Optional: Bestimmte Absender

2️⃣ Extrahiere Aufgabe/Deadline
Betreff und Inhalt der Mail analysieren

In Variablen speichern

3️⃣ Check auf Duplikate
Suche in Excel/ToDo/Planner nach gleichem Task (z. B. per Betreff)

Wenn NEU → Aufgabe hinzufügen

4️⃣ Teams Reminder
„Post a message in Teams“: Reminder für alle neuen Tasks/Deadlines

Visualisierung
┌──────────────┐
│ Neue Mail    │
└─────┬────────┘
      ↓
[Extrahiere Task]
      ↓
[Check: Schon drin?]
      ↓
[Teams Reminder senden]
