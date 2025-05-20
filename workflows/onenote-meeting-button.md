# OneNote Meeting-Button

**Ein Klick, neue Meeting-Notiz mit aktuellem Datum und Überschrift in OneNote – ready für deine Bulletpoints!**

## Anleitung

1. Power Automate öffnen: [https://make.powerautomate.com/](https://make.powerautomate.com/)
2. Flow-Typ: „Sofortiger Cloud-Flow“ (Button)
3. Aktion: „Seite in einem Abschnitt erstellen (V2)“ in OneNote
4. Titel: `JF Nico – @{utcNow('dd.MM.yyyy')}`
5. Inhalt: Bulletpoint-Vorlage

---

1️⃣ Gehe zu Power Automate
Flow-Typ: „Sofortiger Cloud-Flow“ (Button)

2️⃣ Aktion hinzufügen
„Seite in einem Abschnitt erstellen (V2)“

Abschnitt: z. B. „Jour Fixe“

Titel: JF Nico – @{utcNow('dd.MM.yyyy')}

Inhalt:
<h2>JF Nico – @{utcNow('dd.MM.yyyy')}</h2>
<ul><li></li><li></li><li></li></ul>

3️⃣ Flow speichern, testen und Button verwenden

📊 Visualisierung
[Button drücken]
      ↓
[OneNote-Seite "JF Nico – 22.05.2025" wird erstellt]
      ↓
[Meeting starten, Notizen machen]
