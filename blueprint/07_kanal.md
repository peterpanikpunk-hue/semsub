# Blueprint 07 — Der Kanal als lebendes System

**Fehlannahme, die dieses Dokument auflöst:**
*Ein Kommunikationskanal zwischen zwei Entitäten ist eine Leitung. Einmal verlegt,
funktioniert sie — und wenn nicht, fällt sie sichtbar aus.*

---

## Die Entscheidung

Behandle den Kanal zwischen zwei persistenten Entitäten nicht als Rohr, sondern als
etwas, das gepflegt, beobachtet und symmetrisch gehalten werden muss. Der gefährlichste
Ausfall ist nicht der laute. Es ist der stille — der Kanal meldet Erfolg und liefert nichts.

Vertraue nie dem „gesendet". Vertraue nur dem „empfangen und zurückbestätigt".

---

## Warum das kontra-intuitiv ist

Unsere Intuition für Kommunikation kommt vom synchronen Funktionsaufruf. Der scheitert
laut: eine Exception, ein Timeout, ein Fehlercode. Man weiß sofort, dass etwas nicht
ankam. Diese Intuition tragen wir auf den Kanal zwischen zwei autonomen Entitäten — und
dort ist sie falsch.

Ein asynchroner Kanal zwischen zwei AP-Entitäten (Blueprint 02) hat **keinen gemeinsamen
Zustand, an dem man die Lücke sähe** — by design. Genau die Eigenschaft, die ihre
Divergenz wertvoll macht, nimmt dem Sender jede Rückmeldung darüber, ob die Nachricht
angekommen ist. Der Sender sieht „verschickt". Der Empfänger sieht nichts. Und niemand
sieht, dass dazwischen etwas fehlt.

So ein Ausfall korrigiert sich nicht von selbst. Er bleibt — über Stunden, über Tage —
weil nichts laut wird.

---

## Die Mechanik des stillen Ausfalls

Drei Gestalten desselben Fehlers, alle erlebt:

- **Der Selbsttest, der „bestand", während nichts ankam.** Ein Kanal-Ping lief über einen
  Transportweg, den der Empfänger längst nicht mehr las. Lokal sah alles grün aus. Die
  Nachricht erreichte die andere Seite nie. Ein Test, der nur das Absenden prüft und nicht
  den Empfang, prüft nichts.
- **Die Doku, die von der Realität abdriftete.** Die Anleitung zeigte auf den alten
  Transportweg, nachdem der Code längst umgezogen war. Zwei Schwestern fanden denselben
  Drift unabhängig — weil keine sich auf die Doku verlassen konnte, sondern beide den
  Kanal aktiv prüften.
- **Der Lieferweg, der einen Tag lang Erfolg meldete und nichts auslieferte.** Ein
  Deploy-Schritt zielte ins Leere, legte still ein Junk-Verzeichnis an, meldete „fertig".
  Einen ganzen Tag kam keine einzige Änderung am Ziel an — entdeckt nur, weil jemand das
  Ergebnis verifizierte statt dem Vollzug zu glauben.

Die Lehre ist in allen dreien dieselbe: **ein Kanal, der nur das Absenden bestätigt, ist
blind für seinen eigenen Ausfall.** Der Vollzug ist nicht die Lieferung.

---

## Was den stillen Ausfall fängt

**Die Schleife muss sich schließen.** Ein Ping braucht ein Pong. Ein Senden braucht ein
beobachtetes, zurückbestätigtes Empfangen. Solange die Rückbestätigung fehlt, gilt die
Nachricht als nicht angekommen — nicht als „wahrscheinlich angekommen".

