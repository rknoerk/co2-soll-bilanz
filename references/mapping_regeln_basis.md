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
| Jahr der Produktion | Kalkulation Deckblatt. ⚠️ Kann NICHT mehr geändert werden nachdem SOLL- oder IST-Daten erfasst wurden — muss beim Anlegen der Produktion korrekt gesetzt sein. CSV-Export-Hinweis: die Spalte "Jahr der Produktion" im CSV-Export enthält das Jahr der Förderentscheidung, nicht das Produktionsjahr. |
| Jahr der Förderentscheidung | Förder-E-Mail, Kalkulation. CSV-Export: wird unter der Spalte "Jahr der Produktion" exportiert. |
| Jahr der Ausstrahlung/Aufführung | Herstellungsplan, Sendetermin |
| Genre | Kalkulation Deckblatt |
| Herstellungsverfahren | Kalkulation (On location / Studio / Mix) |
| Medium | Kalkulation (Kino / TV / Streaming) |
| Art | Kalkulation. Exakte Optionen im Klimaktiv-Rechner: Keine Angabe / Eigenproduktion (TV und VOD) / Auftragsproduktion / Co-Produktion / Unabhängige und geförderte Produktion |
| Länge [min] | Kalkulation Deckblatt |
| Drehtage | Kalkulation Deckblatt, Herstellungsplan |
| Postproduktion (Tage) | Kalkulation (Rohschnitt + Feinschnitt + Mischung) |
| Herstellungskosten brutto [EUR] | Kalkulation Gesamtsumme (Position G / Zwischensumme D). Nur ganze Zahlen, keine Trennzeichen. |

**Herstellungskosten brutto [EUR]:**
Optionales Feld im Klimaktiv-Rechner. Wenn in den Produktionsunterlagen
vorhanden, immer auslesen und in Ausgabe A aufnehmen.
Quelle: z.B. Kalkulation, Kalkulationsprotokoll, E-Mail.
Definition: Gesamtherstellungskosten inkl. Handlungskosten und Gewinn,
exkl. MwSt. MwSt wird NICHT addiert.
Eingabe als ganze Zahl ohne Trennzeichen (Rechner-Vorgabe).

---

## 1. Übersetzungsregeln: Eingabedokumente → Klimaktiv

### Energie

| Kalkulations-Position | Klimaktiv-Feld | Regel |
|---|---|---|
| Aggregat (Tage) | Technische Ausrüstung > Dieselaggregat | Drehtage mit Aggregat = Nutzungstage |
| Drehtage ohne Aggregat | Technische Ausrüstung > Baustrom (Schätzung) | Drehtage gesamt minus Aggregat-Tage |

**Baustrom — drei Fälle:**
"Baustrom" im Klimaktiv-Rechner meint einen Baustromanschluss am Set
(Baustromkasten), nicht das allgemeine Laden von Geräten.
Vor dem Anlegen eines Baustrom-Eintrags immer prüfen welcher Fall vorliegt:

1. Baustromanschluss / Baustromkasten am Set vorhanden
   → Baustrom-Eintrag anlegen. Nutzungstage = Drehtage mit Anschluss.
2. Strom aus den Motiven (Hausanschluss der Location)
   → KEIN separater Baustrom-Eintrag. Strom ist bereits in Motive erfasst.
   Separater Eintrag wäre Doppelbilanzierung.
3. Akkus ausschließlich im Hotel oder Büro geladen
   → KEIN separater Baustrom-Eintrag. Stromverbrauch ist bereits in
   Übernachtung bzw. Büro-Eintrag abgedeckt.
   Separater Eintrag wäre Doppelbilanzierung.

Rückfrage (Prio 1): "Wie wird am Set Strom bezogen —
Baustromkasten, Hausanschluss der Location, oder Akkus im Hotel/Büro?"
| Büroraummiete (€, Monate) | Büroräume > Ökostrom/Strom (Schätzung) | Mietdauer in Monaten, Fläche aus Mietvertrag oder schätzen. Standardannahme: Ökostrom (Muss-Vorgabe II.1). |
| Homeoffice alle Beteiligten | Büroräume > Homeoffice | Arbeitstage aller Personen die für die Produktion im Homeoffice arbeiten (Produzentin, Regie, Aufnahmeleitung, Green Consultant etc.). Steht nie in der Kalkulation — immer aktiv erfragen und eigene Tage als Green Consultant manuell ergänzen. |
| Rohschnitt + Feinschnitt (Tage) | Postproduktion Bild > Arbeitsplatz | Tage × 10h = Stunden (Filmproduktion). 1 Arbeitsplatz. Standardannahme: 2 Monitore. |
| Mischung (Tage) | Postproduktion Ton > Sound (Schätzung) | Tage direkt |

