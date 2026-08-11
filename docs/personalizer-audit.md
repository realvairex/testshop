# Personalizer-Audit (teeinblue) — Stand 11.08.2026

Grundlage: Screenshot der Live-Produktseite **PLAYDOG**.

## Was der Kunde aktuell vorfindet

Reihenfolge auf der Produktseite von oben nach unten:

```
★★★★☆ (89)
PLAYDOG
€19,95  €24,95  SALE 20%

VERFÜGBARE PRODUKTE   Poster ohne Rahmen · Rahmen Schwarz · Rahmen Weiß · Rahmen Eiche
GRÖSSEN               20x30cm · 40x60cm · 50x75cm

Primärfarbe *         2 Felder
Name deines Hundes *  Textfeld
Sekundärfarbe *       20 Farbfelder
Datum *               Textfeld (Platzhalter "AUGUST 2025")
Hintergrund *         20 Farbfelder
Bild deines Hundes *  Upload, ganz unten

[ ] Haftungs-Checkbox
IN DEN WARENKORB
Zahlungs-Icons
Produktbeschreibung / Pflegehinweise
```

---

## Befund A — Neun Pflichtentscheidungen für ein 20-€-Impulsprodukt

**Schweregrad: kritisch**

Jedes Feld ist mit `*` als Pflicht markiert. Der Kunde muss **neun Entscheidungen**
treffen, davon zwei aus je 20 Farbfeldern — über **40 Farbfelder insgesamt** —
bevor er kaufen kann.

Das ist Konfigurator-Logik für ein Geschenkprodukt mit niedriger Kaufhürde. Wer ein
Poster verschenken will, will nicht Grafikdesigner werden. Das ist mit hoher
Wahrscheinlichkeit der größte einzelne Conversion-Verlust im Shop.

**Zu tun:** Progressive Disclosure. Foto zuerst, sofortige Vorschau, dann optionales
Feintuning hinter "Design anpassen". Alle Farbfelder sinnvoll vorbelegen, sodass
das Standardergebnis bereits gut aussieht.

---

## Befund B — Der Foto-Upload steht ganz unten

**Schweregrad: kritisch**

Das Hochladen des Hundefotos ist der emotionale Kern des Produkts — der Moment, in dem
aus einem generischen Poster *das eigene Tier* wird. Aktuell kommt er **nach sieben
anderen Entscheidungen**.

Damit passiert der Wow-Effekt erst, wenn der Kunde die anstrengende Arbeit schon hinter
sich hat. Falls er überhaupt so weit kommt.

**Zu tun:** Upload an die erste Stelle. Foto rein → Vorschau mit dem eigenen Hund →
dann erst Farben, Name, Datum. Das ist die wirkungsvollste Einzeländerung.

---

## Befund C — Keine sichtbare Live-Vorschau neben den Bedienelementen

**Schweregrad: kritisch**

Im gesamten Formularbereich ist kein Vorschaubild zu sehen. Der Kunde wählt aus
40 Farben, ohne das Ergebnis zu sehen.

Genau das ist das Verkaufsversprechen der Personalisierung — und es ist unsichtbar.

**Noch zu prüfen:** Ob weiter oben oder daneben eine Vorschau existiert, die live
mitaktualisiert. Auf Mobilgeräten dürfte sie in jedem Fall aus dem Sichtfeld
gescrollt sein.

**Zu tun:** Sticky-Vorschau, die beim Scrollen mitläuft. Jede Farbänderung muss
sofort sichtbar sein.

---

## Befund D — Der Haftungstext direkt über dem Kaufen-Button

**Schweregrad: hoch**

> „Ich habe alle personalisierten Eingaben sorgfältig geprüft und bestätige, dass diese
> korrekt und vollständig sind. Mir ist bekannt, dass das Produkt genau nach diesen
> Angaben produziert wird und nachträgliche Änderungen, Korrekturen oder Rückgaben
> aufgrund fehlerhafter Eingaben ausgeschlossen sind."

Rechtlich nachvollziehbar (§18 Abs. 1 Z 3 FAGG), psychologisch eine kalte Dusche
im Moment der höchsten Kaufbereitschaft. Der Text schiebt das gesamte Risiko zum
Kunden und sät Zweifel genau dort, wo Sicherheit gebraucht wird.

