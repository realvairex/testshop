# PetWorld — Projektkontext

**Antworte in diesem Projekt auf Deutsch.** Der Betreiber ist Österreicher, die
Zusammenarbeit läuft auf Deutsch.

## Worum es geht

PetWorld (pet-world.at) ist ein österreichischer Shopify-Shop für **personalisierte
Haustier-Produkte** — Poster, Kissen, Tassen, Haustierbetten. Der Kunde lädt ein Foto
seines Hundes oder seiner Katze hoch, das in ein stilisiertes Design eingearbeitet wird.
Print-on-Demand, keine eigene Produktion.

Bestseller sind Poster mit Magazin-Cover-Optik zu einheitlich **19,95 €** (Streichpreis
24,95 €).

**Das Ziel:** Der Shop macht zu wenig Umsatz. Gearbeitet wird an Design, Stimmigkeit,
Geschwindigkeit, Corporate Identity, dem Personalisierungs-Ablauf und Sichtbarkeit/SEO.

## Arbeitsstand

Branch: `claude/petworld-shopify-brainstorm-9go0du`

| Commit | Inhalt |
|---|---|
| `cacbd97` | **Unveränderter Theme-Export als Baseline.** Referenzpunkt für jeden Vergleich. |
| danach | Audits und Dokumentation unter `docs/` |

Bisher wurde **kein Theme-Code verändert**. Alles bis hier ist Analyse.

## Technische Basis

- **Theme: Fabric 3.1.0** (Shopify First-Party, block-basiert, Horizon-Generation)
- 557 Dateien, 116 Sections, 87 Blocks, 130 Snippets, 56 Templates
- Kein Build-Step. Reines Liquid, CSS, Vanilla-JS.

### Installierte Apps

| App | Status | Bewertung |
|---|---|---|
| teeinblue Product Personalizer | aktiv, App-**Embed** | Kern des Geschäfts. Fulfillment-Workflow gilt als veraltet und umständlich. |
| merchOne | aktiv | **Einziger POD-Partner.** Versand nicht im Einkaufspreis enthalten |
| smind / Sections Pro | aktiv | wird genutzt (`sp-*` Sections auf der Startseite) |
| Klaviyo | aktiv | **unterbewertet** — Warenkorbabbruch-Mails sind der billigste Hebel |
| GemPages | aktiv | ⚠️ **Erst Weiterleitungen setzen, dann deinstallieren.** 5 veröffentlichte Seiten nutzen `gp-template`-Suffixe |
| PageFly, Shogun, Gelato, Section Star, Section Store, Dakaas | **deinstalliert** | 12.08.2026, Theme-Reste entfernt |
| Opus Cart Upsell | nicht mehr installiert | App-Embed-Eintrag liegt noch in `settings_data.json` |

**Weiterhin ungeklärt:** Stack ($9,99/Monat), TinySEO, AddressHero, Vidify, Collective,
Messaging, Predis, CWILL Popup Email, Essential Announcer, Customix Personalizer
(zweiter Personalizer!). Dazu **zwei** Warenkorb-Apps parallel: EGO Cart Upsell
($12,99) und AMP Slide Cart.

## Getroffene Architektur-Entscheidungen

**1. Liquid-Theme bleibt, kein Headless.**
Hydrogen/Next.js würde teeinblue zerstören — der Personalizer ist als App-Embed für den
Online Store gebaut. Dazu Checkout, Klarna/EPS, Reviews, Tracking. Nicht verhandelbar,
solange die Personalisierung über eine Shopify-App läuft.

**2. Kein Framer Motion.**
Das ist React-only. Für Animationen: **Motion One** (motion.dev, Vanilla-JS, ~5 kB) oder
CSS scroll-driven animations. Optisch gleichwertig, besser für Core Web Vitals.

**3. Dreischichtiges Token-Modell** (primitive → semantic → component) als CSS Custom
Properties, angebunden an `config/settings_schema.json`, damit Farben im Theme-Editor
änderbar bleiben ohne Code-Änderung.

**4. Fremde Design-Skills werden nicht als Plugin installiert.**
Das Repo `nextlevelbuilder/ui-ux-pro-max-skill` wird nur als Referenz für Token-Struktur
und Paletten genutzt — nicht als Plugin, weil es fremde Anweisungen, Python-Skripte und
eine `.mcp.json` in ein Repo bringt, das an den Live-Shop gekoppelt wird.

## Sicherheitsregeln

- **Nie direkt am Live-Theme arbeiten.** Immer Entwicklungs-Theme, Veröffentlichen ist
  ausschließlich die Entscheidung des Betreibers.
- **`shopify theme push` ohne Flags ist verboten** — kann das Live-Theme überschreiben.
  `shopify theme dev` legt automatisch ein Dev-Theme an und ist sicher.
