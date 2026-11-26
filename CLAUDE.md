# MACS Spiele – Hinweise für Claude

Kleine Browser-Spiele und Web-Apps. Marcus lernt hier Programmieren mit Claude,
ohne Vorkenntnisse. Lernen steht im Vordergrund.

## Arbeitsweise

- Antworten auf Deutsch, klar und knapp. Kurz erklären, was du tust und warum.
- Klein starten: lieber schnell etwas Spielbares als ein großer Plan.
- Größere Aufgaben erst im Plan-Modus planen, dann umsetzen.
- Jede Änderung auf einem eigenen Branch, dann Pull Request. Gemergt wird nur nach Marcus' OK.
- Keine neuen Kosten (Abos, Dienste, API-Schlüssel) ohne Freigabe. Rahmen: ca. 50 € pro Monat.
- Keine fremden Erweiterungen (Skills, Plugins, MCP-Server) installieren. Vorschlagen ist erlaubt,
  geprüft und eingetragen wird in `docs/erweiterungen.md`.
- Sicherheitsregeln in `.claude/settings.json` nie selbst lockern.

## Aufbau

- `index.html` – Startseite mit Links zu allen Spielen
- `spiele/<name>/index.html` – jedes Spiel in einem eigenen Ordner, alles in einer Datei
  (HTML, CSS, JavaScript), ohne Build-Schritt und ohne externe Bibliotheken
- `docs/` – Ausbauplan, Erweiterungsliste und andere Notizen
- `.claude/agents/` – Helfer-Agenten (z. B. `reviewer`)

Live über GitHub Pages: https://shiconsu.github.io/Macs-spiele/ (Branch `main`, Groß-/Kleinschreibung beachten).

## Neues Spiel

1. Ordner `spiele/<name>/` mit `index.html` anlegen (Name klein, ohne Leerzeichen).
2. Link mit Emoji und kurzer Beschreibung auf der Startseite ergänzen.
3. Hell- und Dunkelmodus, Handy-Breite und Tastatur/Touch mitdenken.
4. Lokal testen: Datei im Browser öffnen.
5. Vor dem PR den Agenten `reviewer` drüberschauen lassen.

## Fertig heißt (drei Prüfstufen)

1. **Läuft:** Seite lädt ohne Fehler in der Browser-Konsole. (Später automatisch per Playwright.)
2. **Review:** `reviewer` hat nichts Ernstes gefunden, oder die Funde sind behoben.
3. **Freigabe:** Marcus hat es gespielt und den PR gemergt.

## Privatsphäre

Marcus bleibt anonym: keine privaten Namen oder E-Mail-Adressen in Code, Commits oder Texten.

## Ausbau

Dieses Setup ist bewusst klein. Wie es später wachsen kann, steht in `docs/ausbau-roadmap.md`.
