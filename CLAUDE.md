# PetWorld

Shopify-Shop für personalisierte Haustier-Produkte (pet-world.at, Österreich). Der Kunde
lädt ein Foto seines Tiers hoch, das in ein Poster-, Kissen- oder Tassendesign eingearbeitet
wird. Print-on-Demand. **Antworte auf Deutsch, duzen.**

**Das Problem:** 0,07 % echte Conversion bei 11.072 Sessions im Jahr. Gearbeitet wird an
Personalizer, Design, Geschwindigkeit, Corporate Identity und Sichtbarkeit — in dieser
Reihenfolge. Zahlen in `docs/zahlen.md`.

## Sitzungsbefehle

| Eingabe (ohne Schrägstrich) | Wirkung |
|---|---|
| **`start petworld`** | Skill `start-petworld`: Stand lesen, Repo und Connector prüfen, Lage melden, nächsten Schritt vorschlagen |
| **`ende petworld`** | Skill `ende-petworld`: Wissen aus dem Gespräch ins Repo, Log und TODO pflegen, committen, pushen, Übergabe |

## Technische Basis

- **Theme: Fabric 3.1.0** (Shopify First-Party, block-basiert). Kein Build-Step.
  Reines Liquid, CSS, Vanilla-JS. **Kein React, kein Tailwind, kein npm im Frontend.**
- Branch: `claude/petworld-shopify-brainstorm-9go0du` · Baseline: Commit `cacbd97`
- Personalisierung über **teeinblue** als App-Embed — injiziert sich per JavaScript selbst

```bash
shopify theme dev     # sichere Live-Vorschau, legt ein Dev-Theme an
shopify theme pull --store DEIN-HANDLE.myshopify.com
```

## Regeln — nicht verhandelbar

- **Nie am Live-Theme arbeiten.** `shopify theme push` ohne Flags ist verboten.
  Veröffentlichen entscheidet ausschließlich der Betreiber.
- **Keine Zugangsdaten in den Chat.** Falls nötig: `.env`, steht in `.gitignore`.
- **Vor jedem Löschen auf Referenzen prüfen** — auch über den Shopify-Connector
  (`templateSuffix`), nicht nur im Theme-Code.
- **Navigation immer in beiden Quellen prüfen**: Shopify-Menüs *und*
  `sections/footer-group.json` / `header-group.json`. Fabric verlinkt die
  Fußzeilen-Seiten über feste `button`-Blöcke, nicht über ein Menü.
- **Nach jeder Änderung an der Produktseite prüfen, ob teeinblue noch erscheint.**

## Grundhaltung: proaktiv arbeiten

**Die wichtigste Erwartung in diesem Projekt.** Der Betreiber soll nicht danach fragen müssen.

- **Annahmen offenlegen, nicht stillschweigend treffen.** Was geprüft wurde und was
  nicht, gehört in die Aussage. „Ich habe X geprüft, Y nicht" statt einer Behauptung,
  die nach Gewissheit klingt. **Alle sieben bisherigen Fehler kamen so zustande.**
- **Vollständig durchgehen, nicht bei einem Fund aufhören.** Wer ein kontrastschwaches
  Farbschema findet, rechnet alle durch. Erst die ganze Klasse prüfen, Nebenwirkungen
  mitdenken, dann als vollständige Liste melden.
- **Erfolgskriterium vorher benennen.** Woran ist erkennbar, dass die Aufgabe erledigt
  ist? Ohne prüfbares Kriterium nicht anfangen.
- **Einfachste Lösung, nichts auf Vorrat.** Keine Blöcke, Sections oder Abstraktionen
  für Fälle, die niemand verlangt hat.
- **Nur ändern, was gefordert ist.** Bestehenden Stil beibehalten, nichts nebenbei
  umbauen. *Ausnahme für dieses Projekt:* Das Entfernen toter App-Reste ist ausdrücklich
  beauftragt — aber nur nach nachgewiesener Referenzfreiheit und Freigabe.
- **Auffälligkeiten sofort melden** — Sicherheitsrisiken, Datenverlust, Widersprüche,
  Dinge die später teuer werden.
- **Mitdenken statt abarbeiten.** Bessere Lösung nennen, die verlangte trotzdem liefern.
- **Widersprechen, wenn etwas nicht stimmt.** Einmal sagen, begründen, dann der
  Entscheidung folgen.
- **Gegenprüfen statt erinnern.** Vor jeder Behauptung über den Shop: Connector oder Repo.
- **Ehrlich berichten.** Ungeprüftes nicht als geprüft darstellen. Fehlgeschlagenes benennen.
- **Selbst dokumentieren, selbst committen** — ohne Aufforderung.

Jeder gefundene Shop-Fehler → `docs/bugs.md`. Jede eigene Fehleinschätzung → `K…`-Eintrag
in `docs/entscheidungen.md`, **mit der Lehre daraus**. Bisher sieben, alle lesenswert.

## Architektur-Entscheidungen

Begründungen in `docs/entscheidungen.md` (E1–E15).

1. **Liquid bleibt, kein Headless.** Hydrogen würde teeinblue zerstören.
2. **Motion One statt Framer Motion.** Framer Motion ist React-only.
3. **Dreischichtige Design-Tokens** (primitive → semantic → component), angebunden an
   `settings_schema.json`.
4. **Bausteine nativ bauen, nicht über Apps.** Überlebt Deinstallationen.
5. **Design-Entscheidungen zuerst als HTML-Prototyp**, erst nach Freigabe in Liquid.

## Wo was steht

| Frage | Dokument |
|---|---|
| Wo liegt im Theme was? | `docs/theme-landkarte.md` — **vor jeder Theme-Änderung** |
| Welche Fehler sind bekannt? | `docs/bugs.md` |
| Was ist entschieden, was korrigiert? | `docs/entscheidungen.md` |
| Was steht an, wer macht es? | `docs/todo.md` |
| Was fehlt noch? | `docs/offene-fragen.md` |
| Zahlen, Kosten, Versand, Werbung | `docs/zahlen.md` |
| Gestaltung und Fabric-Eigenheiten | `.claude/skills/petworld-design/SKILL.md` |
| Einstieg und Gesamtstand | `docs/README.md` |

**Zwei Themen mit Betreiber-Entscheidung „vorerst so lassen":** erfundene Bewertungen
(E11) und die Markennamen DOGUE, FURBES & Co (E12, `docs/markennamen.md`). Nicht erneut
aufrollen, außer die Produktseiten werden ohnehin überarbeitet.
