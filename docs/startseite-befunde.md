# Startseite — Befunde aus der Sichtprüfung

Stand 12.08.2026. Grundlage: zwei Screenshots des Betreibers (Hero-Bereich und
Newsletter-Abschnitt), Desktop-Breite. **Nicht** auf einem Mobilgerät geprüft — und
78 % des Traffics ist mobil.

## Was gut ist

Das sollte beim Umbau erhalten bleiben:

- **Die Poster-Motive tragen.** Magazin-Cover-Optik, kräftige Farben, klare Typografie
  auf den Covern. Das Konzept funktioniert visuell.
- **Der Ton passt.** Wellenformen, Pfotenabdrücke, Sprechblase — verspielt und warm,
  genau richtig für ein Geschenkprodukt.
- **Die Headline sitzt.** „Mach dein Haustier unvergesslich." ist kurz, konkret und
  emotional.

> Korrektur zu einer früheren Einschätzung: Ich hatte das Pfoten-Muster pauschal als
> „wirkt günstig" abgetan. Auf der Startseite ist es dezent und funktioniert. Der
> Einwand gilt nur dort, wo es **hinter Formulartext** liegt — im Personalizer.

## Befund 1 — Kein Call-to-Action im Hero

**Schweregrad: hoch**

Der Hero füllt einen ganzen Bildschirm und enthält **keinen einzigen Button**. Der
Besucher muss selbst darauf kommen, zu scrollen oder ins Menü zu gehen.

Das ist die wertvollste Fläche der Seite. Bei 0,07 % echter Conversion ist eine Fläche
ohne Handlungsaufforderung einer der teuersten Einzelposten.

**Zu tun:** Primärer Button („Jetzt Poster gestalten") direkt unter der Headline,
verlinkt auf die POSTER-Kollektion oder das Bestseller-Produkt.

## Befund 2 — Der Hero zeigt nicht, worum es geht

**Schweregrad: hoch**

Zu sehen sind drei fertige Poster mit **fremden** Tieren. Die eigentliche Idee — *dein*
Hund kommt aufs Cover — kommt visuell nicht vor.

Bei personalisierten Produkten ist das der entscheidende Moment: Der Besucher muss in
einer Sekunde begreifen, dass sein eigenes Tier dort landet.

**Zu tun:** Vorher/Nachher im Hero. Links ein gewöhnliches Handyfoto eines Hundes,
rechts das fertige Poster. Nichts überzeugt bei diesem Sortiment schneller.

## Befund 3 — Kontrast der Hauptnavigation, sichtbar bestätigt

**Schweregrad: mittel bis hoch**

Die Menüpunkte (BESTSELLER, POSTER, KISSEN, TASSEN, HAUSTIERBETT) stehen weiß auf
Petrol und wirken auf dem Screenshot blass.

**Das bestätigt die Rechnung aus `kontrast-audit.md`: `scheme-2` erreicht 2,2:1 statt
der geforderten 4,5:1.** Der Befund ist damit nicht nur berechnet, sondern belegt.

Dasselbe im Newsletter-Kasten: „NEWSLETTER" steht dunkel und sitzt gut, der Satz
darunter („Als Dank erhältst du…") ist weiß auf Petrol und deutlich schwächer.

**Damit ist auch die offene Frage aus dem Kontrast-Audit beantwortet** — von den beiden
gegensätzlich gefärbten Texten ist der **weiße** der problematische.

**Zu tun:** Petrol auf etwa `#3d7d78` abdunkeln, Weiß beibehalten. Ergibt ~4,6:1 bei
nahezu unverändertem Erscheinungsbild. Gehört in die CI-Phase, weil es die Markenfarbe
berührt.

## Befund 4 — Länderauswahl zeigt Flagge und Sprache widersprüchlich

**Schweregrad: niedrig**

Oben rechts steht die **österreichische Flagge** neben **„EUR / DE"**. Für einen
österreichischen Shop wirkt das unstimmig — entweder AT als Sprachkürzel, oder die
Flagge zur Sprache passend wählen.

## Befund 5 — Viel Fläche für wenig Information

**Schweregrad: mittel**

Der Hero nimmt die volle Bildschirmhöhe für eine Headline und eine Sprechblase. Auf
dem Handy bedeutet das: Der Besucher muss scrollen, bevor er ein einziges Produkt oder
einen Preis sieht.

**Zu tun:** Hero verdichten, erste Produkte früher sichtbar machen. Auf Mobil sollte
mindestens eine Produktkachel ohne Scrollen angeschnitten sein.

## Noch zu prüfen

- [ ] **Alles oben auf einem echten Mobilgerät nachvollziehen.** Alle Befunde stammen
      aus Desktop-Screenshots.
- [ ] Sitzt die Sprechblase am rechten Rand korrekt, oder wird sie abgeschnitten?
      Im Screenshot endet der Text an der Bildkante — kann am Ausschnitt liegen.
- [ ] Ladezeit messen, sobald GemPages entfernt ist (Lighthouse, mobil)
