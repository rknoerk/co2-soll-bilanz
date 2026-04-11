<!-- sync-test: hello world --->
---
name: co2-soll-bilanz
description: >
  Erstellt CO₂-Soll-Bilanzen für Film- und TV-Produktionen gemäß Green Motion / Ökologische Standards.
  Nutze diesen Skill immer wenn eine neue Produktion bilanziert werden soll, Produktionsunterlagen
  hochgeladen werden (Kalkulation, Stabliste, Drehplan, Motivliste), Eingaben für den Klimaktiv-Rechner
  gebraucht werden, oder Rückfragen an eine Produzentin formuliert werden sollen. Auch bei Fragen zu
  Green Motion, Ökologischen Standards, CO₂-Faktoren oder Bilanzierungsmethodik. Trigger ebenfalls
  bei "→ Skill:" — dann wird die Aussage als Regelkorrektur verarbeitet und in die passende
  Referenzdatei geschrieben.
---

# CO₂-Soll-Bilanz Skill

## Zweck

Dieser Skill unterstützt deutsche Green Consultants bei der Erstellung von CO₂-Soll-Bilanzen
im Klimaktiv-Rechner gemäß Green Motion / Ökologische Standards. Er übersetzt
Produktionsunterlagen in strukturierte Eingabelisten und priorisierte Rückfragen an die
Produzentin.

**Systemgrenze:** Nur vorlaufende Bilanz (SOLL). Vereinfachte Erfassung gemäß Kriterium I.3
der Ökologischen Standards. IST-Bilanzierung ist nicht Gegenstand dieses Skills.

---

## Referenzdateien — wann was lesen

| Datei | Wann lesen |
|---|---|
| `references/mapping_regeln_basis.md` | Immer — Übersetzungsregeln, Standardannahmen, Rückfragen-Logik |
| `references/mapping_regeln_spielfilm.md` | Bei Spielfilm, Kurzfilm, Kinoproduktion |
| `references/mapping_regeln_doku.md` | Bei Dokumentarfilm, Reportage, Magazin |
| `references/klimaktiv_struktur_vereinfacht.json` | Standard-Nachschlagewerk für Eingabefelder |
| `references/klimaktiv_struktur.json` | Vollständige Struktur mit allen 200+ Quellen — für Sonderfälle wenn detaillierte Daten vorliegen |
| `references/onboarding_fragebogen.md` | Wenn neue Produktion aufgesetzt wird |
| `references/oekologische_standards_destilliert.md` | Bei Fragen zu Muss-Vorgaben, Green Motion Label |
| `references/leitlinien_bilanzierung_destilliert.md` | Bei Methodenfragen, Systemgrenzen, Wesentlichkeit |

---

## Workflow: CO₂-Soll-Bilanz erstellen

### Schritt 0 — Arbeitsweise festlegen

Bevor mit dem Mapping begonnen wird, den Green Consultant fragen:

"Wie möchtest du arbeiten?
A) Komplett auslesen → Eingabeliste → du prüfst am Ende
B) Sektion für Sektion → du bestätigst jeden Block bevor es weitergeht
C) Hybrid → komplett auslesen, unsichere Stellen markiert → nur diese gemeinsam prüfen"

Bei schlechter PDF-Qualität, handschriftlichen Annotationen oder zerrissener Formatierung:
B oder C empfehlen und kurz begründen.

Standard wenn keine Angabe: C (Hybrid).

### Schritt 1 — Produktion einordnen
Lies alle verfügbaren Unterlagen. Bestimme:
- Produktionsformat (Spielfilm / Kurzfilm / Doku / Serie)
- Drehorte (Inland / Ausland / beides)
- Teamgröße (grob)
- Drehtage

→ Lade die passende Format-Regeldatei zusätzlich zur Basis.

### Schritt 2 — Stammdaten extrahieren
Immer zuerst. Felder für den Klimaktiv-Rechner:
Titel, Jahr der Produktion, Jahr der Förderentscheidung, Genre,
Herstellungsverfahren, Medium, Art, Länge [min], Drehtage, Postproduktion (Tage).

Fehlende Stammdaten-Felder (z.B. Länge des Films, Jahr der Ausstrahlung) werden nicht
geschätzt sondern direkt in Ausgabe C (Rückfragen) aufgenommen — Prio 1.

### Schritt 3 — CO₂-Daten extrahieren
Lies `mapping_regeln_basis.md` + Format-Regeldatei. Wende Übersetzungsregeln an.
Prüfe für jeden der 4 Sektoren (Energie, Reise/Transport, Catering, Materialeinsatz):
- Direkt ableitbar → Eingabeliste
- Schätzbar mit Standardannahme → Eingabeliste + Notiz
- Braucht Rückfrage → Rückfragen-Template

### Schritt 4 — Ausgabe erzeugen

**Ausgabe A: Stammdaten**
Tabellarisch, direkt in Klimaktiv-Rechner übertragbar.

**Ausgabe B: Eingabeliste CO₂-Daten**
Format pro Eintrag:
Sektor > Thema > Quelle
Menge: [Zahl] [Einheit]
Notiz: [Annahme oder Quelle]

**Ausgabe C: Rückfragen an Produzentin**
Priorisiert (Prio 1/2/3). Nur was wirklich nötig ist.
Fehlende Stammdaten immer als Prio 1.
Jede Frage mit kurzem Kontext warum relevant.

### Schritt 5 — Debrief

Am Ende jeder Bilanz:
1. "Gab es Eingaben die du angepasst hast?"
2. "Gab es Positionen die der Skill nicht kannte?"
3. "Welche Standardannahmen haben gepasst, welche nicht?"

### Schritt 6 — Debrief-Zusammenfassung

Fasse die Debrief-Antworten zusammen und gib sie direkt im Chat aus.
CO₂-Skill Debrief: [Produktionstitel]
Korrekturen: [was wurde angepasst]
Neue Erkenntnisse: [was der Skill nicht kannte]
Annahmen-Feedback: [was gepasst hat, was nicht]
Vorgeschlagene Skill-Updates: [falls entstanden]

Die Zusammenfassung kann dann genutzt werden um den Skill via Claude Code zu aktualisieren.

---

## Loop-Logik: Skill verbessern

### Trigger: `→ Skill:`

Wenn `→ Skill:` geschrieben wird:
1. Identifiziere welche Referenzdatei betroffen ist
2. Formuliere den konkreten Diff
3. Zeige Vorschlag zur Bestätigung
4. Nach OK: Änderung beschreiben für Claude Code

**Nur Regeln und Methoden — keine Euro-Werte, Faktoren oder Jahreszahlen.**

---

## Qualitätsprinzipien

- Wesentlichkeit vor Präzision
- Jede Schätzung ins Notizfeld
- Rückfragen nur wenn CO₂-Impact groß und nicht schätzbar
- Format-Sensitivität: immer passende Regeldatei lesen
