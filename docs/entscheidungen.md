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
