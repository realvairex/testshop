# Personalizer-Vorlage für teeinblue

Stand 13.08.2026. **Arbeitsanweisung zum Abarbeiten im teeinblue-Admin.**
Grundlage: `personalizer-audit.md` (Befunde A–I) und die echten Produktvarianten,
am 13.08. über den Shopify-Connector geprüft.

> **Erfolgskriterium:** Du kannst diese Vorlage im teeinblue-Admin abarbeiten, ohne
> zwischendurch fragen zu müssen. Jedes Feld hat Name, Typ, Pflicht-Status,
> Vorbelegung, Bedingung und fertigen Text.
>
> **Messbar erledigt ist es, wenn** ein Testkauf auf dem Handy vom Öffnen der
> Produktseite bis „In den Warenkorb" mit **zwei Eingaben** möglich ist: Foto und Name.

---

## Vorher / Nachher

| | Heute | Nach der Umstellung |
|---|---|---|
| Pflichtfelder | **9** | **2** (Foto, Name) |
| Farbfelder sichtbar | **über 40** | **0** — eingeklappt hinter „Design anpassen" |
| Position des Foto-Uploads | ganz unten, nach 7 Entscheidungen | **erste Stelle** |
| Rahmenauswahl | nackte Textbuttons ohne Bild und Preis | Miniatur + Preisaufschlag |
| Erster Wow-Moment | nach der ganzen Arbeit | **sofort nach dem Foto** |

---

## Voraussetzung: ein Test, fünf Minuten

**Kann ein Bild-Upload in teeinblue als Bedingung für andere Felder dienen?**
Davon hängt ab, welchen der beiden Zweige unten du nimmst. Ich kann es von hier nicht
prüfen — `teeinblue.com` ist aus meiner Umgebung nicht erreichbar (U2).

