# PetWorld — Projektkontext

**Antworte in diesem Projekt auf Deutsch.** Der Betreiber ist Österreicher, die
Zusammenarbeit läuft auf Deutsch.

## Worum es geht

PetWorld (pet-world.at) ist ein österreichischer Shopify-Shop für **personalisierte
Haustier-Produkte** — Poster, Kissen, Tassen, Haustierbetten. Der Kunde lädt ein Foto
seines Hundes oder seiner Katze hoch, das in ein stilisiertes Design eingearbeitet wird.
Print-on-Demand, keine eigene Produktion.

Bestseller sind Poster mit Magazin-Cover-Optik zu einheitlich **19,95 €** (Streichpreis
24,95 €).

**Das Ziel:** Der Shop macht zu wenig Umsatz. Gearbeitet wird an Design, Stimmigkeit,
Geschwindigkeit, Corporate Identity, dem Personalisierungs-Ablauf und Sichtbarkeit/SEO.

## Arbeitsstand

Branch: `claude/petworld-shopify-brainstorm-9go0du`

| Commit | Inhalt |
|---|---|
| `cacbd97` | **Unveränderter Theme-Export als Baseline.** Referenzpunkt für jeden Vergleich. |
| danach | Audits und Dokumentation unter `docs/` |

Bisher wurde **kein Theme-Code verändert**. Alles bis hier ist Analyse.

## Technische Basis

- **Theme: Fabric 3.1.0** (Shopify First-Party, block-basiert, Horizon-Generation)
- 557 Dateien, 116 Sections, 87 Blocks, 130 Snippets, 56 Templates
- Kein Build-Step. Reines Liquid, CSS, Vanilla-JS.

### Installierte Apps

| App | Status | Bewertung |
|---|---|---|
| teeinblue Product Personalizer | aktiv, App-**Embed** | Kern des Geschäfts. Fulfillment-Workflow gilt als problematisch. |
| smind / Sections Pro | aktiv | wird genutzt (`sp-*` Sections) |
| Opus Cart Upsell | aktiv | wird genutzt |
| GemPages | aktiv | ⚠️ **5 veröffentlichte Seiten hängen daran** — erst nativ nachbauen, dann deinstallieren |
| PageFly | aktiv | ✅ von keinem Objekt referenziert — sofort deinstallierbar |
| Shogun | Reste im Theme | ✅ von keinem Objekt referenziert — sofort deinstallierbar |
| Dakaas Store Effects | deaktiviert | — |

## Getroffene Architektur-Entscheidungen

**1. Liquid-Theme bleibt, kein Headless.**
Hydrogen/Next.js würde teeinblue zerstören — der Personalizer ist als App-Embed für den
Online Store gebaut. Dazu Checkout, Klarna/EPS, Reviews, Tracking. Nicht verhandelbar,
solange die Personalisierung über eine Shopify-App läuft.

**2. Kein Framer Motion.**
Das ist React-only. Für Animationen: **Motion One** (motion.dev, Vanilla-JS, ~5 kB) oder
CSS scroll-driven animations. Optisch gleichwertig, besser für Core Web Vitals.

**3. Dreischichtiges Token-Modell** (primitive → semantic → component) als CSS Custom
Properties, angebunden an `config/settings_schema.json`, damit Farben im Theme-Editor
änderbar bleiben ohne Code-Änderung.

**4. Fremde Design-Skills werden nicht als Plugin installiert.**
Das Repo `nextlevelbuilder/ui-ux-pro-max-skill` wird nur als Referenz für Token-Struktur
und Paletten genutzt — nicht als Plugin, weil es fremde Anweisungen, Python-Skripte und
eine `.mcp.json` in ein Repo bringt, das an den Live-Shop gekoppelt wird.

## Sicherheitsregeln

- **Nie direkt am Live-Theme arbeiten.** Immer Entwicklungs-Theme, Veröffentlichen ist
  ausschließlich die Entscheidung des Betreibers.
- **`shopify theme push` ohne Flags ist verboten** — kann das Live-Theme überschreiben.
  `shopify theme dev` legt automatisch ein Dev-Theme an und ist sicher.
- **Keine API-Keys, Theme-Access-Passwörter oder Tokens in den Chat.** Falls nötig:
  `.env` mit `.gitignore`.
- **Vor dem Löschen von Page-Builder-Dateien** immer die `templateSuffix`-Zuweisung
  über den Connector prüfen — nicht nur die Theme-Templates. Genau daran wäre die
  erste Einschätzung fast gescheitert: Fünf veröffentlichte Seiten hängen an
  GemPages, obwohl im Theme nichts darauf hindeutet.

## Navigationslücke

Das Hauptmenü führt nur zu Kollektionen, die Fußzeile nur zu den fünf Rechtstexten.
**FAQ, Über uns, Kontakt, Bild-Leitfaden und Weiterempfehlen sind über kein Menü
erreichbar** — jede dieser Seiten existiert sogar doppelt (eine GemPages- und eine
native Fassung), beide veröffentlicht, beide unverlinkt.

