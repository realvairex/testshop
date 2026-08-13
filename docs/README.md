# Übergabe

Stand: **13.08.2026**

## Sitzung starten

Schreib in einen neuen Chat einfach:

```
start petworld
```

Das liest den Projektstand, prüft Repo und Shopify-Connector und meldet, wo wir stehen.
Zum Abschluss einer Sitzung entsprechend `ende petworld` — das sichert alles Wissen
aus dem Gespräch ins Repo, bevor der Chat geschlossen wird.

## Dokumente

| Datei | Inhalt |
|---|---|
| [`../CLAUDE.md`](../CLAUDE.md) | Kontext, Architektur, Sicherheitsregeln, Grundhaltung. Wird automatisch geladen |
| [`entscheidungen.md`](entscheidungen.md) | Entscheidungen E1–E18 · **Korrekturen K1–K9** |
| [`bugs.md`](bugs.md) | **Fehlerregister** — offene Defekte, rechtliche Risiken, Behobenes |
| [`theme-landkarte.md`](theme-landkarte.md) | **Wo im Theme was liegt** — vor jeder Änderung lesen |
| [`todo.md`](todo.md) | Was ansteht, nach Zuständigkeit getrennt |
| [`offene-fragen.md`](offene-fragen.md) | Was beantwortet ist, was fehlt, was blockiert |
| [`zahlen.md`](zahlen.md) | Traffic, Conversion, Kosten, Versand, Werbung |
| [`theme-audit.md`](theme-audit.md) | Fabric 3.1.0, Page-Builder, Karteileichen |
| [`personalizer-audit.md`](personalizer-audit.md) | Neun Befunde zum teeinblue-Ablauf |
| [`personalizer-vorlage.md`](personalizer-vorlage.md) | **Arbeitsanweisung für den teeinblue-Admin** — Felder, Bedingungen, fertige Texte |
| [`kontrast-audit.md`](kontrast-audit.md) | WCAG-Rechnung aller 13 Farbschemata |
| [`startseite-befunde.md`](startseite-befunde.md) | Sichtprüfung Hero und Newsletter |
| [`markennamen.md`](markennamen.md) | DOGUE & Co, Vergleich mit heybalu.com |
| [`ci-palette-kandidat.md`](ci-palette-kandidat.md) | Salbei-Palette für den geplanten CI-Wechsel, mit Kontrastrechnung |
| [`personalizer-app-entscheidung.md`](personalizer-app-entscheidung.md) | teeinblue behalten oder Customily |
| [`setup-lokal.md`](setup-lokal.md) | Lokale Live-Vorschau einrichten |
| [`archiv-gempages/`](archiv-gempages/) | Gesicherte Inhalte vor dem GemPages-Ausbau |
| [`artefakt/`](artefakt/) | Quelldatei der geteilten Audit-Seite samt Anleitung zum Aktualisieren |

Als lesbare Seite: **[PetWorld Shop-Audit](https://claude.ai/code/artifact/eb8007e1-4516-470e-94ce-376c38daacdb)**
— teilbar, wird gelesen, **muss bei Änderungen mit aktualisiert werden**
(Anleitung in [`artefakt/README.md`](artefakt/README.md)).

## Der Stand in sechs Sätzen

1. Das Theme (**Fabric 3.1.0**) ist eine gute Basis — die Probleme lagen in den
   Aufsätzen, und die sind größtenteils entfernt.
2. **Die Conversion ist das Kernproblem: 0,07 % echt**, nachdem Familien- und
   Testbestellungen herausgerechnet sind. Rund ein Zwanzigstel des Medians.
3. **Der Personalizer überfordert** — neun Pflichtfelder, über 40 Farbfelder, der
   Foto-Upload steht ganz unten. Das ist der größte Hebel im Projekt.
4. **Traffic gibt es aktuell keinen.** Facebook-Werbung lief Dezember bis Februar,
   seitdem nichts mehr. Die Werbung hat funktioniert, die Seite hat nicht abgeholt.
5. **Die Marge trägt**: 16,63 € Deckungsbeitrag beim Basis-Poster, 40,60 € beim
   gerahmten 40×60. Der Rahmen-Upsell entscheidet, ob Werbung je rechenbar wird.
6. **Zwei Entscheidungen des Betreibers stehen aus**: der Preis (19,95 €?) und die
   Bundle-Staffel.

## Was in dieser Sitzung erledigt wurde

- Theme-Baseline gesichert (`cacbd97`), vollständiges Audit
- **Shogun, PageFly und vier verwaiste Sections** aus dem Theme entfernt
- **Sechs Apps deinstalliert**: PageFly, Gelato, Section Star, Section Store, Dakaas
- **Zwei gefährliche Rabattcodes deaktiviert** (`Danke` 40 €, `DANKE26` 13,85 €) —
  beide waren unbegrenzt oft und ohne Ablaufdatum nutzbar
- **GemPages-Inhalte archiviert**, bevor die App entfernt wird
- **`page.about-us.json`** angelegt, `page.json` neutralisiert — der Über-uns-Text
  lag im Standard-Template und erschien auf jeder Seite ohne eigenes Template
- **Produktseite**: Hinweis auf den Bilder-Leitfaden unter dem Titel,
  Vertrauens-Leiste unter dem Kaufen-Button
- Kontrast-Audit aller Farbschemata, Sichtprüfung der Startseite
- **Neun eigene Fehleinschätzungen korrigiert und dokumentiert** (K1–K9) — jede mit der Lehre daraus

## Als Nächstes

**Am 13.08. mit aktivem Connector erledigt:** sechs 301-Weiterleitungen gesetzt,
die fünf GemPages-Zwillinge und das doppelte Impressum stillgelegt, das
Fußzeilenmenü korrigiert. Danach **GemPages vollständig aus dem Theme entfernt** —
96 Dateien, das Theme schrumpft von 116 auf 46 Sections. Versandschwelle
gegengeprüft: steht noch bei 50 €.

**Beim Betreiber:** GemPages kann jetzt im Admin deinstalliert werden.

**Beim Betreiber, größter Hebel:** Die **Personalizer-Vorlage** abarbeiten
(`personalizer-vorlage.md`). Von neun Pflichtfeldern auf zwei, Foto-Upload nach oben.
Zuerst der Fünf-Minuten-Test, ob ein Bild-Upload als Bedingung dienen kann.

**Beim Betreiber:**
Versandschwelle auf 35 € · Live-Theme duplizieren · GemPages noch **nicht**
deinstallieren · Preis- und Bundle-Entscheidung

## Was lokal besser wird

Diese Umgebung erreicht nur GitHub und Paket-Registries. Offen blieb daher alles, was
nur im Browser sichtbar ist: Live-Vorschau des Personalizers, Verhalten auf dem Handy,
Warenkorb-Vorschaubild, Lighthouse-Messungen, teeinblue-Doku. Siehe
[`setup-lokal.md`](setup-lokal.md).
