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
| GemPages | aktiv | **auf keiner Live-Seite genutzt** — Kandidat zum Deinstallieren |
| PageFly | aktiv | **auf keiner Live-Seite genutzt** — Kandidat zum Deinstallieren |
| Shogun | Reste im Theme | **auf keiner Live-Seite genutzt** — Kandidat zum Deinstallieren |
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
- **Vor dem Löschen der Page-Builder-Dateien** muss im Shopify-Admin geprüft werden, ob
  eine echte Seite ein `gp-template` zugewiesen hat. Es gibt 12 solcher Templates.

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

## Wirtschaftlicher Vorbehalt

Bei 19,95 € pro Poster bleibt nach Druck, Versand und Zahlungsgebühren wenig
Deckungsbeitrag. Ein CPA von 15–25 € ist in dieser Nische normal — damit ist bezahlte
Werbung bei diesem Preis kaum finanzierbar. Vergleichbare Shops (Crown & Paw,
West & Willow) verkaufen bei 50–90 $.

Der permanente Streichpreis 24,95 → 19,95 ist außerdem nach der EU-Omnibus-Richtlinie
heikel: Der durchgestrichene Preis muss der niedrigste der letzten 30 Tage sein.

**Das ist keine Design-Frage.** Sie muss trotzdem beantwortet werden, sonst optimieren
wir einen Shop, der sich keinen Traffic leisten kann.

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
