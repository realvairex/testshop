# Übergabe an die lokale Session

Stand: **11.08.2026**. Bis hier wurde ausschließlich analysiert — **kein Theme-Code
verändert**.

## Zuerst lesen

| Datei | Inhalt |
|---|---|
| [`../CLAUDE.md`](../CLAUDE.md) | Projektkontext, Architektur-Entscheidungen, Sicherheitsregeln. Wird von Claude Code automatisch geladen. |
| [`entscheidungen.md`](entscheidungen.md) | Was entschieden ist, was offen ist, was bewusst zurückgestellt wurde |
| [`offene-fragen.md`](offene-fragen.md) | Checkliste zum Abhaken |

## Analysen

| Datei | Inhalt |
|---|---|
| [`theme-audit.md`](theme-audit.md) | Fabric 3.1.0, drei ungenutzte Page-Builder, Karteileichen, Design-Tokens |
| [`personalizer-audit.md`](personalizer-audit.md) | Neun Befunde zum teeinblue-Ablauf, aus einem Screenshot der Live-Produktseite |
| [`personalizer-app-entscheidung.md`](personalizer-app-entscheidung.md) | teeinblue behalten oder zu Customily wechseln — offene Entscheidung mit Kostenrechnung |
| [`setup-lokal.md`](setup-lokal.md) | Von null zur Live-Vorschau auf dem eigenen Rechner |

Dazu: [`.claude/skills/petworld-design/SKILL.md`](../.claude/skills/petworld-design/SKILL.md)
— Design-Regeln, wird bei Gestaltungsarbeit automatisch herangezogen.

Als lesbare Seite: **[PetWorld Shop-Audit](https://claude.ai/code/artifact/eb8007e1-4516-470e-94ce-376c38daacdb)**

## Der Stand in fünf Sätzen

1. Das Theme (**Fabric 3.1.0**) ist eine gute Basis — das Problem sind die Aufsätze.
2. Der **Personalizer überfordert**: neun Pflichtfelder, über 40 Farbfelder, der
   Foto-Upload steht ganz unten.
3. **Drei ungenutzte Page-Builder** (GemPages, PageFly, Shogun) laden auf jeder Seite mit.
4. Die Marke hat **kein Typo-System** — eine Schriftfamilie für alles, Überschriften auf
   76 % Deckkraft.
5. Zwei Fragen außerhalb des Codes blockieren die Strategie: der **Preis** (19,95 € lässt
   kaum Werbebudget) und die **Markennamen** (Parodien von Vogue, Playboy, Forbes,
   National Geographic).

## Als Nächstes

**Phase 1 — startklar, blockiert durch nichts:**
- 2,4 MB tote Page-Builder-Dateien und 31 unbenutzte Templates entfernen
  *(vorher prüfen: nutzt eine echte Seite ein `gp-template`?)*
- Token-System aufsetzen, Heading-Kontrast korrigieren

**Phase 2 — braucht eine Design-Richtung:**
Entweder Referenz-Shops nennen (Frage 21) oder einen Vorschlag als Prototyp machen
lassen und darauf reagieren.

**Phase 3 — im teeinblue-Admin, nicht im Theme:**
Bedingungsketten für den Schritt-für-Schritt-Ablauf, Upload nach vorn, Pflichtfelder
auf zwei reduzieren.

## Erster Satz für die neue Session

> Lies CLAUDE.md und docs/. Wir arbeiten an PetWorld weiter. Die Audits sind fertig,
> Phase 1 steht an.

## Was lokal besser wird

Die Cloud-Session konnte nur GitHub und Paket-Registries erreichen. Deshalb blieb
offen, was nur im Browser sichtbar ist: die Live-Vorschau des Personalizers, das
Verhalten auf dem Handy, das Warenkorb-Vorschaubild, Lighthouse-Messungen und die
teeinblue-Doku. Diese Punkte stehen in `offene-fragen.md` unter
*„Zu prüfen, sobald der Shop lokal läuft"*.
