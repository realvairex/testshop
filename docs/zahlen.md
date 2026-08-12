# Die echten Zahlen

Abgerufen am 12.08.2026 über den Shopify-Connector. Shop: `wkbyft-ex.myshopify.com`
(pet-world.at), Plan **Basic**, Währung EUR, Österreich.

> Diese Datei ersetzt alle vorherigen Schätzungen. Wo frühere Dokumente von Annahmen
> ausgehen, gilt diese hier.

## Traffic — Zusammenbruch nach dem Winter

| Monat | Sessions |
|---|---|
| Aug 2025 | 12 |
| Sep 2025 | 47 |
| Okt 2025 | 56 |
| Nov 2025 | 276 |
| **Dez 2025** | **3.306** |
| **Jan 2026** | **3.681** |
| **Feb 2026** | **2.688** |
| Mär 2026 | 758 |
| Apr 2026 | 73 |
| Mai 2026 | 66 |
| Jun 2026 | 46 |
| Jul 2026 | 37 |
| Aug 2026 | 26 |

**11.072 Sessions im Jahr — davon 9.675 (87 %) in nur drei Monaten.**
Seit April praktisch kein Traffic mehr. Rückgang vom Höchststand: **99,3 %**.

### Woher der Traffic kam

| Quelle | Gerät | Sessions |
|---|---|---|
| social | mobile | 8.188 |
| direct | mobile | 1.302 |
| direct | desktop | 973 |
| social | tablet | 350 |
| direct | tablet | 84 |
| social | desktop | 60 |
| search | mobile | 54 |
| search | desktop | 44 |

- **78 % social**, fast ausschließlich mobil
- **Suche: 98 Sessions. Im ganzen Jahr.** SEO ist faktisch bei null.
- Mobil dominiert vollständig — jede Design-Entscheidung ist eine Mobil-Entscheidung

## Conversion — das eigentliche Problem

| | |
|---|---|
| Sessions gesamt | 11.072 |
| Bestellungen gesamt | **16** |
| Bruttoumsatz | **616,09 €** |
| **Conversion Rate** | **0,14 %** |

Der Shopify-Median liegt bei etwa 1,4 %. **Der Shop liegt rund zehnfach darunter.**

### Letzte 90 Tage

| | |
|---|---|
| Sessions | 141 |
| davon mit Warenkorb-Zulage | 6 |
| davon bis Checkout | 3 |
| davon abgeschlossen | **0** |

### ⚠️ Vorbehalt bei den Bestellungen

Von 16 Bestellungen tragen **acht** den Nachnamen **Kases** (Julian ×4, Gerald ×2,
Petra, Paul). Mehrere davon über exakt 11,00 € — unter dem Posterpreis von 19,95 €,
also vermutlich mit Testrabatt.

**Falls das Test- oder Familienbestellungen sind, liegt die echte Conversion bei rund
0,07 %.** Muss der Betreiber bestätigen.

## Marge — deutlich besser als angenommen

Echte Einkaufspreise aus dem Shop (`inventoryItem.unitCost`):

| Produkt | VK | EK | Deckungsbeitrag | Marge |
|---|---|---|---|---|
| Poster 20×30 | 19,95 € | 3,32 € | **16,63 €** | 83 % |
| Poster 40×60 | 29,95 € | 6,89 € | 23,06 € | 77 % |
| Poster 50×75 | 39,95 € | 8,45 € | 31,50 € | 79 % |
| Rahmen schwarz 20×30 | 39,95 € | 10,70 € | 29,25 € | 73 % |
| **Rahmen schwarz 40×60** | 64,95 € | 24,35 € | **40,60 €** | 62 % |

**Korrektur:** Frühere Dokumente warnten, bei 19,95 € bleibe zu wenig Deckungsbeitrag
für bezahlte Werbung. Das basierte auf geschätzten Kosten und war **zu pessimistisch**.
Mit 16,63 € Deckungsbeitrag ist ein CPA von 10–14 € grundsätzlich tragfähig.

**Offen:** Ob `unitCost` die Versandkosten des POD-Partners enthält. Falls nicht, sinkt
der Deckungsbeitrag um geschätzte 4–6 €.

**Wichtig:** Ein gerahmtes 40×60 bringt **2,4-mal so viel** Deckungsbeitrag wie das
Basis-Poster. Der Rahmen-Upsell (Befund E im Personalizer-Audit) ist damit
quantifiziert — er wird aktuell als nackter Textbutton ohne Bild und Preis verschenkt.

