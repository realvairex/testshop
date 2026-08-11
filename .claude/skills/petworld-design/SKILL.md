---
name: petworld-design
description: Design- und Frontend-Regeln für den PetWorld-Shopify-Shop (Fabric 3.1.0). Verwenden, sobald am Theme gestaltet wird — Sections, Blocks, CSS, Tokens, Animationen, Produktseite, Personalizer-Umfeld.
---

# PetWorld Design-System

Regeln für jede gestalterische Arbeit an diesem Shop. Sie ergänzen `CLAUDE.md`,
überschreiben es nie.

## Plattform-Grenzen — nicht verhandelbar

Das hier ist **kein React-Projekt**. Häufige Fehlannahmen:

| Nicht verfügbar | Stattdessen |
|---|---|
| React, JSX, Komponenten | Liquid Sections und Blocks |
| Framer Motion | **Motion One** (motion.dev, Vanilla-JS) oder CSS |
| Tailwind, Build-Step, PostCSS | Handgeschriebenes CSS in `assets/` |
| npm-Pakete im Frontend | Alles muss ohne Bundler laufen |
| 21st.dev-Komponenten kopieren | Als visuelle Vorlage nutzen, nach Liquid portieren |

Fabric 3.1.0 ist **block-basiert** (Horizon-Generation). Sections definieren ihr Schema,
Blocks werden über `{% content_for 'blocks' %}` gerendert. Neue Bausteine gehören nach
`blocks/`, nicht als Hardcode in Sections — sonst kann der Betreiber sie im Theme-Editor
nicht mehr anordnen.

## Token-Architektur

Drei Schichten, als CSS Custom Properties:

```
primitive   →  --pw-teal-500: #76b2ae        Rohwerte, aus settings_schema.json
semantic    →  --pw-accent: var(--pw-teal-500)   Rollen
component   →  --pw-btn-bg: var(--pw-accent)     Bauteil-spezifisch
```

**Regeln:**
- Nie ein Farb-Literal direkt in eine Komponente schreiben. Immer über die semantische
  Ebene.
- Die primitive Ebene wird an `config/settings_schema.json` angebunden, damit Farben im
  Theme-Editor änderbar bleiben, ohne dass jemand Code anfasst.
- Spacing auf einem **8px-Raster**. Ausnahmen begründen.

## Farbe

Bestand aus dem Live-Theme:

| Rolle | Wert | Anmerkung |
|---|---|---|
| Hintergrund | `#f5f5f5` | |
| Text | `#1a1a1a` | |
| Akzent | `#76b2ae` | Petrol. Für Text auf Hell zu kontrastarm — abgedunkelte Variante nutzen |
| Buttons | `#030302` | |
| Sale/Alarm | `#da3c24` | Sehr heiß. Gedämpfte Variante wirkt hochwertiger |

**Zu korrigieren:**
- `foreground_heading` steht auf `#030302c2` — Schwarz mit 76 % Deckkraft. Überschriften
  gehören auf volle Deckkraft. Kontrast- und Accessibility-Problem.
- 13 Farbschemata, davon eines (`scheme-3`) komplett transparent und damit defekt.
  Auf 4–5 sinnvolle reduzieren.

⚠️ **Offen (O4):** Ob die Palette so bleibt, ist noch nicht entschieden. Bis dahin
mit dem Bestand arbeiten und Vorschläge als Prototyp zeigen.

## Typografie

**Der zentrale Befund:** Aktuell ist **Asap** für alle vier Rollen gesetzt — Body,
Heading, Subheading, Accent — unterschieden nur durch Strichstärke. Das ist der
Hauptgrund, warum der Shop generisch wirkt. Es gibt keine Hierarchie, nur unterschiedlich
fettes Grau.

**Zu tun:** Zweite Schriftfamilie für Headlines, echte Typo-Skala, Strichstärken
bewusst einsetzen.

⚠️ **Offen (O4):** Konkrete Schriftwahl noch nicht entschieden.