**Zu tun:** Aufklärungspflicht erfüllen, aber positiv rahmen. Etwa: sichtbare
Design-Bestätigung mit Vorschau („So wird dein Poster gedruckt"), daneben ein
Vertrauenssatz („Unser Team prüft jedes Design vor dem Druck"), und der rechtliche
Hinweis knapper und weniger bedrohlich formuliert.

---

## Befund E — Der Rahmen-Upsell wird verschenkt

**Schweregrad: hoch**

„Poster ohne Rahmen · Rahmen Schwarz · Rahmen Weiß · Rahmen Eiche" — als nackte
Textbuttons, **ohne Bild und ohne Preisangabe**.

Der Rahmen ist bei diesem Sortiment der stärkste AOV-Hebel überhaupt. Aktuell muss
der Kunde raten, wie „Rahmen Eiche" aussieht und was er kostet.

**Zu tun:** Miniatur-Vorschau je Rahmen, Preisaufschlag sichtbar („+15 €"), eine
Option als empfohlen markieren.

---

## Befund F — Beschriftungen sind aus Systemsicht formuliert

**Schweregrad: mittel**

| Aktuell | Problem | Vorschlag |
|---|---|---|
| „VERFÜGBARE PRODUKTE" | Keine Kundensprache, meint eigentlich den Rahmen | „Rahmen wählen" |
| „Primärfarbe" / „Sekundärfarbe" | Kunde weiß nicht, was gefärbt wird | „Schriftfarbe" / „Akzentfarbe" |
| „Datum" | Unklar, wofür | „Datum auf dem Poster (optional)" |
| Platzhalter „AUGUST 2025" | Veraltet — aktuell ist August 2026 | Dynamisch oder neutral |

Der veraltete Platzhalter ist ein Detail, signalisiert aber Vernachlässigung.

---

## Befund G — 89 Bewertungen bei 4,5 Sternen, unsichtbar platziert

**Schweregrad: mittel**

Echtes Social Proof, gerendert als kleine graue Zeile über dem Titel. Nicht anklickbar,
keine Foto-Reviews, keine Bewertungen weiter unten auf der Seite.

**Zu tun:** Sternebewertung prominenter, verlinkt auf einen Bewertungsblock mit
Kundenfotos weiter unten. Bei personalisierten Produkten sind Fotos anderer Kunden
das stärkste Kaufargument.

---

## Befund H — Fehlende Sicherheit rund um den Kaufen-Button

**Schweregrad: mittel**

Es fehlen: Lieferzeit-Angabe, Versandkosten-Hinweis, Zufriedenheitsgarantie,
Hinweis auf Produktion in der EU. Die Zahlungs-Icons allein tragen das nicht.

---

## Befund I — Dekoratives Pfoten-Muster im Hintergrund

**Schweregrad: niedrig**

Hinter dem Formular liegen große graue Pfotenabdrücke. Sie senken die Lesbarkeit des
Formulars und wirken günstig — gegenläufig zum Ziel, das Produkt hochwertiger
erscheinen zu lassen.

---

## Empfohlene Reihenfolge des Personalizer-Umbaus

1. **Foto-Upload nach oben**, Vorschau direkt daneben — größter Einzeleffekt
2. **Pflichtfelder reduzieren**: nur Foto und Name als Pflicht, alles andere vorbelegt
   und optional hinter „Design anpassen"
3. **Sticky-Vorschau**, die jede Änderung sofort zeigt
4. **Rahmen-Upsell mit Bild und Preis**
5. **Haftungstext umformulieren** und mit einer Design-Bestätigung koppeln
6. **Beschriftungen in Kundensprache**
7. **Bewertungsblock mit Kundenfotos** weiter unten auf der Seite

Punkte 1–3 und 6 liegen in teeinblue selbst (Campaign-Konfiguration), nicht im Theme.
Punkte 4, 5 und 7 sind gemischt Theme und App.

## Offene Prüfpunkte

- Gibt es oberhalb des Formulars eine Live-Vorschau, und aktualisiert sie sich?
- Wie sieht der Warenkorb aus — erscheint dort das Design des Kunden oder das Stock-Foto?
- Wie verhält sich der Personalizer auf einem echten Mobilgerät?
- Bietet teeinblue eine App-Block-Einbindung statt des Embeds?
