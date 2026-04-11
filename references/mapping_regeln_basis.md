# Mapping-Regeln: Basis

Gilt für alle Produktionsformate. Wird immer geladen.
Format-spezifische Ergänzungen: `mapping_regeln_spielfilm.md` / `mapping_regeln_doku.md`

**Input kann sein:** Kalkulation (SESAM/FFA), Herstellungsplan, Stabliste, Drehplan,
Motivliste, E-Mail, WhatsApp-Nachricht, Meeting-Transkript, Onboarding-Fragebogen —
oder jede Kombination davon.

---

## 0. Stammdaten des Klimaktiv-Rechners

| Feld | Wo typischerweise zu finden |
|---|---|
| Titel der Produktion | Deckblatt Kalkulation, Herstellungsplan |
| Jahr der Produktion | Kalkulation Deckblatt |
| Jahr der Förderentscheidung | Förder-E-Mail, Kalkulation |
| Jahr der Ausstrahlung/Aufführung | Herstellungsplan, Sendetermin |
| Genre | Kalkulation Deckblatt |
| Herstellungsverfahren | Kalkulation (On location / Studio / Mix) |
| Medium | Kalkulation (Kino / TV / Streaming) |
| Art | Kalkulation. Exakte Optionen im Klimaktiv-Rechner: Keine Angabe / Eigenproduktion (TV und VOD) / Auftragsproduktion / Co-Produktion / Unabhängige und geförderte Produktion |
| Länge [min] | Kalkulation Deckblatt |
| Drehtage | Kalkulation Deckblatt, Herstellungsplan |
| Postproduktion (Tage) | Kalkulation (Rohschnitt + Feinschnitt + Mischung) |
| Herstellungskosten brutto [EUR] | Kalkulation Gesamtsumme (Position G / Zwischensumme D). Nur ganze Zahlen, keine Trennzeichen. |

---

## 1. Übersetzungsregeln: Eingabedokumente → Klimaktiv

### Energie

| Kalkulations-Position | Klimaktiv-Feld | Regel |
|---|---|---|
| Aggregat (Tage) | Technische Ausrüstung > Dieselaggregat | Drehtage mit Aggregat = Nutzungstage |
| Drehtage ohne Aggregat | Technische Ausrüstung > Baustrom (Schätzung) | Drehtage gesamt minus Aggregat-Tage |
| Büroräume (Miete × Monate) | Büroräume > Ökostrom/Strom (Schätzung) | Mietdauer in Monaten, Fläche schätzen |
| Rohschnitt + Feinschnitt (Tage) | Postproduktion Bild > Arbeitsplatz | Tage × 10h = Stunden (Filmproduktion). 1 Arbeitsplatz. Standardannahme: 2 Monitore. |
| Mischung (Tage) | Postproduktion Ton > Sound (Schätzung) | Tage direkt |
| Motivliste (m², Gebäudeart, Tage) | Motive > Strom (Schätzung) | Pro Motiv ein Eintrag. Wenn keine Motivliste: Gebäudeart aus Drehplan ableiten, m² schätzen (50–150 m² je nach Raumtyp), Notiz "Fläche geschätzt". Zusätzlich "Motive: Wärmebedarf (pauschal)" wenn in der Heizperiode gedreht wird (Oktober–April). |

### Reise / Transport

| Kalkulations-Position | Klimaktiv-Feld | Regel |
|---|---|---|
| Reisekosten Inland (€) | Personentransporte > Bahn oder PKW | Art aus Kontext ableiten, Notiz setzen |
| Km-Geld (€) | Personentransporte > Pkw Distanzschätzung | Betrag ÷ Erstattungssatz = km. Kraftstofftyp ist separater Eintrag. Nur anwenden wenn echtes km-Geld ausgewiesen — Fahrzeug-Tagessätze sind kein km-Geld und können nicht auf km umgerechnet werden. |
| Benzin/Diesel (€) | Personentransporte > Diesel/Benzin Kosten | Direktübernahme |
| Taxi / Shuttle (€) | Personentransporte > Taxikosten | Direktübernahme |
| Flüge Ausland (Anzahl) | Flugreisen > Pauschal oder Detailliert | Streckenklasse aus Drehortstrecke |
| Hotelkosten Inland (€) | Übernachtung > Hotel DE | Nächte aus Personen × Drehtage ableiten |
| Hotelkosten Ausland (€) | Übernachtung > Hotel Europa/International | Analog Inland |
| Fahrzeugtransporte LKW (€) | Warentransport > Diesel Kosten | Kraftstoffanteil schätzen, Notiz |

### Catering

| Kalkulations-Position | Klimaktiv-Feld | Regel |
|---|---|---|
| Catering Set (€/Tag × Tage) | Essen > Vollverpflegung (ohne Frühstück) | Portionen = Drehtage × Personen am Set |
| Catering Vorbereitungsperiode | Essen > Mahlzeit (standard) | Portionen = Vorbereitungstage × Personen |
| Zusatzverpflegung / Diäten | Essen > Mahlzeit (einfach) | Aus Diäten-Tagen × Personen ableiten |

### Materialeinsatz