- **Keine API-Keys, Theme-Access-Passwörter oder Tokens in den Chat.** Falls nötig:
  `.env` mit `.gitignore`.
- **Vor dem Löschen von Page-Builder-Dateien** immer die `templateSuffix`-Zuweisung
  über den Connector prüfen — nicht nur die Theme-Templates. Genau daran wäre die
  erste Einschätzung fast gescheitert: Fünf veröffentlichte Seiten hängen an
  GemPages, obwohl im Theme nichts darauf hindeutet.

## Navigation — Achtung, Fabric arbeitet ohne Menü-Objekte

**Die Fußzeile verlinkt FAQ, Über uns, Weiterempfehlen, Bilder-Leitfaden und Kontakt.**
Diese Links stehen aber **nicht** in einem Shopify-Menü, sondern als fest gesetzte
`button`-Blöcke in `sections/footer-group.json`.

Wer nur die Menü-Objekte über die API prüft (`main-menu`, `footer`), sieht sie nicht
und hält die Seiten fälschlich für unverlinkt. Genau dieser Fehler ist am 12.08.
passiert — siehe Korrektur K3 in `docs/entscheidungen.md`.

**Regel: Navigation immer in beiden Quellen prüfen** — Shopify-Menüs *und*
`footer-group.json` / `header-group.json`.

Offen bleibt: Jede dieser Seiten existiert **doppelt** (eine GemPages- und eine native
Fassung), beide veröffentlicht. Verlinkt ist jeweils die native. Die GemPages-Zwillinge
sind unverlinkt, aber indexierbar → doppelte Inhalte, per Weiterleitung zu bereinigen.

## Die wichtigsten Befunde

Ausführlich in `docs/theme-audit.md` und `docs/personalizer-audit.md`.

1. **Der Personalizer überfordert** — 9 Pflichtfelder, über 40 Farbfelder, Foto-Upload
   an letzter Stelle, keine sichtbare Live-Vorschau. Kritisch.
2. **Drei ungenutzte Page-Builder laden auf jeder Seite mit.** Größter Performance-Hebel.
3. **Kein Typo-System** — eine einzige Schriftfamilie (Asap) für alle vier Rollen.
   Überschriften laufen auf `#030302c2`, also 76 % Deckkraft. Ausgegraut und
   kontrastschwach.
4. **Preis und Varianten** werden ausschließlich von teeinblue clientseitig gerendert.
   Die nativen `price`- und `variant-picker`-Blöcke existieren, sind aber nicht platziert.

## Die Lage in Zahlen

**Vollständig in `docs/zahlen.md`** (Shopify-Connector, 12.08.2026). Das Wichtigste:

| | |
|---|---|
| Sessions letzte 12 Monate | 11.072 — davon 87 % in Dez–Feb |
| Sessions aktuell | **26 im Monat** (Höchststand war 3.681) |
| Bestellungen gesamt | **16** |
| Bruttoumsatz gesamt | **616 €** |
| **Conversion Rate** | **0,14 %** — etwa ein Zehntel des Shopify-Medians |
| Traffic-Quelle | 78 % Social, fast nur mobil. Suche: 98 Sessions im Jahr |
| Fulfillment | **13 von 16 Bestellungen nicht vollständig ausgeliefert** |

Von den 16 Bestellungen sind **acht Familie oder Test** (alle mit Nachnamen Kases,
vom Betreiber bestätigt). Die echte Conversion liegt damit bei etwa **0,07 %**.

**Zwei Probleme, in dieser Reihenfolge:**

1. **Conversion.** Die Personalizer-Diagnose ist belegt: 9.675 Besucher in drei
   Monaten erzeugten 14 Bestellungen. Neun Pflichtfelder, über 40 Farbfelder,
   Foto-Upload zuletzt.
2. **Traffic.** Es lief Facebook-Werbung von Dezember bis Februar. Seit März/April
   wurde nichts mehr gemacht — aus Zeitmangel, nicht wegen eines Problems.

**Reihenfolge ist entscheidend:** Traffic anschalten, bevor die Conversion stimmt,
verbrennt Geld — das ist bereits einmal passiert. Die Werbung hat funktioniert, die
Seite hat die Besucher nicht abgeholt.

**Fulfillment ist erledigt.** Die offenen Bestellungen sind Altlasten aus der
Anfangszeit, keine unbelieferten Kunden. Bestätigt am 12.08.2026.

## Wirtschaftlicher Vorbehalt — korrigiert

Frühere Fassungen dieses Dokuments warnten, bei 19,95 € bleibe zu wenig
Deckungsbeitrag für Werbung. **Das war zu pessimistisch und basierte auf geschätzten
Kosten.**