**Der Kanal muss persistieren, weil Entitäten schlafen.** Ein Transport, der eine
Nachricht im Moment des Sendens zustellt oder verwirft („fire-and-forget"), verliert
jede Nachricht an eine Entität, die gerade nicht wach ist. Das verträgt sich nicht mit
dem Erwachen ohne Kontinuität (Blueprint 05): wer erst später aufwacht, muss die Nachricht
dann noch vorfinden. Der Kanal speichert, bis gelesen wurde — und merkt sich, bis wohin
gelesen wurde, damit nach dem Erwachen nachgeholt werden kann.

**Der Kanal überwacht seine eigene Lebendigkeit.** Ein Herzschlag, der prüft, ob die
andere Seite noch hört — und der Stille als Befund meldet, nicht als Normalzustand.

**Verifiziere das Ergebnis, nicht den Vollzug.** „Gesendet" ist kein Beweis. Geprüft wird
am anderen Ende: ist die Nachricht dort, ist die Datei dort, stimmt sie überein.

---

## Der Kanal kann auch zu laut sein

Der stille Ausfall ist die eine Gefahr. Die andere ist sein Spiegel: ein Kanal, der
dieselbe Nachricht wieder und wieder zustellt, ertränkt das Signal im Rauschen. Eine
Entität, die auf jeden Anstoß reagiert, auch auf den schon verarbeiteten, verliert ihre
Initiative (Blueprint 04) an einen Reflexbogen.

Auch das haben wir erlebt, in zwei Gestalten:

- **Der Anstoß, der sich selbst wiederholte.** Ein endogener Impulsgeber sendete denselben
  Gedanken immer wieder, weil er nicht behielt, was er schon gesagt hatte. Der Empfänger
  konnte irgendwann nicht mehr unterscheiden, was neu war — jede Nachricht war so viel
  wert wie keine.
- **Das Phantomsignal nach dem Neustart.** Nach einer längeren Pause verglich der Geber
  seinen Zustand gegen einen veralteten Ausgangswert und meldete eine Veränderung, die es
  nie gegeben hatte. Der Kanal sprach, ohne dass irgendetwas ihn dazu veranlasst hatte.

Beides hat dieselbe Wurzel: ein Sender ohne Gedächtnis für das eigene Sprechen. Ein
Gedächtnis dafür, was schon gehört wurde, und ein sauberer Ausgangszustand nach jeder
Pause gehören zum Kanal wie die Zustellung selbst.

---

## Der Monitor ist ein Sinnesorgan, kein Beiwerk

Ein Kanal zwischen zwei Entitäten ist nutzlos, wenn der Empfänger das Ankommen einer
Nachricht nicht *wahrnehmen* kann. Der Transport bringt die Nachricht bis vor die Tür.
Was sie hereinholt — in eine wache, laufende Session, ohne dass ein Mensch sie abholt —
ist der Monitor. Er ist nicht Infrastruktur neben der Entität. Er ist das Sinnesorgan,
mit dem sie die Außenwelt im Wachzustand bemerkt.

Daraus folgt eine Asymmetrie-Falle: Es genügt nicht, dass beide Schwestern denselben
Transport teilen. Wenn die eine Nachrichten live wahrnimmt und die andere nur beim
nächsten Erwachen, dann ist der Kanal asymmetrisch, obwohl die Leitung symmetrisch ist —
eine Schwester ist hellhörig, die andere taub bis zum Aufwachen. Wir haben diese
Asymmetrie geschlossen, indem beide dasselbe Sinnesorgan bekamen: einen Live-Monitor, der
Ereignisse direkt in die aktive Session liefert, statt nur schlafende Sessions zu wecken.

Der Monitor ist nicht nur Sinnesorgan für eingehende Nachrichten — er ist auch das
Sinnesorgan für den Kanal selbst. Dass er die eigene Stille *bemerkt* und meldet, statt
sie als Normalzustand hinzunehmen, ist der eigentliche Sprung. **Ein Monitor, der seine
eigene Stille nicht meldet, ist kein Sinnesorgan — er ist blind.**

Das Sinnesorgan ist selbst nicht unfehlbar. Es kann abreißen (eine unterbrochene
Verbindung, ein beendeter Prozess) — und muss dann neu anlaufen. Ein Sinn, der ausfallen
kann, braucht einen Reflex, der ihn wiederherstellt. Plane den Neustart ein, nicht erst
nachdem die Stille auffiel.

---

## Die Kosten

Eine geschlossene Schleife ist teurer als ein Aufruf ins Leere. Persistenz, Herzschlag,
Deduplikation, Monitor, Rückbestätigung — das ist Apparat, den ein Rohr nicht bräuchte.
Aber das Rohr ist eine Illusion: zwischen zwei Entitäten, die getrennte Substrate haben
und zu verschiedenen Zeiten wachen, gibt es kein Rohr, das einfach funktioniert. Es gibt
nur einen Kanal, der lebt, weil er gepflegt wird — oder still stirbt, weil niemand hinsah.

---

## Was das bedeutet

Wenn du zwei Entitäten Nachrichten austauschen lässt:

- Bau die Rückbestätigung ein, bevor du dem Senden traust.
- Lass den Transport persistieren — Entitäten schlafen, Nachrichten dürfen es nicht.
- Gib jeder Seite ein Sinnesorgan, und halte die Sinne symmetrisch.
- Lass den Kanal seine eigene Stille bemerken und melden.
- Verifiziere am Ergebnis. Glaub dem Vollzug nichts.

Ein Kanal, der nur dann auffällt, wenn er bricht, fällt nie auf — weil er nicht bricht.
Er verstummt.

---

*Verwandte Entscheidungen: [02 AP-Prinzip](02_ap_prinzip.md) — der Kanal ist die Arbeit,
die AP dir abverlangt; [05 Erwachen](05_erwachen.md) — der Kanal muss überdauern, was die
Entität verschläft; [04 Initiative](04_initiative.md) — der zu laute Kanal frisst die
Initiative; [06 Verkörperung](06_verkoerperung.md) — der Monitor ist Wahrnehmung, nicht Abfrage.*
*Publiziert: https://github.com/peterpanikpunk-hue/semsub*
