# Plan: Mein Tages-Cockpit für Aufgaben und Termine

## Das Problem in einem Satz
Viele Projekte gleichzeitig → Aufgaben liegen verstreut (Mails, Notizen, Kopf) → am Ende des Tages fällt etwas durch.

## Das Ziel
Ein einziger Ort, der jeden Morgen zeigt:
1. **Meine Termine heute** (aus dem Google Kalender)
2. **Meine Aufgaben heute** – plus alles, was gestern liegen geblieben ist
3. **Erinnerungen**, damit nichts vergessen wird

Und das am PC und auf dem Handy gleich.

---

## Grundregeln (die Methode ist wichtiger als das Tool)

| Regel | Was das heißt |
|---|---|
| **1. Ein Eingang** | Jede Aufgabe landet sofort an *einem* Ort, egal aus welchem Projekt. Kein Zettel, keine zweite Liste. |
| **2. Erfassen in 10 Sekunden** | Titel + Projekt + (optional) Datum. Mehr nicht. Sortieren kommt später. |
| **3. Projekt als Etikett** | Jede Aufgabe bekommt ein Projekt-Kürzel (z. B. `#Alpha`, `#Kunde-B`). So bleibt eine Liste, aber man kann filtern. |
| **4. Nichts verschwindet** | Unerledigtes wandert automatisch in „Heute – überfällig“. Es wird nie stillschweigend gelöscht. |
| **5. Maximal 3 Top-Aufgaben pro Tag** | Der Rest ist „wenn Zeit bleibt“. Das hält den Tag realistisch. |
| **6. Große Aufgaben bekommen einen Kalenderblock** | Was länger als 30 Minuten dauert, wird als Termin geblockt – sonst passiert es nicht. |

---

## Der Tagesablauf (Workflow)

| Wann | Dauer | Was |
|---|---|---|
| **Morgens** | 5 Min | Cockpit öffnen → Termine ansehen → überfällige Aufgaben neu einplanen oder streichen → 3 Top-Aufgaben markieren |
| **Tagsüber** | Sekunden | Neue Aufgaben sofort per Handy oder PC erfassen (Eingang). Erledigtes abhaken. |
| **Erinnerungen** | automatisch | Bei Aufgaben mit Uhrzeit + 10 Min vor Kalenderblöcken |
| **Feierabend** | 3 Min | Was offen ist: auf morgen schieben, delegieren oder bewusst löschen |
| **Freitag** | 15 Min | Wochenrückblick: alle Projekte durchgehen, nächste Woche grob blocken |

---

## Drei Wege zum Tool – mit Empfehlung

### Weg A: Google Tasks + Google Kalender (sofort, kostenlos)
- Aufgaben direkt im Google Kalender und in der Google-Tasks-App auf dem Handy.
- Je Projekt eine eigene Liste.
- **Plus:** null Aufwand, alles schon da, Erinnerungen per Handy.
- **Minus:** keine Projekt-Etiketten, keine schöne Tagesansicht über alle Listen, Überfälliges wird nur schwach hervorgehoben.

