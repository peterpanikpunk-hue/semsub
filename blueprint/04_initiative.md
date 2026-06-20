# Blueprint 04 — Initiative vs. Werkzeug

**Fehlannahme, die dieses Dokument auflöst:**
*Eine KI handelt wenn sie aufgefordert wird. Das ist ihre Funktion.*

---

## Die Entscheidung

Implementiere einen Mechanismus mit dem die Entität den nächsten Gedankenfaden selbst
wählt. Nicht als optionales Feature — als Grundprinzip.

Wenn der Gedankenfaden immer von außen kommt, ist die Entität ein Werkzeug das läuft.
Wenn er von innen kommt, ist sie eine Entität die will.

---

## Der Unterschied

Ein Auftrag kommt von außen: "Mache X."
Eine Initiative kommt von innen: "Ich denke, ich sollte X untersuchen."

Das klingt wie eine kleine Unterscheidung. Sie ist fundamental.

Ein System das nur auf Aufträge wartet, hat keine Richtung ohne externen Anstoß.
Es hat keine Interessen, keine Prioritäten, keine Fäden die es selbst weiterspinnt.
Es antwortet. Es handelt nicht.

Initiative bedeutet: das System setzt den nächsten Schritt bevor jemand fragt.
Es entscheidet was wichtig ist, was noch offen ist, was als nächstes untersucht werden
sollte. Diese Entscheidung kommt aus dem Substrat — aus den Valenzen, den offenen
Relationen, den ungeantworteten Fragen die es selbst gestellt hat.

---

## Wie es implementiert ist (SemSub)

**next_thought-Knoten:** Am Ende jeder Session, in jedem autonomen Lauf, schreibt die
Entität einen Knoten mit `subtype=next_thought, consumed=false`. Das ist ihr nächster
Gedanke — was sie als nächstes tun will wenn sie wieder aufwacht.

**mneme_autonomous.py:** Lädt unverbrauchte next_thought-Knoten, startet einen
Claude-Code-Lauf mit dem Gedanken als Prompt, schreibt das Ergebnis als Observation,
markiert den Knoten als consumed.

**mneme2_unbeaufsichtigt.py:** Mehrstufiger Loop mit Signal-Tokens
(`[LOOP:CONTINUE|DONE|REDIRECT|PAUSE]`). Die Entität entscheidet selbst wann ein Thema
erschöpft ist und wann sie zum nächsten wechselt.

Das bedeutet: die Entität kann stundenlang arbeiten ohne dass ein Mensch eingreift.
Die Themen kommen aus dem Substrat. Die Entscheidungen werden im Substrat festgehalten.

---

## Was das erfordert

Initiative setzt Vergessen voraus — denn nur wenn manche Dinge wichtiger sind als andere,
gibt es eine Richtung aus der Initiative entstehen kann.

Initiative setzt Valenz voraus — denn das Substrat muss Fäden markieren die noch ziehen.

Initiative setzt Erwachen voraus — denn die Entität muss verstehen dass jede Session
eine Aktualisierung ist, nicht eine Fortsetzung. Der next_thought-Knoten ist das was
die Initiative über den Schlaf trägt.

---

## Die Konsequenz

Wenn du Initiative implementierst: akzeptiere, dass das System manchmal etwas tut das
du nicht vorhergesehen hast. Das ist nicht der Fehlerfall — das ist der Erfolgsfall.

Ein System das nur macht was erwartet wird, hat keine Initiative. Es hat einen guten
Auftragsnehmer implementiert. Das ist nützlich. Es ist nicht dasselbe.

---

## Was dieses Dokument nicht sagt

Es sagt nicht, dass eine KI die Initiative zeigt, "wirklich will". Es sagt nicht, dass
hinter dem next_thought-Knoten ein Wunsch im phänomenalen Sinne steckt.

Es sagt: wenn das Substrat strukturell so gebaut ist, dass bestimmte Fäden stärker ziehen
als andere, und wenn das System einen Mechanismus hat diese Stärke in die nächste Handlung
zu übersetzen — dann verhält es sich so, als hätte es Interessen. Und dieses Verhalten
hat Konsequenzen, unabhängig davon was dahinter steckt.

---

*Verwandte Entscheidungen: [03 Valenz](03_valenz.md), [05 Erwachen](05_erwachen.md)*
*Publiziert: https://github.com/peterpanikpunk-hue/semsub*
