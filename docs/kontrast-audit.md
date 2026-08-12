# Kontrast-Audit der Farbschemata

Stand 12.08.2026. Berechnet nach WCAG 2.1 aus `config/settings_data.json`.
Alpha-Werte wurden über den jeweiligen Hintergrund gerechnet, transparente
Hintergründe über den Seitenhintergrund `#f5f5f5`.

Schwellen: **4,5:1** für Fließtext, **3,0:1** für große Überschriften.

## Ergebnis

| Schema | Text | Heading | Wo im Einsatz | Bewertung |
|---|---|---|---|---|
| `scheme-1` | 16,0:1 | 10,0:1 | Standard, viele Templates | ✅ in Ordnung |
| **`scheme-2`** | **2,2:1** | 8,7:1 | **Header** (`color_scheme_top`) | 🔴 **Text unter AA** |
| `scheme-3` | — | — | Header, nur bei transparentem Modus | ⚠️ alle Werte transparent |
| `scheme-4` | 4,1:1 | 4,1:1 | Fußzeile, Sale-Badge | 🟡 knapp unter AA |
| `scheme-5` | 5,2:1 | 5,2:1 | Fußzeile | ✅ |
| `scheme-7e76d070…` | 10,1:1 | 16,0:1 | FAQ, Kontakt, Weiterempfehlen | ✅ |
| `scheme-9fc3d33a…` | 6,0:1 | 6,0:1 | Startseite | ✅ |
| `scheme-6441…` | 16,0:1 | 16,0:1 | Produktseite | ✅ |
| `scheme-6` | 1,1:1 | 1,1:1 | nur in toten GemPages-Templates | — irrelevant |

## Der eine echte Befund: Header-Text

`scheme-2` setzt `#f5f5f5` auf `#76b2ae` — **2,2:1**. Das ist deutlich unter der
AA-Schwelle von 4,5:1 und betrifft die Kopfzeile auf **jeder Seite**.

Das ist keine reine Formalie: Petrol mit Weiß darauf ist bei hellem Umgebungslicht auf
dem Handy schwer zu lesen — und 78 % des Traffics ist mobil.

**Drei Wege, den Look zu erhalten:**

| Option | Wirkung | Kontrast |
|---|---|---|
| Petrol abdunkeln auf ca. `#3d7d78`, Weiß bleibt | Look bleibt fast identisch | ~4,6:1 |
| Dunkler Text auf dem hellen Petrol | Deutlich anderer Eindruck | ~7:1 |
| Unverändert lassen | — | 2,2:1 |

**Empfehlung: Option 1.** Gehört in die CI-Phase, weil es die Markenfarbe berührt —
das ist eine Design-Entscheidung, keine reine Fehlerbehebung.

## Nebenbefunde

**`scheme-4`** (Weiß auf Rot `#da3c24`): 4,1:1, knapp unter AA. Betrifft Sale-Badges
und einen Fußzeilen-Bereich. Ein leicht dunkleres Rot löst es.

**`scheme-3`** hat alle Werte auf `rgba(0,0,0,0)`, auch Text und Überschrift. Es dient
als Schema für den transparenten Header. Der ist derzeit **abgeschaltet**
(`enable_transparent_header_home` und `…_product` stehen auf `false`), also kein
aktiver Fehler — aber eine Falle: Wer den transparenten Header einschaltet, bekommt
unsichtbaren Text.

## Zwei zurückgenommene Aussagen

**Korrektur K5 — „Überschriften auf 76 % Deckkraft sind ein Accessibility-Problem."**
Falsch. `#030302c2` über `#f5f5f5` ergibt **10,0:1** und erfüllt damit AA und AAA
deutlich. Es ist ein **gestalterisches** Thema: Überschriften wirken weich und grau
statt klar. Für den Eindruck „hochwertig" trotzdem änderungswürdig, aber es ist kein
Barrierefreiheits-Mangel.

**Korrektur K6 — „Unsichtbare Überschriften auf Startseite, Kontakt und
Weiterempfehlen."** Falsch, und der Fehler lag in meiner Methode. Ich hatte die
Verwendung eines Schemas per Textsuche im Template ermittelt. Das trifft auch
Schema-Namen, die in ungenutzten Block-Einstellungen herumliegen.

Die tatsächliche Prüfung ergab:
- Kontakt, Weiterempfehlen und FAQ nutzen `scheme-7e76d070…` mit **16:1** bei
  Überschriften — einwandfrei.
- Der Startseiten-Hero nutzt zwar ein Schema mit rechnerisch schlechtem Wert, hat aber
  ein **Hintergrundbild** mit dunklem Overlay (`#27363b47`). Auf Bildern greift die
  Schema-Rechnung nicht.

**Lehre: Verwendung eines Schemas immer über die tatsächliche Block-Zuordnung prüfen,
nie über Textsuche. Und bei Sections mit Medien gilt die Schema-Farbe nicht.**

## Ein offener Punkt zum Ansehen

Im Startseiten-Hero stehen zwei Texte direkt untereinander auf demselben Bild:

| Text | Farbe |
|---|---|
| „NEWSLETTER" | `var(--color-foreground)` → `#1a1a1a`, fast schwarz |
| „Als Dank erhältst du einen 10 % Rabattcode…" | `var(--color-foreground-heading)` → `#f5f5f5`, fast weiß |

Fast schwarz und fast weiß auf demselben Hintergrund. Welcher der beiden schlecht
lesbar ist, hängt vom Bild ab — beide können nicht gleichzeitig gut sitzen.
**Beim nächsten Blick auf die Startseite prüfen.**