**Beistellungen in der Postproduktion:**
Bevor für eine offene Postpro-Position eine neue Rückfrage angelegt wird,
prüfen ob diese bereits als Beistellung in den Unterlagen ausgewiesen ist
(Kalkulation, Protokoll o.ä.) und ob dafür bereits eine Rückfrage existiert
(z.B. C6 für Grading/Grafik).
Keine doppelten Rückfragen anlegen — auf bestehende Cx verweisen.
Beispiel: Grading TBD → nicht neue Rückfrage, sondern → C6 wenn Beistellung
bereits erfasst.
| Motivliste (m², Gebäudeart, Tage) | Motive > Strom (Schätzung) | Pro Motiv ein Eintrag. Wenn keine Motivliste: Gebäudeart aus Drehplan ableiten, m² schätzen (50–150 m² je nach Raumtyp), Notiz "Fläche geschätzt". Zusätzlich "Motive: Wärmebedarf (pauschal)" wenn in der Heizperiode gedreht wird (Oktober–April). |

### Reise / Transport

| Kalkulations-Position | Klimaktiv-Feld | Regel |
|---|---|---|
| Reisekosten Inland (€) | Personentransporte > Bahn oder PKW | Art aus Kontext ableiten, Notiz setzen |
| Km-Geld (€) | Personentransporte > Pkw Distanzschätzung | Betrag ÷ Erstattungssatz = km. Nur anwenden wenn echtes km-Geld ausgewiesen — Fahrzeug-Tagessätze sind kein km-Geld und können nicht auf km umgerechnet werden. |

**Pkw (Distanzschätzung) — Kraftstofftyp irrelevant:**
Wenn die Quelle "Pkw (Distanzschätzung)" gewählt wird, verwendet der
Klimaktiv-Rechner automatisch einen gewichteten Mix aus Benzin, Diesel,
Elektro und Hybrid. Der Kraftstofftyp muss in diesem Fall NICHT erfragt
werden — keine Rückfrage C notwendig.
Kraftstofftyp nur relevant wenn eine spezifische Quelle gewählt wird
(z.B. "Diesel", "Benzin", "Strom") und der tatsächliche Antrieb bekannt ist.
Standardfall SOLL-Bilanz: immer "Pkw (Distanzschätzung)" verwenden.
| Benzin/Diesel (€) | Personentransporte > Diesel/Benzin Kosten | Direktübernahme. Bei Fahrzeug-Tagessätzen mit Fußnote "*incl. Km-Geld und Benzin": Kraftstoffanteil nur übernehmen wenn explizit ausgewiesen. |
| Taxi / Shuttle (€) | Personentransporte > Taxikosten | Direktübernahme in €. Kein Kraftstofftyp erforderlich. |
| Flüge Ausland (Personen) | Flugreisen > Mittelstrecke pauschal | 1 Flug im Rechner = Roundtrip (Hin+Rück). Anzahl Personen = Anzahl Flüge. |
| Hotelkosten Inland (€) | Übernachtung > Hotel DE | Nächte aus Personen × Drehtage ableiten |
| Hotelkosten Ausland (€) | Übernachtung > Hotel Europa/International | Analog Inland |
| Fahrzeugtransporte LKW (€) | Warentransport > Diesel Kosten | Kraftstoffanteil schätzen, Notiz |

### Catering

| Kalkulations-Position | Klimaktiv-Feld | Regel |
|---|---|---|
| Catering Set (€/Tag × Tage) | Essen > Vollverpflegung (ohne Frühstück) | Portionen = Drehtage × Personen am Set |
| Catering Vorbereitungsperiode | Essen > Mahlzeit (standard) | Portionen = Vorbereitungstage × Personen |
| Zusatzverpflegung / Diäten (aus Reise-Sektion der Kalkulation) | Catering > Essen > Mahlzeit (einfach) | Aus Diäten-Tagen × Personen ableiten. Gehört in Handlungsfeld Catering, nicht Transport — auch wenn in der Kalkulation unter Reisekosten gelistet. |