Der Bild-Leitfaden ist besonders wichtig: Ein gutes Kundenfoto ist die Voraussetzung
für ein gutes Poster. Aktuell findet ihn niemand.

## Die wichtigsten Befunde

Ausführlich in `docs/theme-audit.md` und `docs/personalizer-audit.md`.

1. **Der Personalizer überfordert** — 9 Pflichtfelder, über 40 Farbfelder, Foto-Upload
   an letzter Stelle, keine sichtbare Live-Vorschau. Kritisch.
2. **Drei ungenutzte Page-Builder laden auf jeder Seite mit.** Größter Performance-Hebel.
3. **Kein Typo-System** — eine einzige Schriftfamilie (Asap) für alle vier Rollen.
   Überschriften laufen auf `#030302c2`, also 76 % Deckkraft. Ausgegraut und
   kontrastschwach.
4. **Preis und Varianten** werden ausschließlich von teeinblue clientseitig gerendert.
   Die nativen `price`- und `variant-picker`-Blöcke existieren, sind aber nicht platziert.

## Die Lage in Zahlen

**Vollständig in `docs/zahlen.md`** (Shopify-Connector, 12.08.2026). Das Wichtigste:

| | |
|---|---|
| Sessions letzte 12 Monate | 11.072 — davon 87 % in Dez–Feb |
| Sessions aktuell | **26 im Monat** (Höchststand war 3.681) |
| Bestellungen gesamt | **16** |
| Bruttoumsatz gesamt | **616 €** |
| **Conversion Rate** | **0,14 %** — etwa ein Zehntel des Shopify-Medians |
| Traffic-Quelle | 78 % Social, fast nur mobil. Suche: 98 Sessions im Jahr |
| Fulfillment | **13 von 16 Bestellungen nicht vollständig ausgeliefert** |

**Drei Probleme, in dieser Reihenfolge:**

1. **Fulfillment.** Bezahlte Bestellungen aus Dezember 2025 stehen weiterhin auf
   `IN_PROGRESS`. Entweder nie geliefert oder der POD-Partner meldet den Status nicht
   zurück. Dringend, unabhängig von allem anderen.
2. **Conversion 0,14 %.** Die Personalizer-Diagnose ist damit belegt: 9.675 Besucher in
   drei Monaten haben 14 Bestellungen erzeugt.
3. **Traffic.** Aktuell praktisch keiner.

**Reihenfolge ist entscheidend:** Traffic anschalten, bevor die Conversion stimmt,
verbrennt Geld — das ist bereits einmal passiert.

## Wirtschaftlicher Vorbehalt — korrigiert

Frühere Fassungen dieses Dokuments warnten, bei 19,95 € bleibe zu wenig
Deckungsbeitrag für Werbung. **Das war zu pessimistisch und basierte auf geschätzten
Kosten.**

Echte Zahlen: Poster 20×30 kostet im Einkauf **3,32 €** bei 19,95 € Verkaufspreis —
**16,63 € Deckungsbeitrag, 83 % Marge.** Ein gerahmtes 40×60 bringt **40,60 €**.
Ein CPA von 10–14 € ist damit tragfähig.

Offen bleibt, ob `unitCost` den Versand des POD-Partners enthält.

Der permanente Streichpreis 24,95 → 19,95 bleibt nach der EU-Omnibus-Richtlinie
heikel: Der durchgestrichene Preis muss der niedrigste der letzten 30 Tage sein.

⚠️ Ebenfalls zu klären: Die Produktseite zeigt **89 Bewertungen** bei **16
Bestellungen** insgesamt. Erfundene oder nicht verifizierte Bewertungen sind nach
UWG und Omnibus-Richtlinie unzulässig.

## Markenrechtlicher Vorbehalt

Die Poster heißen DOGUE (Vogue), PLAYDOG/PLAYCAT (Playboy), FURBES (Forbes),
NATIONAL PAWGRAPHIC (National Geographic). Alle vier Rechteinhaber gehen aktiv gegen
kommerzielle Markenparodien vor. Konsequenzen: Ad-Ablehnungen und Kontosperren bei
Meta/TikTok, Shopify-Takedowns, und auf diese Namen ist kein SEO aufbaubar.

Empfehlung: Designs behalten, Namen eigenständig machen. **Entscheidung liegt beim
Betreiber und ist offen.**

## Vorgehen

Siehe `docs/entscheidungen.md` für den Stand aller Entscheidungen und
`docs/offene-fragen.md` für das, was noch fehlt.

Phasen: 1) Aufräumen + Tokens · 2) Corporate Identity · 3) Personalizer ·
4) Seiten polieren · 5) SEO und Sichtbarkeit.

Arbeitsweise, die sich bewährt hat: **Design-Entscheidungen zuerst als HTML-Prototyp
zeigen**, erst nach Freigabe in Liquid umsetzen. Spart Runden.
