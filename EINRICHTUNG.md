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