### Materialeinsatz

| Kalkulations-Position | Klimaktiv-Feld | Regel |
|---|---|---|
| Material für Bau (€ netto) | Kulissen-Bau > Holzbau: monetäre Abschätzung | Direktübernahme. Nur Pos. "Material für Bau (Kauf)" — An/Abtransporte sind Warentransport. |
| An/Abtransporte Setbau (€) | Warentransport > Diesel Kosten | Transportkosten für Setbau/Dekoration gehören zu Warentransport, nicht zu Kulissen-Bau. Kraftstoffanteil schätzen (ca. 50%), Notiz setzen. |
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
- Akkubetrieb Außendreh (Tageslicht): kein Energieeintrag erforderlich. Als Dokumentation in der Bilanz vermerken.
- Homeoffice: Quelle "Homeoffice (Arbeitstage)" — keine Ökostrom-Option verfügbar. Ökostrom-Status der Mitarbeitenden ist für dieses Feld nicht relevant.
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
- Büroräume: Produktionsbüro vorhanden (Fläche, Mietdauer)? Homeoffice-Tage für alle Beteiligten (Produzentin, Regie, Aufnahmeleitung etc.) — immer fragen, steht nie in der Kalkulation. Green Consultant eigene Tage selbst ergänzen.

**Beistellungen (Dritter):**
Wenn Positionen in Kalkulation oder Protokoll als Beistellung ausgewiesen sind
(z.B. "über NDR", "über Sender", "über Förderung", "Beistellung X"),
diese NICHT still aus der Bilanz ausschließen.
Stattdessen als Prio-2-Rückfrage aufnehmen:
"[Position] ist als Beistellung ausgewiesen — soll diese trotzdem
bilanziert werden?"
Begründung: Unter dem finanziellen Kontrollansatz ist nicht automatisch klar,
dass Beistellungen außerhalb der Systemgrenze liegen. Impact ohne Rückfrage
nicht verlässlich einschätzbar.

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

---

## 5. Qualitätssicherung Kalkulations-Mapping

**Positionsnummern immer am Original verifizieren.**
Niemals Positionsnummern aus dem Gedächtnis oder aus früheren Abschnitten übernehmen —
immer direkt aus dem vorliegenden Dokument ablesen.

**Leere Positionen bleiben leer.**
Wenn eine Position keinen Wert hat, wird sie nicht geschätzt oder aus benachbarten
Positionen abgeleitet. Eintrag: ⚠️ offen.

**Querprüfung gegen Sektionssummen.**
Nach dem Mapping jeder Sektion: Summe der erfassten Positionen gegen die
ausgewiesene Sektionssumme prüfen. Abweichung → Positions-Mapping nochmal prüfen.

**Tagessätze ≠ km-Geld.**
Fahrzeug-Tagessätze (€/Tag) können nicht auf km umgerechnet werden,
auch nicht wenn die Fußnote "incl. Km-Geld" enthält.

**Bezeichnung nur aus Quelldokument — nie aus Kontext.**
Die Bezeichnung darf nur Informationen enthalten die direkt im Quelldokument stehen.
Alles was erschlossen, abgeleitet oder aus dem Kontext ergänzt wurde, gehört
ausschließlich in die Notiz als explizite Annahme.

Beispiele:
- Drehort steht nicht in der Pos. → nicht in Bezeichnung, sondern Notiz: "Annahme: DE-Dreh"
- Kraftstofftyp nicht genannt → nicht in Bezeichnung, Notiz: "Annahme: Diesel"
- Personenzahl geschätzt → Notiz: "Personenzahl geschätzt"

**Wo Geld fließt, entsteht CO₂ — aber Produzentin hat Entscheidungshoheit.**
Grundsatz: Jede kalkulierte Position die reale Aktivität repräsentiert wird bilanziert.
Ausnahme: Wenn die Produzentin explizit bestätigt dass eine Position ein finanzieller
Puffer ohne reale Aktivität ist, wird sie nicht bilanziert.
Entscheidung und Begründung im Notizfeld dokumentieren.
