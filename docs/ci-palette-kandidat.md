# CI-Palette — Kandidat für den Farbwechsel

Vom Betreiber am **13.08.2026** übergeben, als Bild aus einem Design-Post
(Wasserzeichen „Uxintace"). **Noch nicht entschieden, noch nicht im Einsatz** —
liegt hier für die CI-Phase bereit.

Sichtbar als [`ci-palette-kandidat.svg`](ci-palette-kandidat.svg).

## Die sechs Töne

| Hex | Charakter |
|---|---|
| `#E7F5DC` | fast weiß, sehr heller Grünstich |
| `#CFE1B9` | helles Salbei |
| `#B6C99B` | mittleres Salbei |
| `#98A77C` | gedecktes Oliv |
| `#88976C` | dunkleres Oliv |
| `#728156` | dunkelster Ton, Moosgrün |

Eine **monochrome Salbei-Skala** — sechs Abstufungen einer einzigen Farbfamilie,
kein Kontrast- oder Akzentton dabei.

## Kontrastrechnung — vor dem Einsatz lesen

Berechnet nach WCAG 2.1, dieselbe Methode wie in `kontrast-audit.md`.

| Ton | vs. Weiß `#fff` | vs. Off-White `#f5f5f5` | vs. Schwarz `#030302` |
|---|---|---|---|
| `#E7F5DC` | 1,14 | 1,04 | **18,17** |
| `#CFE1B9` | 1,39 | 1,27 | **14,86** |
| `#B6C99B` | 1,78 | 1,63 | **11,61** |
| `#98A77C` | 2,58 | 2,36 | **8,01** |
| `#88976C` | 3,14 | 2,88 | **6,57** |
| `#728156` | 4,21 | 3,86 | **4,90** |

**Kein einziger Ton trägt weißen Text nach WCAG AA.** Selbst der dunkelste kommt
gegen reines Weiß nur auf 4,21 und gegen unser Off-White auf 3,86 — beide unter der
Schwelle von 4,5.

Auch der dunkelste Ton **als Text** auf den hellen Tönen reicht nicht:
`#728156` auf `#E7F5DC` ergibt nur 3,71.

### Was daraus folgt

1. **Das ist eine Flächenpalette, keine Textpalette.** Sie funktioniert für
   Hintergründe, Karten, Sektionen — nicht für Text auf farbigem Grund.
2. **Ein dunkler Textanker muss dazu.** Das vorhandene `#030302` passt: gegen jeden
   der sechs Töne zwischen 4,90 und 18,17, also durchgehend AA, meist AAA.
3. **Ein Akzentton fehlt.** Für Buttons, Preise, Sale-Badges braucht es eine zweite
   Farbe. Das heutige Rot `#da3c24` ist ein möglicher Kandidat, muss aber gegen die
   Grüntöne neu gerechnet werden.
4. ⚠️ **Fehler B1 würde sich sonst wiederholen.** Der heutige Header setzt weißes
   `#f5f5f5` auf Petrol `#76b2ae` — 2,2:1. Wer die neue Palette 1:1 in dieselben
   Farbschemata einsetzt, bekommt bei `#98A77C` mit 2,36 fast exakt denselben Fehler.

## Vergleich mit der heutigen CI

| | Hex | vs. Weiß | vs. Schwarz |
|---|---|---|---|
| Petrol | `#76b2ae` | 2,40 | 8,60 |
| Schwarz | `#030302` | 20,63 | — |
| Off-White | `#f5f5f5` | 1,09 | 18,93 |
| Rot | `#da3c24` | 4,51 | 4,57 |

Petrol und die mittleren Grüntöne liegen in derselben Helligkeitsklasse — der Wechsel
wäre ein Farbton-Wechsel, keine Helligkeitsumstellung. Die bestehenden Farbschemata
könnten die Struktur behalten.

## Offen

- Passt Salbeigrün zum Sortiment? Haustier-Poster, warme Motive — Grün wirkt ruhig
  und natürlich, aber auch zurückhaltend. Gegenprobe an `heybalu.com` (E12/O4).
- Welcher Akzentton für Buttons und Preise?
- Bleibt Asap als Schrift, oder kommt der Wechsel zusammen mit der zweiten
  Schriftfamilie?

Gehört in die **CI-Phase** — nach Personalizer und Design, siehe Reihenfolge in
`CLAUDE.md`.
