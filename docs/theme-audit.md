# Theme-Audit PetWorld — Stand 11.08.2026

Basis: Theme-Export `petworldatbackup110826`, unverändert als Commit `cacbd97` im Repo.

## Ausgangslage

| | |
|---|---|
| Theme | **Fabric 3.1.0** (Shopify, First-Party) |
| Generation | Block-basiert (Horizon-Generation), nicht Dawn |
| Dateien | 557 · 116 Sections · 87 Blocks · 130 Snippets · 56 Templates |
| Sprachen | 51 Locale-Dateien (Standard) |

Das Basis-Theme ist gut. Fabric ist modern, schnell und sauber gebaut. Die Probleme
liegen nicht im Theme, sondern in dem, was darüber gestapelt wurde.

---

## Befund 1 — Preis und Varianten kommen ausschließlich aus teeinblue

**Schweregrad: mittel**

> **Korrektur 11.08.2026:** Ursprünglich als "Produktseite ohne Preis" notiert. Ein
> Screenshot der Live-Seite zeigt: Preis (€19,95, Streichpreis, Sale-Badge) und
> Varianten (Rahmen, Größen) **werden angezeigt** — teeinblue rendert sie selbst.
> Der Befund bleibt bestehen, aber als Robustheits- und SEO-Thema, nicht als Notfall.

`templates/product.json` → Section `product-information` → `product-details` enthält:

```
group (icon: price_tag + Text "(89)")
product-title
buy-buttons  → quantity, add-to-cart, accelerated-checkout
payment-icons
accordion    → "Produktbeschreibung", "Pflegehinweise"
```

Kein `price`-Block. Kein `variant-picker`-Block. Beide existieren im Theme
(`blocks/price.liquid`, `blocks/variant-picker.liquid`), sind aber nicht platziert.

`sections/product-information.liquid` rendert nichts fest — die Section ist zu 100 %
block-gesteuert (`{% content_for 'blocks' %}`). Es gibt also keinen Fallback.

**Folge:** Preis und Größenauswahl kommen ausschließlich aus dem teeinblue-App-Embed.

- Beides erscheint erst, nachdem teeinblue-JS geladen und initialisiert hat
- Bei langsamer Verbindung oder App-Fehler: Produktseite mit Titel und Kaufen-Button,
  ohne Preis und ohne Auswahl
- Preis fehlt im server-gerenderten HTML → relevant für Google Merchant Center,
  Product-Schema und Preis-Snippets in der Suche

**Der Block `group` mit `price_tag`-Icon und dem Text `(89)`** ist die Bewertungsanzahl.
Auf der Live-Seite stehen davor 4,5 Sterne, die eine Bewertungs-App rendert. Das Icon
`price_tag` passt nicht dazu und gehört auf ein Stern-Icon geändert.

**Zu tun:** Prüfen, ob teeinblue einen App-Block statt eines Embeds anbietet. Falls ja,
umstellen — dann ist die Platzierung im Theme-Editor steuerbar und wir können Preis,
Varianten und Trust-Elemente gezielt drumherum anordnen.

---

## Befund 2 — Drei Page-Builder gleichzeitig aktiv

**Schweregrad: hoch**

App-Embeds laut `config/settings_data.json`:

| App | Status | Im Theme |
|---|---|---|
| GemPages | **an** | 60 `gp-section-*`, `gp-global.css` (68 KB), 52 Verweise auf `assets.gemcommerce.com` |
| PageFly | **an** | App-Embed aktiv |
| Shogun | — | 5 `shogun-*` Sections, 3 Layouts, eigene Templates |
| smind / Sections Pro | **an** | `sp-*` Sections, `smi-swiper-bundle.min.js` (109 KB), `smi-footer-1.min.css` (29 KB) |
| Opus Cart Upsell | **an** | Cart-Drawer |
| teeinblue | **an** | Personalizer (App-Embed, injiziert sich selbst) |
| Dakaas Store Effects | aus | — |

**Die Live-Templates nutzen davon nichts.** Homepage und Produktseite laufen auf
nativen Fabric-Sections plus den `sp-*`-Sections von smind:

```
index.json    hero · product-list · hero · section ·
              sp-before-and-after · sp-tiles · sp-marquee · section

product.json  product-information · section · section · sp-marquee · product-list
```

> **Korrektur 12.08.2026 — die Prüfung über den Shopify-Connector hat ergeben, dass
> „auf keiner Live-Seite verwendet" für GemPages falsch war.** Die Zuweisung passiert
> über `templateSuffix` im Admin, nicht in den Theme-Templates. Details unten.

### Was tatsächlich womit läuft

| Objekt | Template | Folge |
|---|---|---|
| **Alle Produkte** | nativ (`templateSuffix` leer) | ✅ unberührt |
| Kollektion BESTSELLER | `gp-template-562355879467287637` | Template **existiert nicht im Theme** → Rückfall auf `collection.json` ✅ |
| Kollektion POSTER | dieselbe, ebenfalls fehlend | ✅ läuft bereits nativ |
| **5 Seiten** | `gp-template-*`, **existieren** | ⚠️ **brechen beim Deinstallieren** |

