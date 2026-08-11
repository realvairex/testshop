# teeinblue behalten oder zu Customily wechseln?

Stand: 11.08.2026. **Offene Entscheidung.**

## Wie sich die Lage geändert hat

Meine erste Einschätzung war: bei teeinblue bleiben, weil sieben von acht gefundenen
Problemen Konfiguration sind und nicht App-Limitierung. Diese Analyse steht weiterhin.

**Was neu dazugekommen ist:** Der Betreiber beschreibt den **Fulfillment-Workflow bei
teeinblue als katastrophal** und die App insgesamt als veraltet.

Das ist genau das Kriterium, an dem sich die Vergleiche unterscheiden. Damit wird die
Entscheidung offen — vorher war sie es nicht.

## Die zwei Probleme sauber trennen

Es sind **zwei unabhängige Probleme**, und sie haben unterschiedliche Lösungen.

| | Problem A: Kunden-UX | Problem B: Fulfillment |
|---|---|---|
| Symptom | 9 Pflichtfelder, Upload zuletzt, keine Vorschau | manueller Aufwand pro Bestellung, veraltete Oberfläche |
| Ursache | **Eure Konfiguration** | **Die App selbst** |
| Lösung | Umkonfigurieren — kostenlos, Tage | Migration — teuer, Wochen |
| Wechsel hilft? | **Nein** — die neun Pflichtfelder wären in jeder App neun Pflichtfelder | **Ja, potenziell** |

Der entscheidende Punkt: **Ein Wechsel löst Problem B, aber nicht Problem A.**
Wer migriert und die Felder genauso konfiguriert, hat denselben überfordernden
Personalizer in einer neueren Oberfläche.

## Was für Customily spricht

- Breitere Integrationen und druckfertige Dateien
- Stärkere Fulfillment-Automatisierung — genau der genannte Schmerzpunkt
- Modernere Oberfläche
- Einordnung in den Vergleichen: *„Wenn du bereits weißt, dass Personalisierung
  funktioniert und jetzt bessere Automatisierung, breitere Plattform-Abdeckung und
  einen strafferen Fulfillment-Workflow brauchst, ist Customily meist die stärkere
  Wahl."* ([printondemandbusiness.com](https://www.printondemandbusiness.com/blog/customily-vs-teeinblue/))

## Was dagegen spricht

**1. Der Wizard ist auch dort nicht belegt.**
Für Customily konnte ich genauso wenig einen dokumentierten Schritt-für-Schritt-Flow
mit Fortschrittsanzeige finden wie für teeinblue. Conditional Logic ja, Live-Vorschau
ja — Multi-Step-Wizard unbestätigt. **Risiko: migrieren und dieselbe Lücke vorfinden.**

**2. Die Kosten bei aktuellem Volumen.**

| | teeinblue | Customily |
|---|---|---|
| Grundgebühr | plan-abhängig, erste 50 Bestellungen frei | **49 $/Monat fix** |
| Pro Bestellung | 1,8 % vom Produktpreis | 0,10–1,00 $ pro personalisiertem Artikel |
| Bei 19,95 € Poster | ≈ 0,36 € | 0,09–0,90 € **plus** 45 € fix |

