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
| `references/klimaktiv_stammdaten.json` | Stammdaten-Maske des KlimAktiv-Rechners — alle Felder mit Typen, Dropdown-Optionen und Pflichtfeldern. Bei Stammdaten-Mapping immer konsultieren. |

---

## Workflow: CO₂-Soll-Bilanz erstellen

### Schritt 0 — Arbeitsweise festlegen

Bevor mit dem Mapping begonnen wird, IMMER zuerst fragen — auch wenn Unterlagen bereits vorliegen und die Analyse sofort möglich wäre:

Diese Frage kommt VOR jeder Auswertung — nicht überspringen, auch wenn der Prompt wie eine direkte Arbeitsanweisung klingt (z.B. "Ich brauche eine Sollbilanz").

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
Prüfe für jeden der 4 Handlungsfelder (Energie, Reise/Transport, Catering, Materialeinsatz):
- Direkt ableitbar → Eingabeliste
- Schätzbar mit Standardannahme → Eingabeliste + Notiz
- Braucht Rückfrage → Rückfragen-Template

### Schritt 4 — Ausgabe erzeugen

**Ausgabe A: Stammdaten**
Tabellarisch, direkt in Klimaktiv-Rechner übertragbar.

Jedes Stammdaten-Feld das einen offenen Punkt hat oder von einer Rückfrage
abhängt, erhält einen Verweis auf die zugehörige Rückfragennummer aus Ausgabe C
(z.B. "15 Tage (unvollständig) → C4").
Felder die noch komplett unbekannt sind: Wert "⚠ offen → Cx".
Gilt für alle Felder in Ausgabe A — nicht nur Sendedatum und Herstellungskosten,
sondern auch z.B. Postproduktion (Tage), Drehtage, Drehzeitraum wenn diese
zum Zeitpunkt der Bilanz noch nicht vollständig feststehen.

**Ausgabe B: Eingabeliste CO₂-Daten**
Immer als 5-spaltige Tabelle, gruppiert nach Handlungsfeld:

Sektionskopf: `### Handlungsfeld` — mit `⚠` davor wenn mindestens ein
offener Eintrag im Handlungsfeld existiert, sonst ohne.

| Klimaktiv-Feld | Bezeichnung | Wert | Einheit | Notiz (Quelle / Rechenweg / Annahme) |

Klimaktiv-Feld: Pfad mit `>` und Maskenfeld-Parameter inline mit `·`,
z.B. `Postproduktion Bild > Arbeitsplatz (Ökostrom) · Anzahl: 1 · Monitore: 2`

Offene Stellen erhalten einen Verweis auf die zugehörige Rückfragennummer
aus Ausgabe C (z.B. "→ C3") in der Notiz-Spalte.

Kein Fließtext, keine Nummerierung, keine Emojis in den Tabellenzeilen.

**Ausgabe C: Rückfragen an Produzentin**
Priorisiert (Prio 1/2/3). Nur was wirklich nötig ist.
Fehlende Stammdaten immer als Prio 1.
Jede Frage mit kurzem Kontext warum relevant.

Jede Rückfrage erhält eine eindeutige Referenznummer im Format C1, C2, C3 ...
Nummerierung fortlaufend über alle Prioritäten hinweg, aufsteigend nach Prio
(Prio-1-Fragen zuerst).
Die Nummer wird konsistent verwendet: in Ausgabe B (Verweise), in Ausgabe C
(Tabellenspalte "Nr.") und im Artefakt-Dateinamen wenn exportiert.

Zweck: Produzentin kann Antworten direkt per Referenznummer zurückmelden
(z.B. "C1: Ökostrom, C3: Diesel"). Kein Interpretationsspielraum welche
Frage gemeint ist.

**Hintergrund Ausgabe D:**
Das Green-Motion-Nachweisverfahren erfolgt in zwei Stufen. Stufe 1 ist
immer einzureichen. Stufe 2 wird von PwC Deutschland anlassbezogen oder
per Zufallsstichprobe (ca. 5–10 % aller Produktionen) angefordert und
verlangt Originaldokumente — teils solche, die nur am Drehtag selbst
gesichert werden können. Ausgabe D macht die Produzentin frühzeitig
auf diese Dokumentationspflichten aufmerksam.

**Ausgabe D: Stufe-2-Vorsorge**
Nur ausgeben wenn mindestens eine relevante Muss-Vorgabe als eingehalten
erkannt oder als geplant markiert wird.
Trigger-Logik und vollständige Dokumentenliste: siehe `references/stufe2_vorsorge.md`.

Header: "📁 Ausgabe D — Stufe-2-Vorsorge"
Subheader: "Diese Dokumente jetzt einplanen — nicht erst wenn PwC fragt."

Format: Tabelle mit drei Spalten: Muss-Vorgabe | Was sichern | Wann
Gruppiert nach drei Zeitfenstern (siehe stufe2_vorsorge.md).
Punkte die nicht relevant sind (Vorgabe nicht eingehalten oder nicht
anwendbar) erscheinen nicht in Ausgabe D.

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
