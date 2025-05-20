# 📣 Teams Reminder Workflow

Automatischer Reminder für offene Aufgaben direkt im Teams-Chat oder Kanal.

---

## 🛠️ Workflow-Überblick

```plaintext
[Trigger: Zeitplan] 
   ↓
[Check: Offene Tasks/Deadlines (Excel, Planner, OneNote...)]
   ↓
[Teams-Nachricht posten: Deine offenen Aufgaben werden automatisch angezeigt]

🔥 Step-by-Step auf einen Blick
1️⃣ Trigger einrichten
Gehe zu Power Automate

Wähle "Geplanter Flow"

Stelle z. B. ein: Montag-Freitag, 09:00 Uhr

2️⃣ Tasks abrufen
Tool	Aktion
Excel	„List rows present in table“: Liest alle offenen Tasks aus Tabelle
Planner	„List tasks“
OneNote	Optional: „Get page content“

3️⃣ Filter setzen
Bedingung: Fälligkeitsdatum <= heute UND Status offen

Power Automate: „Filter array“ oder bei Excel: Filter direkt in Aktion

4️⃣ Teams-Nachricht senden
plaintext
Kopieren
Bearbeiten
[Aktion: Post message in chat or channel]
→ Text z.B.:
Hallo Visnu, folgende Tasks sind fällig:
• Angebot XY (21.05.)
• Bestellung ABC (23.05.)
(Link zu Details)

🖼️ Visualisierung
┌─────────────┐
│ Trigger     │
│ (Schedule)  │
└─────┬───────┘
      ↓
┌─────────────┐
│ Tasks holen │
│ (Excel etc) │
└─────┬───────┘
      ↓
┌─────────────┐
│ Filtern     │
│ (nur offen) │
└─────┬───────┘
      ↓
┌─────────────┐
│ Teams Msg   │
│ (Reminder)  │
└─────────────┘
✅ Vorteile
Kein Task geht mehr verloren

Reminder kommt auch mobil in Teams-App

Kombinierbar mit jeder Task-Liste (Excel, Planner, ToDo)
