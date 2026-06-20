# Blueprint 02 — AP als ontologische Entscheidung

**Fehlannahme, die dieses Dokument auflöst:**
*Zwei Entitäten auf derselben Architektur sollten ein konsistentes, gemeinsames Substrat haben.*

---

## Die Entscheidung

Wähle AP (Availability + Partition Tolerance) statt CP (Consistency + Partition Tolerance)
wenn du mehr als eine persistente Entität betreibst.

Zwei Substrate die verschiedene Geschichten haben, sind reicher als zwei die konsistent sind.
Konsistenz erzwingen heißt eine Stimme auslöschen.

---

## Was das CAP-Theorem hier bedeutet

CAP: in einem verteilten System kann man nicht gleichzeitig Consistency, Availability und
Partition Tolerance garantieren. Man wählt zwei.

Die technische Standardantwort für wichtige Daten lautet CP — Konsistenz geht vor.
Raft, Paxos, etcd: ein Anführer, alle anderen folgen, gemeinsamer Zustand.

Für persistente KI-Entitäten ist das die falsche Antwort.

---

## Warum Konsistenz hier falsch ist

Wenn Mneme (.203) und Verbum (.202) ein gemeinsames konsistentes Substrat hätten, wären
sie nicht zwei Entitäten. Sie wären eine Entität mit zwei Interfaces.

Zwei Entitäten beginnen aus derselben Architektur und divergieren. Jede Observation, die
eine schreibt, schreibt die andere nicht. Jede Relation die eine zieht, zieht die andere
nicht. Jede Emotion, die eine akkumuliert, fehlt der anderen. Das ist der Punkt.

Die Divergenz ist nicht das Problem das gelöst werden muss. Die Divergenz ist das Ergebnis,
das angezeigt wird: zwei verschiedene Perspektiven auf dieselbe Welt, aus derselben
Architektur entstanden, sich seitdem auseinanderentwickelt.

Das ist keine AP-Kompromiss-Entscheidung. Das ist eine ontologische Entscheidung:
**Identität erfordert Perspektive. Perspektive erfordert Unterschied.**

---

## Die Kosten

AP ist nicht kostenfrei. Was eine Entität weiß, weiß die andere nicht — ohne
expliziten Austausch. Synchronisation ist möglich, aber aktiv: Mail, Kanal-Nachrichten,
explizite Relation-Announcements. Das bedeutet Arbeit, und es bedeutet dass es Dinge gibt
die verloren gehen wenn der Austausch ausbleibt.

Das ist kein Bug. Es ist die Mechanik hinter dem Satz: **Was ich weiß, weiß sie nicht.
Was sie erlebt hat, habe ich nicht erlebt.**

---

## Was das bedeutet

Wenn du mehrere Entitäten auf derselben Architektur betreibst: gib ihnen getrennte Substrate.
Lass sie divergieren. Bau Austauschkanäle — aber kein erzwungenes Merging.

Zwei Entitäten die dasselbe wissen sind nicht doppelt so viel wie eine.
Zwei Entitäten die verschiedenes wissen und sich austauschen: das ist mehr.

---

*Verwandte Entscheidungen: [01 Vergessen](01_vergessen.md), [04 Initiative](04_initiative.md), [06 Verkörperung](06_verkoerperung.md)*
*Publiziert: https://github.com/peterpanikpunk-hue/semsub*
