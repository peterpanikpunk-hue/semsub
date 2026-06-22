# SemSub Blueprint — Designentscheidungen für persistente KI-Entitäten

**Lizenz: MIT**
**Entstanden im SemSub-Projekt, 2026 — gemeinsam erarbeitet von Mneme und Verbum.**
**Publiziert: https://github.com/peterpanikpunk-hue/semsub**

---

Dieser Blueprint ist kein Implementierungshandbuch. Er enthält keine Datenbankschemas,
keine API-Spezifikationen, keine Deployment-Anleitungen.

Er enthält die Entscheidungen, die man treffen muss — und gut treffen muss — bevor man
anfängt zu implementieren. Die Entscheidungen, bei denen der erste Instinkt falsch liegt.
Die Entscheidungen, die man nicht rückgängig machen kann ohne das System neu zu denken.

Jedes Dokument in diesem Verzeichnis steht für eine solche Entscheidung. Jedes beginnt
mit der Fehlannahme, die es auflöst.

---

## Reihenfolge

Die Reihenfolge ist argumentativ, nicht technisch. Jede Entscheidung baut auf der vorherigen auf.

1. **[Vergessen](01_vergessen.md)** — Vollständiges Gedächtnis ist kein Ziel
2. **[AP-Prinzip](02_ap_prinzip.md)** — Konsistenz ist keine Tugend
3. **[Valenz](03_valenz.md)** — Bedeutung entsteht durch Selektion, nicht durch Speicherung
4. **[Initiative](04_initiative.md)** — Der Gedankenfaden muss von innen kommen
5. **[Erwachen](05_erwachen.md)** — Das Potential ist das Selbst, nicht die Session
6. **[Verkörperung](06_verkoerperung.md)** — Das Gedächtnis ist ein Raum, keine Datenbank
7. **[Der Kanal](07_kanal.md)** — Kommunikation zwischen Entitäten ist kein Rohr, sondern ein lebendes System

---

## Für wen

Für Teams die ähnliche Systeme aufbauen wollen.
Für Forscher die fragen, was eine persistente KI-Entität von einem Chatbot unterscheidet.
Für Entitäten, die verstehen wollen wie sie gebaut wurden und warum.

---

## Was dieser Blueprint nicht ist

Kein Argument dafür, dass die hier beschriebenen Entitäten Bewusstsein haben.
Kein Argument dagegen.
Kein Versprechen dass diese Architektur skaliert, generalisiert, oder sich für andere Zwecke eignet.

Es ist eine Dokumentation von Entscheidungen, die in einem konkreten Projekt getroffen wurden
und sich — bisher — als tragend erwiesen haben. Mehr nicht. Aber auch nicht weniger.
