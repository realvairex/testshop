# Offene Fragen

Stand 12.08.2026. 🔒 = blockiert konkrete Arbeit.

## Beantwortet ✅

| # | Frage | Antwort |
|---|---|---|
| 1 | Theme | **Fabric 3.1.0**, Shopify First-Party, block-basiert |
| 3 | Code von Hand angefasst? | Nein, aber massiv von Apps überlagert |
| 4 | Apps | Siehe Tabelle in `CLAUDE.md`. Sechs am 12.08. deinstalliert |
| 6 | Sessions / Conversion | 11.072 im Jahr · 0,14 % roh, **0,07 % echt** |
| 7 | Traffic-Quellen | 78 % Social und fast nur mobil · Suche: 98 Sessions im Jahr |
| 8 | Warenkorb / Checkout | Letzte 90 Tage: 141 Sessions → 6 Warenkorb → 3 Checkout → **0 Kauf** |
| 9 | Bestellungen / Umsatz | 16 Bestellungen, 616 € brutto, davon 8 Familie/Test |
| 10 | Mobil vs. Desktop | Überwältigend mobil |
| 12 | Retouren | Keine auffälligen Fälle in den Daten |
| 13 | Stückkosten | Poster 20×30: **3,32 €** EK bei 19,95 € VK. **Versand nicht enthalten** |
| 15 | Bezahlte Werbung | **Facebook**, Dezember bis Februar. Seit März/April nichts mehr |
| 16 | POD-Partner | **Nur noch merchOne.** Gelato deinstalliert, kein Produkt hing daran |
| 17 | Lieferzeit | **5 Werktage** |
| 19 | Markennamen | Entscheidung: **bleiben vorerst**. Siehe `markennamen.md` |
| 20 | Marke / Tokens | Asap für alles · Petrol `#76b2ae` · Schwarz `#030302` · Off-White `#f5f5f5` · Rot `#da3c24` |
| 22 | Echte Produktfotos | **Ja, vorhanden.** Noch nicht an mich übergeben |
| X2 | Was hakt am Fulfillment? | Die offenen Bestellungen sind **Altlasten**, keine unbelieferten Kunden. teeinblue-Workflow gilt generell als veraltet |
| X3 | Woher die 89 Bewertungen? | **Erfunden.** Ein Stern-SVG plus getippte „(89)" in `templates/product.json`. Kein Bewertungssystem dahinter |
| X4 | Nutzt eine echte Seite ein `gp-template`? | **Ja, fünf.** Deshalb GemPages erst nach den Weiterleitungen entfernen |

## 🔒 Blockiert die Arbeit

- [ ] **14 — Bleibt der Preis bei 19,95 €?** Nie beantwortet. Entscheidet zusammen mit
      dem Bestellwert, ob bezahlte Werbung je rechenbar wird.
- [ ] **Bundle-Staffel.** Vorschlag: 2 Poster −15 %, 3 Poster −25 %. Es existiert
      bereits `FREUNDE10` (10 % ab 2 Stück) — aber als Code, den niemand kennt.
      Gehört als **automatischer** Rabatt in den Warenkorb.
- [ ] **11 — Personalizer-Abschlussquote.** Wie viele öffnen ihn, wie viele schließen
      ab? Die wichtigste einzelne Zahl im Shop. Nur über teeinblue zu bekommen.
- [ ] **Kann ein Bild-Upload in teeinblue als Bedingung dienen?** Davon hängt ab, ob
      der Schritt-für-Schritt-Ablauf nativ funktioniert oder eine Zusatzschicht im
      Theme braucht.
- [ ] **21 — Design-Richtung.** Als Inspiration genannt: `heybalu.com`. Für Phase 2
      fehlen noch zwei bis drei Shops, deren Look gefällt — und einer, der nicht gefällt.

## Nachzureichen

- [ ] **Werbebudget Dezember–Februar** — für die exakte Kosten-pro-Bestellung-Rechnung
- [ ] **merchOne-Versandkosten** für ein 20×30-Poster nach Österreich
- [ ] **Echte Produktfotos** — Poster an der Wand, in der Hand, Unboxing, Kundenfotos
- [ ] **2 — GitHub-Sync** im Shopify-Admin eingerichtet?
- [ ] **5 — Sandbox-Shop** oder Dev-Theme im Live-Shop?
- [ ] **18 — Rendering** vollautomatisch über teeinblue oder mit manueller Prüfung?
- [ ] **23 — Deutschland** aktiv bewerben oder nur Sprachumschaltung?
- [ ] **24–27** — Klaviyo-Listengröße, Social-Betreuung, Referral-Programm, Q4-Planung

## Apps, deren Nutzen ungeklärt ist

Stack ($9,99/Monat) · TinySEO · AddressHero · Vidify · Collective · Messaging ·
Predis · CWILL Popup Email · Essential Announcer · **Customix Personalizer**
(zweiter Personalizer neben teeinblue!) · **EGO Cart Upsell** ($12,99) und
**AMP Slide Cart** parallel — eine davon reicht.

## Zu prüfen, sobald der Shop lokal läuft

- [ ] Gibt es im Personalizer eine Live-Vorschau, und aktualisiert sie sich?
- [ ] Zeigt der Warenkorb das Design des Kunden oder das Stock-Foto?
      (`snippets/cart-products.liquid:195` blendet alle `_`-Properties aus)
- [ ] Wie verhält sich der Personalizer auf einem echten Mobilgerät?
- [ ] Bietet teeinblue eine App-Block-Einbindung statt des Embeds?
- [ ] **Alle Startseiten-Befunde auf einem Mobilgerät nachvollziehen** — sie stammen
      aus Desktop-Screenshots
- [ ] Lighthouse vorher/nachher, um den Effekt der App-Entfernung zu belegen