## Fulfillment — der Befund des Betreibers ist belegt

**13 von 16 Bestellungen sind nicht vollständig ausgeliefert:**

| Status | Anzahl |
|---|---|
| FULFILLED | 3 |
| IN_PROGRESS | 9 |
| UNFULFILLED | 3 |
| PARTIALLY_FULFILLED | 1 |

Darunter Bestellungen aus **Dezember 2025 und Januar 2026** — alle mit Zahlungsstatus
`PAID`. Eine Bestellung vom **6. Mai 2026** steht weiterhin auf `UNFULFILLED`.

Zwei mögliche Erklärungen, beide ernst:

1. **Die Bestellungen wurden nie ausgeliefert.** Bezahlte, nicht gelieferte Ware —
   Rückbuchungs- und Haftungsrisiko.
2. **Der POD-Partner liefert, meldet den Status aber nicht an Shopify zurück.**
   Dann bekommen Kunden keine Versandbestätigung und keine Sendungsverfolgung.

Muss der Betreiber prüfen. Das ist der dringendste Punkt im ganzen Projekt.

## POD-Partner (Frage 16 ✅)

Angebundene Fulfillment-Services:

| Service | Handle | Typ |
|---|---|---|
| **merchOne** | `picanova` | Drittanbieter |
| **gelato** | `gelato` | Drittanbieter |
| Manuell | `manual` | — |

Relevant für die Customily-Frage: **Gelato ist breit integriert** und wird von
teeinblue wie Customily unterstützt. merchOne/Picanova ist seltener angebunden —
das vor einer Migration prüfen.

## Meistverkaufte Produkte

| Produkt | Bestellungen | Bruttoumsatz |
|---|---|---|
| FURBES | 4 | 99,80 € |
| DOGUE | 3 | 104,85 € |
| PLAYDOG | 3 | 124,85 € |
| PAWS | 3 | 79,85 € |
| PLAYCAT | 2 | 49,90 € |
| NATIONAL PAWGRAPHIC | 1 | 39,95 € |
| Personalisiertes Haustierbett | 1 | 49,99 € |
| Poster Bild | 1 | 64,95 € |

Die Parodie-Poster sind die Verkäufer. Nebenbei existiert bereits ein Produkt mit
eigenständigem Namen — **DER SCHNÜFFLER** — was zeigt, dass die Umbenennung (offene
Entscheidung O2) gestalterisch machbar ist.

## ⚠️ Die 89 Bewertungen

Die Produktseite PLAYDOG zeigt 4,5 Sterne aus **89 Bewertungen**. Der Shop hat
insgesamt **16 Bestellungen**.

Diese Bewertungen können nicht von echten Kunden dieses Shops stammen. Falls sie
importiert oder generiert sind: Nach der EU-Omnibus-Richtlinie und dem österreichischen
UWG sind erfundene oder nicht verifizierte Bewertungen unzulässig und abmahnbar.

Zu klären, woher sie kommen.

## Was das für die Priorisierung bedeutet

Zwei Probleme, beide real, in dieser Reihenfolge:

1. **Fulfillment** — bezahlte Bestellungen ohne Auslieferungsstatus. Dringend,
   unabhängig von allem anderen.
2. **Conversion 0,14 %** — die Personalizer-Diagnose ist damit belegt. In Dezember bis
   Februar kamen 9.675 Besucher, überwiegend mobil über Social Media, und es entstanden
   14 Bestellungen.
3. **Traffic** — aktuell 26 Sessions im Monat. Ohne Besucher wirkt keine Optimierung.

**Die Reihenfolge ist entscheidend:** Traffic wieder anschalten, bevor die Conversion
stimmt, verbrennt Geld. Das ist bereits einmal passiert — 9.675 Besucher haben
14 Bestellungen erzeugt.

Umgekehrt bringt eine perfekte Conversion bei 26 Sessions im Monat ebenfalls nichts.
Beides muss gelöst werden, aber Conversion zuerst.

## Neue offene Fragen

- **Was war Dezember bis Februar?** Bezahlte Werbung oder organisches TikTok? Falls
  organisch, ist es günstig wiederholbar. Falls bezahlt: Budget und ROAS?
- **Warum wurde es gestoppt?**
- Sind die Kases-Bestellungen Test- oder Familienbestellungen?
- Enthält `unitCost` den Versand?
- Woher stammen die 89 Bewertungen?
