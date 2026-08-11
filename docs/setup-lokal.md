# Lokal weiterarbeiten

Diese Anleitung führt von null zu einer Live-Vorschau des Shops auf dem eigenen Rechner.

## Voraussetzung

Node.js 18 oder neuer.

## Einrichten

```bash
npm install -g @anthropic-ai/claude-code
npm install -g @shopify/cli@latest

git clone https://github.com/realvairex/testshop.git
cd testshop
git checkout claude/petworld-shopify-brainstorm-9go0du
```

## Mit dem Shop verbinden

```bash
shopify theme pull --store DEIN-HANDLE.myshopify.com
```

Öffnet den Browser für den Login. `DEIN-HANDLE.myshopify.com` ist die interne
Shopify-Adresse, **nicht** pet-world.at.

> Der Theme-Export vom 11.08.2026 liegt bereits im Repo (Commit `cacbd97`). Ein
> `theme pull` holt den aktuellen Stand und zeigt per `git diff`, was sich seitdem
> im Live-Shop geändert hat.

## Live-Vorschau starten

```bash
shopify theme dev
```

Startet einen lokalen Server mit Hot-Reload. Änderungen am Code sind sofort im Browser
sichtbar. Es wird automatisch ein **Entwicklungs-Theme** verwendet — der Live-Shop wird
dabei nicht angefasst.

## Claude Code starten

```bash
claude
```

Die Datei `CLAUDE.md` im Projektwurzelverzeichnis wird automatisch geladen. Die neue
Session kennt damit Projektkontext, Architektur-Entscheidungen und Sicherheitsregeln.

**Ein guter erster Satz für die neue Session:**

> Lies CLAUDE.md und docs/. Wir arbeiten an PetWorld weiter. Stand: Audits sind fertig,
> Phase 1 (Aufräumen + Design-Tokens) steht als Nächstes an.

## ⚠️ Gefährliche Befehle

| Befehl | Warum gefährlich |
|---|---|
| `shopify theme push` | **Kann das Live-Theme überschreiben.** Nie ohne Flags ausführen. |
| `shopify theme pull --live` | Überschreibt lokale Änderungen mit dem Live-Stand |

`shopify theme dev` ist sicher — es legt automatisch ein separates Entwicklungs-Theme an.

## Alternative: GitHub-Sync (kein Terminal nötig)

Funktioniert auch ohne lokale Installation, direkt im Shopify-Admin:

1. **Online Store → Themes → Add theme → Connect from GitHub**
2. Repo `realvairex/testshop`, Branch `claude/petworld-shopify-brainstorm-9go0du`
3. Shopify legt daraus ein unveröffentlichtes Theme an

Ab dann zieht Shopify jeden Push automatisch nach, meist unter einer Minute. Über
**Vorschau** ist das Ergebnis im echten Shop sichtbar, mit echten Produkten und echtem
teeinblue.

Die Synchronisation läuft in beide Richtungen: Änderungen im Theme-Editor kommen als
Commits zurück ins Repo.

⚠️ **Nie an das Live-Theme koppeln.** Immer an ein Entwicklungs-Theme.

## Was lokal zusätzlich möglich wird

Die Cloud-Session war durch einen Netzwerk-Filter eingeschränkt — erreichbar waren nur
GitHub und Paket-Registries. Lokal fällt das weg:

- teeinblue-Doku und -Admin aufrufen
- pet-world.at direkt analysieren
- Lighthouse und PageSpeed messen
- Shopify Admin API nutzen (Custom App mit Lese-Rechten, Token in `.env`, `.gitignore`)
- Optional der offizielle Shopify-Dev-MCP-Server für API-Doku:
  `claude mcp add shopify-dev -- npx -y @shopify/dev-mcp@latest`

## Sicherheit

Keine API-Keys, Theme-Access-Passwörter oder Shop-Logins in den Chat. Falls Tokens
gebraucht werden: `.env` anlegen, in `.gitignore` eintragen, Custom App mit reinen
Lese-Rechten verwenden.