Die fünf betroffenen Seiten: `/pages/faq`, `/pages/kontakt`, `/pages/ueber-uns`,
`/pages/weiterempfehlen`, `/pages/bild-leitfaden` — alle veröffentlicht.

### Aber: Diese fünf Seiten sind verwaist

Sie sind in **keinem Menü** verlinkt. Der einzige Ort im gesamten Theme, der auf sie
zeigt, ist `sections/gp-global-section-562366337729430539.liquid` — die GemPages-eigene
Kopf-/Fußzeile, die nur auf GemPages-Templates gerendert wird.

**Es ist eine geschlossene Insel:** fünf Seiten, die sich gegenseitig verlinken, vom
restlichen Shop aus aber nicht erreichbar.

Gleichzeitig existiert zu jeder von ihnen eine **native Zweitfassung** (`faqs-2`,
`kontakt2`, `about-us`, `weiterempfehlen-2`, `leitfaden`) — ebenfalls veröffentlicht,
ebenfalls in keinem Menü.

**Zwei Konsequenzen:**

1. **Kunden erreichen weder FAQ noch Über uns, Kontakt, Bild-Leitfaden oder
   Weiterempfehlen.** Das Hauptmenü führt ausschließlich zu Kollektionen, die Fußzeile
   nur zu den fünf Rechtstexten. Besonders bitter beim **Bild-Leitfaden** — die
   Anleitung für ein gutes Foto ist die Voraussetzung für ein gutes Poster.
2. **Doppelte Inhalte im Index.** Beide Fassungen sind veröffentlicht und
   crawlbar → SEO-Kannibalisierung.

### Daraus folgt für das Aufräumen

| App | Verdikt |
|---|---|
| **PageFly** | ✅ **Sofort deinstallierbar** — kein Objekt referenziert sie |
| **Shogun** | ✅ **Sofort deinstallierbar** — kein Objekt referenziert sie |
| **GemPages** | ⚠️ Erst die 5 Seiten nativ nachbauen und Weiterleitungen setzen, dann deinstallieren |

---

## Befund 3 — Karteileichen

- **31 von 56 Templates** sind Backups von Page-Buildern (`gem-`, `gp-template`, `shogun`)
- **2,4 MB** allein an `gp-section-*.liquid`
- `sections/sp-trust-badges.liquid` und `sp-faq.liquid` existieren, sind aber auf keiner
  Live-Seite platziert — Trust-Elemente liegen also ungenutzt herum

---

## Befund 4 — Design-Tokens

**Schriften** (`config/settings_data.json`):

```
type_body_font        asap_n5     type_heading_font   asap_n6
type_subheading_font  asap_n5     type_accent_font    asap_n4
```

Eine einzige Schriftfamilie (**Asap**) für alle vier Rollen, unterschieden nur durch
Strichstärke. Das ist der Hauptgrund, warum der Shop generisch wirkt — es gibt keine
typografische Hierarchie, nur unterschiedlich fettes Grau.

**Farben** (13 Schemata, davon `scheme-3` komplett transparent = defekt/ungenutzt):

| Rolle | Wert |
|---|---|
| Hintergrund | `#f5f5f5` |
| Text | `#1a1a1a` |
| Primär / Akzent | `#76b2ae` (gedämpftes Petrol) |
| Buttons | `#030302` auf Weiß |
| Sale / Alarm | `#da3c24` |

Die Palette selbst ist brauchbar — ruhig, warm-neutral, mit Petrol als Akzent.

**Aber:** `foreground_heading` ist `#030302c2` — Schwarz mit 76 % Deckkraft.
Überschriften werden also absichtlich ausgegraut. Das kostet Kontrast, wirkt
verwaschen und ist ein Accessibility-Problem.

---

## Was der Export beantwortet

| Frage | Antwort |
|---|---|
| 1 — Theme | Fabric 3.1.0, First-Party, block-basiert |
| 3 — Code angefasst? | Nicht von Hand. Aber massiv von Apps überlagert |
| 4 — Apps | GemPages, PageFly, Shogun, smind, Opus Cart Upsell, teeinblue |
| 20 — Marke | Asap · Petrol `#76b2ae` · Schwarz · Off-White · Rot `#da3c24` |

**Weiterhin offen:** Analytics-Zahlen (6–12), Stückkosten (13), Preisentscheidung (14),
Markennamen (19), Referenz-Shops (21).

---

## Empfohlene Reihenfolge

1. **Preis + Varianten-Picker nativ auf die PDP** — kleinster Aufwand, größte Wirkung
2. **GemPages, PageFly, Shogun deinstallieren** (nach Template-Prüfung) und
   Theme-Leichen entfernen
3. **Typo-Hierarchie**: zweite Schriftfamilie für Headlines, Heading-Deckkraft auf 100 %
4. **Homepage neu strukturieren**: zwei Heroes direkt hintereinander auflösen,
   Trust-Bar und Reviews einbauen
5. **Bundles und Foto-Reviews** — AOV und Social Proof
