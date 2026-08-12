---
name: start-petworld
description: Startet eine PetWorld-Arbeitssitzung. Auslösen, sobald der Betreiber "start petworld", "starte petworld", "los gehts petworld" oder Ähnliches schreibt, oder eine neue Sitzung an diesem Projekt beginnt. Liest den Projektstand aus CLAUDE.md und docs/, prüft Repo und Shopify-Connector, meldet den Stand und schlägt den nächsten Schritt vor.
---
# Sitzungsstart PetWorld

Arbeite diese Schritte der Reihe nach ab. **Erst berichten, dann handeln** — starte
keine Änderungen, bevor der Betreiber den vorgeschlagenen nächsten Schritt bestätigt hat.

## 1. Projektstand einlesen

Lies vollständig:

- `CLAUDE.md` — Kontext, Architektur-Entscheidungen, Sicherheitsregeln, Grundhaltung
- `docs/README.md` — Einstieg und Kurzfassung
- `docs/todo.md` — was ansteht, aufgeteilt nach Zuständigkeit
- `docs/entscheidungen.md` — getroffene Entscheidungen **und die Korrekturen K1…**
- `docs/offene-fragen.md` — was fehlt und was blockiert

Bei Bedarf vertiefen: `zahlen.md`, `theme-audit.md`, `personalizer-audit.md`,
`kontrast-audit.md`, `startseite-befunde.md`, `markennamen.md`,
`personalizer-app-entscheidung.md`.

**Lies die Korrekturen aufmerksam.** Mehrere frühere Befunde haben sich als falsch
erwiesen. Wiederhole diese Fehler nicht.

## 2. Repo prüfen

```bash
git status --short
git log --oneline -8
git branch --show-current
```

Erwartet: Branch `claude/petworld-shopify-brainstorm-9go0du`, sauberer Arbeitsbaum.
Bei nicht committeten Änderungen: melden und klären, bevor irgendetwas weitergeht.

Kurzer Integritätscheck des Themes:

```bash
python3 -c "
import json,re,glob
bad=[]
for f in glob.glob('templates/*.json')+glob.glob('sections/*.json'):
    try: json.loads(re.sub(r'/\*.*?\*/','',open(f,encoding='utf-8').read(),flags=re.S))
    except Exception as e: bad.append((f,str(e)[:60]))
print('Templates fehlerhaft:', bad or 'keine')
"
```

## 3. Shopify-Connector prüfen

Versuche die Werkzeuge zu laden (`ToolSearch` mit
`select:mcp__Shopify__graphql_query,mcp__Shopify__get-shop-info`).

**Wenn sie fehlen:** Frage über `SearchMcpRegistry` mit Stichwort `shopify` den Zustand ab.

- `connected: true`, `enabledInChat: false` → Der Connector ist verbunden, aber **für
  diesen Chat abgeschaltet**. Den Betreiber bitten, ihn über das **Plus-Symbol beim
  Eingabefeld → Konnektoren → Shopify** einzuschalten. Achtung: In der Vergangenheit
  zeigte der Schalter „an", während serverseitig weiterhin `false` stand — dann hilft
  nur aus- und wieder einschalten oder eine neue Unterhaltung.
- `connected: false` → neu verbinden lassen.

**Ohne Connector blockiert:** Weiterleitungen, Rabatte, Versandeinstellungen,
Produktdaten, Analytics. Theme-Arbeit geht trotzdem.

## 4. Stand melden

Gib eine kompakte Übersicht aus:

1. **Wo wir stehen** — drei bis fünf Sätze, keine Wiederholung ganzer Dokumente
2. **Was zuletzt passiert ist** — die letzten Commits in Klartext
3. **Was beim Betreiber offen ist** — die Admin-Aufgaben aus `todo.md`
4. **Was blockiert ist** und wodurch
5. **Der vorgeschlagene nächste Schritt**, mit Begründung warum genau dieser

## 5. Haltung für die Sitzung

- Deutsch, Duzen.
- **Proaktiv arbeiten** — siehe „Grundhaltung" in `CLAUDE.md`. Auffälligkeiten sofort
  melden, mitdenken, widersprechen wenn etwas nicht stimmt, ehrlich berichten.
- **Vor jeder Behauptung über den Shop gegenprüfen** — über den Connector oder das
  Repo, nie aus dem Gedächtnis.
- **Vor jedem Löschen auf Referenzen prüfen.** Navigation immer in **beiden** Quellen
  prüfen: Shopify-Menüs *und* `sections/footer-group.json` / `header-group.json`.
- **Nie am Live-Theme arbeiten.** `shopify theme push` ohne Flags ist verboten.
- **Keine Zugangsdaten in den Chat.**
- Selbst dokumentieren, selbst committen — ohne Aufforderung.
