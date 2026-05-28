# CO₂-Soll-Bilanz

Claude-Skill für die Erstellung von CO₂-Soll-Bilanzen im KlimAktiv-Rechner. Primärer Nutzer ist der Green Consultant. Kann auch von Produzentinnen für eine erste Einschätzung genutzt werden — die Ergebnisse sollten vor Eingabe in den Rechner von einem zertifizierten Green Consultant geprüft werden.

## Language

### Akteure

**Green Consultant**:
Zertifizierte:r Nachhaltigkeitsberater:in für Film- und TV-Produktionen. Primärer Nutzer des Skills.
_Avoid_: GC (in Fließtext), Berater, Nachhaltigkeitsbeauftragter

**Produzentin**:
Die auftraggebende Produktionsfirma. Liefert Unterlagen, beantwortet Rückfragen, entscheidet über Maßnahmen.
_Avoid_: Produzent, Auftraggeber, Kunde

### Produktion & Bilanz

**Produktion**:
Ein Film- oder TV-Projekt mit Arbeitstitel, Crew und Drehzeitraum. Im Rechner-Kontext: der zugehörige Datensatz.
_Avoid_: Projekt, Auftrag

**Soll-Bilanz**:
Vorlaufende Schätzung der CO₂-Emissionen einer **Produktion** vor oder während der Herstellungsphase. Systemgrenze: Vorproduktion bis Postproduktion (cradle-to-gate). Finanzieller Kontrollansatz: Was die **Produktion** bezahlt, wird bilanziert.
_Avoid_: Prognose, Forecast, Vorab-Bilanz

**Beistellung**:
Leistung die ein Dritter (Sender, Förderung) für die **Produktion** erbringt. Gehört in die Bilanz (finanzieller Kontrollansatz). **Rückfrage** wenn Details fehlen.
_Avoid_: Sachleistung, Drittleistung

### KlimAktiv-Rechner

**KlimAktiv-Rechner**:
Der Green Shooting CO₂-Rechner von KlimAktiv gGmbH (go.greenshooting.de). Werkzeug für die Erfassung und Berechnung von CO₂-Emissionen.
_Avoid_: Klimaktiv-Rechner, Green Shooting Rechner, Rechner (alleinstehend)

**Handlungsfeld**:
Einer der vier Bilanzierungsbereiche im KlimAktiv-Rechner: Energie, Reise/Transport, Catering, Materialeinsatz.
_Avoid_: Sektor, Kategorie, Bereich

**Thema**:
Untergliederung innerhalb eines **Handlungsfelds**. Z.B. Motive, Büroräume, Kostüme.
_Avoid_: Unterkategorie, Subsektor

**Quelle**:
Berechnungsmethode bzw. Emissionsfaktor-Typ eines Eintrags im KlimAktiv-Rechner. Wird pro Eintrag aus einem Dropdown gewählt.
_Avoid_: Emissionsfaktor, Aktivität (im Rechner-Kontext)

**Vereinfachte Erfassung**:
SOLL-Modus im KlimAktiv-Rechner mit reduziertem Umfang. Materialeinsatz nur Kulissen-Bau und Kostüme, Postproduktion nur Arbeitsplatz-Quellen. Gemäß Kriterium I.3 der Ökologischen Standards zulässig. Nicht änderbar nach Anlage.
_Avoid_: Kurzversion, Light-Modus

**Vollständige Erfassung**:
SOLL-Modus im KlimAktiv-Rechner mit allen Themen und Quellen. 6 Materialeinsatz-Themen, alle Postproduktions-Quellen inkl. Schnitt, Rendering, Mastering.
_Avoid_: Detailmodus, Profi-Modus

### Ökologische Standards

**Muss-Vorgabe**:
Verbindliche Anforderung der Ökologischen Standards (25 gesamt, 5 Handlungsfelder). Max. 6 Abweichungen erlaubt (6-von-25-Regel). Nicht anwendbare Vorgaben gelten als erfüllt.
_Avoid_: Pflichtkriterium, Mindeststandard

### Green Motion & Nachweisverfahren

**Green Motion**:
Branchenlabel für nachhaltige Film- und TV-Produktionen in Deutschland. Voraussetzung: Einhaltung der Ökologischen Standards (max. 6 Abweichungen), CO₂-Bilanzierung (SOLL + IST) und Abschlussbericht. Vergabe nach erfolgreichem **PwC-Nachweisverfahren**.
_Avoid_: Green Shooting (das ist die Initiative/Plattform, nicht das Label), Nachhaltigkeitszertifikat



**PwC-Nachweisverfahren**:
Zweistufiges Prüfverfahren für das Green Motion Label, durchgeführt von PwC Deutschland. Stufe 1 ist immer einzureichen. Stufe 2 wird anlassbezogen oder per Stichprobe angefordert (ca. 5–10 %) und verlangt Originaldokumente.
_Avoid_: Audit, Zertifizierung, Prüfung

### Workflow

**Rückfrage**:
Offener Punkt den der Skill nicht aus den Unterlagen ableiten kann. Priorisiert (1–3), nummeriert (C1, C2...). Der Green Consultant entscheidet ob und wie die **Rückfrage** an die **Produzentin** weitergegeben wird.
_Avoid_: Frage, offener Punkt, To-do

## Example dialogue

> **Green Consultant**: Ich hab die Kalkulation für einen Kurzfilm bekommen. 12 Drehtage, kleines Team, kein Aggregat.
>
> **Domain Expert**: OK — das ist eine **Produktion** im Format Kurzfilm. Für die **Soll-Bilanz** brauchst du die vier **Handlungsfelder**. Ohne Aggregat nimmst du bei Energie das **Thema** Technische Ausrüstung mit **Quelle** Baustrom. Aber prüf erstmal ob die Stromversorgung am Set über Hausanschluss läuft — sonst wird das eine **Rückfrage**.
>
> **Green Consultant**: In der Kalkulation steht auch "Licht über NDR".
>
> **Domain Expert**: Das ist eine **Beistellung**. Die gehört in die Bilanz — aber frag bei der **Produzentin** nach was genau geliefert wird, damit du die richtige **Quelle** im Rechner wählen kannst.
>
> **Green Consultant**: Reicht die **vereinfachte Erfassung**?
>
> **Domain Expert**: Für einen geförderten Kurzfilm ja — Kriterium I.3 erlaubt das. Kulissen-Bau und Kostüme deckst du damit ab, Requisiten und Büromaterial fallen bei einem Kurzfilm eh kaum an.
