# Entscheidungs-Log

Stand: 11.08.2026. Neue Entscheidungen bitte hier ergänzen, damit jede Session den
gleichen Stand hat.

## Entschieden

| # | Entscheidung | Begründung |
|---|---|---|
| E1 | **Liquid-Theme bleiben, kein Headless** | Hydrogen/Next.js würde teeinblue zerstören. Der Personalizer ist als App-Embed für den Online Store gebaut. |
| E2 | **Fabric 3.1.0 behalten**, nicht neu aufsetzen | Modernes First-Party-Theme, block-basiert, gute Basis. Das Problem liegt in den Aufsätzen, nicht im Theme. |
| E3 | **Motion One statt Framer Motion** | Framer Motion ist React-only. Motion One ist Vanilla-JS, ~5 kB, optisch gleichwertig, besser für Ladezeit. |
| E4 | **Grunddesign behalten, polieren statt neu erfinden** | Wunsch des Betreibers. Palette und Grundstruktur bleiben, Hierarchie und Konsistenz kommen dazu. |
| E5 | **ui-ux-pro-max-skill nur als Referenz**, nicht als Plugin installieren | Bringt fremde Anweisungen, Python-Skripte und eine `.mcp.json` in ein Repo, das an den Live-Shop gekoppelt wird. Token-Modell und Paletten trotzdem nutzbar. |
| E6 | **Design-Entscheidungen als HTML-Prototyp**, erst danach Liquid | Schneller zu vergleichen, spart Push-Runden. |
| E7 | **Schritt-für-Schritt-Personalizer ist das Ziel** | Ausdrücklicher Wunsch: erst nur Foto-Upload sichtbar, dann Primärfarbe, dann der Rest. |
| E8 | **Keine Credentials über den Chat** | Ephemere Container, persistenter Verlauf. Falls nötig: `.env` mit `.gitignore`. |
| E9 | **Proaktive Arbeitsweise ist verbindlich** | Ausdrückliche Anweisung des Betreibers am 12.08. Ausformuliert in `CLAUDE.md` unter „Grundhaltung". |
| E10 | **Gratisversand-Schwelle Österreich auf 35 €** | Ein gerahmtes 20×30 (39,95 €) löst damit Gratisversand aus — der Versand wird zum Verkaufsargument für den Rahmen statt zur Hürde. Umsetzung durch den Betreiber im Admin. |
| E11 | **Fake-Bewertungen bleiben vorerst** | Betreiber-Entscheidung vom 12.08.: wird beim Design-Umbau angegangen, nicht jetzt. Technisch ein Stern-SVG plus getippte „(89)" in `templates/product.json` — jederzeit in Minuten entfernbar. |
| E12 | **Markennamen bleiben vorerst** | Betreiber-Entscheidung vom 12.08. Siehe `docs/markennamen.md` für die Faktenlage und den risikoärmeren Kompromiss. |
| E13 | **KALENDAR und PUZZLE sind geplante Produktreihen** | Keine Karteileichen. Solange leer, sollten sie aber nicht im Menü verlinkt sein. |

## Offen — muss der Betreiber entscheiden

| # | Frage | Warum sie blockiert |
|---|---|---|
| O1 | **Bleibt der Preis bei 19,95 €?** | Bestimmt, ob bezahlte Werbung finanzierbar ist. Ohne Werbung kein Traffic. |
| O2 | **Markennamen behalten oder ersetzen?** (DOGUE, PLAYDOG, FURBES, NATIONAL PAWGRAPHIC) | Blockiert SEO- und Ads-Strategie komplett. |
| O3 | **teeinblue behalten oder zu Customily wechseln?** | Siehe `docs/personalizer-app-entscheidung.md`. Neue Info vom 11.08.: Fulfillment-Workflow bei teeinblue gilt als problematisch — das verschiebt die Bewertung. |
| O4 | **Design-Richtung** — Referenz-Shops | Bestimmt Schrift- und Farbentscheidung in Phase 2. Alternative: Vorschlag machen und reagieren lassen. |

## Bewusst zurückgestellt

| # | Thema | Warum später |
|---|---|---|
| Z1 | **Eigenen Personalizer bauen** | Canvas-Rendering, Druckdaten in 300 dpi, Hintergrundentfernung, POD-Anbindung — das ist ein eigenes Produkt, kein Website-Feature. Und ein Single Point of Failure für ein Geschäft, das nur personalisierte Ware verkauft. Frühestens bei deutlich höherem Umsatz. |
| Z2 | **teeinblue-API-Zugriff** | Beantwortet keine der aktuellen Fragen — die drehen sich um Rendering und UX, nicht um Daten. Später sinnvoll für Campaign-Audits und Bestellauswertung. |
| Z3 | **Netzwerk-Policy der Cloud-Umgebung erweitern** | Wird durch lokales Arbeiten hinfällig. |

## Korrekturen

| Datum | Was | Richtigstellung |
|---|---|---|
| 11.08. | „Produktseite ohne Preis" | Falsch. Preis und Varianten **werden** angezeigt — teeinblue rendert sie selbst. Bleibt ein Robustheits- und SEO-Thema, aber kein Notfall. |
| 11.08. | „Customily lohnt sich nicht" | Zu absolut. Basierte auf der Annahme, dass Fulfillment kein Schmerzpunkt ist. Der Betreiber hat widersprochen — Bewertung wurde überarbeitet. |
| 12.08. | **K1** — „GemPages wird auf keiner Live-Seite genutzt" | Falsch. Fünf veröffentlichte Seiten nutzen `gp-template`-Suffixe. Die Zuweisung steht im Admin (`templateSuffix`), nicht in den Theme-Templates. |
| 12.08. | **K2** — „Das 109-KB-Swiper-Bundle belastet die Ladezeit" | Falsch. Es war von keiner Datei referenziert und wurde nie geladen. Der echte Kostenfaktor sind die App-Embeds, nicht die Theme-Dateien. |
| 12.08. | **K3** — „FAQ, Über uns, Kontakt, Bild-Leitfaden und Weiterempfehlen sind über kein Menü erreichbar" | **Falsch.** Geprüft wurden nur die Shopify-Menü-Objekte. Fabric verlinkt alle fünf Seiten über `button`-Blöcke in `sections/footer-group.json`. **Lehre: Navigation immer in beiden Quellen prüfen.** |
| 12.08. | **K4** — „Der Über-uns-Text existiert nur in GemPages" | Falsch. Er stand im Standard-Template `templates/page.json` und wurde darüber ausgeliefert. Inzwischen in ein eigenes `page.about-us.json` ausgelagert. |
| 12.08. | **K5** — „Überschriften auf 76 % Deckkraft sind ein Accessibility-Problem" | Falsch. Gerechnet ergibt `#030302c2` auf `#f5f5f5` **10,0:1** und erfüllt AA wie AAA. Es bleibt ein gestalterisches Thema, kein Barrierefreiheits-Mangel. Details in `kontrast-audit.md`. |
| 12.08. | **K6** — „Unsichtbare Überschriften auf Startseite, Kontakt und Weiterempfehlen" | Falsch. Die Schema-Verwendung war per Textsuche ermittelt, was auch ungenutzte Block-Einstellungen trifft. Tatsächlich 16:1. **Lehre: Verwendung über die Block-Zuordnung prüfen, und bei Sections mit Medien gilt die Schema-Farbe nicht.** |
