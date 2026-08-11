# Offene Fragen

Checkliste zum Abhaken. 🔒 = blockiert konkrete Arbeit.

## Beantwortet ✅

| # | Frage | Antwort |
|---|---|---|
| 1 | Welches Theme? | **Fabric 3.1.0**, Shopify First-Party, block-basiert |
| 3 | Code von Hand angefasst? | Nein. Aber massiv von Apps überlagert |
| 4 | Welche Apps? | teeinblue, smind/Sections Pro, Opus Cart Upsell, GemPages, PageFly, Shogun-Reste |
| 20 | Marke / Brand-Tokens | Schrift **Asap** für alles · Petrol `#76b2ae` · Schwarz `#030302` · Off-White `#f5f5f5` · Rot `#da3c24` |

## Technik

- [ ] **2** 🔒 GitHub-Sync im Shopify-Admin eingerichtet? (Online Store → Themes →
      Add theme → Connect from GitHub, Branch `claude/petworld-shopify-brainstorm-9go0du`)
- [ ] **5** Gibt es einen Sandbox-Shop, oder arbeiten wir auf einem Dev-Theme im Live-Shop?
- [ ] **X1** Nutzt eine echte Seite ein `gp-template`? (Admin → Seiten prüfen, bevor
      GemPages/PageFly/Shogun deinstalliert werden — es gibt 12 solcher Templates)

## Zahlen aus Shopify Analytics

- [ ] **6** 🔒 Sessions pro Monat und Conversion Rate
- [ ] **7** 🔒 Traffic-Quellen (Direkt / Organic / TikTok / Meta / sonst)
- [ ] **8** Add-to-Cart-Rate und Checkout-Abbruchrate
- [ ] **9** Bestellungen und Umsatz der letzten 3 Monate, AOV
- [ ] **10** Mobil vs. Desktop — getrennt nach Traffic *und* Bestellungen
- [ ] **11** 🔒 Wie viele öffnen den Personalizer, wie viele schließen ihn ab
      *(wichtigste einzelne Zahl im Shop)*
- [ ] **12** Retourenquote und häufigste Support-Gründe

## Geschäftsmodell

- [ ] **13** 🔒 Stückkosten pro Poster: Druck + Versand + Zahlungsgebühren
- [ ] **14** 🔒 Bleibt der Preis bei 19,95 €?
- [ ] **15** Läuft bezahlte Werbung? Budget und ROAS
- [ ] **16** 🔒 **Welcher POD-Partner?** (Printful, Gelato, Prodigi, CustomCat, eigener)
      *— entscheidet die Customily-Frage*
- [ ] **17** Realistische Lieferzeit von Bestellung bis Haustür
- [ ] **18** Rendering vollautomatisch über teeinblue oder manuelle Prüfung?
- [ ] **X2** 🔒 **Was genau ist am Fulfillment-Workflow katastrophal?**
      Manueller Datei-Transfer? Fehlende Synchronisation? Fehlerhafte Druckdaten?

## Marke & Design

- [ ] **19** 🔒 Markennamen behalten oder ersetzen? (DOGUE, PLAYDOG, FURBES,
      NATIONAL PAWGRAPHIC)
- [ ] **21** 🔒 Zwei bis drei Shops, deren Look gefällt — und einer, der nicht gefällt.
      *Alternative: Vorschlag machen lassen und darauf reagieren*
- [ ] **22** Echte Produktfotos vorhanden (Poster an der Wand, in der Hand, Unboxing)
      oder nur Mockups?
- [ ] **23** Deutschland aktiv bewerben oder nur Sprachumschaltung?

## Marketing

- [ ] **24** E-Mail-Tool und Listengröße
- [ ] **25** Wer betreut TikTok/Instagram, wie oft wird gepostet?
- [ ] **26** Referral-Programm real oder Platzhalter?
- [ ] **27** Wie lief das letzte Weihnachtsgeschäft?

## Zu prüfen, sobald der Shop lokal läuft

- [ ] Gibt es oberhalb des Personalizer-Formulars eine Live-Vorschau, und aktualisiert
      sie sich bei jeder Änderung?
- [ ] Zeigt der Warenkorb das Design des Kunden oder das generische Produktfoto?
      *(`snippets/cart-products.liquid:195` blendet alle `_`-Properties aus — dort legen
      Personalizer-Apps üblicherweise die Vorschau-URL ab)*
- [ ] Wie verhält sich der Personalizer auf einem echten Mobilgerät?
- [ ] Bietet teeinblue eine App-Block-Einbindung statt des Embeds?
- [ ] Lighthouse-Messung vorher/nachher, um den Effekt der App-Deinstallation zu belegen

## Wenn nur fünf beantwortet werden

**1** ✅ erledigt · **6+7** (Traffic & CR) · **13** (Stückkosten) · **14** (Preis) ·
**16** (POD-Partner) · **19** (Markennamen)
