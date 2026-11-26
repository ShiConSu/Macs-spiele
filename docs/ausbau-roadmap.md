# Ausbau-Roadmap: vom Mini-Setup zum vollen Entwicklungs-Setup

Stand: 26.11.2026. Grundlage ist die Prüfung des „Development OS“-Konzepts.

Das Setup startet klein und wächst nur, wenn ein echtes Projekt zeigt, dass etwas fehlt.
Jede Stufe hat einen **Auslöser** (wann sie sich lohnt) und einen **Andockpunkt** (wo sie technisch hingehört).
Die Rollen und Gates aus dem großen Konzept gehen nicht verloren, sie kommen später an diesen Stellen dazu.

## Stufe 1 – Mini-Setup (jetzt)

- `CLAUDE.md` mit Regeln und Aufbau
- Agent `reviewer` (nur lesen, Modell `opus`) in `.claude/agents/`
- Berechtigungsregeln in `.claude/settings.json`
- Drei Prüfstufen: läuft · Review · Marcus' Freigabe
- Kosten: nur das bestehende Claude-Abo

## Stufe 2 – Automatisch prüfen

| Baustein | Auslöser | Andockpunkt |
| --- | --- | --- |
| Playwright-Test pro Spiel | Ein Spiel ging nach einer Änderung kaputt, ohne dass es auffiel | `tests/`, Befehl in `CLAUDE.md` |
| GitHub Actions führt Tests bei jedem PR aus | Es gibt mindestens einen Test | `.github/workflows/` |
| Agent `tester` (Modell `sonnet`) | Mehr als drei Tests | `.claude/agents/tester.md` |
| Hook: Linter nach jeder Änderung | Wiederkehrende Flüchtigkeitsfehler | `.claude/settings.json` → `hooks` |

## Stufe 3 – Wiederverwenden

| Baustein | Auslöser | Andockpunkt |
| --- | --- | --- |
| Eigener Skill „Neues Spiel anlegen“ | Drittes Spiel nach gleichem Muster | `.claude/skills/neues-spiel/SKILL.md` |
| Skill „Barrierefreiheit prüfen“ (ehem. Rolle UX/Accessibility) | Erste Web-App mit Formularen | `.claude/skills/` |
| Offizielle Anthropic-Skills, einzeln geprüft | Konkreter Bedarf | Eintrag in `docs/erweiterungen.md`, dann `.claude/skills/` |
| Retro-Notizen pro Projekt | Ab jetzt nach jedem Spiel | `docs/retro.md` |

## Stufe 4 – Projektübergreifend

| Baustein | Auslöser | Andockpunkt |
| --- | --- | --- |
| Gemeinsame Agenten und Skills für alle Repos | Zweites Repo (z. B. eine Web-App) | `~/.claude/agents/`, `~/.claude/skills/` oder ein eigenes Plugin |
| Agent `rechercheur` (Modell `haiku`/`sonnet`) | Häufige Fragen zu Bibliotheken | `.claude/agents/` |
| Git Worktrees für zwei Aufgaben parallel | Wartezeit wird zum Engpass | Subagent-Feld `isolation: worktree` |
| Wissen in Obsidian lesen | Wunsch nach Übersicht | Repo-Ordner als Vault öffnen, ohne Plugin oder MCP |

## Stufe 5 – Volles Setup (erst nach Freigabe, ggf. mit Kosten)

| Baustein | Auslöser | Voraussetzung |
| --- | --- | --- |
| Backend mit Datenbank | Ein Projekt braucht Speicherung für mehrere Nutzer | Hoster und Kosten geprüft und freigegeben |
| Weitere Gates (Security-Scan, Accessibility, Release) | Projekte mit echten Nutzern | Stufe 2 läuft stabil |
| Agent Teams (mehrere Agenten parallel) | Projekt mit klar getrennten Teilen | Kostenfreigabe; laut Anthropic ca. 7-facher Tokenverbrauch, noch experimentell (Stand 11/2026) |
| Verbesserungsschleife mit Vergleichstests | Ca. 10 vergleichbare Projekte mit Retro-Notizen | `docs/retro.md` als Datengrundlage |
| Mobile- oder Desktop-Apps | Web sitzt sicher | eigene Werkzeugkette, ggf. Kosten (muss geprüft werden) |

## Feste Regeln für jeden Ausbau

- Sicherheitsregeln, Berechtigungen und Freigaberegeln ändert nur Marcus.
- Neue Erweiterungen erst nach Prüfung und Eintrag in `docs/erweiterungen.md`.
- Neue Kosten nur nach Freigabe.
- Eine Stufe wird erst begonnen, wenn die vorige im Alltag funktioniert.