| Kalkulations-Position | Klimaktiv-Feld | Regel |
|---|---|---|
| Material für Bau (€ netto) | Kulissen-Bau > Holzbau: monetäre Abschätzung | Direktübernahme |
| Kostüm Kauf (€) | Kostüme > Kostümkauf | Direktübernahme |
| Kostüm Miete (€) | Kostüme > Kostümmiete/Weiternutzung | Direktübernahme |
| Anfertigung Kostüm (€) | Kostüme > Kostümkauf | Wird wie Kauf behandelt |

---

## 2. Standardannahmen

Immer im Notizfeld dokumentieren.

**Energie:**
- Stromversorgung Set: Baustrom, durchschnittlicher Verbrauch — wenn kein Aggregat in Kalkulation
- Postproduktion: Ökostrom — immer Standardannahme (extern: Muss-Vorgabe II.4 / intern: Muss-Vorgabe II.1). Quelle "Arbeitsplatz (Ökostrom)" immer wählen.
- Postproduktion Bild: 1 Schnittplatz, 2 Monitore, Tage × 10h = Stunden (Filmproduktion)
- Postproduktion Ton: analog Bild, 1 Arbeitsplatz
- Motive: konventioneller Strom — Standardannahme. Begründung: "Ist nicht eindeutig zu
  klären ob zertifizierter Ökostromtarif, muss von konventionellem Tarif ausgegangen
  werden" (Leitlinien CO₂-Bilanzierung). Ökostrom nur wenn vom Vermieter bestätigt.
- Motive Wärme: nur erfassen wenn Dreh in Heizperiode (Oktober–April). Quelle: "Motive: Wärmebedarf (pauschal)". Pro Motiv separater Eintrag.
- Büro: Ökostrom — Standardfall DE 2025+

**Transport:**
- Fahrzeugantrieb: Diesel, Euro 6 — wenn kein Hinweis auf E-Fahrzeuge
- Übernachtungstyp: Hotel durchschnittlich — wenn kein Hinweis auf Ferienwohnung

**Catering:**
- Fleischkonsum: Mischkost — wenn keine Angabe
- Produktionsweise: konventionell — wenn kein Hinweis auf Bio
- Regionalität: standard — wenn kein Hinweis

---

## 3. Rückfragen-Logik

### Prio 1 — immer stellen
- Fehlende Stammdaten (Länge, Ausstrahlung etc.)
- Stromquelle am Set: Ökostrom oder konventionell? Aggregat oder Hausanschluss?
- Auslandsdreh: von welchen Städten fliegen Crewmitglieder?
- E-Fahrzeuge: eingesetzt? Mit Ökostrom geladen?

### Prio 2 — stellen wenn unsicher
- Teamgröße am Set (wenn nicht aus Stabliste ableitbar)
- Anzahl Übernachtungsnächte (wenn nur Pauschalbudget)
- Catering-Konzept: vegetarischer Tag? Externes Catering?
- Drehdatum unbekannt: Heizperiode (Oktober–April)? → Motive: Wärmebedarf (pauschal) zusätzlich pro Motiv

### Prio 3 — Schätzwert reicht
- Motiv-Flächen in m² (Schätzung nach Gebäudeart)
- Ökostrom Büro (Standardannahme + Notiz)
- Kostüm-Split (wenn nur Gesamtbudget)

---

## 4. Bezeichnung und Notiz

Jeder Rechner-Eintrag hat zwei Felder:

**Bezeichnung** — aussagekräftiger Name des Eintrags. Was ist das?
Beispiele: "Roh- und Feinschnitt", "Flüge BG-Dreh", "Set-Catering DE", "Produktionsfahrzeug DE"

**Notiz** — Quelle, Rechenweg, Annahme (nur wenn relevant).
Format: Quelle + Rechenweg + Annahme (was zutrifft)
Beispiele:
- `Rohschnitt 10 + Feinschnitt 5 = 15 Tage × 10h. Nico Hertel (Berlin). Annahme: Ökostrom`
- `Kalkulation Pos. 154: 10 DT × 50€. 500 ÷ 0,20€/km = 2.500 km. Annahme: Bahn`
- `Kalkulation Pos. 140: 11 DT × 150€ = 1.650€. 1.650 ÷ 0,30€/km = 5.500 km. Diesel Euro 6`
- `Schätzung: kein Aggregat in Kalkulation → Baustrom angenommen`

Felder die in der Rechner-Maske als eigene Eingabe existieren (Anzahl Arbeitsplätze,
Monitore, Gebäudeart etc.) werden nicht in der Notiz wiederholt.

Maskenfelder die nicht in der Notiz stehen, werden stattdessen in der ersten Spalte
(Klimaktiv-Feld) als Zusatz notiert, z.B.:
'Postproduktion Bild > Arbeitsplatz (Ökostrom) · Anzahl: 1 · Monitore: 2'
'Motive > Strom (Schätzung) · Bürogebäude · durchschnittl. Verbrauch'
Gilt für alle Felder die direkt in der Rechner-Maske als Dropdown existieren.

Ausgabe-Format Eingabeliste:
| Klimaktiv-Feld | Bezeichnung | Wert | Einheit | Notiz (Quelle / Rechenweg / Annahme) |
