# OneNote Meeting-Button

**Ein Klick, neue Meeting-Notiz mit aktuellem Datum und Überschrift in OneNote – ready für deine Bulletpoints!**

## Anleitung

1. Power Automate öffnen: [https://make.powerautomate.com/](https://make.powerautomate.com/)
2. Flow-Typ: „Sofortiger Cloud-Flow“ (Button)
3. Aktion: „Seite in einem Abschnitt erstellen (V2)“ in OneNote
4. Titel: `JF Nico – @{utcNow('dd.MM.yyyy')}`
5. Inhalt: Bulletpoint-Vorlage

---

## Visualisierung

![OneNote Meeting Button Flow](../img/onenote-button.png)
