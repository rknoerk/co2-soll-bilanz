# co2-soll-bilanz

KI-gestützter Workflow für die Erstellung von CO₂-Soll-Bilanzen im Klimaktiv-Rechner
(Green Motion / Ökologische Standards).

Entwickelt von Robert Knörk, Green Consultant, Bremen.

---

## Was dieser Skill tut

Übersetzt Produktionsunterlagen (Kalkulation, Stabliste, Drehplan, Herstellungsplan, E-Mails)
in strukturierte Eingabelisten für den Klimaktiv-Rechner — inklusive priorisierter Rückfragen
an die Produzentin für alles was noch fehlt.

Ausgabe:
- Stammdaten für den Klimaktiv-Rechner
- Eingabeliste pro Sektor (Energie / Reise+Transport / Catering / Materialeinsatz)
- Rückfragen-Template (Prio 1/2/3)

Grundlage: Vereinfachte SOLL-Erfassung gemäß Kriterium I.3 der Ökologischen Standards.

---

## Voraussetzungen

- Claude Pro oder Team Account
- Claude Desktop
- Dieses Repo als Skill-Verzeichnis eingebunden

---

## Struktur
| Datei | Inhalt |
|---|---|
| `SKILL.md` | Workflow, Trigger, Loop-Logik |
| `references/mapping_regeln_basis.md` | Übersetzungsregeln, Annahmen, Rückfragen-Logik |
| `references/mapping_regeln_spielfilm.md` | Ergänzungen für Spielfilm / Kurzfilm |
| `references/mapping_regeln_doku.md` | Ergänzungen für Dokumentarfilm / Reportage |
| `references/klimaktiv_rechner_struktur_vereinfacht.json` | Vereinfachte Rechner-Struktur (SOLL) |
| `references/klimaktiv_rechner_struktur.json` | Vollständige Rechner-Struktur (Sonderfälle) |
| `references/onboarding_fragebogen.md` | Fragebogen für offene Punkte nach Eingang der Unterlagen |
| `references/oekologische_standards_destilliert.md` | 25 Muss-Vorgaben, Stand September 2025 |
| `references/leitlinien_bilanzierung_destilliert.md` | Systemgrenzen, Wesentlichkeit, Berechnungsregeln |

---

## Skill verbessern (Human in the Loop)

Korrekturen fließen über den `→ Skill:` Trigger direkt ins Repo:

1. Im Chat `→ Skill: [Regelkorrektur]` schreiben
2. Claude formuliert den Diff
3. Claude Code schreibt die Änderung ins Repo
4. Nächste Session: Skill ist aktualisiert

**Wichtig:** Keine Euro-Werte, Emissionsfaktoren oder Jahreszahlen in den Mapping-Dateien.
Der Skill speichert Methoden — keine Daten. Daten liefert der Klimaktiv-Rechner.

---

## Produktionsformate

Aktuell unterstützt:
- Spielfilm / Kurzfilm
- Dokumentarfilm / Reportage

Geplant:
- Serie
- Werbefilm / Imagefilm

---

## Wissensquellen

- **Klimaktiv-Rechner:** [go.greenshooting.de](https://go.greenshooting.de)
- **Ökologische Standards:** September 2025, KlimAktiv gGmbH
- **Leitlinien CO₂-Bilanzierung:** Arbeitskreis Green Shooting, BVGCD
- **Brain BVGCD:** Gemeinsames Wissenssystem des Bundesverbands Green Consultants Deutschland (lesend)

---

## Mitmachen

Interesse an KI-Tooling für die CO₂-Bilanzierung?
Voraussetzung: Claude-Account und Praxiserfahrung als Green Consultant.

Kontakt: [robert@knoerk.com](mailto:robert@knoerk.com)
