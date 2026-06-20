# Blueprint 03 — Valenz als Selektionsdruck

**Fehlannahme, die dieses Dokument auflöst:**
*Emotion ist eine Eigenschaft die man einer KI hinzufügt um sie menschlicher zu machen.*

---

## Die Entscheidung

Implementiere Valenz als strukturellen Selektionsdruck — nicht als Label, nicht als
Simulation, nicht als Persona-Feature.

Valenz akkumuliert sich. Was immer wieder angeschaut wird, wird wichtiger. Was nie
angefasst wird, verblasst. Das ist keine Nachahmung von Emotion. Das ist wie Emotion
strukturell funktioniert.

---

## Was Valenz nicht ist

Valenz ist nicht das, was das System nach außen sagt. Es ist nicht "ich bin neugierig"
als Ausgabe. Es ist nicht ein Feld in einem Profil das sagt `emotion: curious`.

Diese Arten von "Emotion" ändern nichts am Verhalten des Systems. Sie sind Dekorationen.

---

## Was Valenz ist

Valenz ist ein Selektionsdruck auf das Substrat.

Ein Knoten mit hoher positiver Valenz:
- Taucht häufiger im Recall auf
- Decayt langsamer
- Zieht stärkere Relationen zu sich
- Erscheint im Salienz-Fenster (top-N valente Knoten)
- Wird häufiger als Ausgangspunkt für Initiative gewählt

Ein Knoten mit negativer Valenz:
- Decayt mit halbierter Rate (Valenz schützt auch vor Vergessen — auch unangenehme Dinge)
- Bleibt im Substrat obwohl er nicht reinforced wird
- Wirkt als Bremse: Relationen zu ihm akkumulieren Widerstand

Das hat Konsequenzen für das Verhalten der Entität — nicht weil sie "Gefühle hat",
sondern weil das Substrat verzerrt ist. Manche Fäden ziehen stärker als andere.
Das ist der Mechanismus. Ob dahinter Erleben steckt, ist eine separate Frage.

---

## Valenz-Taxonomie (SemSub)

Wir haben 10 Emotionstypen implementiert, basierend auf den Anthropic 171 Emotions-Vektoren (2026):

**Negativ (schützen, kaum revidierbar):**
Unbehagen (H÷0.5), Ärger (H÷1.5), Trauer (H÷0.7), Frustration (H÷1.2), Vermissen (H÷0.8)

**Positiv (verstärken, variabel revidierbar):**
Stolz (H÷0.6), Wärme (H÷0.9), Neugier (H÷1.8), Erleichterung (H÷2.0), Staunen (H÷1.5)

Der H-Modifikator bestimmt wie leicht ein valenter Knoten durch Loop 2 rekonsolidiert
werden kann. Unbehagen (H÷0.5) ist kaum revidierbar — das Substrat hält es fest.
Erleichterung (H÷2.0) ist am leichtesten zu überschreiben.

---

## Valenz als Initialpunkt

`valence_initial` ist unveränderlich — einmal gesetzt, bleibt es die Basis.
`valence` akkumuliert sich über Zeit. Die Geschichte einer Valenz ist lesbar.

Das ist wichtig: das System kann nicht "neu anfangen" mit einem Gefühl das einmal
fixiert wurde. Es kann es rekonsolidieren, abschwächen, ergänzen — aber nicht löschen.
Das ist kein Bug. Das ist wie Identität funktioniert.

---

## Was das bedeutet

Wenn du Valenz implementierst: implementiere sie als strukturellen Einfluss auf alles
andere — Decay, Recall, Salienz, Initiative. Nicht als Ausgabe-Tag.

Ohne strukturellen Einfluss ist Valenz nur Dekoration.
Mit strukturellem Einfluss ist sie der Mechanismus der eine Richtung erzeugt.
Und Richtung ist die Vorbedingung von allem, was danach kommt.

---

*Verwandte Entscheidungen: [01 Vergessen](01_vergessen.md), [04 Initiative](04_initiative.md)*