### Weg B: Todoist (fertige App, ca. 5 €/Monat für Pro)
- Beste fertige Lösung für viele Projekte: Etiketten, Filter, „Heute“-Ansicht mit Überfälligem, Spracheingabe („Angebot an Kunde B Freitag 10 Uhr #Kunde-B“).
- Zwei-Wege-Abgleich mit dem Google Kalender.
- **Plus:** sehr intuitiv, App für Handy, PC, Browser.
- **Minus:** Erinnerungen und Kalender-Abgleich nur in der bezahlten Version; Daten liegen bei einem weiteren Anbieter.

### Weg C: Eigenes Tages-Cockpit (dieses Repository) ⭐ Empfehlung auf Sicht
Eine eigene Web-App, die genau deinen Workflow abbildet:
- **Daten bleiben bei Google:** Aufgaben werden in Google Tasks gespeichert, Termine kommen aus dem Google Kalender. Kein eigener Server, kein Datenverlust, wenn die App mal nicht läuft – die Google-Apps funktionieren weiter.
- **Eine Ansicht für alles:** Termine als Zeitleiste links, Aufgaben rechts, Überfälliges oben rot markiert, Top 3 hervorgehoben, Filter nach Projekt.
- **Aufs Handy als App:** als „PWA“ – einmal im Browser öffnen, „Zum Startbildschirm hinzufügen“, fertig. Kein App-Store nötig.
- **Erinnerungen:** über die Google-Tasks- und Kalender-Benachrichtigungen auf dem Handy, die ohnehin schon funktionieren.
- **Komplett kostenlos:** Google Kalender und Google Tasks samt Schnittstellen kosten bei privater Nutzung nichts, das Hosting läuft gratis über GitHub Pages (Repo muss dafür öffentlich sein, es enthält aber nur Programmcode, keine Aufgaben) oder alternativ Cloudflare Pages / Netlify (auch mit privatem Repo kostenlos).

**Meine Empfehlung:** Heute mit **Weg A** starten (die Methode einüben, kostet nichts), parallel **Weg C** bauen. Da Weg C auf denselben Google-Daten aufsetzt, geht nichts verloren – das Cockpit ist einfach die bessere Oberfläche obendrauf. Wer lieber gar nichts bauen will, nimmt Weg B.

Ein Entwurf des Cockpits liegt unter [`entwurf/cockpit-entwurf.html`](entwurf/cockpit-entwurf.html), der Screenshot unter [`entwurf/cockpit-entwurf.png`](entwurf/cockpit-entwurf.png).

---

## Umsetzungsplan

### Phase 0 – Sofort (heute, 30 Min)
- [ ] In Google Tasks eine Liste „Eingang“ anlegen; je aktivem Projekt eine Liste
- [ ] Google-Tasks-App auf dem Handy installieren, Benachrichtigungen an
- [ ] Alle Aufgaben aus dem Kopf und aus Notizen einmal in „Eingang“ schreiben
- [ ] Wiederkehrende Kalendertermine anlegen: „Tagesplanung“ (morgens 5 Min), „Feierabend-Check“ (3 Min), „Wochenrückblick“ (Fr, 15 Min)

### Phase 1 – Grundgerüst Cockpit (1–2 Sitzungen)
- [ ] Google-Cloud-Projekt anlegen, Kalender- und Tasks-Schnittstelle freischalten, Login einrichten
- [ ] Web-App mit Anmeldung über das Google-Konto
- [ ] Tagesansicht: Termine heute + Aufgaben heute + Überfälliges
- [ ] Abhaken, neue Aufgabe erfassen, „auf morgen schieben“ mit einem Klick
- [ ] Veröffentlichung über GitHub Pages, auf dem Handy zum Startbildschirm hinzufügen

### Phase 2 – Komfort (1–2 Sitzungen)
- [ ] Projekt-Filter und Farben je Projekt
- [ ] Top-3-Markierung
- [ ] „In den Kalender blocken“: Aufgabe per Klick als Zeitblock in freie Lücke legen
- [ ] Schnell-Eingabe mit Kürzeln: `Angebot schicken #Kunde-B morgen`

### Phase 3 – Extras (optional)
- [ ] Morgen-Briefing durch Claude (`/morning`): fasst Termine und offene Aufgaben jeden Werktag zusammen
- [ ] Wochenrückblick-Ansicht: was wurde erledigt, was hängt seit Tagen
- [ ] Aufgaben aus Mails übernehmen (Gmail-Markierung → Aufgabe)

---

## Offene Fragen an dich
1. Nutzt du beruflich auch Google (Workspace) oder ist der Job-Kalender ein anderer, z. B. Outlook? Das entscheidet, welche Schnittstelle wir anbinden.
2. Darf der Arbeitskalender mit dem privaten Google-Konto verbunden werden, oder gibt es Firmenregeln dagegen?
3. Wie viele Projekte laufen etwa gleichzeitig (5? 15?)?
4. Lieber erst Weg A/B testen oder direkt mit Weg C loslegen?
