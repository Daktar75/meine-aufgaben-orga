# Plan: Schluss mit den gelben Zetteln

## Ziel
Alle beruflichen To-Dos an **einem** Ort statt auf Zetteln am Schreibtisch:
- zeigt jeden Morgen, was **heute** dran ist,
- behält Unerledigtes sichtbar, bis es erledigt oder bewusst gestrichen ist,
- erinnert per Handy,
- am PC und auf dem Handy gleich, **komplett kostenlos**.

**Abgrenzung:** Feste Termine bleiben im Outlook-Kalender. Hier geht es nur um To-Dos.
**Speicherort:** Google Tasks im privaten Google-Konto.

---

## Die Regeln (wichtiger als das Tool)

| Regel | Was das heißt |
|---|---|
| **1. Kein neuer Zettel** | Jedes To-Do sofort ins Handy oder in den PC tippen. Der Zettelblock kommt in die Schublade. |
| **2. In 10 Sekunden erfassen** | Titel + Projekt, Datum nur wenn nötig. Sortiert wird später. |
| **3. Jedes To-Do hat ein Projekt** | Kürzel vorn im Titel, z. B. `[Alpha] Protokoll verschicken`. Alles ohne Projekt landet in „Eingang“. |
| **4. Nichts verschwindet** | Unerledigtes von gestern taucht oben unter „Liegen geblieben“ auf, bis du es erledigst, verschiebst oder bewusst löschst. |
| **5. Höchstens 3 Top-To-Dos pro Tag** | Der Rest heißt „wenn Zeit bleibt“. |
| **6. Erinnerung nur, wo nötig** | Uhrzeit nur setzen, wenn es wirklich zu einer Zeit passieren muss (Rückruf, Abgabe). |

**Datenschutz-Hinweis:** Da es ein privates Konto ist, nur Stichworte notieren (z. B. „Angebot Kunde B finalisieren“), keine vertraulichen Inhalte, Zahlen oder Personendaten.

---

## Der Tagesablauf

| Wann | Dauer | Was |
|---|---|---|
| **Morgens** | 3 Min | Ansicht „Heute“ öffnen → Liegengebliebenes auf heute/morgen schieben oder streichen → 3 Top-To-Dos markieren |
| **Tagsüber** | Sekunden | Statt Zettel: Handy oder PC, Plus-Knopf, tippen, fertig |
| **Feierabend** | 2 Min | Offenes verschieben oder streichen, Eingang leeren |
| **Freitag** | 10 Min | Alle Projekte durchgehen: Was hängt? Was ist erledigt? |

---

## Umsetzung in zwei Stufen

### Stufe 1 – Sofort, mit der Google-Tasks-App (heute, 30 Min)
- [ ] Google-Tasks-App aufs Handy (Android/iOS), Benachrichtigungen erlauben
- [ ] Am PC: Google Tasks ist in Gmail/Google Kalender rechts in der Seitenleiste, oder direkt unter tasks.google.com
- [ ] Listen anlegen: **Eingang** + eine Liste je aktivem Projekt
- [ ] **Zettel-Ablöse:** alle gelben Zettel einmal abtippen. Abkürzung: Zettel fotografieren, Foto hier im Chat hochladen, Claude macht daraus eine fertige Liste mit Projekt-Kürzeln zum Abtippen.
- [ ] Zettel wegwerfen

Damit ist das Kernproblem schon gelöst. Die Lücke von Google Tasks: Es gibt **keine gemeinsame „Heute“-Ansicht über alle Listen**, Überfälliges ist nur klein rot markiert und Top 3 gibt es nicht. Das schließt Stufe 2.

### Stufe 2 – Eigenes Cockpit „Heute“ (2–3 Sitzungen)
Eine kleine Web-App, die auf **dieselben Google-Tasks-Daten** zugreift, nur mit besserer Oberfläche (siehe Entwurf):
- [ ] Anmeldung mit dem privaten Google-Konto (Google-Cloud-Projekt, Tasks-Schnittstelle, kostenlos)
- [ ] Ansicht „Heute“: Liegen geblieben · Top 3 · Wenn Zeit bleibt, über alle Listen hinweg
- [ ] Ein Klick: „→ Heute“, „→ Morgen“, „Erledigt“, „★ Top“
- [ ] Schnell-Eingabe: `Angebot schicken #KundeB morgen 15:00` → richtige Liste, richtiges Datum
- [ ] Projektübersicht: wie viel ist je Projekt offen, was hängt seit Tagen
- [ ] Kostenlos online über GitHub Pages / Cloudflare Pages; aufs Handy über „Zum Startbildschirm hinzufügen“

Weil alles in Google Tasks gespeichert bleibt, funktionieren die Google-App und ihre Erinnerungen parallel weiter. Fällt das Cockpit mal aus, geht nichts verloren.

Entwurf: [`entwurf/cockpit-entwurf.html`](entwurf/cockpit-entwurf.html) · Screenshot: [`entwurf/cockpit-entwurf.png`](entwurf/cockpit-entwurf.png)

---

## Stand der App (`docs/`)

**Release 1 – fertig, läuft lokal im Browser (PWA, installierbar):**
- Ansichten: Heute (Liegen geblieben · Top heute · Wenn Zeit bleibt · Erledigt heute), Markiert, Geplant, Erledigt, je Projekt, Suche
- Schnell-Erfassung per Text: `Angebot schicken #KundeB morgen 15:00 *` setzt Projekt, Datum, Uhrzeit und Stern
- Tagesplanung beim ersten Öffnen am Tag: Liegengebliebenes und Eingang mit einem Klick auf heute, morgen, nächste Woche oder löschen
- Wiederholungen (täglich, werktags, wöchentlich, monatlich), Notizen, Rückgängig nach jeder Aktion
- Erinnerungen zur Uhrzeit (solange die App geöffnet ist), Sicherung/Wiederherstellung als Datei
- Handy: Tab-Leiste, großer Plus-Knopf, Eingabe als Bottom-Sheet

**Release 2 – Abgleich PC ↔ Handy über das Google-Konto** (Entscheidung offen, siehe Chat)

**Release 3 – Optionen:** Erinnerungen auch bei geschlossener App über den Google Kalender; Import der bestehenden Google-Tasks-Listen
