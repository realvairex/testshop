# Fehlerregister

Bekannte Defekte im Shop. Stand 12.08.2026.

Getrennt von `entscheidungen.md` — dort stehen **meine** Fehleinschätzungen (K1–K7),
hier stehen **Fehler im Shop selbst**.

Neue Funde werden hier ergänzt, behobene abgehakt statt gelöscht.

---

## 🔴 Offen — hoch

### B1 · Header-Kontrast 2,2:1

`scheme-2` setzt Weiß `#f5f5f5` auf Petrol `#76b2ae`. WCAG AA fordert 4,5:1.
**Betrifft jede Seite**, bei 78 % mobilem Traffic besonders relevant.
Berechnet **und** auf Screenshots sichtbar bestätigt.

*Fundort:* `config/settings_data.json` → `color_schemes.scheme-2`, verwendet als
`color_scheme_top` in `sections/header-group.json`
*Lösung:* Petrol auf ca. `#3d7d78` abdunkeln → ~4,6:1 bei fast unverändertem Look.
Gehört in die CI-Phase, weil es die Markenfarbe berührt.
*Details:* `kontrast-audit.md`

### B2 · Hero ohne Handlungsaufforderung

Der Hero füllt einen ganzen Bildschirm und enthält keinen einzigen Button.
*Details:* `startseite-befunde.md`, Befund 1

### B3 · Preis und Varianten nur clientseitig

Die Produktseite enthält weder `price`- noch `variant-picker`-Block. teeinblue rendert
beides per JavaScript. Folgen: nichts sichtbar, bevor die App geladen hat; kein Preis
im server-gerenderten HTML für Merchant Center und Suchergebnisse.
*Fundort:* `templates/product.json`
*Details:* `theme-audit.md`, Befund 1

### B4 · Doppelte Seiten im Index

Fünf GemPages-Seiten sind unverlinkte Zwillinge der nativen Fassungen — beide
veröffentlicht und crawlbar. Dazu existiert das Impressum zweimal
(`impressum` und `copy-of-uber-uns`).
*Lösung:* 301-Weiterleitungen auf die native Fassung, dann GemPages entfernen.
**Braucht den Shopify-Connector.**

---

## 🟠 Offen — mittel

### B5 · Newsletter-Text weiß auf Petrol