*So testest du es:* Lege in der Campaign ein beliebiges Textfeld an und versuche, ihm
eine Bedingung zu geben, die auf das Upload-Feld verweist („nur anzeigen, wenn Foto
hochgeladen"). Steht das Upload-Feld in der Bedingungsliste zur Auswahl?

- **Ja** → **Zweig A** (nativer Wizard). Das ist der Idealfall.
- **Nein** → **Zweig B** (alles auf einer Seite, aber sortiert und eingeklappt).
  Verliert wenig, weil der entscheidende Effekt aus der Reihenfolge kommt, nicht aus
  der Schrittlogik.

Beide Zweige nutzen dieselben Felder und Texte. Es unterscheidet sich nur, ob die
späteren Felder **versteckt** oder nur **weiter unten** sind.

---

## Die neue Reihenfolge

### 1 · Foto — das Erste, was der Kunde sieht

| | |
|---|---|
| **Beschriftung** | `Foto deines Lieblings` |
| **Typ** | Bild-Upload |
| **Pflicht** | ja |
| **Hilfetext darunter** | `Quer oder hoch, Hauptsache scharf und hell. Wir schneiden passend zu. → So gelingt das beste Foto` |
| **Link im Hilfetext** | `/pages/leitfaden` |

Der Link zeigt auf die native Leitfaden-Seite. **Nicht** auf `/pages/bild-leitfaden` —
die GemPages-Fassung ist seit 13.08. stillgelegt und wird umgeleitet.

**Warum ganz oben:** Das ist der Moment, in dem aus einem generischen Poster *das
eigene Tier* wird (Befund B). Er darf nicht hinter sieben Entscheidungen liegen.

### 2 · Name

| | |
|---|---|
| **Beschriftung** | `Name deines Lieblings` |
| **Typ** | Textfeld, max. 15 Zeichen |
| **Pflicht** | ja |
| **Platzhalter** | `z. B. Luna` |
| **Bedingung (Zweig A)** | erst zeigen, wenn ein Foto hochgeladen ist |

Die Zeichenbegrenzung ist wichtig: Lange Namen sprengen das Layout im Druck. 15 ist
großzügig genug für praktisch jeden Tiernamen.

### 3 · Format und Rahmen — hier entsteht der Umsatz

Das sind Shopify-Varianten, keine teeinblue-Felder. Falls teeinblue sie nicht nach
unten verschieben kann, bleiben sie oben — dann trotzdem die Beschriftungen und Preise
wie hier angeben.

**Beschriftung statt „VERFÜGBARE PRODUKTE": `Rahmen wählen`**
**Beschriftung statt „GRÖSSEN": `Größe`**

Die echten Varianten und Preise, am 13.08. geprüft:

| Größe | ohne Rahmen | mit Rahmen | Aufschlag |
|---|---|---|---|
| 20×30 cm | 19,95 € | 39,95 € | **+20 €** |
| 40×60 cm | 29,95 € | 64,95 € | **+35 €** |
| 50×75 cm | 39,95 € | **gibt es nicht** | — |

**So darstellen:**

- Jede Rahmenoption mit **Miniaturbild** (Schwarz, Weiß, Eiche) statt als Textbutton
- Preisaufschlag direkt am Button: `+20 €`
- **Rahmen Schwarz** als `Beliebteste Wahl` markieren
- Vorbelegung: **20×30 cm, ohne Rahmen**

**Warum die günstigste Variante vorbelegt ist:** Bei 0,07 % Conversion ist die
Einstiegshürde das Problem, nicht der Warenkorbwert. Erst wenn Leute überhaupt kaufen,
lohnt es sich, die Vorbelegung nach oben zu schieben. Der Rahmen wird über Bild und
Sichtbarkeit verkauft, nicht über die Vorauswahl.

**Der Hebel dahinter:** Ein gerahmtes 40×60 bringt **40,60 €** Deckungsbeitrag, das
Basis-Poster **16,63 €** — das 2,4-fache (`zahlen.md`).

> ⚠️ **Pflicht-Bedingung, sonst Sackgasse:** Für **50×75 cm existiert keine
> Rahmenvariante**. Wer diese Größe wählt, darf die Rahmenoptionen nicht mehr
> angeboten bekommen — sonst führt die Auswahl in eine Kombination, die es nicht gibt.
> Umgekehrt: Wer einen Rahmen gewählt hat, darf 50×75 nicht mehr sehen.

### 4 · „Design anpassen" — alles Übrige, eingeklappt

Ein **zugeklappter** Abschnitt mit der Beschriftung:

```
Design anpassen (optional)
Sieht auch ohne Änderung gut aus.
```

Darin, in dieser Reihenfolge — **alle optional, alle vorbelegt**:

| Feld | Neue Beschriftung | Bisher | Vorbelegung |
|---|---|---|---|
| Primärfarbe | `Schriftfarbe` | „Primärfarbe" (2 Felder) | dunkler Ton, passt zu allen Motiven |
| Sekundärfarbe | `Akzentfarbe` | „Sekundärfarbe" (20 Felder) | auf **6 kuratierte** reduzieren |
| Hintergrund | `Hintergrund` | „Hintergrund" (20 Felder) | auf **6 kuratierte** reduzieren |
| Datum | `Datum auf dem Poster (optional)` | „Datum", Platzhalter „AUGUST 2025" | **leer lassen** |

**Zu den Farbfeldern:** 20 Felder sind keine Auswahl, sondern eine Zumutung
(Befund A). Nimm die sechs, die mit den meisten Fotos funktionieren — welche das sind,
siehst du in deinen bisherigen Bestellungen besser als ich. Der Rest kann weg; niemand
wird ihn vermissen, und die Vorbelegung muss ohnehin für sich stehen können.

**Zum Datumsfeld:** Der Platzhalter „AUGUST 2025" ist im August 2026 ein Signal von
Vernachlässigung (B9). Entweder leer lassen oder neutral: `z. B. Seit 2019`.

---

## Der Kaufabschluss

### Haftungstext — neu formuliert

**Heute** (Befund D) — eine kalte Dusche im Moment der höchsten Kaufbereitschaft:

> „Ich habe alle personalisierten Eingaben sorgfältig geprüft und bestätige, dass diese
> korrekt und vollständig sind. Mir ist bekannt, dass das Produkt genau nach diesen
> Angaben produziert wird und nachträgliche Änderungen, Korrekturen oder Rückgaben
> aufgrund fehlerhafter Eingaben ausgeschlossen sind."

**Neu** — dieselbe Aufklärung, andere Wirkung:

> **So wird dein Poster gedruckt.**
> Schau dir die Vorschau noch einmal an — Name und Schreibweise übernehmen wir genau so.
> Weil jedes Stück einzeln für dich gefertigt wird, ist ein Umtausch bei Tippfehlern
> leider nicht möglich.
>
> ☑ Passt, so soll es gedruckt werden.

**Warum das trägt:** Die Aufklärungspflicht nach § 18 Abs. 1 Z 3 FAGG verlangt, dass
der Kunde über den Verlust des Rücktrittsrechts bei personalisierter Ware informiert
wird und dem zustimmt. Das leistet die neue Fassung — „einzeln für dich gefertigt",
„Umtausch nicht möglich", aktive Checkbox. Sie erklärt statt zu drohen.

> **Kein Rechtsrat.** Ich habe die Formulierung an der Fundstelle im bestehenden Text
> ausgerichtet, nicht juristisch geprüft. Wenn du beim ursprünglichen Wortlaut anwaltlich
> beraten wurdest, lass die Neufassung gegenlesen, bevor sie live geht.

### Vertrauenssatz darunter

```
Unser Team schaut sich jedes Design vor dem Druck an.
```

Nur setzen, **wenn es stimmt** — also wenn du die Designs tatsächlich vor der Weitergabe
an merchOne ansiehst. Falls das Rendering vollautomatisch läuft, den Satz weglassen.
(Das ist die offene Frage 18 in `offene-fragen.md`.)

---

## Feldliste zum Abhaken

| # | Feld | Typ | Pflicht | Bedingung |
|---|---|---|---|---|
| 1 | Foto deines Lieblings | Upload | ✅ ja | — |
| 2 | Name deines Lieblings | Text, max. 15 | ✅ ja | nach Foto (Zweig A) |
| 3 | Größe | Variante | — | 50×75 schließt Rahmen aus |
| 4 | Rahmen wählen | Variante | — | nur bei 20×30 und 40×60 |
| 5 | Schriftfarbe | Farbwahl | ❌ optional | in „Design anpassen" |
| 6 | Akzentfarbe (6 statt 20) | Farbwahl | ❌ optional | in „Design anpassen" |
| 7 | Hintergrund (6 statt 20) | Farbwahl | ❌ optional | in „Design anpassen" |
| 8 | Datum (optional) | Text | ❌ optional | in „Design anpassen" |
| 9 | Design-Bestätigung | Checkbox | ✅ ja | direkt über dem Kaufen-Button |

**Von neun Pflichtfeldern auf zwei.**

---

## Was nicht in teeinblue liegt

Diese Punkte aus dem Audit gehören ins Theme und mache ich, sobald du grünes Licht gibst:

- **Sticky-Vorschau**, die beim Scrollen mitläuft (Befund C) — auf dem Handy verschwindet
  die Vorschau sonst aus dem Sichtfeld, und 78 % des Traffics ist mobil
- **Sticky „In den Warenkorb"** auf Mobil
- **Bewertungsblock** weiter unten (Befund G) — hängt an E11, kommt zur Design-Phase
- **Pfoten-Muster hinter dem Formular** entfernen (Befund I)

Ob teeinblue statt des App-Embeds eine **App-Block-Einbindung** anbietet, ist noch
offen. Damit ließe sich die Position im Theme steuern, statt sie der App zu überlassen.

---

## Zwei Funde aus der Variantenprüfung

**1 · Die Produktoption „Color" hat nur einen einzigen Wert: `Default`.**
Eine Variantenoption mit genau einem Wert ist funktionslos. Je nachdem, wie teeinblue
und das Theme sie rendern, erscheint sie als leere oder sinnlose Auswahl im
Bestellprozess — und sie taucht in jedem Variantentitel auf
(`Poster ohne Rahmen / Default / 20x30cm`). Das steht auch so in den Bestelldaten.
*Empfehlung:* Im Shopify-Admin entfernen. **Vorher prüfen, ob teeinblue die Campaign
über diese Option zuordnet** — sonst bricht die Zuordnung.

**2 · Für 50×75 cm gibt es keinen Rahmen.** Ohne Bedingung führt die Größenauswahl in
eine nicht existierende Kombination. Siehe die Warnung in Abschnitt 3.

---

## Reihenfolge der Umsetzung

Wenn du nicht alles auf einmal machen willst — so ist der Effekt pro Aufwand am größten:

1. **Foto-Upload nach oben** (Befund B) — die wirkungsvollste Einzeländerung
2. **Pflicht-Sternchen von den sieben anderen Feldern nehmen**, alles vorbelegen
3. **Farbfelder von 20 auf 6**, in „Design anpassen" einklappen
4. **Rahmen mit Bild und Preis**
5. **Beschriftungen** in Kundensprache
6. **Haftungstext** ersetzen

Schritte 1 und 2 sind zusammen vielleicht eine halbe Stunde und nehmen den größten Teil
der Reibung heraus.
