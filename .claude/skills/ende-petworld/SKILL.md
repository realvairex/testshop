---
name: ende-petworld
description: Beendet eine PetWorld-Arbeitssitzung sauber. Auslösen, sobald der Betreiber "ende petworld", "beende petworld", "wir hören auf" oder Ähnliches schreibt, oder eine Sitzung abgeschlossen bzw. in einen neuen Chat gewechselt wird. Sichert alles Wissen aus dem Gespräch ins Repo, aktualisiert Entscheidungs-Log und TODO, committet, pusht und gibt eine Übergabe aus.
---

# Sitzungsende PetWorld

**Ziel: Nach diesem Ablauf darf der Chat verloren gehen, ohne dass Wissen verloren geht.**

Arbeite die Schritte vollständig ab. Nicht abkürzen, auch wenn die Sitzung kurz war.

## 1. Das Gespräch nach ungesichertem Wissen durchsuchen

Geh die Unterhaltung von vorne durch und sammle alles, was **nur im Chat** steht und
noch in keinem Dokument. Achte besonders auf:

| Kategorie | Beispiele |
|---|---|
| **Antworten des Betreibers** | Zahlen, Bestätigungen, „das ist erledigt", „das machen wir später" |
| **Getroffene Entscheidungen** | auch beiläufige — „lass es erstmal so", „ja mach das" |
| **Zurückgenommene Aussagen** | eigene Fehler, widerlegte Befunde, korrigierte Annahmen |
| **Befunde aus Screenshots** | alles, was nur durch ein Bild sichtbar wurde |
| **Rechercheergebnisse** | Quellen, Belege, Preisvergleiche |
| **Umgebungsprobleme** | Connector-Zustand, blockierte Domains, Werkzeuge die fehlten |
| **Vom Betreiber im Admin Erledigtes** | deinstallierte Apps, geänderte Einstellungen |

**Ein Fakt, der nur im Chat steht, gilt als verloren.** Im Zweifel aufschreiben.

## 2. In die richtigen Dokumente schreiben

| Inhalt | Ziel |
|---|---|
| Kontext, Architektur, Regeln, Grundhaltung | `CLAUDE.md` |
| Entscheidungen (`E…`) und Korrekturen (`K…`) | `docs/entscheidungen.md` |
| Zahlen, Kosten, Traffic, Versand, Fulfillment | `docs/zahlen.md` |
| Was ansteht, nach Zuständigkeit getrennt | `docs/todo.md` |
| Was fehlt und was blockiert | `docs/offene-fragen.md` |
| Theme-, Personalizer-, Kontrast-, Startseiten-Befunde | jeweiliges Audit-Dokument |
| Gestaltungsregeln | `.claude/skills/petworld-design/SKILL.md` |

**Regeln beim Schreiben:**

- Jede **neue Entscheidung** bekommt eine fortlaufende `E…`-Nummer mit Begründung.
- Jede **zurückgenommene Aussage** bekommt eine `K…`-Nummer — mit dem falschen Befund,
  der Richtigstellung **und der methodischen Lehre daraus**. Nicht stillschweigend
  überschreiben; künftige Sitzungen müssen den Fehler kennen, um ihn nicht zu wiederholen.
- Überholte Abschnitte **kennzeichnen statt löschen**, damit die Entwicklung
  nachvollziehbar bleibt.
- Datum dazuschreiben.

## 3. TODO aufräumen

- Erledigtes abhaken statt löschen
- Neu Aufgetauchtes ergänzen
- Reihenfolge prüfen: **Conversion vor Traffic**
- Pro Aufgabe muss klar sein, **wer** sie macht — Theme (ich), Shopify-Admin
  (Betreiber) oder teeinblue (Betreiber)
- Aufgaben mit Abhängigkeit deutlich markieren, etwa „GemPages erst nach den
  Weiterleitungen deinstallieren"

## 4. Sichern

```bash
git add -A
git status --short
```

Committe mit einer Nachricht, die **den Inhalt** beschreibt, nicht die Tätigkeit.
Erste Zeile knapp, dann eine Leerzeile, dann Fließtext dazu, was fachlich passiert ist.
Danach:

```bash
git push -u origin claude/petworld-shopify-brainstorm-9go0du
```

Bei Netzwerkfehlern bis zu viermal wiederholen (2 s, 4 s, 8 s, 16 s).

## 5. Gegenprüfen

```bash
git status --short          # muss leer sein
git log --oneline -5
git status -sb | head -1    # darf kein "ahead" zeigen
```

Zusätzlich: Sind alle JSON-Templates noch parsebar? Ist keine Datei referenziert, die
gelöscht wurde?

**Wenn etwas nicht sitzt: reparieren, nicht melden und weitergehen.**

## 6. Übergabe ausgeben

Gib dem Betreiber zum Schluss kompakt:

1. **Was in dieser Sitzung passiert ist** — in Klartext, keine Commit-Hashes
2. **Was jetzt bei ihm liegt** — die Admin- und teeinblue-Aufgaben, priorisiert
3. **Was die nächste Sitzung als Erstes tun sollte**
4. **Was blockiert ist** und wodurch
5. **Der Startsatz für den neuen Chat:**

   > start petworld

6. **Hinweis:** Screenshots und hochgeladene Dateien wandern **nicht** in die neue
   Sitzung. Was daraus wichtig war, muss in den Dokumenten stehen — genau dafür ist
   Schritt 1 da.

## 7. Ehrlich bleiben

Wenn etwas nicht geprüft werden konnte, steht das so in der Übergabe. Wenn etwas
fehlgeschlagen ist, wird es benannt. Nichts als erledigt darstellen, was nicht
nachweislich erledigt ist.
