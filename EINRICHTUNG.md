# Einrichtung: App online stellen und mit Google abgleichen

Einmalig etwa 20 Minuten. Danach sind PC und Handy immer auf demselben Stand.

## Teil 1: App ins Internet stellen (GitHub Pages)

Im Repository gibt es nur Programmcode. Deine Aufgaben liegen nie dort, sondern nur in deinem Google-Konto.

1. Auf GitHub das Repository `daktar75/meine-aufgaben-orga` öffnen → **Settings** → ganz unten **Danger Zone** → **Change visibility** → **Make public**.
2. **Settings** → links **Pages**.
3. Unter **Build and deployment**: Source **Deploy from a branch**. Branch **`claude/vibrant-mendel-ebrcu8`**, Ordner **`/docs`** → **Save**.
4. Nach 1–2 Minuten steht oben die Adresse: **https://daktar75.github.io/meine-aufgaben-orga/**

Diese Adresse im Browser öffnen. Das ist deine App.

## Teil 2: Google-Zugang einrichten (kostenlos)

Das erlaubt der App, eine einzige Datei in einem privaten Bereich deines Google Drive zu lesen und zu schreiben. Auf deine anderen Drive-Dateien hat sie keinen Zugriff.

1. **https://console.cloud.google.com** öffnen, mit dem privaten Google-Konto anmelden.
2. Oben **Projekt auswählen** → **Neues Projekt** → Name `Aufgaben` → **Erstellen**.
3. Menü **APIs & Dienste** → **Bibliothek** → nach **Google Drive API** suchen → **Aktivieren**.
4. Menü **APIs & Dienste** → **OAuth-Zustimmungsbildschirm** (bei neuer Oberfläche: **Google Auth Platform**):
   - Nutzertyp **Extern**, App-Name `Meine Aufgaben`, deine E-Mail als Support- und Kontakt-Adresse.
   - Bereiche (Scopes) hinzufügen: **`.../auth/drive.appdata`** („Eigene Konfigurationsdaten in Google Drive ansehen und verwalten“).
   - Veröffentlichungsstatus bleibt auf **Test**. Unter **Zielgruppe → Testnutzer** die eigene Gmail-Adresse eintragen. („In Produktion“ verlangt Startseite und Datenschutzerklärung, das ist für eine private App unnötig. Google fragt dann etwa einmal pro Woche erneut nach der Zustimmung.)
5. Menü **Anmeldedaten** → **Anmeldedaten erstellen** → **OAuth-Client-ID**:
   - Anwendungstyp **Webanwendung**, Name `Aufgaben-App`.
   - Bei **Autorisierte JavaScript-Quellen** eintragen: `https://daktar75.github.io` (ohne Schrägstrich am Ende und ohne Pfad).
   - **Erstellen**. Die angezeigte **Client-ID** kopieren (endet auf `.apps.googleusercontent.com`).

## Teil 3: In der App verbinden

1. App öffnen → **⚙ Einstellungen** → **Google-Abgleich**.
2. Client-ID einfügen → **Speichern** → **Mit Google verbinden** → mit dem Google-Konto anmelden und zustimmen.
3. Falls Google „App nicht geprüft“ zeigt: **Erweitert** → **Weiter zu Meine Aufgaben**.
4. Auf dem Handy dasselbe: App-Adresse öffnen → Client-ID einfügen → verbinden.

**Tipp:** Schick mir die Client-ID im Chat. Sie ist kein Geheimnis. Dann trage ich sie fest in die App ein, und du musst sie auf keinem Gerät mehr eingeben.

## Teil 4: Aufs Handy als App

- **iPhone (Safari):** Teilen-Symbol → **Zum Home-Bildschirm**.
- **Android (Chrome):** Menü ⋮ → **App installieren** / **Zum Startbildschirm hinzufügen**.

## Wenn etwas nicht klappt