Im Newsletter-Kasten der Startseite steht der Anreiztext („Als Dank erhältst du…")
weiß auf Petrol und ist schwach lesbar. Die Überschrift daneben ist dunkel — beide
können auf demselben Grund nicht gleichzeitig sitzen.
*Fundort:* `templates/index.json` → `hero_QX7PYt`

### B6 · Falsches Icon bei der Bewertungsanzeige

Neben der Bewertungszahl steht ein `price_tag`-Icon. Gemeint sind Sterne.
*Fundort:* `templates/product.json` → `group_czKG4R` → `icon_6xHTXt`

### B7 · Tote Links im Kundenkonto-Menü

**KALENDAR** hat 0 Produkte, **PUZZLE** hat 2 Produkte, die beide auf `ARCHIVED`
stehen. Beide Kollektionen sind im Menü „Entdecken" verlinkt und führen auf leere
Seiten.
*Lösung:* Aus dem Menü nehmen, solange sie leer sind. Puzzle-Produkte auf `DRAFT`
setzen — sie sind geplant, nicht eingestellt (E13).

### B8 · `scheme-4` knapp unter AA

Weiß auf Rot `#da3c24` ergibt 4,1:1 statt 4,5:1. Betrifft Sale-Badges und einen
Fußzeilen-Bereich. Ein leicht dunkleres Rot löst es.

### B9 · Veralteter Platzhalter im Personalizer

Das Datumsfeld zeigt „AUGUST 2025". Aktuell ist August 2026.
*Lösung:* im teeinblue-Admin, dynamisch oder neutral formulieren.

### B10 · Flagge und Sprachkürzel widersprüchlich

Oben rechts steht die österreichische Flagge neben „EUR / DE".

---

## 🟡 Offen — niedrig

### B11 · Kollektions-Templates zeigen ins Leere

**BESTSELLER** und **POSTER** haben den `templateSuffix`
`gp-template-562355879467287637`, das zugehörige Template existiert im Theme nicht.
Shopify fällt auf `collection.json` zurück — funktioniert, ist aber unsauber und
verwirrt bei der nächsten Analyse.

### B12 · Leichen in `settings_data.json`

Der App-Embed-Eintrag für **Opus Cart Upsell** steht noch drin, die App ist nicht mehr
installiert. Ebenso Einträge für inzwischen entfernte Apps.

### B13 · Verwaiste Rabattcodes

Sieben `LX-…`-Codes stammen von **Loox**, die App ist deinstalliert. Je einmal nutzbar,
10 %, keiner je eingelöst — harmlos, aber Ballast.
`Weihnachten2025` ist im August 2026 noch aktiv und untergräbt die nächste
Weihnachtsaktion.

### B14 · `scheme-3` vollständig transparent

Alle Werte inklusive Text und Überschrift stehen auf `rgba(0,0,0,0)`. Dient als Schema
für den transparenten Header, der derzeit **abgeschaltet** ist. Kein aktiver Fehler,
aber eine Falle: Wer ihn einschaltet, bekommt unsichtbaren Text.

---

## ⚖️ Rechtliche Risiken

Keine technischen Fehler, aber Haftungsthemen. Entscheidungen des Betreibers liegen vor.

### R1 · Erfundene Bewertungen

Die Produktseite zeigt 4,5 Sterne aus **89 Bewertungen** bei 16 Bestellungen insgesamt.
Technisch ein hochgeladenes Stern-SVG plus getippte „(89)" — kein Bewertungssystem
dahinter. Nach UWG (Anhang Z 23b/c) und Omnibus-Richtlinie unzulässig.
*Status:* **Betreiber-Entscheidung E11 — bleibt vorerst**, wird in der Design-Phase
angegangen.
*Fundort:* `templates/product.json` → `group_czKG4R`

### R2 · Markennamen und SEO-Text

DOGUE, PLAYDOG, PLAYCAT, FURBES, FURCUS, NATIONAL PAWGRAPHIC. Besonders exponiert:
Die Meta-Beschreibung von DOGUE nennt wörtlich **„im Vogue-Stil"**.
*Status:* **Betreiber-Entscheidung E12 — bleibt vorerst.**
*Details:* `markennamen.md`, inklusive Präzedenzfall Condé Nast gegen Dogue

### R3 · Dauerhafter Streichpreis

24,95 → 19,95 € permanent. Nach der Omnibus-Richtlinie muss der durchgestrichene Preis
der niedrigste der letzten 30 Tage sein.
*Status:* offen, hängt an der Preisentscheidung.

---

## 🛠 Umgebung und Werkzeuge

Keine Shop-Fehler, aber sie kosten in jeder Sitzung Zeit.

### U1 · Shopify-Connector trotz aktivem Schalter nicht verfügbar

`SearchMcpRegistry` meldete `connected: true`, aber `enabledInChat: false`, während die
Oberfläche den Schalter als **an** anzeigte. Der Zustand wurde offenbar nicht
gespeichert.
*Umgang:* Schalter aus- und wieder einschalten, App neu laden — sonst neue Unterhaltung.
Der Ablauf steht im Skill `start-petworld`.

### U2 · Netzwerk der Cloud-Umgebung stark eingeschränkt

Erreichbar sind nur GitHub und Paket-Registries. **Blockiert:** `pet-world.at`,
`teeinblue.com`, `support.teeinblue.com`, alle `shopify.com`-Domains, `cdn.shopify.com`.
`WebSearch` funktioniert, `WebFetch` auf diese Domains nicht.
*Folge:* Live-Ansicht, Lighthouse und teeinblue-Doku gehen nur lokal.
*Details:* `setup-lokal.md`

---

## ✅ Behoben

| # | Fehler | Behoben am | Wie |
|---|---|---|---|
| B15 | Standard-Template `page.json` enthielt den Über-uns-Text und spielte ihn auf **jeder** Seite ohne eigenes Template aus | 12.08. | Inhalt nach `page.about-us.json` ausgelagert, `page.json` auf Titel und Seiteninhalt reduziert |
| B16 | `page.about-us.json` fehlte, obwohl die Seite `/pages/uber-uns` es per `templateSuffix` erwartete | 12.08. | Template angelegt |
| B17 | Rabattcode `Danke` gab **40 €** unbegrenzt oft, ohne Kundenlimit und ohne Ablauf — bei Produkten von 19,95–64,95 € praktisch Gratisbestellungen. Dazu ein leicht erratbares Wort | 12.08. | Deaktiviert (`EXPIRED`), unabhängig gegengeprüft |
| B18 | Dasselbe bei `DANKE26` (13,85 €), bereits 6× genutzt | 12.08. | Deaktiviert |
| B19 | Shogun lud über `{% include 'shogun-content-handler' %}` in `theme.liquid` auf **jeder Seite** mit, obwohl die App längst deinstalliert war | 12.08. | 15 Dateien und alle Includes entfernt |
| B20 | PageFly-Dateien und vier `ss-`Sections deinstallierter Apps lagen ungenutzt im Theme | 12.08. | Entfernt |
| B21 | Bilder-Leitfaden nur über die Fußzeile erreichbar, obwohl ein gutes Foto die Voraussetzung für ein gutes Poster ist | 12.08. | Hinweis mit Link direkt unter dem Produkttitel |