Unabhängig davon gilt:
- Fließtext bei etwa 65 Zeichen Zeilenlänge
- Überschriften `text-wrap: balance`
- Versal-Labels mit leichtem `letter-spacing`
- `font-variant-numeric: tabular-nums` überall, wo Zahlen untereinander stehen (Preise!)

## Bewegung

**Motion One**, nicht Framer Motion. Und sparsam.

- Scroll-Reveals dezent, kurze Distanz, keine großen Sprünge
- Hover-Zustände auf allem Klickbaren
- `prefers-reduced-motion` immer respektieren
- **Nichts animieren, was den LCP verzögert.** Der Hero und die Produktbilder müssen
  sofort da sein.

Der Shop hat ein Geschwindigkeitsproblem — Animation darf es nicht verschlimmern.

## teeinblue-Umfeld

Der Personalizer läuft als **App-Embed** und injiziert sich per JavaScript selbst.
Daraus folgt:

- **Die Produktseite nie so umbauen, dass der Personalizer die Ankerstelle verliert.**
  Nach jeder Änderung an `templates/product.json` oder
  `sections/product-information.liquid` prüfen, ob er noch erscheint.
- Die nativen `price`- und `variant-picker`-Blöcke sind bewusst nicht platziert —
  teeinblue rendert beides selbst. Nicht ohne Prüfung hinzufügen, sonst stehen zwei
  Preise nebeneinander.
- Falls teeinblue eine **App-Block**-Einbindung anbietet: umstellen. Dann ist die
  Platzierung im Theme-Editor steuerbar.

**Ziel-Ablauf im Personalizer** (Entscheidung E7): Schritt für Schritt. Zuerst nur der
Foto-Upload, dann die nächste Option, dann die übernächste. Umzusetzen über
Bedingungsketten in teeinblue, nicht im Theme.

## Konversions-Muster für dieses Sortiment

Personalisiertes Print-on-Demand hat eigene Regeln:

1. **Vorher/Nachher gewinnt.** Kundenfoto neben fertigem Poster schlägt jedes
   Lifestyle-Bild.
2. **Der Wow-Moment muss zuerst kommen.** Foto hochladen → eigenes Tier sehen → dann
   Details. Nie umgekehrt.
3. **Vorschau immer sichtbar.** Sticky, sodass jede Änderung sofort wirkt.
4. **Kundenfotos schlagen Sternebewertungen.** Bei personalisierten Produkten will man
   sehen, was andere bekommen haben.
5. **Bundles statt Rabatte.** 2 Poster −15 %, 3 −25 % ist bei ~20 € Warenkorb der
   stärkste Hebel auf den Bestellwert.
6. **Rahmen-Upsell mit Bild und Preis.** Nie als nackter Textbutton.
7. **Lieferzeit und Sicherheit am Kaufen-Button.** Nicht nur Zahlungs-Icons.
8. **Rechtliche Hinweise warm formulieren.** Der Widerrufsausschluss nach §18 FAGG ist
   Pflicht — aber er darf nicht wie eine Warnung wirken. Mit einer Design-Bestätigung
   koppeln.

## Sprache und Tonfall

Deutsch, Duzen, Österreich als Hauptmarkt.

- **Kundensprache, nicht Systemsprache.** „Rahmen wählen", nicht „Verfügbare Produkte".
  „Schriftfarbe", nicht „Primärfarbe".
- Warm und persönlich — es geht um das Haustier von jemandem.
- Buttons sagen, was passiert.
- Fehlermeldungen erklären den Fehler und den Weg heraus.
- Keine Superlative, keine künstliche Dringlichkeit außer bei echten Fristen
  (Weihnachts-Deadline ist echt).

## Vor dem Abschluss prüfen

- [ ] Erscheint der teeinblue-Personalizer noch?
- [ ] Alle Farben über Tokens, keine Literale in Komponenten?
- [ ] Auf 375px Breite getestet?
- [ ] Tastatur-Fokus sichtbar?
- [ ] Kontrast ausreichend, besonders bei Überschriften?
- [ ] Bilder lazy geladen, außer dem LCP-Bild?
- [ ] Keine neue Render-blockierende Ressource?
- [ ] Blöcke im Theme-Editor anordenbar geblieben?