- Oben rechts zeigt **☁ tippen**: Die Anmeldung ist abgelaufen (nach etwa einer Stunde). Einmal irgendwo tippen oder das Wolken-Symbol antippen, dann läuft der Abgleich weiter.
- Fehler „redirect_uri_mismatch“ oder „origin_mismatch“: Die Adresse unter „Autorisierte JavaScript-Quellen“ stimmt nicht. Sie muss genau `https://daktar75.github.io` lauten.

## Optional: Aufgaben aus Google Tasks übernehmen

Einmalig, nur lesend. Google Tasks bleibt unverändert.

1. Google Cloud, Projekt „Aufgaben“: **APIs & Dienste → Bibliothek → Google Tasks API → Aktivieren**.
2. **Google Auth Platform → Datenzugriff → Bereiche hinzufügen oder entfernen**: bei „Bereiche manuell hinzufügen“ `https://www.googleapis.com/auth/tasks.readonly` einfügen, zur Tabelle hinzufügen, aktualisieren, speichern.
3. App: **⚙ Einstellungen → Aus Google Tasks übernehmen → Jetzt importieren**. Google fragt nach der Zustimmung (wie beim ersten Verbinden: Erweitert → Weiter).

Jede Google-Liste wird ein Projekt. Die Listen „Eingang“ und „Meine Aufgaben“ landen im Eingang. Erledigte Aufgaben werden nicht übernommen. Datum bleibt erhalten, Uhrzeiten und Sterne gibt Google nicht heraus.

## Optional: Erinnerungen über den Google Kalender

Aufgaben mit Uhrzeit werden als Termin im privaten Google Kalender angelegt (mit Erinnerung). So klingelt das Handy auch bei geschlossener App. Erledigte oder gelöschte Aufgaben entfernen ihren Termin wieder.

1. Google Cloud, Projekt „Aufgaben“: **APIs & Dienste → Bibliothek → Google Calendar API → Aktivieren**.
2. **Google Auth Platform → Datenzugriff → Bereiche hinzufügen oder entfernen**: bei „Bereiche manuell hinzufügen“ `https://www.googleapis.com/auth/calendar.events` einfügen, zur Tabelle hinzufügen, aktualisieren, speichern.
3. App: **Einstellungen → Erinnerungen über Google Kalender → An**. Google fragt einmal nach der Zustimmung (Erweitert → Weiter → Zulassen).
4. Aufgabe mit Datum und Uhrzeit anlegen, zum Beispiel `Rückruf Schulz morgen 10:00`. Der Termin erscheint kurz danach im Google Kalender.
5. Der Vorlauf (zur Uhrzeit, 10, 30 oder 60 Minuten vorher) steht in den Einstellungen unter „Vorlauf“.

## Optional: Automatisch anmelden (ohne stündliches Tippen)

Google lässt die Anmeldung nach etwa einer Stunde ablaufen. Mit dieser Einstellung erneuert die App sie beim Öffnen selbst, über eine kurze Weiterleitung zu Google (der Bildschirm flackert kurz). Nur wenn Google eine neue Zustimmung will (im Status „Test“ etwa einmal pro Woche), steht oben „☁ tippen“.

1. Google Cloud, Projekt „Aufgaben“: **Google Auth Platform → Clients → Aufgaben-App** öffnen.
2. Unter **Autorisierte Weiterleitungs-URIs → URI hinzufügen**: `https://daktar75.github.io/meine-aufgaben-orga/` (genau so, mit Schrägstrich am Ende). **Speichern**. Google braucht danach manchmal ein paar Minuten.
3. **Zuerst am PC**: App öffnen → Einstellungen → **Automatisch anmelden → An**. Die App leitet einmal zu Google und kommt zurück. Erscheint stattdessen eine Google-Fehlerseite („redirect_uri_mismatch“), stimmt Schritt 2 noch nicht: zurück zur App, Einstellung wieder auf Aus, URI prüfen.
4. Klappt es am PC, am Handy dieselbe Einstellung einschalten.