Bei 30 Bestellungen/Monat: teeinblue ≈ 11 € (oder 0 € im Freikontingent),
Customily ≈ 48–72 €.
Quellen: [Customily Pricing](https://www.customily.com/pricing) ·
[teeinblue Pricing FAQs](https://support.teeinblue.com/en/article/pricing-faqs-oyyie2/)

Die Rechnung dreht sich mit steigendem Volumen — bei hohen Stückzahlen ist eine
Fixgebühr plus Cent-Beträge günstiger als 1,8 % vom Umsatz.

**3. Migrationsaufwand.** Alle Campaigns neu bauen, POD-Anbindung neu verdrahten,
Druckdaten-Pipeline neu testen. Realistisch 4–8 Wochen, in denen nichts anderes
vorangeht.

## Was vor der Entscheidung geklärt werden muss

1. **Welcher POD-Partner?** Printful, Gelato, Prodigi, CustomCat, eigener Partner?
   Der ganze Vorteil von Customily hängt daran, ob euer Lieferant dort nativ
   angebunden ist. Wenn nicht, ändert die Migration am Fulfillment nichts.
2. **Was genau ist am Fulfillment katastrophal?** Manuelles Herunter- und Hochladen
   der Druckdateien? Fehlende Bestell-Synchronisation? Fehlerhafte Druckdaten?
   Falsche Auflösung? Je nach Antwort ist die Lösung eine andere.
3. **Wie viele Bestellungen pro Monat?** Entscheidet die Kostenrechnung.
4. **Beide Anbieter dieselbe Frage stellen** — Customily im Sales-Chat, teeinblue im
   Support:

   > Kann der Personalisierungs-Ablauf als Schritt-für-Schritt-Wizard dargestellt
   > werden, bei dem der Kunde zuerst nur den Foto-Upload sieht und weitere Optionen
   > erst danach erscheinen? Gibt es Fortschrittsanzeige und Zurück-Button? Und kann
   > ein Bild-Upload als Bedingung für das Einblenden weiterer Felder dienen?

   Die letzte Teilfrage ist die entscheidende. Wer sie sauber mit Ja beantwortet, hat
   für diesen Shop das bessere Produkt.

## Empfehlung

**Migration ernsthaft prüfen — aber die UX-Fixes nicht davon abhängig machen.**

Konkret:

1. **Sofort und unabhängig:** teeinblue-Campaigns umbauen. Upload nach vorn,
   Pflichtfelder auf zwei, Bedingungsketten, Vorbelegung, Beschriftungen in
   Kundensprache. Kostet nichts, dauert Tage, wirkt sofort.
2. **Parallel:** Die vier Punkte oben klären, Customily-Demo ansehen, POD-Anbindung
   prüfen.
3. **Dann entscheiden** — mit Zahlen statt Bauchgefühl.

Der Grund für diese Reihenfolge: Punkt 1 verbessert den Shop **jetzt** und macht
gleichzeitig sichtbar, wie viel von der schlechten Conversion überhaupt an der App lag.
Diese Information macht die Migrationsentscheidung erst belastbar.

Und falls doch migriert wird: Die Arbeit aus Punkt 1 ist nicht verloren — die
Feldreihenfolge, die Beschriftungen und die Vorbelegungen wandern eins zu eins mit.

## Was teeinblue nachweislich kann

Für den Fall, dass es bei teeinblue bleibt — recherchiert am 11.08.2026:

- **Bedingungen für Layer**: Ein Layer und seine Option erscheinen erst, wenn ein
  anderer Layer eine Bedingung erfüllt
  ([Doku](https://support.teeinblue.com/en/article/add-condition-for-layer-1lrbftu/))
- **Sequenzielles Beispiel in der Doku**: erst Haarfarbe wählen, danach erscheint die
  Frisur-Option
  ([Doku](https://support.teeinblue.com/en/article/personalization-options-for-layers-in-artwork-14bz261/))
- **Toggle-Optionen** für Layer, mit Voreinstellung
  ([Doku](https://support.teeinblue.com/en/article/in-depth-guide-regarding-additional-option-feature-1akinc3/))

Damit lässt sich der gewünschte Schritt-für-Schritt-Flow als **Bedingungskette**
nachbauen: jede Option bekommt die vorherige als Bedingung. Ohne Fortschrittsanzeige
und Zurück-Button, aber die Überforderung verschwindet.

**Ungeklärt:** ob ein Bild-Upload als Bedingung taugt. In allen dokumentierten
Beispielen sind die Auslöser Auswahl-Optionen. Genau das wäre aber Schritt 1.
