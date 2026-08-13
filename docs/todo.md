# Aktuelle TODO

Stand 12.08.2026. Reihenfolge ist bewusst gewählt: **Conversion vor Traffic.**
Bei 26 Sessions im Monat bringt Werbung nichts, solange 0,14 % konvertieren.

---

## ✅ Erledigt

| | |
|---|---|
| Theme-Export als Baseline gesichert | Commit `cacbd97` |
| Vollständiges Audit | Theme, Personalizer, Zahlen |
| Shogun + PageFly aus dem Theme entfernt | 17 Dateien, Includes bereinigt |
| 4 verwaiste `ss-`Sections + ungenutzte Assets entfernt | Section Star / Store |
| GemPages-Seiteninhalte archiviert | `docs/archiv-gempages/` |
| `Danke` (40 €) und `DANKE26` deaktiviert | gegengeprüft |
| Apps deinstalliert | PageFly, Gelato, Section Star, Section Store, Dakaas |
| Arbeitsweise + Entscheidungen dokumentiert | `CLAUDE.md`, `entscheidungen.md` |

---

## 🔨 Bei mir — Theme

### Jetzt: Seiten bereinigen

> Korrigiert am 12.08.: Die Fußzeile verlinkt alle fünf Service-Seiten bereits — über
> `button`-Blöcke in `footer-group.json`, nicht über ein Shopify-Menü. Siehe Korrektur
> K3 in `entscheidungen.md`. Die Aufgabe ist damit kleiner als geplant.

- [x] **`page.about-us.json` angelegt** — der Über-uns-Text lag im Standard-Template
      `page.json` und wurde dadurch auf jeder Seite ohne eigenes Template ausgespielt
- [x] **`page.json` neutralisiert** — zeigt jetzt Seitentitel und Seiteninhalt
- [x] **301-Weiterleitungen** der fünf GemPages-URLs auf die nativen Fassungen (13.08.)
- [x] **Doppeltes Impressum zusammenführen** — `copy-of-uber-uns` stillgelegt und
      umgeleitet, Menüeintrag umgehängt (13.08.)
- [x] **GemPages-Dateien entfernt** (13.08.) — 96 Dateien: 60 Sections, 24 Templates,
      6 Snippets, 5 Layouts, `gp-global.css`. Tote `templateSuffix`-Verweise im Shop
      mitbereinigt (B11). **Die App darf jetzt deinstalliert werden**
- [ ] Nach dem Live-Gang stichprobenartig prüfen, ob die sechs Weiterleitungen im
      Browser wirklich 301 liefern — aus dieser Umgebung nicht prüfbar (U2)
- [ ] Bilder-Leitfaden zusätzlich direkt an den Foto-Upload auf der Produktseite legen

### Produktseite

- [x] **Foto-Hinweis mit Link auf den Bilder-Leitfaden** unter dem Produkttitel
- [x] **Vertrauens-Leiste** unter dem Kaufen-Button: Lieferzeit 5 Werktage ·
      Gratisversand ab 50 € · Produktion in Europa · Einzelfertigung.
      Nativ aus Fabric-Blöcken, nicht über eine App
- [ ] ⚠️ **„ab 50 €" auf „ab 35 €" ändern**, sobald der Versand umgestellt ist —
      sonst steht eine falsche Angabe auf der Seite
