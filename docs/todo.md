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
- [ ] 301-Weiterleitungen der fünf GemPages-URLs auf die nativen Fassungen
- [ ] Doppeltes Impressum zusammenführen (`impressum` und `copy-of-uber-uns`)
- [ ] Erst danach: GemPages-Dateien entfernen — 60 Sections, 31 Templates, `gp-global.css`
- [ ] Bilder-Leitfaden zusätzlich direkt an den Foto-Upload auf der Produktseite legen

### Danach: Produktseite

- [ ] `price`- und `variant-picker`-Block prüfen und sauber verdrahten
- [ ] Trust-Bar mit `sp-trust-badges` (liegt ungenutzt im Theme, schon bezahlt)
- [ ] **Lieferzeit 5 Werktage** an den Kaufen-Button
- [ ] Gratisversand-Hinweis („noch X € bis Gratisversand")
- [ ] Sticky Add-to-Cart auf Mobil — 78 % des Traffics ist mobil
- [ ] FAQ auf der Produktseite mit `sp-faq`
- [ ] Bewertungsblock vorbereiten (Inhalt später, siehe E11)
- [ ] Prüfen, ob zusätzliche Galeriebilder neben der teeinblue-Vorschau möglich sind

### Danach: Design-System

- [ ] Token-Architektur anlegen (primitive → semantic → component)
- [ ] Heading-Deckkraft von `#030302c2` auf 100 % korrigieren
- [ ] Zweite Schriftfamilie für Headlines — aktuell ist alles Asap
- [ ] 13 Farbschemata auf 4–5 reduzieren, `scheme-3` ist komplett transparent

---

## 👤 Bei dir — Shopify-Admin

### Sofort

- [ ] **Live-Theme duplizieren** als Sicherung im Admin
- [ ] **Versandschwelle auf 35 €** (Österreich und Deutschland) — Entscheidung E10 steht
- [ ] **GemPages noch NICHT deinstallieren** — erst wenn ich die Seiten umgehängt habe
- [ ] `Weihnachten2025`-Code auf abgelaufen setzen
- [ ] KALENDAR und PUZZLE aus dem Kundenkonto-Menü nehmen, solange sie leer sind
- [ ] Puzzle-Produkte von `ARCHIVED` auf `DRAFT` — sie sind geplant, nicht eingestellt

### Apps aufräumen — welche nutzt ihr wirklich?

Ungeklärt: **Stack** ($9,99/Monat), **TinySEO**, **AddressHero**, **Vidify**,
**Collective**, **Messaging**, **Predis**, **CWILL Popup Email**,
**Essential Announcer**, **Customix Personalizer** (zweiter Personalizer!).

- [ ] Von **EGO Cart Upsell** ($12,99) und **AMP Slide Cart** eine behalten
- [ ] CWILL vs. Klaviyo — Klaviyo kann Popups selbst

### Informationen, die ich noch brauche

- [ ] **Werbebudget Dezember–Februar** — für die exakte CPA-Rechnung
- [ ] **merchOne-Versandkosten** pro 20×30-Poster nach Österreich
- [ ] **Echte Produktfotos** — Poster an der Wand, in der Hand, Unboxing
- [ ] **Bundle-Staffel**: Vorschlag 2 Poster −15 %, 3 Poster −25 %. Passt das?

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