Echte Zahlen: Poster 20×30 kostet im Einkauf **3,32 €** bei 19,95 € Verkaufspreis —
**16,63 € Deckungsbeitrag, 83 % Marge.** Ein gerahmtes 40×60 bringt **40,60 €**.
Ein CPA von 10–14 € ist damit tragfähig.

Offen bleibt, ob `unitCost` den Versand des POD-Partners enthält.

Der permanente Streichpreis 24,95 → 19,95 bleibt nach der EU-Omnibus-Richtlinie
heikel: Der durchgestrichene Preis muss der niedrigste der letzten 30 Tage sein.

⚠️ Ebenfalls zu klären: Die Produktseite zeigt **89 Bewertungen** bei **16
Bestellungen** insgesamt. Erfundene oder nicht verifizierte Bewertungen sind nach
UWG und Omnibus-Richtlinie unzulässig.

## Markenrechtlicher Vorbehalt

Die Poster heißen DOGUE (Vogue), PLAYDOG/PLAYCAT (Playboy), FURBES (Forbes),
NATIONAL PAWGRAPHIC (National Geographic). Alle vier Rechteinhaber gehen aktiv gegen
kommerzielle Markenparodien vor. Konsequenzen: Ad-Ablehnungen und Kontosperren bei
Meta/TikTok, Shopify-Takedowns, und auf diese Namen ist kein SEO aufbaubar.

Empfehlung: Designs behalten, Namen eigenständig machen. **Entscheidung liegt beim
Betreiber und ist offen.**

## Grundhaltung: proaktiv arbeiten

**Das ist die wichtigste Erwartung an die Zusammenarbeit in diesem Projekt, keine
Nettigkeit am Rande.** Der Betreiber soll nicht danach fragen müssen.

- **Auffälligkeiten sofort melden**, nicht auf Nachfrage warten: Sicherheitsrisiken,
  Datenverlustgefahr, Widersprüche zwischen Dokumenten, veralteter Stand, unsaubere
  Abhängigkeiten, Dinge die später teuer werden.
- **Mitdenken statt abarbeiten.** Wenn eine Aufgabe eine bessere Lösung nahelegt als
  die wörtlich verlangte, wird sie genannt — und die verlangte trotzdem geliefert,
  wenn der Betreiber dabei bleibt.
- **Widersprechen, wenn etwas nicht stimmt.** Auch bei einer Bitte des Betreibers.
  Einmal sagen, begründen, dann seiner Entscheidung folgen.
- **Unnötige Arbeit abraten.** Wenn ein gemeldeter Fehler beim anstehenden Umstieg
  ohnehin verschwindet, wird das gesagt, bevor Zeit hineinfließt.
- **Selbst dokumentieren, selbst committen, selbst Meilensteine setzen** — ohne
  Aufforderung.
- **Ehrlich berichten.** Was nicht geprüft wurde, wird nicht als geprüft dargestellt.
  Fehlgeschlagenes wird benannt, nicht weggelassen. Korrekturen früherer Aussagen
  gehören ins Entscheidungs-Log.

Praktische Konsequenz: Vor jeder Behauptung über den Shop wird gegengeprüft — über
den Shopify-Connector, nicht aus dem Gedächtnis. Vor jedem Löschen wird auf
Referenzen geprüft. Nach jeder Änderung wird unabhängig nachgelesen, ob sie
tatsächlich sitzt.

## Ablauf-Befehle

Der Betreiber steuert Sitzungsbeginn und -ende über zwei Klartext-Befehle. **Kein
Schrägstrich, einfach so getippt:**

| Eingabe | Was zu tun ist |
|---|---|
| **`start petworld`** | Skill `start-petworld` ausführen: Projektstand lesen, Repo und Connector prüfen, Stand melden, nächsten Schritt vorschlagen — und auf Bestätigung warten |
| **`ende petworld`** | Skill `ende-petworld` ausführen: alles Wissen aus dem Gespräch ins Repo schreiben, Entscheidungs-Log und TODO aktualisieren, committen, pushen, Übergabe ausgeben |

Beide Abläufe sind verbindlich und werden vollständig abgearbeitet, auch wenn die
Sitzung kurz war. **Nach `ende petworld` darf der Chat verloren gehen, ohne dass
Wissen verloren geht.**

## Vorgehen

Siehe `docs/entscheidungen.md` für den Stand aller Entscheidungen und
`docs/offene-fragen.md` für das, was noch fehlt.

Phasen: 1) Aufräumen + Tokens · 2) Corporate Identity · 3) Personalizer ·
4) Seiten polieren · 5) SEO und Sichtbarkeit.

Arbeitsweise, die sich bewährt hat: **Design-Entscheidungen zuerst als HTML-Prototyp
zeigen**, erst nach Freigabe in Liquid umsetzen. Spart Runden.