- [ ] Gratisversand-Fortschritt im Warenkorb („noch X € bis Gratisversand")
- [ ] Sticky Add-to-Cart auf Mobil — 78 % des Traffics ist mobil
- [ ] `price`- und `variant-picker`-Block prüfen (teeinblue rendert beides selbst)
- [ ] FAQ auf der Produktseite
- [ ] Prüfen, ob zusätzliche Galeriebilder neben der teeinblue-Vorschau möglich sind
- [ ] Stern-SVG und getippte „(89)" entfernen — siehe E11, kommt zur Design-Phase

### Startseite (Befunde aus der Sichtprüfung, siehe `startseite-befunde.md`)

- [ ] **Call-to-Action im Hero** — aktuell gibt es dort keinen einzigen Button
- [ ] **Vorher/Nachher im Hero** — der Hero zeigt fremde Tiere, nicht die Idee
- [ ] Hero verdichten, erste Produktkachel auf Mobil früher sichtbar
- [ ] Flagge und Sprachkürzel oben rechts angleichen (AT-Flagge neben „DE")

### Danach: Design-System

- [ ] **CI-Farbwechsel prüfen** — Salbei-Palette vom Betreiber übergeben (13.08.),
      liegt in `ci-palette-kandidat.md`. Achtung: reine Flächenpalette, kein Ton
      trägt weißen Text. Braucht dunklen Textanker und einen Akzentton
- [ ] Token-Architektur anlegen (primitive → semantic → component)
- [ ] Heading-Deckkraft von `#030302c2` auf 100 % korrigieren
- [ ] Zweite Schriftfamilie für Headlines — aktuell ist alles Asap
- [ ] 13 Farbschemata auf 4–5 reduzieren, `scheme-3` ist komplett transparent

---

## 👤 Bei dir — Shopify-Admin

### Sofort

- [ ] **Live-Theme duplizieren** als Sicherung im Admin
- [ ] **Versandschwelle auf 35 €** (Österreich und Deutschland) — Entscheidung E10 steht.
      Am 13.08. gegengeprüft: steht **noch bei 50 €** (AT 5,50 €, DE 4,00 €)
- [ ] ✅ **GemPages kann jetzt deinstalliert werden** — Seiten umgehängt, Theme-Dateien
      entfernt, keine `templateSuffix`-Verweise mehr (13.08.)
- [ ] Drei verwaiste **Gelato-Versandprofile** löschen (B22)
- [ ] `Weihnachten2025`-Code auf abgelaufen setzen
- [ ] KALENDAR und PUZZLE aus dem Kundenkonto-Menü nehmen, solange sie leer sind
- [ ] Puzzle-Produkte von `ARCHIVED` auf `DRAFT` — sie sind geplant, nicht eingestellt

### Apps aufräumen

- [x] PageFly, Gelato, Section Star, Section Store, Dakaas deinstalliert (12.08.)

Ungeklärt, ob überhaupt genutzt: **Stack** ($9,99/Monat), **TinySEO**, **AddressHero**,
**Vidify**, **Collective**, **Messaging**, **Predis**, **CWILL Popup Email**,
**Essential Announcer**, **Customix Personalizer** (zweiter Personalizer!).

- [ ] Von **EGO Cart Upsell** ($12,99) und **AMP Slide Cart** eine behalten
- [ ] CWILL vs. Klaviyo — Klaviyo kann Popups selbst
- [ ] Alte Bestellungen stornieren oder archivieren, damit sie die Auswertungen
      nicht weiter verfälschen

### Informationen, die ich noch brauche

- [ ] 🔒 **Bleibt der Preis bei 19,95 €?** Nie beantwortet
- [ ] 🔒 **Bundle-Staffel**: Vorschlag 2 Poster −15 %, 3 Poster −25 %. Passt das?
      `FREUNDE10` (10 % ab 2 Stück) existiert bereits, aber nur als Code
- [ ] **Werbebudget Dezember–Februar** — für die exakte Kosten-pro-Bestellung-Rechnung
- [ ] **merchOne-Versandkosten** pro 20×30-Poster nach Österreich
- [ ] **Echte Produktfotos** — Poster an der Wand, in der Hand, Unboxing
- [ ] **Referenz-Shops** für die Design-Richtung (heybalu.com ist als Inspiration bekannt)

---

## 🎨 Bei dir — teeinblue

Vorlage liefere ich, sobald die Produktseite steht.

- [ ] **Foto-Upload an die erste Stelle**
- [ ] Pflichtfelder auf **zwei** reduzieren (Foto + Name), Rest vorbelegen
- [ ] **Bedingungskette** aufbauen für den Schritt-für-Schritt-Ablauf
- [ ] **Rahmen-Optionen mit Miniaturbild und Preisaufschlag**
- [ ] Beschriftungen in Kundensprache — „Rahmen wählen" statt „Verfügbare Produkte"
- [ ] Veralteten Platzhalter „AUGUST 2025" ersetzen
- [ ] Haftungstext freundlicher formulieren
- [ ] ⚠️ **Testen: Kann ein Bild-Upload als Bedingung dienen?** Davon hängt ab, ob
      Schritt 1 des Wizards nativ funktioniert

---

## ⏸️ Bewusst vertagt

| Thema | Wann wieder aufgreifen |
|---|---|
| **Fake-Bewertungen** (E11) | In der Design-Phase |
| **Markennamen** (E12) | Wenn die Produktseiten ohnehin überarbeitet werden — siehe `markennamen.md` |
| **Customily statt teeinblue** (O3) | Wenn geklärt ist, was am Fulfillment genau hakt |
| **Eigener Personalizer** (Z1) | Frühestens bei deutlich höherem Umsatz |

---

## 🚦 Noch nicht dran: Marketing

Erst wenn die Startlinie erreicht ist:

| Kennzahl | Jetzt | Ziel vor Werbestart |
|---|---|---|
| Conversion Rate | 0,14 % | **≥ 1,0 %** |
| Warenkorbwert | ~25 € | **≥ 40 €** |
| Personalizer-Abschlussquote | unbekannt | gemessen |

Danach: SEO-Grundlagen, Klaviyo-Flows (Warenkorbabbruch zuerst), organisches
TikTok vor bezahlter Werbung.
