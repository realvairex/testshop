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
| E14 | **Vertrauens-Elemente nativ bauen, nicht über Smind** | Ursprünglich war `sp-trust-badges` geplant. Beim Bauen umentschieden: Native Fabric-Blöcke überleben eine App-Deinstallation, nutzen die Theme-Farben automatisch und sparen eine Abhängigkeit. Gilt als Regel für alle weiteren Bausteine. |
| E15 | **Sitzungen laufen über `start petworld` und `ende petworld`** | Klartext-Befehle ohne Schrägstrich, hinterlegt als Skills. Sorgt dafür, dass jede neue Sitzung denselben Stand hat und beim Abschluss kein Wissen im Chat zurückbleibt. |
| E16 | **CLAUDE.md bleibt unter 100 Zeilen** | Ab etwa 80 Zeilen werden Teile überlesen — ausgerechnet die nicht verhandelbaren Regeln gehen dann unter. Am 12.08. von 247 auf 87 Zeilen gekürzt, Detailinhalt in die Fachdokumente verschoben. **Bei jeder Erweiterung prüfen, ob es nicht in ein Dokument gehört.** |
| E17 | **Vier Karpathy-Prinzipien übernommen** | Aus `multica-ai/andrej-karpathy-skills` (MIT, Autor forrestchang), eingearbeitet in die Grundhaltung: Annahmen offenlegen · einfachste Lösung · nur ändern was gefordert ist · Erfolgskriterium vorher benennen. Dazu der Prüfsatz „jede geänderte Zeile muss sich auf eine Anfrage zurückführen lassen". **Nicht als Plugin installiert**, aus demselben Grund wie E5. ⚠️ Nebenbefund: Die Installationsbefehle im README zeigen auf `forrestchang/andrej-karpathy-skills`, nicht auf `multica-ai/…` — wer der Anleitung folgt, installiert aus einer anderen Quelle als der verlinkten. |
| E18 | **„Verify, don't trust" als Arbeitsregel** | Beim Auswerten einer Quelle nie aus dem Gedächtnis oder einer früheren Zusammenfassung arbeiten, sondern die Quelle neu holen und die eigene Aussage gegnerisch gegenlesen. Anlass: K8. **Methodisch wichtig:** `WebFetch` liefert die Zusammenfassung eines kleinen Modells, nicht den Originaltext — für GitHub stattdessen `curl` auf `raw.githubusercontent.com`. |

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
| 12.08. | **K9** — Erfolgsmeldung ohne Aussagekraft | Nach einem fehlgeschlagenen Commit wurde „sauber" gemeldet, obwohl drei Dateien nicht committet waren. Ursache: `git status --short && echo "sauber"` — die Meldung hing an einem Befehl, der **immer** gelingt, unabhängig vom Ergebnis. **Lehre: Eine Prüfung muss fehlschlagen können.** Richtig ist `test -z "$(git status --porcelain)"` oder die Zeilenzahl ausgeben statt eines Festtextes. Gleiches gilt für jedes Prüfskript: Wenn es nie „nein" sagen kann, prüft es nichts. |
| 12.08. | **K8** — Drei Falschaussagen über das Karpathy-Repo, weil auf Zusammenfassungen statt Originaltexten gearbeitet wurde | (a) Behauptet, die Regel „vorhandenen toten Code nicht löschen" widerspreche unserem Aufräumen und müsse angepasst werden. **Der Originaltext enthält bereits „unless asked"** — es gab keinen Widerspruch. Die Zusammenfassung hatte den Zusatz verschluckt. (b) Die Angabe „über 201.000 Sterne" stammt aus keiner Quelldatei, sie war frei erfunden vom zusammenfassenden Modell. (c) Von acht Dateien im Repo nur zwei gelesen und das Ergebnis als vollständige Bewertung dargestellt. **Lehre: siehe E18.** |
| 12.08. | **K7** — Zwei eigene Fehlalarme bei Integritätsprüfungen | `buy_buttons` mit leerem `block_order` wurde als Inkonsistenz gemeldet — es ist Shopifys Normalzustand für statische Kindblöcke. Und ein `{% render %}` in einem `{%- doc -%}`-Kommentarblock wurde als fehlendes Snippet gemeldet. **Lehre: Prüfskripte gegen die Baseline `cacbd97` abgleichen, bevor ein Befund gemeldet wird — und Kommentarblöcke ausnehmen.** Technische Details in `.claude/skills/petworld-design/SKILL.md`. |
