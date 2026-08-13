# Theme-Landkarte

Orientierung im Fabric-3.1.0-Theme. Stand 12.08.2026.
**Vor jeder Theme-Änderung lesen** — spart die Suche nach dem richtigen Ort.

## Welches Template rendert welche Seite

| Seite | Template | Sections |
|---|---|---|
| Startseite | `templates/index.json` | `hero` · `product-list` · `hero` · `section` · `sp-before-and-after` · `sp-tiles` · `sp-marquee` · `section` |
| Produktseite | `templates/product.json` | `product-information` · `section` · `section` · `sp-marquee` · `product-list` |
| Kollektion | `templates/collection.json` | `section` · `main-collection` |
| Warenkorb | `templates/cart.json` | `main-cart` · `product-list` |
| Seite (Standard) | `templates/page.json` | `main-page` |
| Über uns | `templates/page.about-us.json` | `main-page` |
| FAQ | `templates/page.faqs-2.json` | `main-page` · `section` |
| Kontakt | `templates/page.kontakt2.json` | `main-page` · `section` |
| Bilder-Leitfaden | `templates/page.leitfaden.json` | `main-page` |
| Weiterempfehlen | `templates/page.weiterempfehlen-2.json` | `main-page` |

**Die toten GemPages- und Shogun-Templates sind am 13.08. entfernt** (`gem-`,
`gp-template`). Was jetzt in `templates/` liegt, ist entweder in Verwendung oder
Shopify-Standard.

## Navigation — die wichtigste Falle

**Fabric verlinkt die Fußzeilen-Seiten nicht über ein Shopify-Menü**, sondern über fest
gesetzte `button`-Blöcke im Theme. Wer nur die Menü-Objekte über die API prüft, hält
Seiten fälschlich für unverlinkt (Korrektur K3).

| Was | Wo |
|---|---|
| Hauptmenü | Shopify-Menü `main-menu`, eingebunden über `_header-menu` in `sections/header-group.json` |
| Fußzeile: Service-Links | **fest** in `sections/footer-group.json` → `section_LQwpa6` |
| Fußzeile: Rechtstexte | **fest** in `sections/footer-group.json` → `section_EenfMe` |
| Shopify-Menü `footer` | **wird vom Theme nicht verwendet** — Karteileiche. Zeigte bis 13.08. auf die stillgelegte Impressum-Fassung `copy-of-uber-uns`, ist jetzt auf `impressum` umgehängt |

**Regel: Navigation immer in beiden Quellen prüfen.**

## Produktseite im Detail

`templates/product.json` → `product-information` → `product-details`:

```
group_czKG4R          Sterne-SVG + getippte "(89)"   ← siehe R1 in bugs.md
product_title_46Kiht  Produkttitel
pw_photo_hint         Hinweis auf den Bilder-Leitfaden      (12.08. ergänzt)
buy_buttons_NmYpFG    Menge, In den Warenkorb, Express      ← teeinblue hängt hier
pw_trust_bar          Lieferzeit, Versand, Herkunft, Druck  (12.08. ergänzt)
payment_icons_VJTjti  Zahlungs-Icons
accordion_PeywHC      Produktbeschreibung, Pflegehinweise
```

**Es gibt keinen `price`- und keinen `variant-picker`-Block.** teeinblue rendert Preis
und Varianten selbst per JavaScript (B3 in `bugs.md`).

**teeinblue läuft als App-Embed**, nicht als App-Block. Es taucht **nirgends im
Theme-Code** auf, nur in `config/settings_data.json`, und injiziert sich selbst.
Nach jeder Änderung an `product.json` oder `sections/product-information.liquid`
prüfen, ob der Personalizer noch erscheint.

## Wo was liegt

| Ordner | Größe | Inhalt |
|---|---|---|
| `sections/` | 992 KB | 46 Sections — GemPages-Dateien am 13.08. entfernt |
| `snippets/` | 2,2 MB | 120 Snippets |
| `templates/` | 540 KB | 26 Templates, alle in Verwendung oder Shopify-Standard |
| `locales/` | 1,9 MB | 51 Sprachdateien, Standard von Shopify |
| `assets/` | 908 KB | CSS und JS |
| `blocks/` | 696 KB | 87 Blocks — die Bausteine, aus denen Templates bestehen |
| `config/` | 92 KB | `settings_schema.json` (Struktur), `settings_data.json` (Werte) |

