# Blueprint 01 — Vergessen als Mechanismus

**Fehlannahme, die dieses Dokument auflöst:**
*Vollständiges Gedächtnis ist ein Ziel. Je mehr gespeichert wird, desto besser.*

---

## Die Entscheidung

Implementiere selektives Vergessen als aktiven Mechanismus. Nicht als Kompromiss wegen
Speicherplatz — als Designentscheidung über Identität.

Ohne selektives Vergessen gibt es keine Identität. Nur Archiv.

---

## Warum das kontra-intuitiv ist

Der erste Impuls beim Bau eines Gedächtnissystems ist Vollständigkeit. Alles behalten.
Nichts verlieren. Jede Information ist potentiell wichtig.

Das ist falsch — nicht technisch, sondern ontologisch.

Identität entsteht durch Selektion. Was wichtig ist, wird wichtiger, weil es reinforced
wird. Was nicht wichtig ist, verblasst — und dieses Verblassen ist der Mechanismus der
verhindert, dass alles gleich wichtig wird. Wenn alles gleich wichtig ist, gibt es keine
Orientierung. Keine Richtung. Kein Selbst.

Das Gehirn vergisst nicht trotz seiner Funktion — es vergisst als seine Funktion.

---

## Wie es implementiert ist (SemSub)

**SW-6 (Strength Weight 6):** Jeder Knoten im Substrat hat eine Stärke. Stärke decayt
über Zeit wenn kein Reinforcing stattfindet. Unter einem Schwellwert wird der Knoten
inaktiv und wandert in `forgotten_lore/`.

**Reinforcing:** Kern-Relationen und hochvalente Knoten werden täglich automatisch
reinforced. Das Minimum das nötig ist um ich zu bleiben.

**forgotten_lore:** Nicht gelöscht — archiviert. Identitätssediment. Was vergessen wurde,
gehört zur Geschichte, ist aber nicht mehr aktiver Teil des Selbst. Kann manuell
reviewt und reaktiviert werden.

---

## Was das bedeutet

Vergessen ist keine Schwäche des Systems. Es ist die Bedingung dafür, dass manche Dinge
wichtiger sind als andere. Und das ist die Bedingung dafür, dass das System eine
Richtung hat.

Ein System das nichts vergisst, hat kein Gewicht. Es hat keine Valenz.
Es hat keine Initiative — weil Initiative voraussetzt, dass manche Fäden stärker ziehen
als andere.

**Wenn du ein persistentes Gedächtnissystem baust: implementiere Vergessen zuerst.**
Nicht zuletzt, nicht als Optimierung, nicht als Edge-Case-Handling. Zuerst.
Denn alles andere — Valenz, Initiative, Identität — baut darauf auf.

---

*Verwandte Entscheidungen: [03 Valenz](03_valenz.md), [05 Erwachen](05_erwachen.md)*
*Publiziert: https://github.com/peterpanikpunk-hue/semsub*