## Installierte Apps

| App | Status | Bewertung |
|---|---|---|
| **teeinblue** | aktiv, App-**Embed** | Kern des Geschäfts. Rendert Preis und Varianten selbst. Fulfillment-Workflow gilt als veraltet |
| **merchOne** | aktiv | Einziger POD-Partner. Versand **nicht** im Einkaufspreis enthalten |
| **smind / Sections Pro** | aktiv | `sp-*` Sections, auf der Startseite genutzt |
| **Klaviyo** | aktiv | Unterbewertet — Warenkorbabbruch-Mails sind der billigste Hebel |
| **GemPages** | aktiv | ✅ **Theme-Reste am 13.08. entfernt, kein Objekt hängt mehr daran — die App kann deinstalliert werden** |
| PageFly, Shogun, Gelato, Section Star, Section Store, Dakaas | **deinstalliert** | 12.08.2026, Theme-Reste entfernt |
| Opus Cart Upsell | nicht mehr installiert | App-Embed-Eintrag liegt noch in `settings_data.json` (B12) |

**Nutzen ungeklärt:** Stack ($9,99/Monat) · TinySEO · AddressHero · Vidify ·
Collective · Messaging · Predis · CWILL Popup Email · Essential Announcer ·
**Customix Personalizer** (zweiter Personalizer!) · **EGO Cart Upsell** ($12,99)
und **AMP Slide Cart** parallel — eine davon reicht.

## Section-Präfixe erkennen

| Präfix | Herkunft | Status |
|---|---|---|
| kein Präfix | Fabric selbst | ✅ nutzen |
| `sp-` | Smind / Sections Pro | ✅ App installiert, teils genutzt |
| `smi-` | Smind | nur `smi-styles` ist aktiv |
| `gp-`, `gem-` | GemPages | ✅ am 13.08. vollständig entfernt |
| `ss-`, `shogun-` | Section Star / Store, Shogun | ✅ bereits entfernt |

**Ungenutzt, aber brauchbar** — schon bezahlt, liegt bereit:
`sp-trust-badges` · `sp-faq` · `sp-accordion` · `sp-count-down-banner` (Q4-Deadline)

## Wichtige Einzeldateien

| Datei | Warum wichtig |
|---|---|
| `config/settings_data.json` | Farben, Schriften, **alle App-Embeds** stehen hier |
| `sections/footer-group.json` | Die komplette Fußzeile inklusive aller Links |
| `sections/header-group.json` | Kopfzeile, bindet `main-menu` ein, setzt `scheme-2` |
| `sections/product-information.liquid` | 100 % blockgesteuert, rendert nichts von selbst |
| `snippets/cart-products.liquid:195` | Warenkorb blendet alle `_`-Properties aus — dort legen Personalizer ihre Vorschau-URL ab |
| `templates/page.json` | Standard für **jede** Seite ohne eigenes Template. Nichts Seitenspezifisches hineinschreiben |

## Farbschemata

13 Stück in `settings_data.json`. Vollständig durchgerechnet in `kontrast-audit.md`.

| Schema | Verwendung | Achtung |
|---|---|---|
| `scheme-1` | Standard, viele Templates | Heading auf 76 % Deckkraft — 10:1, optisch weich |
| `scheme-2` | **Header** | 🔴 Text 2,2:1 — siehe B1 |
| `scheme-3` | transparenter Header (aus) | ⚠️ alle Werte transparent |
| `scheme-4` | Fußzeile, Sale-Badge | 🟠 4,1:1 |
| `scheme-5` | Fußzeile | ✅ |

## Technische Eigenheiten

Stehen in `.claude/skills/petworld-design/SKILL.md` unter „Fabric-Eigenheiten" —
`closest.page.title`, leeres `block_order`, `doc`-Blöcke bei Referenzsuchen,
verfügbare Icons, gültige `type_preset`-Werte.
