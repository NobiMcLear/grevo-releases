# Grevo – Änderungsliste

## 01.001.143 - Navi-Robustheit + staerkerer Windfilter (13.08.2026)
- Fuenf stille Navi-Fehlerpfade behoben: Standort-Strom heilt sich nach Ausfall selbst, Fortsetzen-Angebot und Fahrt-Aufzeichnung gehen nicht mehr unbemerkt verloren.
- Weniger unnoetige Routen-Neuberechnungen bei laengerem Abseits-Fahren (Reroute-Haeufung gebremst).
- Windfilter deutlich staerker: echtes Hochpass-Filter direkt im Sendeweg (nativ) - Wind-Poltern wird um ein Vielfaches staerker gedaempft; die grevo-Spracherkennung profitiert mit.

## 01.001.141 - Windfilter zurueck (12.08.2026)
- Wind-Filter (Sende-Filter gegen Wind-Poltern) wieder fest eingebaut - immer aktiv, unabhaengig von der Geraeuschunterdrueckung (war in v138 versehentlich entfernt).
- grevo-Spracherkennung filtert Fahrtwind neu vor der Erkennung heraus.
- Fortsetzen-Frage erscheint nicht mehr faelschlich nach einer beendeten Fahrt; beim Fortsetzen wird der Wegpunkt-Fortschritt uebernommen.
- Ankunftserkennung repariert; manuelles Beenden kurz vor dem Ziel (unter 100 m) zaehlt als Ankunft.
- Fahrt-Auswertung ueberlebt das Wegwischen der App (wird beim naechsten Start nachgereicht).

## 01.001.140 (11.08.2026)
- Heimweg-Modus: Beim Verlassen der Route kommt jetzt die Ansage 'Route verlassen ...' plus Entwarnung, und die Route wird automatisch neu berechnet (bisher blieb die App still).
- Der Reroute rechnet nur den Hinweg-Rest neu und haengt den bereits berechneten Rueckweg wieder an - genau ein Routing-Aufruf.
- Rest-Distanz/Ankunftszeit springen nicht mehr auf den Rueckweg; nach 3 Minuten abseits der Route wird die Luftlinie zum Ziel gezeigt.
- Fahransicht: Kennzeichen 'Heimweg' mit Haus-Symbol.
- Navigation und Aufzeichnung laufen auch ohne Sprechfunk im Hintergrund zuverlaessig weiter (Bildschirm aus / Handy in der Tasche).

## 01.001.138 - Verkaufsstand (10.08.2026)
- Alle Test-Schalter entfernt (QS-Aufnahme, Reiner Sprachkanal, Niedrige Latenz, Stark=Aggressiv, Wind-Filter); Geraeuschunterdrueckung Aus/Mittel/Stark bleibt.
- Echo-Modus nur noch fuer Tester, neu 10 s Zyklus, Rueckton-Fix (Feldtest 10.08.).
- E-Mail-Adresse auf Startmaske + Profil sichtbar (mehrere Konten unterscheidbar).
- Fahrtrichtung-oben: Pfeil im unteren Drittel, mehr Sicht voraus, auch in der Geteilt-Ansicht.

## 01.001.138 - Verkaufsstand (10.08.2026)
- Alle Test-Schalter entfernt (QS-Aufnahme, Reiner Sprachkanal, Niedrige Latenz, Stark=Aggressiv, Wind-Filter); Geraeuschunterdrueckung Aus/Mittel/Stark bleibt.
- Echo-Modus nur noch fuer Tester, neu 10 s Zyklus, Rueckton-Fix (Feldtest 10.08.).
- E-Mail-Adresse auf Startmaske + Profil sichtbar (mehrere Konten unterscheidbar).
- Fahrtrichtung-oben: Pfeil im unteren Drittel, mehr Sicht voraus, auch in der Geteilt-Ansicht.

## 01.001.138 - Verkaufsstand (10.08.2026)
- Alle Test-Schalter entfernt (QS-Aufnahme, Reiner Sprachkanal, Niedrige Latenz, Stark=Aggressiv, Wind-Filter); Geraeuschunterdrueckung Aus/Mittel/Stark bleibt.
- Echo-Modus nur noch fuer Tester, neu 10 s Zyklus, Rueckton-Fix (Feldtest 10.08.).
- E-Mail-Adresse auf Startmaske + Profil sichtbar (mehrere Konten unterscheidbar).
- Fahrtrichtung-oben: Pfeil im unteren Drittel, mehr Sicht voraus, auch in der Geteilt-Ansicht.

Schema der Version: **Hauptrelease.Versionszähler.Iteration** (z.B. 00.001.001).
Iteration steigt bei jedem Änderungsdurchlauf, der Versionszähler bei jeder fertigen Funktion.

## Website 23.07.2026 — Web-Editor Touren (Seite /meine-touren v02.001, KEIN App-Release nötig)
- NEU: **Wegpunkt-Planer auf der Website** («am PC planen, am Rad fahren», Konzept Web-Editor §2 Modus 2): Karte (Leaflet + Stadia wie das Portal), Klick = Wegpunkt, Wegpunkte verschieben/löschen, Ortssuche, Fahrzeugprofil, Rundkurs schliessen, Richtung umkehren, Rückgängig/Wiederherstellen, Höhenprofil. Die Route rechnet **dieselbe Edge Function `route`** wie die App — segmentweise mit Browser-Cache (Wegpunkt verschieben = nur 2 Nachbarsegmente neu, Leitlinie «Routing minimieren»). Gespeichert wird **exakt im App-Format in `touren`** → die Tour erscheint sofort in der App unter Touren und ist mit dem Wegpunkt-Navi abfahrbar.
- NEU: **Spur-Werkzeuge** für Portal-Touren vor der Veröffentlichung (Konzept §2 Modus 1, ganz ohne Routing-Aufrufe): Start/Ziel per Regler zuschneiden, Abschnitt herausschneiden (Lücke gerade verbunden), **Lücke von Hand mit Punkten nachzeichnen** (Nobis Ergänzung 23.07.), «Spur säubern» (GPS-Ausreisser), Kennzahlen (km/hm/Zeit) werden beim Speichern neu gerechnet. Original-Aufzeichnung bleibt unangetastet.
- NEU: **Geplante Touren einreichbar** (Entscheid §8.7): Liste «Geplante Touren» auf /meine-touren mit «Zur Portal-Tour machen» — Route wird einmal gerechnet, Track (max. 380 Punkte, Höhen interpoliert) als Portal-Tour angelegt (neue Spalte `portal_touren.quelle_tour`).
- TECHNIK: Edge Functions `route` v14 / `geocode` v9 / `hoehe` v4 um **CORS** ergänzt (Browser-Aufrufe; App unverändert). Abo-Gates greifen unverändert serverseitig. **Seiten-JS ausgelagert** nach Supabase Storage `web-assets/meine-touren-v02001.js` (versionierter Dateiname) — ein WordPress-Render-Filter zerlegte Inline-Skripte (`&&` → `&#038;` in Zeilen mit `<`-Vergleichen); WP-Seite enthält nur noch einen Mini-Lader in einer wp:html-Block-Hülle.
- Deployt auf **STAGING** (Seite 51), End-zu-End getestet (Planen→Speichern→DB, geplante Tour→Portal, Trimmen/Säubern→Kennzahlen). **Live-Gang zusammen mit dem Touren-Portal nach Nobis Abnahme.**

## 01.001.134 (in Arbeit)
- NEU (Nobis Gegentest 29.07. mit Regula, v133: GU Aus = klar auch bei Wind, aber Wind «sehr störend» und Sparmodus-Stille-Uhr käme nie zur Ruhe; GU **Mittel/Stark = «alles abgehackt, keine Verständigung»** — Echo-Analyse belegt: NS frisst 70–100 % der Sprache, Kipppunkt-Befund v130 trifft den Ernstfall): **Diagnose-Schalter «Wind-Filter (Hochpass, Test)»** im Sprechfunk. Eigener Hochpass im SENDEweg per Agora-Equalizer — Tiefenabsenkung 31/62 Hz −15 dB, 125 Hz −9 dB, 250 Hz −3 dB. Wind aufs Mikro ist tieffrequentes Poltern (<300 Hz); die Sprach-Verständlichkeit (>500 Hz) bleibt unangetastet. Gedacht mit Geräuschunterdrückung AUS (die NS-Stufen bleiben unverändert wählbar). Nebenwirkung erwünscht: Die Sparmodus-Stille-Uhr bekommt wieder echte Ruhe-Phasen (Wind unter der Rede-Schwelle) — die Dreifach-Bedienung des Sparmodus (Stille-Uhr automatisch · «grevo spar» · Tasten) bleibt wie sie ist. Wirkt engine-weit → **solo per Echo-Test prüfbar** (Grundsatz; Fahrgeräusch: Klimaanlage/Föhn aufs Mikro). Reiner Sprachkanal setzt den EQ neutral. Pro Gerät gemerkt, Telemetrie `wind_filter`.

## 01.001.133 (released 28.07. abends; 119–132 waren nur Galaxy-Testbuilds)
- BEHOBEN (Nobi 28.07.: «grevo gehört» kommt nur mit langer Pause, «grevo connect» flüssig gesprochen wird verschluckt): Beim Wake-Treffer setzt die Erkennung ihren Puffer zurück — die unmittelbar folgenden Audio-Frames gingen dabei verloren, der Anfang des Kommandoworts fiel ins Loch. Neu hält die App die letzte **halbe Sekunde Audio als Nachhall-Puffer** vor und speist sie nach dem Wake-Reset erneut ein (gedrosselt auf 1×/s) — **flüssiges «grevo connect» funktioniert damit ohne Kunstpause**.

## 01.001.132 (Galaxy-Testbuild)
- VERBESSERT (Nobi 28.07.: «keine Reaktion auf grevo lauter»; Telemetrie belegte `wake_frames_ok` = Audio kommt an, nur das Wake-Wort matchte nie): **Wake-Wort auf Nobis Aussprache abgestimmt** — seine Echo-Takes mit «grevo lauter/leiser/connect/heim» wurden durch das ECHTE Erkennungs-Modell der App geschickt; es hört sein «grevo» als «CREVIL/GRAVEL/CAN-EVER/…». Diese 9 gemessenen Schreibweisen sind jetzt zusätzliche `@wake`-Varianten (die bisherigen bleiben für andere Sprecher). Offline-Ergebnis: 5 von 9 Takes zünden (die verpassten waren undeutlich/leise gesprochen), **0 Fehlauslösungen** über ~15 Minuten Negativ-Material. Die Kommando-Wörter selbst («lauter», «connect» …) trafen schon vorher zuverlässig.

## 01.001.131 (Galaxy-Testbuild)
- VERBESSERT (N1, Nobi-Notiz 28.07.: «letztes benutztes Profil wieder anwählen — in beiden Navi-Teilen»): **Profil-Vorwahl frischt sich jetzt auch bei jeder App-Rückkehr auf**, nicht nur beim Öffnen des Bildschirms. Im Kombi-Modus bleibt das Navi tagelang montiert — es zeigte sonst das alte Profil, wenn zwischenzeitlich z. B. im Solo-Navi mit dem E-Bike gefahren wurde.
- BEHOBEN (N2, Nobi-Notiz 28.07.: «beim Beitreten der Gruppe wird die Lautstärke des Mobiles auf voll geschaltet»): Die App selbst stellt seit v111 nichts mehr um — der Sprung kommt von Android/Bluetooth (Absolute-Volume-Abgleich beim Start des Audio-Streams). Neu wacht ein **Pegel-Wächter**: Medienpegel vor dem Beitritt merken; springt er unmittelbar danach ohne Zutun auf Maximum, wird er still zurückgestellt (Telemetrie-Beleg `vol_beitritt_reset`).

## 01.001.130 (Galaxy-Testbuild)
- BEHOBEN: Die Echo-Sammel-Datei (`echo_gesamt.aac`) zählte sich beim nächsten Teilen selbst als Take mit — die Datei wuchs bei jedem Teilen um die alte Sitzung. Sammel-Datei ist jetzt von Takes-Liste und Aufräumen ausgenommen.
- BEFUND (Echo-Messreihen 28.07., dokumentiert): NS-Kipppunkt hängt am Lärm-zu-Sprache-Verhältnis — Klimaanlage DIREKT am Mikrofon: Mittel/Stark unterdrücken die Sprache mit (78–98 % Stille); Klimaanlage in 1–2 m: Sprache bleibt auch mit Mittel/Stark klar verständlich. Konsequenz: NS-Stufen bleiben wie sie sind; Betriebsgrenze «Starkwind direkt aufs Mikro» wird dokumentiert (Mikro-Ausrichtung/Windschutz), Idee Auto-Rückfall bei Totalunterdrückung notiert.

## 01.001.129 (Galaxy-Testbuild)
- VERBESSERT (Nobi 28.07.: «so viele Files»): **«Echo-Aufnahmen teilen» verschickt jetzt EINE Datei** — alle aufbewahrten Takes werden chronologisch zu einer einzigen AAC zusammengehängt (ein Take ≈ 5 s). Rückfall auf Einzeldateien nur, falls das Zusammenfügen scheitert.

## 01.001.128 (Galaxy-Testbuild)
- VERBESSERT (Nobi 28.07.: frühere Echo-Takes waren beim Teilen schon überschrieben): **Jeder Echo-Durchgang wird einzeln gespeichert** (Dateiname = Uhrzeit, die letzten 12 bleiben erhalten) und der Knopf heisst jetzt **«Echo-Aufnahmen teilen (letzte 12)»** — verschickt alle aufbewahrten Takes in einem Rutsch. So lassen sich Vergleichsreihen (NS Aus/Mittel/Stark, Chorus an/aus) nachträglich komplett auswerten.

## 01.001.127 (Galaxy-Testbuild)
- BEHOBEN (Nobis Echo-Test 28.07. mit v126: «unter Geräuschunterdrückung Mittel und Stark höre ich nicht mehr»): Die KI-Geräuschunterdrückung ist ein **Sprach-Modell** und verträgt das neue 48-kHz-Vollband-Profil nicht — sie würgte das Signal komplett ab. Jetzt wählt die App das Profil automatisch passend: **NS aus (oder Reiner Sprachkanal) → Vollband «MusicStandard» (voller Klang) · NS Mittel/Stark → bewährtes Sprachband «SpeechStandard»** (dort funktioniert das NS-Modell nachweislich). Umschalten wirkt sofort mit der Stufen-Auswahl.

## 01.001.126 (Galaxy-Testbuild)
- VERBESSERT (objektive Analyse von Nobis Echo-Aufnahme 28.07.: Spektrum bricht hart bei ~8 kHz ab, Pegel sauber/kein Clipping): **Voller Stimmklang statt Telefon-Band** — Audio-Profil von «SpeechStandard» (Sprachband, Ursache des «blechernen» Klangs) auf **«MusicStandard» (48 kHz Vollband)** umgestellt. Gilt für Gruppen-Funk UND Echo-Test (gleiche Engine); Geräuschunterdrückung bleibt unverändert. → Gegentest per Echo: Stimme sollte deutlich natürlicher/reiner klingen.

## 01.001.125 (Galaxy-Testbuild)
- NEU (Nobis Befund 28.07.: QS-Aufnahme im Echo-Test → «hat sich nichts geöffnet»): QS-Aufnahme und Echo-Test teilen sich denselben Agora-Recorder — die QS-Aufnahme wurde im Echo-Test still überschrieben. Jetzt: **Knopf «Letzte Echo-Aufnahme teilen»** im Diagnose-Bereich — jede fertige 5-s-Echo-Aufnahme bleibt erhalten (auch nach Test-Ende) und lässt sich direkt verschicken (z. B. an Claude zur objektiven Klang-Analyse). Der QS-Schalter erklärt sich im Echo-Test jetzt klar, statt still zu scheitern.

## 01.001.124 (Galaxy-Testbuild)
- VERBESSERT (Nobis Test 28.07. mit v123: Route stimmt jetzt — Echo kam auf den Ohrhörern —, aber Klang «ein bisschen blechern, nicht richtig rein»): **Echo-Mitschnitt in voller Qualität** — 48 kHz + höchste AAC-Stufe statt mittlerer Qualität (32 kHz); die Wiedergabe bekommt zudem mehr Luft am Ende (6,3 s Fenster), damit kein Satzende abgeschnitten wird. Der alte Routen-Wert («Bluetooth (Anruf)» aus dem SDK-Echo-Test) wird beim Echo-Start zurückgesetzt, die Anzeige zeigt nur noch frisch Gemeldetes.

## 01.001.123 (Galaxy-Testbuild)
- GEÄNDERT (Abschluss der Echo-Routen-Saga 28.07., Nobis Video v122: Ausgabe blieb «Bluetooth (Anruf)»/Lautsprecher): **Eigener Echo-Zyklus statt SDK-Echo-Test.** Der SDK-Loopback (startEchoTest) ist fest auf den Telefon-Modus (HFP/SCO) verdrahtet und liess sich weder per Route-Logik (v120/121) noch per Szenario-Re-Set (v122) auf die Musik-Route umbiegen. Neu tritt die App einem privaten Test-Kanal GANZ NORMAL bei (identisch zum Gruppen-Funk → Musik-Route/Kopfhörer garantiert), nimmt **5 s das Mikrofon durch die komplette Agora-Verarbeitung inkl. Geräuschunterdrückung** auf (Mix-Mitschnitt wie QS-Aufnahme) und spielt es über denselben Medien-Weg zurück — im Dauerzyklus mit Live-Anzeige «🔴 AUFNAHME – sprich jetzt» / «🔊 WIEDERGABE». Nur der Server-Umweg entfällt; Klang-Kette, NS-Stufen, Lautstärke-Regler und Route sind exakt der Ernstfall.
- BEHOBEN? (Nobis Gegentest 28.07. mit v121, Statuszeile lieferte den Beweis: «Ausgabe: Bluetooth (Anruf)» bei Ton aus dem Lautsprecher): Der SDK-Echo-Test schaltet intern in den **Telefon-Modus (HFP/SCO)** — der Anruf-Kanal zum Kopfhörer kommt nicht zustande (Kopfhörer im Musik-Modus), Android spielt ersatzweise auf dem Lautsprecher. Der Gruppen-Funk läuft dagegen im Medien-Szenario über die **Musik-Route**. Fix: Nach dem Echo-Start wird das Audio-Szenario (GameStreaming bzw. Chorus) nochmals explizit gesetzt, damit der Echo-Test dieselbe Musik-Route nimmt wie der Gruppen-Funk. → Gegentest Nobi: Statuszeile sollte «Bluetooth (Musik)» zeigen und das Echo auf dem Kopfhörer kommen.
- BEHOBEN (Nobis Gegentest 28.07. mit v120: Echo weiterhin auf dem Lautsprecher): Der v120-Fix griff nicht, wenn der Kopfhörer schon VOR dem App-Start verbunden war — Agora meldet die Audio-Route nur bei Änderungen, der Merker blieb «unbekannt» und der alte Lautsprecher-Zwang schlug wieder zu. Logik umgedreht: **Lautsprecher wird nur noch erzwungen, wenn Agora ausdrücklich Hörmuschel/Lautsprecher gemeldet hat**; bei unbekannter oder externer Route bleibt die Route unangetastet (im Medien-Szenario spielt es ohne Kopfhörer ohnehin auf dem Lautsprecher, nie leise auf der Hörmuschel). NEU zur Kontrolle: Die Test-Statuszeile im Echo-Test zeigt jetzt die aktuelle **Ausgabe** («Bluetooth (Musik)», «Lautsprecher», …) live an, und `echo_start` landet mit Route in der Telemetrie.
- BEHOBEN (Nobis Echo-Test 28.07. mit Spotify + Bluetooth-Kopfhörer: «die Antwort kommt auf dem Mobillautsprecher»): **Echo-Test respektiert den Kopfhörer.** Der v117-«totenstill»-Fix zwang die Ausgabe beim Echo-Start stur auf den Handy-Lautsprecher. Jetzt merkt sich die App die aktuelle Audio-Route (Agora-Meldung) und erzwingt den Lautsprecher nur noch, wenn KEIN Kopfhörer/Headset (Bluetooth, Kabel, USB) verbunden ist — der Echo-Test spielt auf derselben Route wie der Gruppen-Funk.
- BEHOBEN (T1, Feldtest Auto 26.07.: ganze Fahrt ohne Telemetrie, Ursache per Schnelltest 28.07. bestätigt): **Telemetrie übersteht eine verpatzte Tester-Prüfung.** Bisher lief die Prüfung genau EINMAL pro App-Lauf — schlug sie in diesem Moment fehl (Login-Sitzung noch nicht bereit, Timeout, Netz-Aussetzer), sammelte die App die ganze Fahrt NICHTS. Neu: Ereignisse/GPS-Trace werden IMMER lokal gesammelt (begrenzte RAM-Puffer); ob die Daten das Gerät verlassen, entscheidet erst das Fahrtende anhand des Tester-Flags (Prüfung mit Wiederholung statt Einmal-Sperre; bleibt sie ungeklärt, wird das Paket lokal gepuffert und erst nach bestätigtem Tester hochgeladen — bestätigte Nicht-Tester: alles verworfen, Datenschutz unverändert). Zusätzlich leert die App die Nachliefer-Warteschlange jetzt schon beim App-Start, nicht erst bei der nächsten Fahrt.
- BEHOBEN (T2, Feldtest Auto 26.07.: rote Meldung «Route konnte nicht berechnet werden.» erschien nach der Ankunft in Arth): **Anzeige-Altlast beseitigt** — die Planungs-Fehlermeldung wird jetzt beim Navi-Start und beim Navi-Ende gelöscht (sie stammte von einem folgenlosen clientseitigen Fehlversuch VOR dem Start und war während der ganzen Fahrt nur versteckt). Clientseitige Routen-Fehlversuche (Planung + «Zurück zum Start») landen neu als `route_fehler`-Ereignis in der Telemetrie, damit sie nie mehr unsichtbar sind.
- BEHOBEN (W2, Nutzerwunsch Feldtest 25.07.: «iOS zeigt Lautstärke-Regler nicht an, wenn App läuft»): **iOS-Lautstärke-Balken wieder sichtbar.** Die App unterdrückte die System-Lautstärke-Anzeige für ihre eigenen stillen Pegel-Anpassungen (Solo-Ansagen, «grevo lauter/leiser») — die Unterdrückung ist aber GLOBAL und blieb für den ganzen App-Lauf an, darum zeigte iOS den Balken auch bei Hardware-Tastendruck nicht mehr. Jetzt wird sie nach jeder eigenen Anpassung sofort wieder aufgehoben: Tasten drücken zeigt wieder den normalen iOS-Regler, die stillen App-Anpassungen bleiben still.
- NEU (T6, Feldtest Auto 26.07.: Karte ~1 Minute grau bei Rothenthurm): **Kachel-Fehlerzähler in der Telemetrie** — Karten-Kachel-Ladefehler werden gebündelt (max. 1 Ereignis pro 30 s, mit Anzahl, Kartenstil und Position) als `kachel_fehler` mitgeschrieben. Damit ist beim nächsten Grau-Aussetzer belegbar, wie oft und wo Kacheln ausfallen.
- NEU (Sprachversatz, Nobi 28.07.): **Diagnose-Schalter «Niedrige Latenz (Test)»** im Sprechfunk — schaltet das Agora-Szenario von «GameStreaming» auf **«Chorus»** (Agoras niedrigste Latenz, gleiche Medien-Lautstärke — die Lautstärke-Errungenschaft bleibt). Wirkt engine-weit, also auch im Echo-Test: erst solo den Klang vergleichen, dann zu zweit den Versatz (Zähltest, Netz-Zeile). Pro Gerät gemerkt, Telemetrie-Ereignis `latenz_modus`.
- GEÄNDERT (Nobi 28.07., neuer Test-Grundsatz «alles solo per Echo prüfbar»): **Echo-Test verkürzt und regler-treu** — Wiedergabe-Verzögerung neu **5 Sekunden** (10 s war zu lang), und die Echo-Wiedergabe folgt jetzt dem **Lautstärke-Regler** wie im Gruppen-Kanal (Reiner Sprachkanal = neutral 100 %; Untergrenze 100, nie stumm) statt fest 100 % — damit ist auch Übersteuern solo hörbar. Geräuschunterdrückung wirkt engine-weit ohnehin im Test und lässt sich dort live umschalten. Künftige Audio-Schalter werden immer so gebaut, dass sie im Echo-Test genauso wirken (Fahrgeräusch: Klimaanlage).

## 01.001.118
- BEHOBEN (Nobis Test 24.07.: Falschalarm «Verbinden hängt» nach dem Echo-Test): **Beitritts-Watchdog heilt sich jetzt selbst** — hängt der Kanal-Beitritt 12 s, baut die App EINMAL still komplett neu auf (das half im Feld sofort per «Erneut versuchen»); die Meldung kommt erst, wenn auch das hängt. Während des Echo-Tests meldet der Watchdog gar nicht mehr (der Gruppen-Kanal ist da absichtlich verlassen). Zusätzlich 0,8 s Aufräumzeit nach dem Echo-Test-Ende und Sperre gegen Weck-Signale während des Tests.
- NEU (F1, Feldtest Kaltbrunn 25.07., 17-Minuten-Funkloch): **Wieder-Beitritt gibt nie mehr auf** — das Agora-SDK stoppt sein automatisches Neuverbinden nach ~20 Minuten endgültig; genau dann übernimmt jetzt ein eigener Wecker und baut die Verbindung alle 30 s komplett neu auf (inklusive frischem Token), bis das Netz zurück ist oder man den Kanal verlässt. Die Anzeige bleibt dabei ehrlich bei «Verbindung unterbrochen – verbinde neu …» statt einer Fehlermeldung. Telemetrie-Ereignisse: `funk_sdk_aufgegeben`, `funk_rejoin_neustart`, `funk_rejoin_geschafft`.
- NEU (L1, Feldtest 25.07.: «reichlich lange Verzögerung» + Regulas iOS-Störgeräusche): **Netz-Messwerte im Sprechfunk** — Laufzeit zum Agora-Server (ms) und Paketverlust (Senden/Empfangen) werden mitgeschrieben: im Diagnose-Modus «Reiner Sprachkanal» live als Zeile sichtbar, für Tester zusätzlich alle 30 s als Telemetrie-Stichprobe (`funk_netz`). Damit lässt sich beim nächsten Latenz-/Störgeräusch-Fall belegen, ob das Netz (Puffer/Paketverlust) oder die Gerätekette schuld war.
- NEU (W1, Nutzerwunsch aus der Fahrt 25.07.: «Wie viele Meter sind wir da eigentlich?»): **Aktuelle Höhe in der Fahr-Ansicht** — neben dem Tempo zeigt das Navi jetzt die Höhe in m ü. M. (auch in der geteilten Kombi-Ansicht). GPS-Höhe leicht geglättet und höchstens alle 10 Minuten über die eigene Höhen-Funktion aufs Gelände geeicht (GPS-Höhen liegen sonst gerne ~50 m daneben); ohne Netz einfach die GPS-Höhe. Kein einziger zusätzlicher Routing-Aufruf.

## 01.001.117
- BEHOBEN (Nobis Test 23.07. abends: «Echo-Test totenstill, wie ohne Lautstärke»): Drei Ursachen abgefangen. **(1) Zu früher Start:** Der Echo-Test startete direkt nach dem Kanal-Verlassen — intern war das Verlassen noch nicht abgeschlossen, der Test scheiterte STILL (bekanntes SDK-Verhalten, «already in channel»). Jetzt 0,8 s Wartezeit vor dem Start. **(2) Route/Pegel:** Nach dem Kanal-Verlassen konnte die Ausgabe auf die leise Hörmuschel springen; jetzt werden Lautsprecher-Route, Wiedergabe- und Aufnahme-Pegel (100/100) für den Test erzwungen. **(3) Unsichtbare Fehler:** Beitritts-/Token-Fehler des Test-Kanals liefen ins Leere (Statuserfassung war auf den Gruppenkanal gefiltert) — neu zeigt eine **Test-Statuszeile** unter dem Echo-Knopf live den Agora-Status («connected» = Kanal steht; «failed …» = da klemmt es), damit ein Fehlschlag nie mehr stumm bleibt.

## 01.001.116
- NEU (Feldtest 23.07. nachmittags, «abgehackt / weit weg / schmerzhaft laut» — Nobis Basistest-Idee): **Diagnose-Schalter «Reiner Sprachkanal»** im Sprechfunk. EIN Schalter schaltet ALLES ab, was die Sprachqualität beeinflussen könnte (nichts wird gelöscht, alle gemerkten Einstellungen bleiben): Geräuschunterdrückung hart AUS, «grevo»-Lauschen aus (Leerlauf-Recorder UND Agora-Frame-Abgriff samt Beobachter), Navi-Ansagen inkl. Ducking aus (auch solo), App-Ansagen/Signaltöne aus, Wiedergabe-Verstärker fest neutral 100 % (Aufnahme bleibt 100 %), Sparmodus-Stille-Uhr aus (Kanal bleibt durchgehend offen). Übrig bleibt der nackte, Ende-zu-Ende-verschlüsselte Agora-Kanal — die Basislinie. Danach pro Testfahrt EIN Feature wieder zuschalten, bis der Störer gefunden ist.
- NEU: **Echo-Test** (Solo-Test ohne Partner): Knopf im Sprechfunk startet den Agora-Loopback — sprechen, und nach 10 Sekunden hört man sich selbst, nach dem kompletten echten Weg (Mikrofon → Verarbeitung → Funknetz → Agora-Server → zurück). So lässt sich die Tonqualität ALLEINE beurteilen und jede Einstellung (Unterdrückung, Lautstärke …) direkt vergleichen. Technisch: eigener Einmal-Kanal `echo_<zeit>`, Token mit der Agora-Spezial-uid 0xFFFFFFFF, Verschlüsselung für den Test aus; beim Beenden wird die normale Gruppen-Verbindung komplett neu aufgebaut. Der Gruppen-Funk ist während des Tests getrennt (wird angezeigt).
- GEÄNDERT (Befund 23.07.: Anzeige-Falle!): **Ehrliche Lautstärke-Anzeige** — bisher zeigte der Regler intern/10 an: «100 %» hiess in Wahrheit intern 1000 % = globaler Agora-Verstärker 400 % × Pro-Sprecher 250 % (10-fache Verstärkung, übersteuert/verzerrt → passt zu «schmerzhaft laut» und unverständlich). Neu zeigt der Regler den ECHTEN Wert 0–1000 %: **100 % = normal**, darüber Verstärkung; Zusatzzeile erklärt die Skala. Funktion und gemerkter Wert unverändert (Standard weiterhin 250 %).

## 01.001.115
- NEU (Diagnose zu Nobis Video 23.07., Sprachkommandos ohne Reaktion trotz v114): **Sichtbare Lausch-Anzeige** — der Hinweis «höre auf ‚grevo …'-Kommandos» erscheint jetzt auch WÄHREND der Verbindung (Vollbild UND geteilte Fahr-Ansicht), aber nur, wenn der Agora-Frame-Lauscher wirklich Audio bekommt. Fehlt die Anzeige bei offenem Kanal, kommen die Mikrofon-Frames nicht an — genau das wollen wir unterscheiden. Zusätzlich Tester-Telemetrie `wake_frames_ok`/`wake_frames_none` 6 s nach Kanalbeitritt.
- Hinweis zum Video: Die Bildschirmaufnahme enthielt stumme Lücken (Agora hält das Mikro, der Recorder bekommt nur Fetzen) — sie taugt nicht als Beleg, was die App wirklich hörte. Gegentest-Anleitung: siehe Release-Notizen.

## 01.001.114
- BEHOBEN (Feldtest Nobi 23.07.: «grevo wird nicht erkannt, keine Reaktion»): Das **Weckwort «grevo» löste bei deutscher Aussprache praktisch nie aus** — damit waren ALLE Kommandos tot (auch lauter/leiser, die erst nach dem Weckwort zählen). Befund im Sandbox-Erkennungstest reproduziert: das englische Wortmodell hört deutsch gesprochenes «grevo» als „gre-w-o" (deutsches V = englisches W). Fix: **vierte Weckwort-Schreibweise `▁G RE W O`** plus schärferer Boost (4.0) und tiefere Schwelle (0.04) für alle Weckwort-Varianten — im Test trifft deutsches «grevo» jetzt durchgehend, bei 0 Fehlauslösungen in 10 Gegensätzen (bravo, kredo, gustavo, „die crew", „wo bist du" …). Tipp bleibt: nach «grevo» kurz warten, bis «grevo gehört – Kommando?» erscheint, dann das Kommando.

## 01.001.113
- GEÄNDERT (Feldtest Nobi 23.07., erste Fahrt mit der neuen geteilten Ansicht): **Aufteilung neu 2/3 Navi, 1/3 Sprechen** (statt halb/halb) — die Karte bekommt mehr Platz, der Sprech-Status braucht weniger.
- BEHOBEN: In der geteilten Ansicht überlappte die **Weganzeige die System-Statusleiste** (Uhr/Akku) — der Banner sitzt jetzt um die Statusleisten-Höhe tiefer (auch der Hinweis-Balken).

## 01.001.112
- NEU (Konzept Kombi-Ansicht, Entscheide Nobi 23.07.): **Geteilte Kombi-Ansicht umgebaut** — jetzt **Navi OBEN** (Blickrichtung), Sprechen unten. Die geteilte Ansicht ist eine reine **Fahr-Ansicht ohne Bedienelemente**: der Navi-Teil zeigt nur Karte, Weganzeige und Tempo/Rest-km/Ankunft (keine Kopfzeile, keine Seitenknöpfe, kein «Navigation beenden» — §6.2: Beenden nur im Vollbild); der Sprech-Teil zeigt nur Status-Kreis (im Leerlauf = Verbinden-Tipp), Teilnehmerzahl, Spricht-Anzeige und die EINE **Sparmodus-Taste**. Bedient wird strikt über die Vollbild-Modi (Umschalter unten). Kein Tipp-Einblenden (§6.1: verhindert Fehltipps während der Fahrt). Die Karten-Namensnennung (Stadia/OSM) bleibt als kleine Textzeile.
- NEU (§3): **Weganzeige in Weiss** — Distanz und Anweisungen im Manöver-Banner sind jetzt weiss statt cyan (deutlich besser lesbar auf dem Lenker), in allen laufenden Navi-Sichten (Vollbild + geteilt).
- NEU (§5): Sprachkommando **«grevo spar»** — schickt die ganze Gruppe in den Sparmodus. Wortmodell-Eintrag per Sandbox-Erkennungstest abgesichert (trifft «spar»/«sparmodus», Schwelle 0.15); Kommandoliste in 5 Sprachen ergänzt.
- NEU (Variante a, PFLICHT-Entscheid Nobi): **Wake-Word auch während der aktiven Funkverbindung** — die Erkennung lauscht neu auf den rohen Aufnahme-Frames des Agora-Mikrofons (16 kHz mono, nur lesend). Damit funktionieren «grevo spar» und «grevo lauter/leiser» auch MITTEN im Funk, ganz ohne Taste («alles freihändig — Sicherheit auf dem Fahrrad»). Im Leerlauf lauscht wie bisher der eigene Recorder; die Funk-Kommandos («connect»/«spar») werden ausserdem vom Navi an den Sprechfunk weitergereicht (Kombi). Schutz: «grevo spar» im Leerlauf weckt die Gruppe NICHT (fiel früher in den connect-Zweig). 32-bit-Geräte weiterhin ohne Wake-Word (Absturzschutz).

## 01.001.111
- NEU (Feldtest Uznach 23.07., **R9 Reroute-Beruhigung**): Wer bewusst neben der Route fährt, löst keine Ketten-Neuberechnungen mehr aus (23.07.: 37 Reroutes im 10–15-s-Takt). Folgt auf eine Neuberechnung innert 20 s schon die nächste, zählt eine Kette hoch — ab der dritten in Folge gilt ein 60-s-Ruhefenster mit dem bekannten «Abseits der Route · Ziel x km»-Banner. Lenkt man zurück (Abstand schrumpft 30 m unter das Maximum), wird sofort wieder gerechnet. Zusätzlich: keine Neuberechnung bei grobem GPS-Fix (>50 m) — der erste Fix nach einer Pause (23.07.: 93 m) löste sonst eine Fehl-Neuberechnung aus. Reine Aufruf-Reduktion im Sinn der Routing-Leitlinie; neue Log-Marker `R9 …` in Reroute-Log/Telemetrie.
- NEU (Nobi-Wunsch 23.07.): **Fahrprofil-Merker** — das zuletzt benutzte Fahrprofil (Rad/E-Bike/…) ist beim nächsten Navi-Start vorgewählt, sowohl bei der Planung als auch im Start-Dialog. Gespeichert wird bei manueller Wahl und bei Fahrtstart; Fortsetzen-Angebot und Touren mit eigenem Profil behalten Vorrang.
- GEÄNDERT (Nobi-Entscheid 23.07.): Beim **Gruppenbeitritt wird die Medien-Lautstärke nicht mehr automatisch auf Maximum** gestellt («ganz weglassen»). Die Lauter/Leiser-Regelung in der App bleibt unverändert.

## 01.001.110
- BEHOBEN (Feldtest Beetlis 22.07., **Funk-Zombie**): Die Sprechverbindung blieb nach dem Wegwischen der App offen — der Vordergrunddienst hielt den Prozess samt Agora-Engine am Leben (Symptome: glasklarer Empfang ohne App, Mikrofon blockiert, nach Neustart doppelte Sessions mit katastrophaler Tonqualität und doppelten Navi-Ansagen). Vier Massnahmen: (1) beim App-Start wird eine allfällige Zombie-Engine hart freigegeben und ein verwaister Vordergrunddienst gestoppt, (2) beim Beenden der App («detached») verlässt der Sprechen-Bildschirm den Kanal noch sauber, (3) der Vordergrunddienst stirbt jetzt MIT der App (stopWithTask; Bildschirm-aus/Hintergrund bleibt unberührt), (4) die Telemetrie protokolliert neu auch `funk_leave` — fehlende Leaves (Zombies) sind damit künftig sichtbar.
- NEU (Abo-Grundsatz 22.07., Teil 2 «Ablauf-Gates»): **Start-Paket statt Free** — einmalig CHF 3.– = 300 Sprechminuten + volles Navi- & Tourenwesen, alles 30 Tage gültig, danach zwingend Abo. Serverseitig durchgesetzt: `token_allowed` liefert neu `start_abgelaufen` (403 → App zeigt «Abo wählen»-Hinweis in 5 Sprachen), `navi_erlaubt`/`has_abo` erlauben Start-Konten während der 30 Tage, der Monats-Reset überspringt `start` (einmaliger Topf), RevenueCat-Webhook v5 verbucht `grevo_start_3` (setzt Ablaufdatum) und die Tourist-Stufen; läuft ein Abo aus, fällt das Konto auf `start` zurück, solange die Frist noch läuft.
- GEÄNDERT: **Abo-Seite** bietet Free nicht mehr an (Alt-Stufe nur noch sichtbar, wer sie hat, mit Hinweis aufs Start-Paket); neue Start-Karte mit Einmalpreis, Leistungsumfang und Restlaufzeit («noch x Tage»). Tourist-Stufen erscheinen erst mit dem Tourismus-Modus. Der Startkauf-Knopf wird aktiv, sobald das Store-Produkt `grevo_start_3` angelegt ist (bis dahin Preis-Anzeige CHF 3).

## 01.001.109
- NEU (Abo-Grundsatz 20.07.): **Navi nur mit Abo** — der Navi-Einstieg auf der Startmaske prüft jetzt die Berechtigung (Pro/Mega oder Tester-Flag). Free-Konten sehen einen freundlichen Abo-Hinweis mit Direktlink zu «Abo & Pakete» (Texte in 5 Sprachen). Bei Netzproblemen wird bewusst NICHT gesperrt.
- NEU: **serverseitiges Abo-Gate** in den Edge Functions `route` und `geocode` (RPC `navi_erlaubt`, Abschnitt 37): Routing/Adresssuche antworten ohne Abo/Tester mit 403 `abo_noetig` — die App zeigt dann denselben Abo-Hinweis in der App-Sprache. 60-s-Cache pro Nutzer, fail-open bei Dienststörung.
- NEU: **«Ältere laden» in der Touren-Übersicht** — Aufzeichnungen werden seitenweise (15er-Blöcke) geladen statt alle auf einmal; die Übersicht öffnet auch bei vielen Fahrten schnell.

## 01.001.108
- NEU: **Schweizerkreuz + «Swiss Made»** auf der Startmaske (Auswahl Sprechen/Navi). Rechtlich abgeklärt: Fahne/Kreuz zulässig für Schweizer Software, bewusst kein Wappenschild; «Swiss Made» bleibt unübersetzt.
- BEHOBEN (Tester-Hinweis Thomas 19.07.): **Abgeschnittene Titel in der Kopfzeile** — auf schmalen Geräten wurde z. B. «Meine Gru…» abgeschnitten. Die Schrift verkleinert sich jetzt automatisch, bis der Titel passt (Start- und Navi-Maske, auch bei grosser Systemschrift).
- NEU: **Anmelde-IP (Betrugs-/Missbrauchsschutz)** — nach dem Login ruft die App einmalig die Edge Function `signup-ip` auf; die IP wird nur gesetzt, wenn noch keine hinterlegt ist, und im Admin-Dashboard (IP-Spalte) angezeigt. Datenschutz-Doku ergänzt (Datenschutz-Compliance-Sammlung).

## 01.001.107
- NEU (R8, Feldtest 19.07.): **Zeitlimit für Routing-Aufrufe** — hängt eine Neuberechnung im Funkloch (am 19.07. wartete ein Aufruf 305 Sekunden), bricht die App nach 12 Sekunden ab und weicht über die bestehende Staffel auf das **Offline-Routing (BRouter)** aus. Bei der Tourplanung gilt ein Limit von 30 Sekunden. Kein zusätzlicher Routing-Aufruf — das Limit ersetzt nur den hängenden.
- BEHOBEN (R6b, Fahrer-Befund 19.07.): Die Frage **«Fahrt fortsetzen?» kommt jetzt auch beim direkten Neustart** im laufenden Navi-Bildschirm (Beenden → gleich wieder starten, Normalfall bei Sprechen mit Navi) — bisher nur beim frischen Öffnen des Bildschirms.
- BEHOBEN (Feldtest 17./19.07.): **Höhenmeter deutlich realistischer** — die Höhen werden vor der Summierung auf 10-Sekunden-Stützpunkte ausgedünnt, stärker geglättet und erst ab 5 m Höhenänderung gezählt (bisher +546 hm statt real ~330 auf dem Rieden-Aufstieg).
- BEHOBEN (Feldtest 19.07.): **Reine Fahrzeit zählt Stillstand nicht mehr mit** — massgeblich ist jetzt das gemessene GPS-Tempo (im Stand ~0), nicht mehr die zwischen zwei Punkten zurückgelegte Strecke (GPS-Zittern im Stand täuschte Bewegung vor; die Fahrzeit war exakt gleich der Gesamtdauer).
- GEÄNDERT (Routing-Leitlinie): **Im Stand wird nicht mehr neu berechnet** — steht man abseits der Route (unter 3 km/h), wartet die App mit der Neuberechnung, bis wieder Fahrt aufgenommen wird; das Abseits-Banner informiert derweil.
- NEU (Testmodus-Telemetrie E1+E2): Bei Konten, die im Admin-Dashboard als **Tester** markiert sind, sammelt die App während Navigation und Sprechen automatisch Diagnosedaten (Reroute-Ereignisse mit Ort, Abseits-Phasen, Fortsetzen-Nutzung, reduzierter GPS-Trace alle 10 s, Funk-Abbrüche/Rejoins) und lädt sie **am Fahrtende selbständig hoch** (bei Funkloch: lokale Warteschlange mit Nachlieferung). Vollständig unsichtbar, keine Bedienung nötig; pseudonyme Install-ID statt Nutzerkennung, serverseitige Limits (1 MB/Paket, 10 Pakete/Tag), Löschung nach 90 Tagen. Der manuelle Log-Export entfällt damit künftig.

## 01.001.106
- NEU (R6, Feldtest 16./17.07.): **Unterbrochene Fahrt fortsetzen** — der Navi-Stand (Wegpunkte, Fahrzeugart, laufende Aufzeichnung) wird während der Navigation laufend auf dem Gerät gesichert (auch bei App-Wechsel/Absturz). Beim nächsten Öffnen des Navis fragt die App «Unterbrochene Fahrt von HH:MM fortsetzen?», wenn der Stand jünger als 6 Stunden und die Position näher als 500 m ist. Bei «Ja» wird die Route ab der aktuellen Position frisch gerechnet (ein einziger Routing-Aufruf) und die **Aufzeichnung läuft in derselben Datei weiter** — statt wie bisher ein neues File zu beginnen (Restaurant-Pause Rieden 17.07.). Bei echter Ankunft am Ziel wird der gesicherte Stand gelöscht.
- NEU (R7, Feldtest 17.07.): **Kein Informationsloch mehr abseits der Route** — bleibt die Route länger als ~10 Sekunden verlassen, ohne dass eine neue Route berechnet wird (z. B. im Langsamfahren), zeigt das Banner aktiv «Abseits der Route · Ziel x,x km» statt der eingefrorenen alten Anweisung. Reine Anzeige, kein zusätzlicher Routing-Aufruf. Behebt das «Pampa-Gefühl ohne Information» aus dem Feldtest (belegt: 4,5 Minuten eingefrorenes Banner).

## 01.001.105
- NEU (R1, Feldtest Rapperswil 16.07.): **Neuberechnung startet jetzt in FAHRTRICHTUNG** — eine Sperrzone hinter der Position verhindert, dass die neue Route sofort kehrtmacht; gewendet wird, wenn nötig, erst weiter vorn über vorhandene Strassen. Zeigt eine Antwort trotzdem rückwärts, wird genau EINMAL mit grösserer Sperrzone nachgefasst (Leitlinie: möglichst wenige Routing-Aufrufe). Beendet die Rückwärts-Reroute-Schleife (67 Neuberechnungen am 16.07.).
- NEU (R2): **Hartnäckige Zwischenziele werden automatisch übersprungen** — rückt dasselbe Zwischenziel über 3 Neuberechnungen in Folge weiter weg (bewusst ausgelassen), wird es mit der bekannten Ansage übersprungen. Das Endziel nie.
- GEÄNDERT (R3, Nutzerwunsch): Die Ansage **„Route wird neu berechnet" ist komplett entfernt** (der rote Pfeil zeigt die Suche). Der Störungshinweis nach wiederholten Fehlversuchen bleibt. „Folgen Sie der Strasse…" kommt nach einer Neuberechnung nur noch, wenn sich die Anweisung wirklich geändert hat.
- GEÄNDERT (R4, Nutzerwunsch): Die Karte dreht im Modus „Fahrtrichtung oben" **nur noch nach der GPS-Fahrtrichtung** — kein 180°-Umschlagen mehr, wenn eine neue Route rückwärts zeigt.
- GEÄNDERT (R5, Nutzerwunsch): **Kein rotes Blinken mehr** — der Positionspfeil steht bei Routenabweichung statisch rot; während der Routensuche friert das Anweisungs-Banner ein (keine hochzählenden Meter zu einer Rückwärts-Abbiegung).
- GEÄNDERT: Der **Boost-Regler der Navi-Ansagen zeigt jetzt 0–100 %** statt 100–400 % (nur Beschriftung, Wirkung unverändert; Nutzerwunsch „wer rechnet schon mit mehr als 100 %").
- NEU (QS-Gegentest Störgeräusche): **„QS-Aufnahme (Test)"** im Sprech-Bildschirm zeichnet das Gehörte (Kanal-Mix) auf und öffnet beim Stoppen das Teilen-Blatt — nur mit Wissen aller Teilnehmer verwenden. Dazu Testschalter **„Stark = Aggressiv"** (stärkste Geräuschunterdrückung, A/B-Vergleich zu UltraLowLatency).

## 01.001.104
- GEÄNDERT: **Weckwort-Erkennung auf echte Nutzer-Aussprache kalibriert** — anhand einer Sprachprobe des Nutzers wurde „grevo" als dritte Lautvariante „gri-e-vo" ergänzt und die Schwellen gesenkt (Weckwort #0.06, Kommandos #0.10). In der Sprachprobe werden Weckwort, „connect" und „lauter" jetzt zuverlässig erkannt; keine Weckwort-Fehlauslösungen auf Testsätzen (de+en). „leiser"/„heim" auf Deutsch sind experimentell — englisch „quieter"/„home" sind die sichere Variante.

## 01.001.103
- GEÄNDERT: **Sprachkommandos jetzt zweistufig wie Siri** – erst „grevo" sagen (kurze Rückmeldung „grevo gehört – Kommando?"), dann innert 3 Sekunden das Kommandowort. Kurze Einzelwörter werden vom Erkenner deutlich zuverlässiger verstanden als die bisherigen langen Phrasen (Feldbefund 15.07.: Phrasen wurden auch mit korrekten Schwellwerten kaum erkannt).
- NEU: **Kommandowörter auch auf Deutsch** – „lauter", „leiser", „heim" funktionieren zusätzlich zu „louder", „quieter", „home" (Nutzerwunsch: Kommandos in der eigenen Sprache).
- NEU: Die **Kommandoliste mit Aussprache ist aufklappbar** unter dem Schalter „Freihändig mit ‚grevo …'" (Nutzerwunsch: nur zeigen, wenn man sie sehen will).

## 01.001.102
- KORRIGIERT: Der Schalter **„Freihändig mit ‚grevo …'"** samt Kommandoliste war in der App nicht auffindbar (das Bedienfeld war nie eingebunden). Er steht jetzt sichtbar im Sprech-Bildschirm, sobald die Gruppe im Sparmodus ist — mit der kompletten Kommandoliste inkl. Aussprache als Beschreibung.
- KORRIGIERT: Die **neuen Erkennungs-Parameter aus v101 kamen auf dem Gerät nie an** — die App kopiert die Modell-Dateien nur bei geänderter Dateigrösse neu, und die v101-Änderung war zufällig exakt gleich lang. Kleine Dateien werden jetzt inhaltlich verglichen; die Sprachkommandos nutzen damit wirklich die getesteten Werte.

## 01.001.101
- KORRIGIERT: **Sprachkommandos wurden nicht erkannt** (Feldbefund direkt nach v100) – die Erkennungs-Parameter waren für die langen „grevo …"-Phrasen zu streng (Boost 2.0/Schwelle 0.20 → jetzt 3.0/0.10). Mit synthetischen Sprachproben verifiziert: alle vier Kommandos werden erkannt (inkl. Aussprache-Varianten von „grevo"), normale englische Sätze mit „connect/louder/home" lösen NICHT aus.

## 01.001.100
- NEU: **„grevo …"-Sprachkommandos** (komplett offline, wie Siri mit Präfix): **„grevo connect"** öffnet den Sprechkanal (ersetzt das bisherige „connect"), **„grevo louder"/„grevo quieter"** (sprich „kwai-e-ter") regeln die Medienlautstärke ±20 %, **„grevo home"** startet im Navi die Route nach Hause. Lauscht überall, wo das Mikrofon frei ist: im Sparmodus-Leerlauf UND neu im Solo-Navi. Kommandoliste mit Aussprache steht im Sparmodus-Info (5 Sprachen). Auf 32-bit-Geräten (älteres Tablet) bleibt die Funktion wie bisher aus.

## 01.001.099
- NEU (Navi): **Gesetzte Wegpunkte als Heim/Arbeit speichern** – in der Wegpunkt-Liste hat jeder Punkt ein ⋮-Menü „Als Heim/Arbeit speichern" (mit Nachfrage, wenn schon ein Ort hinterlegt ist).

## 01.001.098
- NEU (Navi): **Heim/Arbeit direkt in der Adresssuche** – die beiden Schnellziel-Knöpfe stehen fix zuoberst in der Suche (ein Tipp startet die Route), und jeder Suchtreffer lässt sich über die Symbole rechts direkt als Heim bzw. Arbeit speichern (es gibt je genau einen; Ersetzen mit Nachfrage). Die Heim/Arbeit-Knöpfe im Panel sind jetzt auch bei gesetzten Wegpunkten sichtbar.

## 01.001.097
- KORRIGIERT (Navi): Die **Distanz-Anzeige im Banner erscheint sofort** – auch im Stand direkt nach dem Start (vorher erst nach ein paar Metern Fahrt).

## 01.001.096
- NEU (Navi/Karte): **Route bleibt immer im Bild** – wer neben der Route steht (>40 m), bekommt den Ausschnitt automatisch so aufgezogen, dass Position, Rückkehrpunkt und nächstes Manöver sichtbar sind (Gegentest 15.07.: Routenlinie war 3× ausserhalb).
- NEU (Navi/Karte): **Voller Zoom in bebautem Gebiet** – folgen die Manöver dicht aufeinander (Stadt), bleibt die Karte auch ZWISCHEN den Abbiegungen auf Maximal-Zoom.

## 01.001.095
- GEÄNDERT (Navi, Log-Auswertung 15.07.): **Verfahren wird viel früher erkannt** – Off-Route-Schwelle 60→45 m und Neuberechnung ab der 2. statt 3. Messung (im Feld wurde das Verlassen erst bei 116–166 m Abstand bemerkt).
- KORRIGIERT (Navi): **Kein „Rückwärts-Rerouting" mehr** – beim Neuberechnen werden bereits passierte Wegpunkte jetzt auch über die Routen-Projektion abgehakt; vorher zielte die neue Route immer wieder auf denselben Punkt hinter dem Fahrer (Fahrt 2, konstant 0,9 km Rest).

## 01.001.094
- NEU (Navi): **Distanz zur nächsten Abbiegung gross links im Banner**, automatisch in m bzw. km – live mitzählend.
- NEU (Navi): **„Reroute-Log teilen"** im Ebenen-Menü – die interne Logdatei der Neuberechnungen lässt sich fürs Debriefing per Teilen-Dialog exportieren.

## 01.001.093
- GEÄNDERT (Navi, Feldtest 15.07.): **Ansage-Timing grundlegend überarbeitet** – Befund „das Navi ist immer zu spät" bestätigt und behoben:
  - **Meter-Countdown im Anweisungs-Banner** („In 140 m", zählt live runter) – bisher stand die Anweisung ohne jede Distanzangabe da.
  - **Banner schaltet erst weiter, wenn die Abbiegung tatsächlich gefahren ist** (vorher sprang es schon bei der Ansage auf die ÜBERNÄCHSTE Anweisung – an der Kreuzung stand die falsche Anweisung).
  - **Kettenmanöver:** Folgt die nächste Abbiegung dichter als ~150 m, wird sie mit angesagt („… – danach sofort: rechts auf Käsereistrasse") und im Banner als zweite Zeile angezeigt. Vorher entfiel die Vorwarnung bei kurzen Abständen ersatzlos (Härtefall Rickenstrasse/427: nur 2–4 s Vorlauf).
  - **Vorwarnung zeitbasiert** (~20 s Fahrzeit vor dem Manöver statt starrem 60–300-m-Fenster), finale Ansage mit ~6,5 s Vorlauf (mind. 60 m, vorher 5 s/45 m).
  - **„Ziel erreicht" ehrlicher:** zusätzlich zur Luftlinie muss der Rest ENTLANG der Route klein sein (Fahrt 2 meldete Ankunft bei real ~300 m Reststrecke).
  - Kosmetik: Komma-Artefakt in Anweisungen („Rickenstrasse, ab") bereinigt.
- NEU (Profil/Navi): **„Meine Orte" – Heim- und Arbeitsadresse** (Nutzerwunsch 15.07.). Im Profil einmal festlegen (Adresssuche oder aktuelle Position); im Navi erscheinen **Schnellwahl-Knöpfe „Heim"/„Arbeit"** in der Zieleingabe – ein Tipp setzt das Ziel und rechnet die Route. Gespeichert im Cloud-Profil (folgt auf jedes Gerät); Server-Schema Abschnitt 33.
- NEU (Profil): **„Passwort ändern"** direkt im Profil (bisher nur über den Umweg „Passwort vergessen"). Dasselbe Grevo-Konto (und damit dasselbe Passwort) gilt in der App und künftig auf der Website.

## 01.001.092
- NEU (Touren): **Geplante Touren zeigen jetzt ebenfalls Kennzahlen und ein Höhenprofil** (Nutzerwunsch 14.07.) – beim Speichern einer Tour werden Distanz und geschätzte Fahrzeit der berechneten Route mitgespeichert, dazu ein Höhenprofil entlang der Route. Die Liste zeigt die Kennzahlen-Zeile; Antippen öffnet eine Detail-Seite mit Höhenprofil und den Aktionen **Tour laden / Umbenennen / Löschen**.
- NEU (Touren): Für ÄLTERE Touren ohne Kennzahlen gibt es in der Detail-Seite den Knopf **„Kennzahlen berechnen"** (eine Routen-Berechnung + Höhen-Abfrage, danach dauerhaft gespeichert).
- SERVER: Neue Edge Function **`hoehe`** (JWT-geschützt, max. 100 Punkte; Quelle Open-Meteo/Copernicus – die App spricht keinen Drittanbieter direkt an); Tabelle `touren` um distanz_m/dauer_s/hm_auf/hm_ab/hoehen_track erweitert (schema.sql Abschnitt 32).

## 01.001.091
- NEU (Start): **Persönliche Begrüssung** – wer beim App-Start schon angemeldet ist, wird auf der Startmaske mit „Willkommen, {Name}!" empfangen (in allen 5 Sprachen).
- GEÄNDERT (Touren): **„Geplante Touren" ist jetzt der erste Reiter** der Touren-Übersicht (Nutzerwunsch: davon gibt es aktuell deutlich mehr als Aufzeichnungen).
- GEÄNDERT (Start/Profil): **„Abmelden" von der Startmaske ins Konto/Profil verschoben** (Nutzer-Befund 14.07.: der Knopf oben rechts wurde ständig versehentlich getroffen → jedes Mal neu anmelden). Die App verlässt man einfach mit der Home-/Zurück-Taste – dafür braucht es kein Abmelden. Im Profil steht „Abmelden" jetzt über „Konto löschen".

## 01.001.090
- NEU (Start): **Konto/Profil direkt auf der Startmaske** (Nutzerwunsch 14.07.) – oben links ein Konto-Knopf (Gegenstück zum Abmelden oben rechts). Das Profil bündelt inzwischen Einstellungen für BEIDE Teile (Körpergewicht fürs Navi, Abo & Pakete, Abrechnung, Ansagen, Sprache, Design) und ist damit nicht mehr nur über den Sprechfunk-Teil erreichbar.

## 01.001.089
- FIX (Profil): **Körpergewicht wird jetzt auch ohne den Haken-Knopf gespeichert** (Nutzer-Befund 14.07.: Eingabe ging verloren, wenn man nur tippte und die Seite verliess) – gespeichert wird zusätzlich bei „Fertig" auf der Tastatur und automatisch beim Verlassen des Eingabefelds (nur wenn sich der Wert geändert hat).
- Hinweis (Touren): Die leere Aufzeichnungs-Liste nach dem Update ist richtig – frühere Aufzeichnungen wurden nur als GPX-Datei geteilt und nirgends gespeichert. Ab jetzt landet jede aufgezeichnete Fahrt dauerhaft in der Touren-Übersicht (mit Kennzahlen und Höhenprofil).

## 01.001.088
- NEU (Start): **„Abo & Pakete" direkt auf der Startmaske** (Nutzerwunsch 14.07.) – unter den zwei Auswahl-Knöpfen Sprechfunk/Navi liegt jetzt ein schlanker dritter Knopf (dezenter Panel-Stil mit grauem Rand), der die Abo-Seite öffnet. Der bisherige Weg über das Profil bleibt bestehen.

## 01.001.087
- NEU (Touren): **Touren-Übersicht als GANZE SEITE** (Nutzerwunsch Feldtest 13.07.) – Lesezeichen-Knopf im Navi öffnet jetzt eine volle Seite mit zwei Reitern: **Aufzeichnungen** (gefahrene Touren) und **geplante Touren**. Pro Aufzeichnung: Kennzahlen (km, Gesamtzeit, reine Fahrzeit, Ø-Tempo, Höhenmeter rauf/runter, Kalorien), **Höhenprofil-Grafik**, dazu **Umbenennen, Teilen (GPX mit Höhe+Zeit), Löschen** (doppelte Sicherheitsabfrage) und **„Nachfahren"** (lädt die Spur mit Ansagen ins Navi). Geplante Touren: Laden/Umbenennen/Löschen + „aktuelle Route speichern". Das alte kleine Touren-Fenster unten ist ersetzt.
- NEU (Statistik): Die Aufzeichnung schreibt pro Punkt jetzt **Zeit, Höhe und Tempo** mit; am Ende werden die Kennzahlen berechnet (reine Fahrzeit = Bewegung >2 km/h; Höhenmeter geglättet mit 3-m-Hysterese; **Kalorien für Rad/E-Bike/Wandern** nach Körpergewicht – E-Bike deutlich tiefer wegen Motor, Töff/Auto ohne). Aufzeichnungen liegen neu in der **Cloud** (Tabelle `aufzeichnungen`, nur eigene sichtbar); ohne Netz am Tour-Ende wird **lokal gepuffert** und beim nächsten Öffnen der Touren-Seite automatisch nachgereicht.
- NEU (Profil): **Körpergewicht**-Feld (nur für die Kalorien-Schätzung; Spalte `profiles.gewicht_kg`).
- NEU (Abo): **„Abo & Pakete"-Seite im Profil** – Stufen-Vergleich Free/Pro/Mega (Preise live aus `plan_tiers`, Store-Preise sobald verfügbar), Monat/Jahr-Umschalter, die drei **Minuten-Blöcke Basis/Plus/Maxi**, Pflicht-Knopf **„Käufe wiederherstellen"**, „Abo im Store verwalten", Rechts-Hinweise. **RevenueCat ist voll integriert** (`purchases_flutter`, Kauf-Identität = Supabase-User-ID): Solange die API-Keys in `app_config.dart` leer sind, sind Käufe app-seitig AUS („noch nicht freigeschaltet") – gefahrlos auslieferbar. Kauf-Verbuchung passiert NUR serverseitig.
- SERVER (sofort aktiv): Tabelle `aufzeichnungen` + `profiles.gewicht_kg` (schema.sql Abschnitt 30); **Edge Function `revenuecat-webhook`** deployed + RPCs `rc_set_tier`/`rc_block_gutschrift`/`rc_touch_account` (Abschnitt 31, idempotent über `rc_events`/`purchases.store_tx`). Offen fürs Scharfschalten: RevenueCat-Konto + Store-Produkte + Keys (siehe RevenueCat-Setup-Checkliste.md).

## 01.001.086
- NEU (Navi, Feldtest 14.07. B6): **Weiches Zwischenziel** – ein Zwischenziel, an dem man nur „irgendwo vorbeifahren" will (Rieden-Fall), gilt jetzt auch als passiert, wenn man ihm einmal auf unter ~250 m nahe war und sich wieder entfernt, ODER wenn man es weiträumig umfährt (Distanz wächst anhaltend, während das nächste Ziel näher kommt). Ansage „Zwischenziel übersprungen", danach wird sofort ab der Fahrtposition zum nächsten Ziel neu gerechnet. Vorher zwang jede Neuberechnung zurück zum Punkt („Rückwärts-Rerouting", Rest-km stieg im Test von 6,0 auf 8,8 km statt zu sinken).
- NEU (Navi, Feldtest 14.07. C8): **Neuberechnungs-Drosselung mit Backoff** – zwischen zwei Reroute-Versuchen liegen jetzt mindestens 10 s (nach Fehlversuchen 20/30/40 s) und ~50 m Fahrt. Vorher feuerte die Neuberechnung im Sekundentakt aufs Tages-Kontingent (14.07.: 92 Routen an einem Vormittag).
- NEU (Navi, Feldtest 14.07. C9): **Reroute startet in Fahrtrichtung** – der Startpunkt der Neuberechnung wird ~25 m entlang der Fahrtrichtung vorgezogen und die Fahrtrichtung zusätzlich an den Server übergeben (der Ausweich-Router nutzt sie direkt). Vorher begann die neue Route oft rückwärts/quer zur Fahrt („reroutete nie in Fahrtrichtung").
- FIX (Navi, Feldtest 14.07. C10): **Serpentinen-Schutz** – das Verfahren-Kriterium „Fahrtrichtung weicht stark ab" (v085/P1) zählt nur noch, wenn auch ein Querabstand von über 25 m zur Route besteht. Auf Haarnadelkurven (Käserei-/Bergstrasse) lag der nächste Routenpunkt sonst auf dem Nachbar-Ast mit Gegenrichtung → Fehlalarm trotz korrekter Fahrt.
- NEU (Navi, Feldtest 14.07. D11): **Störungs-Hinweis statt stummem Blinken** – schlagen Neuberechnungen wiederholt fehl, sagt die App EINMAL „Routendienst nicht erreichbar – ich versuche es weiter" und zeigt den Hinweis rot im Navi-Panel, bis eine Neuberechnung wieder gelingt. Vorher blinkte der Pfeil bis zu 5 Minuten rot, ohne dass erkennbar war warum.
- NEU (Navi, Feldtest 14.07. E13): **Reroute-Logdatei** – jedes Off-Route-Ereignis und jede Neuberechnung (Auslöser, Router-Quelle ORS/Ausweich/Offline, Dauer, Rest-km, Fehler) wird in `navi_reroute_log.txt` (App-Dokumente) protokolliert – fürs Debriefing nach dem Feldtest.
- SERVER (Edge-Function `route` v10, wirkt sofort ohne App-Update): (A1) Ein ORS-„Punkt nicht routbar"-Fehler (4xx) geht jetzt ebenfalls an den Ausweich-Router, statt die App ohne Route stehen zu lassen (14.07.: 5 Minuten ohne Weg im Wald oberhalb Rieden). (A2) Fahrtrichtung wird an den Ausweich-Router durchgereicht (Reroute in Fahrtrichtung). (A3) Kürzere Zeitlimits bei Neuberechnungen (ORS 4 s statt 10 s, Ausweich 1×8 s statt 2×15 s). (A4) Nach 2 ORS-Ausfällen in Folge wird ORS 5 Minuten übersprungen und direkt der Ausweich-Router gefragt. (A5) Ausweich-Router-Radprofil angeglichen (Hybrid-Rad; E-Bike meidet Steigungen kaum mehr) → weniger Schleifen-Umwege.

## 01.001.085
- FIX (Navi, Feldtest 13.07. P1): **Verfahren auf Parallelwegen wird jetzt schnell erkannt.** Bisher griff nur der Querabstand (>60 m) – lief der falsche Weg nahe der Route entlang, stand die Führung minutenlang still (2× im Test). Neu lösen zwei Zusatz-Kriterien die Neuberechnung aus: (a) Fahrtrichtung weicht mehrere Sekunden stark (>60°) von der Routen-Richtung ab, (b) es geht entlang der Route nicht voran, obwohl man fährt (~12 s). Dazu wird die **Rest-km/Ankunfts-Anzeige eingefroren**, solange die Route verlassen ist (zählte vorher die weggefahrene Strecke hoch).
- FIX (Navi, Feldtest 13.07. P2): **„Ziel erreicht" kommt jetzt auch, wenn die Route noch ums Gebäude führen würde** – die Ankunft wird zusätzlich per Luftlinie erkannt (<20 m, oder <40 m bei unter 8 km/h). Rundkurs-Schutz: erst 90 s nach dem Start aktiv.
- FIX (Ansagen, Feldtest 13.07. P5): Klammerzusatz der Ankunfts-Ansage entfernt („Ziel erreicht (geradeaus)" → „Ziel erreicht").
- GEPRÜFT (Musik): Solo-Ansagen laufen bereits mit Navigations-Audiofokus („darf ducken") – Spotify & Co. sollten im Solo-Navi bei jeder Ansage automatisch leiser werden. Das „gekesselte" Musik-Klangbild betrifft den Sprechfunk-Modus (Bluetooth wechselt ins Telefonie-Profil) und ist dort systembedingt; Punkt bleibt in der Auftragsliste.

## 01.001.084
- GEÄNDERT (Navi): **Maximaler Zoom an Verzweigungen** (Nutzerwunsch Feldtest 13.07.) – bei Annäherung an eine Abbiegung/Verzweigung (<180 m) zoomt die Karte jetzt auf die grösstmögliche Stufe (19 statt 18), damit alle Nebenstrassen exakt erkennbar sind. Nach dem Manöver geht es automatisch zurück in den tempo-gesteuerten Zoom.

## 01.001.083
- NEU (Navi): **Karten-Ausrichtung wird dauerhaft gemerkt** (Nutzerwunsch Feldtest 13.07., Prio 1) – wer „Fahrtrichtung oben“ wählt, behält diese Ansicht bis zur nächsten manuellen Änderung: auch nach dem Neuladen einer Route und nach dem Schliessen/Neustarten der App. Gilt ebenso für „Norden oben“ (auch per Kompass-Tipp). Gespeichert pro Gerät.

## 01.001.082
- NEU (Navi): **Roter Blink-Pfeil bei verlassener Route** (Feldtest 13.07. Uznach) – verlässt man die Route bzw. läuft die Neuberechnung, wird der blaue Positionspfeil ROT und BLINKT; sobald man wieder auf der Route ist, wird er wieder blau. Gilt auch im Spur-Modus („Strecke verlassen“).
- GEÄNDERT (Aufzeichnung): **Speicher-Meldung ohne „Teilen“-Knopf und mit sicherem Ausblenden** (Feldtest 13.07.: die Meldung blieb minutenlang stehen und verdeckte die Bedienung). Kürzere Anzeige (5 s) + aktives Wegräumen als Sicherheitsnetz. Umbenennen/Teilen gespeicherter Routen kommt später gesammelt in die Touren-Übersicht (siehe Auftrags-und-Testpunkte.md).

## 01.001.081
- FIX (Avatare): **GREVO-Schnecken-Avatar ohne weisse Rand-Segmente** – das Logo-Bild wurde bereinigt (weisser Hintergrund des abgerundeten Icons überall durch das Markenblau ersetzt, neues Asset `grevo_avatar.png`). Der runde Avatar ist damit auch auf hellem Grund durchgehend dunkelblau.

## 01.001.080
- GEÄNDERT (Design): **GREVO-Farbmodus zeigt jetzt IMMER das dunkle Splash-Design** – auf allen Masken (Sprechteil, Gruppen, Profil, Abfragen), unabhängig von Hell/Dunkel/System (die Umschaltung wirkt nur noch bei den anderen Farben; Hinweis im Profil). Die App-Akzentfarben sind für GREVO auf die Splash-Werte gemappt: Akzente = Cyan, Beschriftungen = Hellblau – damit sehen auch Sprechfunk-Maske und Gruppenlisten wie die Startseite aus.
- NEU (Profil): **Farbmodus-Auswahl als Liste (Combobox) mit Farbpunkt + Name** statt Farbkreisen; an erster Stelle „GREVO – Standard“ mit dunkelblauem Punkt und Cyan-Rand.
- NEU (Avatare): **GREVO-Schnecken-Avatar (App-Logo) an erster Stelle** bei den Vorgabe-Avataren für BENUTZER und GRUPPEN; Gruppen ohne eigenes Bild zeigen jetzt standardmässig die Schnecke.
- FIX (Kontrast): Gefüllte Knöpfe im Sprechteil (Privat beenden, Sparmodus aktiv) wählen die Schriftfarbe jetzt passend zur Helligkeit der Füllfarbe.

## 01.001.079
- GEÄNDERT (Ansagen): **Kleine „Schlenker“ werden nicht mehr als Abbiegen angesagt** (Feldtest 08.07.: Wechsel Radstreifen ↔ Trottoir-Radweg auf der Hauptstrasse kam 2× als „Biegen Sie links ab“). Ist die tatsächliche Richtungsänderung am Manöverpunkt klein (<35°, gemessen ~18 m davor/danach), sagt die App jetzt **„Leicht links/rechts halten“** (sanftes Symbol) statt eines vollen Abbiegers.

## 01.001.078
- GEÄNDERT (Ansagen): **„Wegpunkt X erreicht“ wird nicht mehr angesagt** (Feldtest: verwirrt). Wegpunkte werden weiter still abgehakt; am Wegpunkt kommt nahtlos die nächste Abbiege-Ansage. (Geprüft: Der Namens-Dialog im Testvideo kam automatisch vom System bei „Ziel erreicht“ – keine Fehlbedienung.)
- GEÄNDERT (Aufzeichnung): **Am Ziel erscheint GAR KEIN Dialog mehr** (automatische Dialoge sind beim Auto-/Radfahren gefährlich). Die Aufzeichnung wird automatisch benannt und gespeichert; es erscheint nur eine Snackbar (8 s, verschwindet von selbst) mit optionalem „Teilen“-Knopf.

## 01.001.077
- GEÄNDERT (Design): **GREVO-Dunkel jetzt 1:1 wie der Splash-Screen** (Nutzer-Feedback: das erste Blau traf den Splash nicht). Eigenes, komplettes Theme statt Material-Seed: Hintergrund #0B1220, Panels #1A2433, ALLE Knöpfe als leicht aufgehellte dunkle Panels (#223146) mit hellerem Cyan-Rand und hellblauer (Cyan-)Schrift – exakt die Optik der zwei Auswahl-Buttons auf der Startseite. Auch Dialoge, Blätter, Snackbars, FABs und AppBar in den Splash-Flächenfarben; Haupttext #EAF2FB, Sekundärtext #8B98A9.

## 01.001.076
Feldtest-Feinschliff (Videofahrt 08.07. nachmittags) + Fahrzeugart-Kontrolle:
- NEU (Start): **Fahrzeugart-Kontrolle vor dem Start** – beim Tipp auf „Starten“ fragt die App „Mit Fahrrad starten?“ (Symbol + Name der gewählten Fahrzeugart). „Ändern“ bricht ab, damit man das Profil oben umstellen kann – je nach Fahrzeugart fällt die Route anders aus.
- FIX (Timing): **Pfeil und Ansagen laufen der Realität nicht mehr hinterher.** GPS kommt ~1–2 s verzögert an; die Anzeige-Position wird jetzt um Tempo × 1,5 s ENTLANG der Route vorgehalten, die Ansage-Distanzen messen ab dort. Zusätzlich wächst die Schwelle der finalen Abbiege-Ansage mit dem Tempo (min. 45 m, ~5 s Vorlauf, max. 120 m).
- GEÄNDERT (Aufzeichnung): **Kein Namens-Dialog mit Tastatur mehr am Ziel.** Die Aufzeichnung wird automatisch benannt („Fahrt 08.07.2026 14-41“) und gespeichert; danach nur noch eine 1-Tipp-Frage „Aufzeichnung jetzt teilen?“ (Ja/Nein).

## 01.001.075
- NEU (Design): **Die ganze App kommt standardmässig im Splash-Design (GREVO Brand Kit v2)**: neue Standard-Palette „GREVO“ (Blau #0EA5FF / Cyan, dunkler Hintergrund #0B1220, Panels #1A2433, graue Sekundärtexte) und Standard-Modus **Dunkel**. Alle bisherigen Farben (Pink, Blau, Grün, Orange, Violett, Rot) und Hell/Dunkel/System bleiben im Profil **umschaltbar**; wer früher schon eine Farbe gewählt hat, behält seine Wahl.
- NEU (Schrift): **Poppins ist jetzt als App-Schrift gebündelt** (Regular/Medium/SemiBold/Bold, assets/fonts) und überall aktiv – wie im Splash und im Styleguide.

## 01.001.074
- NEU (Heimweg): Bei **„Zurück zum Start“** werden die **Rückkehrpunkte jetzt als eigene Kreise angezeigt** – fortlaufend weiternummeriert (bei 26 Hinweg-Punkten also 27, 28, 29 …), leicht versetzt und in Blau, damit an derselben Stelle beide Nummern lesbar bleiben. Die letzte Nummer sitzt am Ziel des Heimwegs (= Startpunkt). Gilt für „Gleicher Weg“ voll; bei „Nächster/Anderer Weg“ erscheinen nur Punkte, die der Rückweg tatsächlich berührt. Reine Anzeige – am Routing ändert sich nichts.

## 01.001.073
- NEU (Ansagen): **„Folgen Sie der Strasse für X Kilometer“ kommt jetzt auch beim START der Navigation und nach jeder NEUBERECHNUNG** (bisher nur nach einer Abbiegung). Ausgelöst, wenn das nächste Manöver mehr als 600 m entfernt ist.
- FIX (Ansagen): Ansagen laufen jetzt in einer **Warteschlange nacheinander** – zwei kurz aufeinanderfolgende Ansagen (z.B. Abbiege-Ansage + „Folgen Sie …“) schnitten sich vorher gegenseitig ab.

## 01.001.072
Feldtest-Korrekturen Fahrrad 08.07. (Navi) + Solo-Ansage-Boost:
- NEU (Pfeil): **Der Positionspfeil „klebt“ jetzt auf der Route** – er wird auf die Routenlinie projiziert und zeigt in Richtung der Route (reagiert sofort, kein träges GPS-Heading mehr). Erst wenn das System das Verlassen der Route feststellt (→ Neuberechnung), springt er auf die echte GPS-Position zurück.
- FIX (Wegpunkte): **Die Navigation schaltete sich am ersten Wegpunkt ab.** ORS liefert pro Teilstrecke ein „Ziel erreicht“ (Typ 10) – das beendete die Navigation schon am 1. Wegpunkt; danach „verlor“ sich das System. Zwischen-Ankünfte werden jetzt übersprungen; stattdessen sagt die App „Wegpunkt X erreicht“ und führt weiter bis zum echten Ziel.
- FIX (Ansagen): **Verpasste Manöver blockieren nicht mehr.** Wurde ein Abbiegepunkt ohne 45-m-Ansage passiert (GPS-Lücke, abgekürzte Ecke), blieben alle folgenden Ansagen am alten Ort hängen. Jetzt wird anhand des Fortschritts AUF der Route automatisch zum nächsten Schritt weitergeschaltet.
- FIX (Neustart unterwegs): **Start mitten auf der Runde führt nicht mehr zurück zu Wegpunkt 1.** Beim Nav-Start werden bereits passierte Wegpunkte erkannt (Projektion auf die geplante Route) und ab dem nächsten Punkt in Fahrtrichtung geroutet – die Ansage „an einer ganz anderen Strasse“ ist damit behoben.
- FIX (Rundkurs): Bei Neustart/Neuberechnung unterwegs endete ein Rundkurs an der AKTUELLEN Position statt am Start. Das Rundkurs-Ende wird jetzt bei der Planung fixiert.
- NEU (Lautstärke): **Verstärkungs-Boost für Solo-Navi-Ansagen** (100–400 %, Standard 250 %) im Lautsprecher-Blatt – wie der Empfangs-Boost im Sprechfunk. Die Ansage-Datei wird per Software verstärkt (sanfte Begrenzung, kein Übersteuern); Solo-Ansagen sind damit so laut wie im Kombi-Modus.

## 01.001.071
- GEÄNDERT (Karte/Datenschutz): **EU-Endpunkt aktiviert** (`tiles-eu.stadiamaps.com`, Server Frankfurt/Paris) — Kachel-Anfragen verlassen die EU nicht mehr. Passt zur Datenhaltungs-Story (Supabase Zürich, Brevo EU, Agora EU).
- GEÄNDERT (Karte): Alle Stile jetzt bis **Zoom 20** (laut Stadia-Doku auch Satellit).
- GEÄNDERT (Karte): Attributions-Wortlaut exakt nach Stadia-Vorgabe (Satellit: „© CNES, Distribution Airbus DS, © Airbus DS, © PlanetObserver (Contains Copernicus Data)" zusätzlich zu Stadia/OpenMapTiles/OSM); Domains im ⓘ-Dialog mit angegeben.
- Hinweis: Durch den Endpunkt-Wechsel wird der Offline-Kachel-Cache **einmalig geleert** (Testdaten von heute neu herunterladen).

## 01.001.070
- GEÄNDERT (Karte): Attribution jetzt als **ⓘ-Knopf neben dem Nordpfeil** – gleiche Grösse/Optik (weisser runder Knopf), gut erkennbar. Tipp öffnet „Kartendaten" mit den Quellen (Stadia Maps, OpenMapTiles bzw. Satellit-Quellen, © OpenStreetMap contributors).

## 01.001.069
- FIX (Karte): Das **Attribution-Info-Symbol war verdeckt** (sass unter dem Routen-Panel/den Zoom-Knöpfen). Jetzt sichtbar links unten, neben dem Nordpfeil-Knopf, oberhalb des Panels.

## 01.001.068
- GEÄNDERT (Karte): **Kartenkacheln kommen jetzt von Stadia Maps** statt OpenStreetMap/OpenTopoMap/ArcGIS (Standard→OSM Bright, Topo→Outdoors, Satellit→Alidade Satellite). Grund: OSM-Tile-Policy erlaubt kein Offline-Caching (Launch-Blocker). API-Key in `app_config.dart`.
- NEU (Karte): **Pflicht-Attribution** unten rechts auf der Karte (einklappbar): Stadia Maps, OpenMapTiles, © OpenStreetMap contributors; beim Satellit zusätzlich CNES/Airbus/PlanetObserver.
- GEÄNDERT (Offline-Karten): FMTC-Cache-Schlüssel **ohne api_key** (`obscuredQueryParams`) – ein späterer Key-Wechsel entwertet den Offline-Cache nicht. Beim ersten Start wird der alte OSM-Kachel-Cache **einmalig geleert** (neu herunterladen nötig).

## 01.001.067
- FIX (Touren/Offline): Im **Flugmodus/Funkloch** zeigte das Touren-Blatt eine rohe Netzwerk-Fehlermeldung. Jetzt kommt ein freundlicher Hinweis „Keine Internetverbindung – gespeicherte Touren liegen online". Betrifft Laden, Speichern und Schnell-Speichern.

## 01.001.066
Feldtest-Korrekturen (Navi) + Offline-Routing-Gerüst:
- FIX (Ansage/Solo): **Ansagen ohne Sprechverbindung jetzt hörbar.** Solo werden sie als Sprachdatei synthetisiert und mit **Navigations-Audio-Kontext** abgespielt – so landen sie am aktiven Ausgang (z.B. Bluetooth im Auto), statt evtl. stumm auf dem Medien-Kanal zu bleiben (Rückfall auf System-Stimme). Neues Paket `audioplayers`.
- FIX (Pfeil): In **Fahrtrichtung-oben** zeigte der Positionspfeil falsch – die Kartendrehung wurde doppelt gerechnet. Jetzt korrekt.
- NEU (Zoom): **Kurz vor Abbiegungen zoomt die Karte automatisch näher** heran (bessere Sicht auf den Abzweig), danach zurück zum Tempo-Zoom.
- FIX (Route): **Keine unnötige Neuberechnung mehr während der Fahrt.** Der Abstand zur Route wird jetzt zur Linie (nächstes Segment) gemessen statt nur zum nächsten Stützpunkt – dadurch keine „Bögen/Beulen" mehr; neu berechnet wird erst bei echtem Verlassen (>60 m, mehrfach).
- GEÄNDERT (Route-Linie): Während der Navigation wird nur noch der Teil **ab dem Fahrzeug bis zum Ziel** gezeichnet; der bereits befahrene Teil dahinter verschwindet (ohne Neuberechnung).
- NEU (Ansage): Nach einem Abbiegen kommt **„Folgen Sie der Strasse für X km/m"** bis zur nächsten Anweisung.
- GEÄNDERT (Bedienung): Der **Karten-Ausrichtungs-Knopf** (Nord/Fahrtrichtung) sitzt jetzt unten rechts bei den Zoom-Knöpfen statt oben.
- FIX (Ansage): **Hausnummer im Strassennamen entfällt** in der Ansage („Uznacherstrasse 17" → „Uznacherstrasse").
- NEU (Offline-Routing, Gerüst): rd5-Segment-Download + „Offline-Routing (Beta)" im Offline-Karten-Blatt und Offline-Fallback beim Neuberechnen – die eigentliche BRouter-Engine folgt.

## 01.001.065
- NEU (Navi/Offline · Teil 1): **Offline-Karten.** Über das Ebenen-Menü → „Offline-Karten …" lässt sich der aktuell sichtbare Kartenausschnitt herunterladen (Kachel-Cache, FMTC). So bleibt die Karte auch im **Funkloch** sichtbar. Anzeige des belegten Speichers + Löschen. (Der zweite Teil – **Offline-Routing/Neuberechnung ohne Netz** via BRouter – folgt.) Android + iOS.
- FIX (Datenschutz/Agora): **Medienverkehr an die EU/EMEA-Region gebunden** (`areaCode: areaCodeEu`). Vorher lief die Agora-Engine ohne Area-Code = global; jetzt bleiben Sprach-/Signalisierungs-Server in Europa (Datenresidenz).

## 01.001.064
- FIX (Navi): **Richtungspfeil zeigt jetzt in die Fahrtrichtung.** Die Richtung wird aus der tatsächlichen Bewegung (Strecke zwischen zwei GPS-Punkten) berechnet statt aus dem Geräte-/Kompass-Heading – das lag im Auto (Metallkarosserie) oft falsch. Der Pfeil stimmt jetzt zuverlässig mit der Karte überein.
- GEÄNDERT (Navi/Zoom): **Näher herangezoomt während der Fahrt**, Strassen deutlich besser erkennbar. Weiterhin tempoabhängig (schnell = etwas weiter raus).
- GEÄNDERT (Navi/Ansage): **„Route wird neu berechnet" nur noch EINMAL** beim Verlassen der Route statt bei jeder Neuberechnung. Erst wenn man wieder auf der Route ist, darf ein erneutes Verlassen wieder einmal ansagen.
- FIX (Navi/Reroute): **Neuberechnung auf den in Fahrtrichtung NÄCHSTEN Wegpunkt.** Bereits erreichte oder umfahrene Wegpunkte (die hinter der Fahrtrichtung liegen) werden übersprungen, statt zurück zu einem ausgelassenen Punkt zu leiten. Bei einer reinen Ziel-Route wird wie bisher vom aktuellen Standort neu aufs Ziel gerechnet. Die farbige Route wird dabei neu gezeichnet.
- NEU (Navi): **Bildschirm bleibt an, solange navigiert wird** (ab „Start") – kein Schlafmodus mehr, das Navi bleibt sichtbar. Nach „Beenden" darf das Gerät wieder normal in den Ruhezustand.

## 01.001.063
- GEÄNDERT (Sprechen): **Mikrofon-/Sende-Regler wieder entfernt.** Der Feldtest hat gezeigt, dass „alles zu leise" nicht am Aufnahme-Pegel lag, sondern an der Bluetooth-Kopplung (AirPods am Android: „Absolute Lautstärke deaktivieren" in den Entwickleroptionen löst es). Der Aufnahme-Pegel steht wieder fix auf 100 (kein Übersteuern bei Wind), der Sprech-Bildschirm bleibt schlank. Empfangs-Lautstärke (bis 1000 %) + Medien-Lautstärke-Anhebung bleiben. Android + iOS.

## 01.001.062
- NEU (Sprechen/Lautstärke): **Einstellbarer Mikrofon-/Sende-Pegel.** Zweiter Regler unter der Lautstärke (100–300 %, Standard 100). Hebt die eigene Stimme an der QUELLE an – das wirkt vor dem Limiter des Empfängers und macht eine leise Stimme wirklich lauter, was der reine Empfangs-Regler (Agora deckelt bei ~400–500 %) nicht schafft. Bei Windstille aufdrehen, bei Gegenwind zurück (zu hoch übersteuert). Beide neuen Versionen profitieren sofort; sobald die Gegenstelle updatet, auch dort. Pro Gerät gemerkt. Android + iOS.

## 01.001.061
- FIX (Sprechen/KRITISCH): **Mikrofon-Übertragung wieder hergestellt.** Die in v060 versuchte DTX-Abschaltung (`setParameters che.audio.codec.dtx`) legte im Feldtest die Sende-Übertragung auf BEIDEN Seiten lahm – wieder entfernt.
- FIX (Sprechen/Lautstärke): **Grundproblem „alles zu leise" behoben.** Beim Verbinden hebt die App jetzt die **Medien-Lautstärke des Geräts aufs Maximum** (und setzt sie beim Verlassen zurück). Das Audio läuft über den Medien-Kanal – stand dessen Lautstärke am Handy niedrig, war ALLES zu leise, egal was der In-App-Regler sagte. Zusätzlich koppelt der Regler jetzt auch die Signaltöne/Ansagen (absenkbar; 0 % = still).
- FIX (Netz-Ansage): **Keine falsche „Netzverbindung unterbrochen"-Ansage mehr**, wenn ein weiterer Teilnehmer der Gruppe beitritt oder ein Token erneuert wird. Die Ansage hängt jetzt nur noch am echten Funkloch-Signal (`onConnectionLost`).

## 01.001.060
- FIX (Sprechen/Lautstärke): **Gegenstelle deutlich lauter regelbar.** Der Wiedergabe-Regler geht jetzt bis **1000 %** statt 400 %. Bis 400 % läuft es wie bisher über den globalen Agora-Regler; DARÜBER kommt zusätzlich ein **Pro-Sprecher-Verstärker** (`adjustUserPlaybackSignalVolume`, bis 400 %) obendrauf – die beiden Faktoren multiplizieren sich. So wird auch eine sehr leise Gegenstelle (Partnerin auf altem Stand 1.1.16, Gegenwind/Schotter) verständlich laut, ohne den Aufnahme-Pegel zu erhöhen (der übersteuert bei Wind). Wirkt auf alle Teilnehmer und auch auf neu Dazukommende. Android + iOS.
- FIX (Sprechen/Anfang): **Erste Silbe geht beim Losreden nicht mehr verloren.** DTX (Discontinuous Transmission) abgeschaltet – der Codec pausierte bei Stille und brauchte beim Sprechbeginn einen Moment zum Hochfahren, dabei wurde der Anfang verschluckt („Gegenüber versteht meinen Anfang nicht"). Jetzt sendet er durchgehend, der Sprechbeginn kommt sofort sauber an. Android + iOS.
- NEU (Sprechen): **Netz-Ansagen.** Bricht die Verbindung unterwegs weg (Funkloch), sagt die App **„Netzverbindung unterbrochen"**, bei der Wiederkehr **„Netzverbindung wieder vorhanden"** – als Sprach-Clip lokal abgespielt (auch ohne Netz hörbar), 5 Sprachen, jede Ansage nur einmal je Zustandswechsel. Android + iOS.
- DESIGN (Startbildschirm): Der **Sprechfunk-Knopf** ist jetzt gleich gestaltet wie der Navi-Knopf (dunkles Panel mit Cyan-Rand) statt blau gefüllt – beide Knöpfe wirken einheitlich. Android + iOS.
- FIX (Navi): **Navigation hängt nicht mehr am Start.** Beim Navi-Start/Neustart wird die Route jetzt **ab der aktuellen Position** frisch berechnet, statt eine früher (an anderem Ort) berechnete Route ab Schritt 0 abzuspielen. Damit kommen die Anweisungen von dort, wo man WIRKLICH ist – auch nach mehreren gefahrenen Kilometern oder einem Neustart. (Nur bei Wegpunkt-Planung; GPX-Tracks bleiben unverändert.) Android + iOS.

## 01.001.059
- GEÄNDERT (Navi): **„Zurück zum Start" fragt jetzt den Rückweg-Modus ab** (Auswahl-Menü statt automatischer Erkennung): **Nächster Weg zum Start** (direkt/kürzeste), **Anderer Weg (Hinweg meiden)**, **Gleicher Weg ab gemeinsamem Punkt** (Hinweg rückwärts; liegt der letzte Punkt auf einem früheren, ab dort). Zuverlässiger als die frühere Auto-Erkennung.
- NEU (Navi): **„Zurück zum Start" auch direkt im unteren Feld** sichtbar, sobald eine Route mit mindestens zwei Punkten steht (nicht mehr nur im Wegpunkt-Blatt).

## 01.001.058
- FIX (Navi): **Das ✕ neben „Spur nachfahren" entfernt jetzt wirklich die geladene Spur.** Vorher reagierte es nicht (es rief die Wegpunkt-Löschung auf, die es bei einem GPX-Track ohne Wegpunkte gar nicht gibt).
- NEU (Navi): **„Zurück zum Start" (Heimweg).** Im Wegpunkt-Blatt gibt es einen Knopf, der einen Rückweg anhängt. Zwei Fälle automatisch: liegt der **letzte Punkt auf einem früheren Punkt**, wird ab diesem gemeinsamen Punkt der Hinweg **exakt rückwärts** zum Start gefahren; sonst eine **Rundfahrt über einen anderen Weg** (der Hinweg wird beim Routing gemieden). Fällt kein anderer Weg, wird der normale Rückweg genommen.

## 01.001.057
- FIX (Navi-Editor): **Vorläufiger Punkt liegt jetzt ÜBER den bestehenden Punkten.** Setzt man einen neuen Punkt auf einen vorhandenen (z. B. der Hinfahrt), war er vorher verdeckt – jetzt wird er zuoberst gezeichnet und lässt sich besser kontrollieren.

## 01.001.056
- NEU (Navi): **Zoom-Knopf mit 3 Modi.** Der Knopf schaltet reihum: **Tempo** (folgt der Fahrt) → **Start ↔ Ziel** → **ganze Route**. Der dritte Modus zeigt die komplette Strecke im Bild – wichtig bei **Rundfahrten**, wo Start und Ziel am selben Ort sind. Der gewählte Modus wird kurz eingeblendet.
- NEU (Navi-Editor): **Markierungen nicht mehr verlieren.** Solange gesetzte Punkte noch nicht gespeichert sind, gibt es unten **„Rückgängig"** (nimmt die letzte Markierung zurück, mehrfach möglich) und **„Speichern"**. Verlässt man das Navi mit ungespeicherten Markierungen, fragt die App, ob **gespeichert**, **verworfen** oder **abgebrochen** werden soll.

## 01.001.055
- FIX (Navi): **Fahrzeug↔Ziel-Zoom reagiert jetzt sofort.** Vorher wirkte der Knopf erst beim nächsten GPS-Signal – im Stand also gar nicht. Jetzt passt die Karte beim Drücken direkt an (an = Fahrzeug + Ziel im Bild, aus = normaler Zoom).

## 01.001.054
- GEÄNDERT (Navi): **Beim Löschen einer Tour steht jetzt der Routenname in der Rückfrage** („Tour „XY" löschen?") – so sieht man vor dem Bestätigen genau, welche Tour betroffen ist.
- GEÄNDERT (Navi-Editor): **Zoom bleibt beim Setzen von Punkten erhalten** – die Karte springt nicht mehr auf die ganze Route zurück, sondern bleibt auf dem aktuellen Ausschnitt. (Die ganze Route einpassen macht weiterhin nur „Route berechnen".)
- NEU (Navi-Editor): **Punkt setzen mit Bestätigung.** Ein Karten-Tipp setzt den Punkt zunächst nur vorläufig (verschiebbar durch erneutes Tippen); mit dem großen **grünen ✓** am rechten Rand wird er übernommen, mit dem **roten ✗** verworfen. Verhindert Fehl-Punkte durch versehentliche Berührungen.
- NEU (Navi): **Zoom-Modus „Fahrzeug ↔ Ziel".** Während der Navigation optional umschaltbar (Knopf rechts): zeigt dauerhaft die eigene Position UND das Ziel im Bild. Standard bleibt der tempo-abhängige Auto-Zoom.

## 01.001.053
- FIX (Navi): **„Spur nachfahren"-Knopf erscheint jetzt auch bei geladener GPX-/aufgezeichneter Spur.** Vorher zeigte das untere Panel bei einem geladenen Track nur die Distanz + „Ziel entfernen" – der Start-Knopf fehlte. Jetzt steht dort **„Spur nachfahren"** (Ziel entfernen als kleines ✕ daneben).

## 01.001.052
- FIX (Navi): **Touren löschen jetzt mit doppelter Sicherheitsabfrage.** Beim Mülleimer im Touren-Blatt kam vorher gar keine Rückfrage – jetzt zwei Schritte („Diese Tour löschen?" → „kann NICHT rückgängig gemacht werden").
- FIX (Navi): **Bedienknöpfe werden nicht mehr vom Suchfeld verdeckt.** Zoom, Zentrieren und Kompass sitzen jetzt dynamisch immer knapp über dem unteren Panel (Adress-Suche/Route/Navi), egal wie hoch es gerade ist.
- GEÄNDERT (Navi): **Dauer über 60 Minuten in Stunden + Minuten** (z. B. „1 Std 35 min" statt „95 min").

## 01.001.051
- NEU (Navi): **Aufgezeichnete/importierte Spur nachfahren – mit Sprachführung (Variante A).** Eine als GPX geladene Strecke lässt sich jetzt mit dem Knopf **„Spur nachfahren"** navigieren. Die Abbiege-Ansagen („links abbiegen", „leicht rechts halten", „bitte wenden" …) werden aus der Form der aufgezeichneten Linie erzeugt – der Weg bleibt exakt der Originalweg, es wird **nicht** über Strassen neu berechnet.
- NEU (Navi): **Bei Verlassen der Spur** kommt die Ansage „Aufzeichnung verlassen – {n} m zurück zur Strecke"; bei Rückkehr auf die Linie „Wieder auf der Strecke". Es wird bewusst **keine** neue Route berechnet (du wirst zurück auf die Originalspur geführt).

## 01.001.050
- FIX (Navi/Kombi): **Navi-Ansage jetzt so laut wie die Gespräche.** Läuft parallel ein Sprechfunk, wird die Ansage jetzt als kurze Sprachdatei ÜBER die Agora-Verbindung abgespielt (playEffect) – damit gilt dieselbe Wiedergabe-Lautstärke (bis 400 %) wie für die Gesprächsstimmen, und die Ansage wird im Anruf nicht mehr gedämpft. (Fallback auf System-Stimme + Ducking, falls die Sprachdatei nicht erzeugt werden kann.)
- Hinweis (Tablet): fehlte die Navi-Stimme, weil keine Standard-Sprachausgabe gesetzt war – Google-TTS ist jetzt als Standard gesetzt (ggf. deutsche Stimme in den Einstellungen laden).

## 01.001.049
- FIX (Navi): **Navi-Ansage lauter.** Beim reinen Navigieren war die gesprochene Ansage auch bei 100 % zu leise (durch die Medien-Lautstärke gedeckelt). Jetzt wird die Medien-Lautstärke für die Dauer der Ansage automatisch aufs Maximum gehoben und danach wieder auf den vorherigen Wert gesetzt.

## 01.001.048
- FIX (Design): **App-Icon ohne weissen Rahmen.** Adaptives Android-Icon (dunkler Hintergrund #0A121D + freigestelltes Logo im Vordergrund) statt der Kachel auf weissem Grund – so füllt das Icon die Launcher-Form randlos. Alt-Icons ebenfalls auf vollflächig dunkel umgestellt.

## 01.001.047
- NEU (USP): **Navi + Sprechfunk gleichzeitig.** In einer Gruppe gibt es unten einen **3-Wege-Umschalter: Sprechen · Navi · Geteilt**. Die Sprechverbindung bleibt beim Wechsel zum Navi bestehen (beide laufen parallel), „Geteilt" zeigt beide halb/halb. Das Navi startet erst, wenn man es zum ersten Mal öffnet.
- NEU: **Navi-Ansagen legen sich sauber über das Gespräch** – während einer Ansage wird die Partnerstimme kurz abgesenkt (Ducking), danach wieder normal.
- NEU (Punkt 1): **Navi-Ansage-Lautstärke regelbar** (Lautsprecher-Symbol im Navi → Regler 0–100 % + Stumm-Schalter, pro Gerät gemerkt).
- GEÄNDERT (Punkt 2): **Wegpunkte „Alle löschen" jetzt mit doppelter Sicherheitsabfrage** (wie bei Gruppe/Konto).
- GEÄNDERT (Design): **Neues App-Icon** (GREVO v2, Schnecke + Mikrofon) auf Android und iOS.

## 01.001.046
- NEU (Design): **Startseite ist jetzt ein Marken-Splash** (GREVO Brand Kit v2) – dunkler Hintergrund mit Logo und Claim, die zwei Auswahl-Buttons **„Sprechfunk"** und **„Navi"** kompakt nebeneinander im unteren Bereich (Sprechfunk gefüllt im Blau→Cyan-Verlauf, Navi als Panel mit Cyan-Rand).
- GEÄNDERT (Design): **In-App-Logo aufs neue v2-Icon** getauscht (Schnecke + Mikrofon), wirkt auch auf dem Anmelde-Bildschirm. Neuer Claim „Schlau kommunizieren. Sicher navigieren. Gemeinsam weiterkommen." in 5 Sprachen.

## 01.001.045
- FIX (Navi): **Abbiege-Symbol zeigte immer nach rechts**, auch wenn die Ansage „links" sagte. Das Symbol richtet sich jetzt nach dem echten Manöver (links/rechts/scharf/leicht/wenden/Kreisel/Ziel), geliefert von ORS.
- NEU (Navi): **Automatische Neuberechnung**, wenn man von der Route abkommt (>50 m) – mit Ansage „Route wird neu berechnet", ab der aktuellen Position. (Abbiege-Ansagen wie „bitte wenden" kommen von ORS; „Ziel erreicht" ist eingebaut.)
- GEÄNDERT (Sicherheit): **Doppelte Sicherheitsabfrage** beim Löschen von **Gruppe** und **Konto** – zweiter Schritt mit deutlichem Hinweis „kann NICHT rückgängig gemacht werden".

## 01.001.044
- NEU (Navi, Runde 2): **Karten-Modi** – Umschalter Norden-oben ⇄ Fahrtrichtung-oben (Karte dreht mit) plus **Kompass** unten links (zeigt die Ausrichtung, Tipp = zurück nach Norden). **Fahrt aufzeichnen**: beim Start der Navigation Frage „Fahrt aufzeichnen?", am Ende „Aufzeichnung speichern?" → als **GPX** teilen/sichern; zusätzlich ein Aufnahme-Knopf oben. **Tempo-abhängiger Auto-Zoom** (schnell = weiter raus, langsam = näher heran; +/- übersteuert, Zentrieren aktiviert ihn wieder). **Tempolimit-Schild** aus OpenStreetMap (`maxspeed`), wo hinterlegt – sonst kein Schild (OSM-Abdeckung lückenhaft). Texte in 5 Sprachen. (Sonderziele/POIs bewusst zurückgestellt.)

## 01.001.043
- NEU (Navi, Runde 1 – im Auto-Test war die Navigation unbrauchbar): **Karte folgt jetzt der Fahrt** (zentriert laufend auf die eigene Position statt nur beim Start). **Vorwarn-Ansage** vor jeder Abbiegung („In 200 m – …") zusätzlich zur Ansage direkt am Abzweig. **Eigener Standort als blaues Dreieck**, Spitze in Fahrtrichtung. **Tempo (km/h) + Rest-Kilometer + Ankunftszeit** während der Navigation. **Zoom-Knöpfe** (+/−) zum Vergrößern der Karte. **Ansagen stummschalten** (Lautsprecher-Symbol oben). Texte in 5 Sprachen.

## 01.001.042
- FIX (Sprechen): **Sprech-Anfang wurde abgeschnitten** („Haken am Anfang", Fahrrad-Feldtest 05.07.). Ursache: die starke Geräuschunterdrückung (Modus „Aggressive") behandelte die erste Silbe kurz als Rauschen und schnitt sie weg – senderseitig, daher hörten die anderen nur den Beginn abgehackt. Stufe **„Stark" nutzt jetzt „UltraLowLatency"**: draußen weiterhin kräftige Filterung, aber ohne den Onset zu verschlucken. Stufen „Aus"/„Mittel" unverändert.

## 01.001.041
- NEU (Sprechen): **Empfangsqualitäts-Anzeige** – senkrechter Balken am rechten Rand auf Höhe des Status-Kreises, grün/orange/rot je nach Agora-Netzqualität (schlechtere Richtung Senden/Empfangen). So erkennt man, ob eine schlechte Verbindung der Grund ist, wenn jemand nicht antwortet.
- NEU (Gruppe): Admin kann eine **Gruppe löschen** (Gruppen-Einstellungen, mit Sicherheitsabfrage). RPC `delete_group`.
- GEÄNDERT (Gruppe): **Beitritts-Code ohne 0 und O** (Verwechslung Null/Buchstabe O vermeiden) – neues Code-Alphabet `gen_join_code()`.

## 01.001.040
- GEÄNDERT (Sparmodus): Der Kanal schließt jetzt wieder **nach echter Ruhe** (statt fix nach dem Öffnen). Die Fenster-Uhr wird **nur durch wirklich lautes Reden** zurückgesetzt (hohe Lautstärke-Schwelle) – **leise Fahrt-/Restgeräusche werden ignoriert** und halten den Kanal NICHT mehr offen. So bleibt der Kanal beim Reden offen und schließt erst, wenn es das eingestellte Fenster lang wirklich still ist.

## 01.001.039
- NEU (Sparmodus = jetzt GRUPPEN-Sache, vom Admin gesteuert): Sparmodus an/aus + Offen-Fenster (Sek.) werden in den **Gruppen-Einstellungen** vom Admin gesetzt und gelten für alle. **Standard bei neuen Gruppen: an, 60 s.** Die ganze Gruppe schläft und wacht gemeinsam – keine Erreichbarkeitslücke, minimale Kosten. (DB: neue Spalten `sparmodus_an`, `sparmodus_fenster_sek`.)
- GEÄNDERT (Sprechen): **Keine Stimmerkennung mehr** zum Offenhalten (löst die Restgeräusch-Falle auf dem Fahrrad). Der Kanal bleibt nach dem Öffnen ein **festes Fenster** offen und schließt dann für alle. Aufwecken nur per **„connect"** oder **rotem Finger-Knopf** (von jedem, öffnet für die ganze Gruppe).
- GEÄNDERT (Sprechen): Der individuelle Sparmodus-Schalter/Regler/Wake-Word-Schalter in der Sprech-Maske entfällt; stattdessen eine Taste **„Gruppe in Sparmodus"** (schließt die Gruppe sofort). Gesamte Logik im Dokument *Sparmodus-Gruppenlogik.md* und in der Hilfe (5 Sprachen).

## 01.001.038
- GEÄNDERT (Sprechen): **Beim Betreten der Gruppe ist man jetzt zuerst VERBUNDEN**, auch wenn der Sparmodus-Schalter an ist. In den Sparmodus-Leerlauf fällt man erst durch **Stille** (Fenster-Uhr) oder durch **Tastendruck**. Vorher war man sofort im Leerlauf – das war verwirrend.
- GEÄNDERT (Sprechen): Die Tasten „Sparmodus für mich/für alle" treiben jetzt Richtung **Leerlauf** (statt den Modus an/aus). „Für mich" verbindet aus dem Leerlauf wieder (wie der Status-Kreis), „für alle" holt zusätzlich die Gruppe in den Leerlauf.
- NEU (Sprechen): Pink markiert wird **nur die Taste, die den Leerlauf ausgelöst hat** – „für mich" (auch beim Auslösen per Stille-Uhr) bzw. „für alle". Beim Wieder-Verbinden werden beide wieder normal.
- Empfänger von „für alle" fällt jetzt ebenfalls zuverlässig in den Leerlauf (mit temporärer Diagnose-Meldung ✓/✗).

## 01.001.036
- FIX/DIAGNOSE (Sprechen): Empfänger von „Sparmodus für alle" schaltete trotz Meldung nicht um. Kanal-Abbau in `_aufraeumen` bekam eine **Zeitsperre (2 s)**, damit ein hängendes `removeChannel` das Umschalten nicht mehr blockiert. Zusätzlich temporäre Diagnose-Meldung („Sparmodus aktiviert ✓/✗") beim Empfänger.

## 01.001.035
- FIX (Sprechen): **Sparmodus-Einschalten über die Tasten repariert.** Beim Umschalten wird `_verbunden` jetzt korrekt zurückgesetzt und nach dem Neu-Aufbau ein Rebuild ausgelöst – vorher blieb die Anzeige hängen und der Sparmodus wirkte nicht.
- NEU (Sprechen): Beide Tasten sind jetzt **Umschalter** (nochmal drücken = aus, wie der Status-Kreis oben). Volle Beschriftung **„Sparmodus für mich"** / **„Sparmodus für alle"**. Beide sind im Aus-Zustand **normal (umrandet)** und werden **pink**, sobald der Sparmodus aktiv ist; beim Ausschalten wieder normal.

## 01.001.033
- FIX (Sprechen): **„Sparmodus für alle" schaltet jetzt wirklich alle Geräte** um. Vorher kam bei den Empfängern zwar die Meldung, aber das Umschalten brach ab, weil es mitten in der Broadcast-Callback lief und den Signal-Kanal abbaute – jetzt wird es sauber danach ausgeführt.
- NEU (Sprechen): Die Sparmodus-Taste ist in **zwei Tasten auf einer Linie** aufgeteilt: links **„Nur ich"** (nur mein Gerät), rechts **„Für alle"** (ganze Gruppe).

## 01.001.032
- NEU (Sprechen): **„Sparmodus für alle"-Taste.** Ein Tipp schaltet dich UND die ganze Gruppe in den Sparmodus (Kanal nur bei Sprache offen) – jeder kann für sich sofort wieder raus. Hilft, wenn kleine Restgeräusche den automatischen Sparmodus blockieren. Android + iOS.
- NEU (Sprechen): Beim **Aufwecken aus dem Sparmodus** (per „connect" oder Taste) ertönt der **Verbunden-Dreiklang jetzt bei allen Beteiligten**, nicht nur beim Auslöser.
- VERBESSERT (Sprechen): Der **Live-Sprech-Screen ist kompakter** – alle Regler und Knöpfe passen ohne Scrollen auf eine Seite.
- FIX (Gruppen): Im Gruppen-Bereich gibt es jetzt oben rechts einen **Knopf zurück zur Auswahlmaske** (Sprechen / Navi).
- VERBESSERT (Dashboard): Startet standardmäßig mit **15 s Auto-Aktualisierung** (Änderung wird gemerkt); **Werbe-Topf und Treuhand-Topf** stehen jetzt **zuunterst**.
- FIX (iOS): Fehlenden Info.plist-Schlüssel `NSLocationAlwaysAndWhenInUseUsageDescription` ergänzt (Apple-Hinweis ITMS-90683).

## 01.001.031
- NEU (Navi): **Touren speichern & laden.** Über das Lesezeichen-Symbol oben: die aktuelle Tour (Wegpunkte inkl. Adressen + Rundkurs/Richtung/Profil) unter einem **Namen speichern**, gespeicherte Touren **laden** oder löschen. Gespeichert in Supabase (neue Tabelle `touren`, nur eigene per Zugriffsschutz) – die Basis fürs spätere **Leader-Teilen** an die Gruppe. Android + iOS.

## 01.001.030
- VERBESSERT (Navi): In der leeren unteren Leiste ist die **Adresssuche jetzt der Haupt-Knopf** (großer „Adresse oder Ort suchen"-Button), das Antippen der Karte steht als kleiner Zweit-Hinweis darunter. Android + iOS.

## 01.001.029
- FIX (Navi): Der „Zur eigenen Position"-Knopf lag genau über dem „Route berechnen"-Knopf. Er ist jetzt als kleinerer Knopf **nach oben gerückt** und überdeckt die untere Leiste nicht mehr. Android + iOS.

## 01.001.028
- NEU (Navi): Auch in der unteren Leiste („Tippe auf die Karte …", wenn noch kein Wegpunkt gesetzt ist) gibt es jetzt eine **Lupe** für die Adresssuche – so kann man den ersten Punkt auch per Suche setzen statt nur per Karten-Tipp. Android + iOS.

## 01.001.027
- NEU (Navi): In der **Wegpunkt-Liste** gibt es jetzt oben eine **Lupe** – damit die Adresssuche direkt aus der Liste öffnen und den Treffer als weiteren Wegpunkt hinzufügen, ohne die Liste zu verlassen. Android + iOS.

## 01.001.026
- VERBESSERT (Navi): In der **Wegpunkt-Liste** wird jetzt die **Adresse** jedes Punkts angezeigt (statt „Wegpunkt 1/2/3"). Beim Antippen auf die Karte wird die Adresse per Reverse-Geocoding (Edge-Function `geocode`) im Hintergrund nachgeladen; aus der Adresssuche ist sie sofort da. Außerdem beim **E-Bike-Icon** der Blitz vom Fahrrad **abgesetzt** (oben rechts mit Abstand), damit er klar erkennbar ist. Android + iOS.

## 01.001.025
- KLEIN (Navi): Das **E-Bike-Profil** nutzt jetzt dasselbe **Fahrrad-Symbol** wie „Fahrrad", zusätzlich mit einem kleinen **Blitz** oben rechts – dadurch klarer als Fahrrad-Variante erkennbar. Android + iOS.

## 01.001.024
- VERBESSERT (Navi/Adresssuche): Vorschläge erscheinen jetzt **live beim Tippen** (ab 3 Zeichen), plus ein Hinweis zur Bedienung: Strasse eingeben und antippen; für ein bestimmtes Haus die Hausnummer anhängen (z. B. „Bahnhofstrasse 5, Zug"). In 5 Sprachen. Android + iOS.

## 01.001.023
- NEU (Navi): **Mehrere Wegpunkte.** Tippe auf die Karte → nummerierte Punkte 1, 2, 3 …; die Route führt der Reihe nach durch alle (auch die Adresssuche fügt einen Wegpunkt hinzu). Über die **Wegpunkt-Liste** (Listen-Symbol unten): Reihenfolge per **Ziehen** ändern, einzelne Punkte löschen, **Alle löschen**. **Rundkurs** (zurück zum Start) als Schalter, dazu **Richtung umkehren**. Neues Profil **E-Bike** (ORS `cycling-electric` – nimmt Anstiege anders als das normale Fahrrad). Turn-by-turn funktioniert auch über mehrere Wegpunkte. Android + iOS.

## 01.001.022
- NEU (Navi): **Adresssuche** – über das Lupen-Symbol eine Adresse/einen Ort eingeben (ORS-Geocoding über die neue Edge-Function `geocode`, Key bleibt geheim), Treffer antippen → als Ziel gesetzt, Karte springt hin. **Karten-Umschalter** (Ebenen-Symbol oben): **Standard**, **Gelände** (OpenTopoMap), **Satellit** (Esri). FIX: Ein Profilwechsel nach einem GPX-Import routet nicht mehr zum Track-Ende (der importierte Track bleibt stehen). Android + iOS.

## 01.001.021
- FIX (Navi/GPX): Der GPX-Import scheiterte auf dem Gerät sofort mit „GPX konnte nicht geladen werden". Der Dateiwähler filtert jetzt **nicht** mehr strikt auf die Endung `gpx` (manche Android-Dateiwähler lehnen diesen Filter ab) und liest die Datei bevorzugt über die **Bytes** (Scoped Storage liefert oft keinen Dateipfad). Im Fehlerfall zeigt die Meldung jetzt den echten Grund an. Android + iOS.

## 01.001.020
- NEU (Navi): **GPX-Import.** Über den Knopf oben rechts („GPX laden") lässt sich eine vorbereitete Route aus einer `.gpx`-Datei laden (`<trkpt>`/`<rtept>`). Der Track wird als Linie auf der Karte gezeigt, mit Gesamt-Länge. Ein GPX-Track enthält keine Abbiege-Anweisungen → vorerst reine Anzeige/Sicht-Navigation; sprachgeführtes GPX folgt. Neues Paket `file_picker`. Android + iOS.

## 01.001.019
- NEU (Navi): **Profilwahl** (Rad/Wandern/Auto/Töff) als Icon-Leiste oben – bei Wechsel wird die Route neu berechnet. **Turn-by-turn mit Sprachansagen:** „Starten" beginnt die Navigation, ein Banner zeigt die nächste Abbiegung, und die App **spricht** die Anweisungen (`flutter_tts`) beim Erreichen jedes Abbiegepunkts, mit „Ziel erreicht" am Ende. Die Anweisungen kommen **mehrsprachig** von ORS (Edge-Function `route` um `language` erweitert). Töff nutzt vorerst das Auto-Profil (kurvig/Pässe folgen mit GraphHopper/Kurviger). Android + iOS.

## 01.001.018
- NEU (Navi, Tag 2): Der Navi-Bereich zeigt jetzt eine echte **Karte** (OpenStreetMap) mit der **eigenen Position** (GPS) und einem „Auf meine Position zentrieren"-Knopf. **Ziel** per Tipp auf die Karte setzen → **„Route berechnen"** zeichnet die **Fahrrad-Route** und zeigt **Distanz + Zeit**. Das Routing läuft serverseitig über die neue Supabase-Edge-Function `route` (OpenRouteService; der API-Key liegt als Secret in Supabase, nicht in der App). Neue Standort-Berechtigung (Android-Manifest + iOS-Info.plist). Turn-by-turn-Sprachansagen und die Profilwahl (Rad/Wandern/Auto/Töff) folgen als Nächstes. In 5 Sprachen. Android + iOS.

## 01.001.017
- NEU: **Zwischenmaske nach dem Login.** Nach der Anmeldung erscheint jetzt eine Auswahl mit zwei großen Kacheln – **Sprechfunk** (führt wie bisher zur Gruppenliste „Meine Gruppen") und **Navi** (persönliches Navi, aktuell noch Platzhalter „kommt bald"). Damit ist der neue Navi-Bereich (**Prio 1**) von Anfang an im Einstieg verankert. Mit dem Zurück-Pfeil kommt man jederzeit zur Auswahl zurück und wechselt zwischen Funk und Navi, ohne sich neu anzumelden. Abmelden ist oben rechts erreichbar. In 5 Sprachen. Android + iOS.
- MIT AUSGELIEFERT (bereits gebaut, bisher unveröffentlicht): **Konto-Löschung** in der App (Profil → „Konto löschen" mit Sicherheitsabfrage + Server-Edge-Function `konto-loeschen`) sowie der **Hilfe-Cache-Buster** (die In-App-Hilfe lädt zuverlässig die neueste Fassung). Android + iOS.

## Backend/Geschäft – 2026-07-03 (Preise & Free-Kontingent, keine App-Funktionsänderung)
- PREISE erhöht (mit Konkurrenzabgleich – BlinkTalk nur Funk ~€11/Jahr, Navi-Abos ~€60/Jahr → Grevo bündelt beides): **Pro 3.90→4.90/Mt (39→49/Jahr)**, **Mega 7.90→9.90/Mt (79→99/Jahr)**. **Free-Kontingent 10→20 Min/Monat.** Einmalkäufe neu als drei Blöcke **Basis (500 Teiln.-Min · 2.90) · Plus (1.200 · 4.90) · Maxi (3.000 · 9.90)** – ersetzen die früheren Ausflugs-Bündel + das Stunden-Paket. Umgesetzt in Supabase `plan_tiers` (live-UPDATE + `schema.sql`), `Grevo-Finanzmodell.xlsx`, Doku (Abomodell/Markteinführung/RevenueCat-Ablauf) + PDFs. Free=20 greift serverseitig sofort; die Kaufpreise kommen später über RevenueCat.

## Backend/Geschäft – 2026-07-02 (Finanzen, keine App-Funktionsänderung)
- FINANZEN: **Werbe-Reserve 10 % vom Gewinn** ergänzt – gleiche Basis wie das Treuhand-Honorar (operativer Gewinn *vor* Treuhand und *vor* Werbe-Reserve, nur positiv). Baut über die Zeit ein Budget für bezahlte Werbung (TikTok, Google Ads u. a.) auf. Nach Werbe-Reserve + Treuhand verbleiben ~80 % des operativen Gewinns als Gewinn vor Steuer. Umgesetzt im Finanzmodell (`Grevo-Finanzmodell.xlsx`: neuer Parameter `Eingaben!B17`=10 %, neue Szenario-Zeile + ausgewiesenes Jahres-Werbebudget, mit LibreOffice nachgerechnet → 0 Formelfehler), im Live-Dashboard (`WERBUNG=0.10`, Ausgaben-Liste + Verlaufsprognose) und in Abomodell-/Marketing-Doku. Steuerhinweis in der Doku: als reine Rücklage erst bei tatsächlicher Ausgabe abzugsfähig.

## Backend/Geschäft – 2026-07-01 (Produkt & Finanzen, keine App-Funktionsänderung)
- ENTFERNT: Teilnehmer-Obergrenze je Gruppe (`plan_tiers.max_participants`, Abschnitt 20 – in Supabase gedroppt) und das „Plätze"-Zusatzpaket. Gruppen sind unbegrenzt groß; Bündel zählen als reiner Teilnehmer-Minuten-Topf. Doku (Abomodell) angepasst.
- FINANZEN: Ausgaben um **bexio „Advanced" 42 CHF/Mt** (Buchhaltung, Nobi + Treuhänderin) und **Treuhänderin-Honorar 10 % vom Gewinn** (vor Honorar, nur positiv) ergänzt – im Finanzmodell (Grevo-Finanzmodell.xlsx, neu strukturiert, 0 Formelfehler), im Live-Dashboard und in Abomodell-/Marketing-Doku.

## Backend/Schema – 2026-07-01 (Notbremse-Ausnahme, keine App-Änderung)
- FIX (Fairness): Die globale Notbremse gilt jetzt NICHT mehr für Gratis-Nutzer, die ein **Zeitpaket gekauft** haben. Bedingung in `token_allowed` ergänzt: `tier='free' AND extra_minutes <= 0`. Wer bezahlte Minuten im Zusatz-Topf hat, spricht diese **immer** auf – unabhängig vom globalen Budget; erst wenn sie aufgebraucht sind, greift die Bremse wieder. Migration `notbremse_ausnahme_zeitpaket` in Supabase eingespielt; mit Rollback-Test verifiziert (ohne Paket → gesperrt, mit Paket → erlaubt).

## Backend/Schema – 2026-07-01 (Abschnitt 19, keine App-Änderung)
- KOSTENSCHUTZ VERVOLLSTÄNDIGT (nur `supabase/schema.sql`, Abschnitt 19 – idempotent nachträglich ausführen). Baut auf 14/15 auf: Monats-Reset und Notbremse waren logisch vorhanden, aber nicht bedienbar.
  - **Konfigurierbarer Kostenfaktor**: `app_config.kostenfaktor` (Vorgabe 0,001 CHF/Teiln.-Min) statt der hart codierten `0.001`. `token_allowed` nutzt jetzt `current_month_spend_chf()`.
  - **Globale Notbremse bedienbar**: `admin_set_notbremse(budget, aktiv)` setzt das Monatsbudget, `admin_notbremse_status()` zeigt Budget/aktiv/Verbrauch/Rest/Anteil. Beide nur für **Super-Admins** (`app_config.super_admins.ids`, Gate via `is_super_admin()`). Bei Erreichen des Budgets wird nur die **Gratis-Stufe** gedrosselt. Verbrauch zählt **netto** – erst NACH dem Agora-Gratis-Kontingent (`frei_minuten`, Vorgabe 10.000 Teiln.-Min/Monat = 0 CHF) entstehen echte Kosten.
  - **Live-Dashboard**: neuer Notbremse-Streifen (Budget, Netto-Verbrauch, Rest, Fortschrittsbalken, Status aktiv/aus + Drossel-Warnung).
  - **Robuster Monats-Reset**: `reset_all_due_periods()` (proaktiv, für Zeitplan) + optionaler `pg_cron`-Job (1. des Monats, guarded). `my_billing()` setzt die eigene Periode jetzt lazy zurück → Abrechnungsansicht bleibt aktuell.
  - GRUNDSATZ unverändert **FAIL-OPEN** in der Token-Prüfung. Verifiziert: gesamtes Schema + alle neuen PL/pgSQL-Funktionen mit dem echten Postgres-Parser geprüft.

## 01.001.016
- BUILD/iOS: Die **iOS-Build-Nummer** wird jetzt **aus der Version abgeleitet** (`codemagic.yaml`): `01.001.016 → 1001016` (gleiche Basis wie der Android-versionCode), statt eines separaten Auto-Zählers. Damit gehören Version und Build-Nummer auf TestFlight konsistent zusammen und steigen monoton. Hintergrund: Die zuvor auf TestFlight sichtbare „(13)" war NICHT die Version, sondern der Upload-Zähler. Keine App-Funktionsänderung gegenüber 01.001.015. Android + iOS.

## 01.001.015
- NEU: Eigene, beruhigende Meldung, wenn die **globale Notbremse** greift. Bisher zeigte die App bei jedem 403 des Token-Servers „Kontingent aufgebraucht". Jetzt wird unterschieden: Bei `reason: 'notbremse'` (globales Monatsbudget des Gratis-Diensts erreicht) erscheint **„Der Gratis-Dienst ist gerade ausgelastet. Bitte später erneut versuchen – oder mit Upgrade/Paket sofort weiter."**; bei leerem persönlichem Kontingent bleibt es bei „Kontingent aufgebraucht". Auswertung über `FunctionException.details['reason']`. In 5 Sprachen. Android + iOS.
- Backend: Notbremse-Monatsbudget auf **25 CHF** gesetzt und aktiv (`app_config.notbremse`).

## 01.001.014
- NEU: **Push-Benachrichtigungen jetzt auch auf iOS** („Ich warte auf dich"). Der App-Code war bereits plattformübergreifend; ergänzt wurde die native iOS-Anbindung: APNs-Authentifizierungsschlüssel in Firebase hinterlegt, iOS-App im Firebase-Projekt registriert (`GoogleService-Info.plist` ins iOS-Projekt eingebunden), Push-Capability + `aps-environment=production`-Entitlement, `remote-notification`-Hintergrundmodus. Die Edge Function `warte-push` sendet zusätzlich einen `apns`-Block (Ton + hohe Priorität), damit der Push auf dem iPhone sofort mit Ton erscheint. Android unverändert. Android + iOS.

## 01.001.013
- BESTÄTIGT BEHOBEN (Sponsor-Ende-Meldung): Der Diagnose-Build 012 hat gezeigt, dass die Übernahme-Frage bei aktiv Verbundenen jetzt zuverlässig ankommt – auf **Android UND iOS**: Beim Beenden des Sponsorings (bzw. Rückzug der Vollmacht) erscheint bei den anderen Verbundenen die „Auf eigene Kosten weiter?"-Frage (Ja/Nein), und das automatische „Nein" nach ~20 s ohne Antwort löst ebenfalls korrekt aus. Damit greifen die Wege aus 009–011 (Broadcast + Realtime, REPLICA IDENTITY FULL) wie vorgesehen.
- AUFGERÄUMT: Das temporäre gelbe Diagnose-Feld „Sponsor-Diagnose" im Sprech-Bildschirm sowie die Diagnose-Einblendung im Gruppen-Detail wurden wieder **entfernt**. Keine sonstige Funktionsänderung. Android + iOS.

## 01.001.012
- DIAGNOSE (Sponsor-Ende-Meldung kommt bei aktiv Verbundenen nicht an): Da die letzten drei Versuche (009–011) das Signal redundant nachgelegt haben und es weiterhin scheitert, wird jetzt – wie beim iOS-Iris-Bug – eine **sichtbare Diagnose** eingebaut, statt blind einen vierten Weg hinzuzufügen. Im Sprech-Bildschirm erscheint ein gelbes Protokoll-Feld „Sponsor-Diagnose", das pro Ereignis zeigt: ob der **Realtime-UPDATE** der groups-Zeile ankommt (alt/neu Sponsor, `_verbunden`), ob das **Broadcast-Signal** `sponsor_ended` ankommt, ob die Übernahme-Frage **ausgelöst oder abgebrochen** wird (mit Grund), sowie der **Subscribe-Status** des Watch-Kanals. Zusätzlich meldet das Gruppen-Detail per kurzer Einblendung, ob das Broadcast-Signal beim Beenden wirklich **abgesendet** wurde (inkl. Subscribe-Status). So zeigt EIN Testdurchlauf, welcher Weg versagt. Reiner Diagnose-Build – keine Funktionsänderung; wird nach Klärung der Ursache wieder entfernt. Android + iOS.

## 01.001.011
- FIX (Sponsor-Beenden im Detail wurde nicht erkannt): Beendet der Sponsor sein Sponsoring **im Gruppen-Detail** (z. B. nachdem er die Sprechrunde verlassen hat), sendet die App jetzt zusätzlich ein **Live-Signal über den Broadcast-Kanal**, den die Verbundenen ohnehin abonniert haben. Damit erscheint die Übernahme-Frage zuverlässig – unabhängig vom Realtime-Weg. Außerdem `groups` mit REPLICA IDENTITY FULL (schema.sql Abschnitt 18, in Supabase ausgeführt), damit auch der Realtime-Weg die Sponsor-Änderung sicher ausliefert. Gilt auch, wenn ein Admin den Sponsor entfernt. Android + iOS.

## 01.001.010
- FIX: Nach dem Verlassen der Sprechrunde wird die **Gruppen-Detailseite neu geladen** – sie zeigt damit den aktuellen Zahler/Sponsor (vorher blieb dort veraltet „Bezahlt von …" stehen, bis man manuell aktualisierte).
- FIX: Beendet der Sponsor sein Sponsoring **im Gruppen-Detail** (oder ohne selbst in der Sprechrunde zu sein), bekamen die Verbundenen bisher kein Signal. Jetzt lauschen alle Verbundenen direkt auf die Gruppen-Änderung (Supabase-Realtime) und werden zuverlässig gefragt – unabhängig davon, wo/wie der Sponsor beendet. (Voraussetzung: `groups` in der Realtime-Publication, schema.sql Abschnitt 18, in Supabase ausgeführt.) Android + iOS.

## 01.001.009
- NEU: Der **Sponsor kann sein Sponsoring selbst beenden** – auch ohne Admin zu sein (Knopf „Sponsoring beenden" im Sprech-Bildschirm und im Gruppen-Detail). Danach zahlt die Gruppe wieder selbst.
- NEU: Beendet der Sponsor WÄHREND einer laufenden Runde, bekommen alle gerade Verbundenen sofort die Frage „… hat die Kostenübernahme beendet. Ab jetzt auf eigene Kosten weiterreden?" – **Ja:** bleibt verbunden (zahlt ab jetzt selbst). **Nein** oder keine Antwort (nach ~20 s automatisch): Verbindung wird getrennt, zurück zur Gruppe. So zahlt niemand ungewollt weiter.
- VERBESSERT: Die Gruppen-Übersicht frischt die **Verbindungsanzahl** je Gruppe nun regelmäßig automatisch auf (alle ~12 s), auch wenn ein Live-Update mal ausbleibt. In 5 Sprachen. Android + iOS.

## 01.001.008
- NEU: **Ende-zu-Ende-Verschlüsselung** der Live-Sprache (Agora AES-256-GCM2). Jede Gruppe hat einen geheimen Schlüssel, den nur ihre Mitglieder kennen (über Supabase, NIE an Agora) – die Sprache ist damit abhörsicher, auch Agora kann nicht mithören. Im Sprech-Bildschirm zeigt ein grünes Schloss „Ende-zu-Ende verschlüsselt". Technisch: enableEncryption vor dem Beitritt; alle im Kanal nutzen denselben Gruppen-Schlüssel. Fail-open: falls der Schlüssel fehlt, wird wie bisher verbunden. Android + iOS.

## 01.001.007
- NEU: Auf der Startseite erscheint bei einer Gruppe, in der DU als Sponsor vorgeschlagen wurdest, ein deutlicher Hinweis „Sponsor-Anfrage – tippen zum Beantworten". Antippen öffnet die Gruppe, wo du mit Annehmen/Ablehnen antwortest. So findet man die Anfrage sofort, ohne in die Gruppe suchen zu müssen. In 5 Sprachen. Android + iOS.

## 01.001.006
- NEU: **Sponsor** (frei bestimmbarer Zahler je Gruppe). Ein Admin kann ein beliebiges Mitglied als „Sponsor" der Gruppe bestimmen – dann läuft die Verbindungszeit aller Teilnehmer über dessen Konto. Das vorgeschlagene Mitglied muss ZUSTIMMEN (kein Belasten fremder Konten ohne Einverständnis); wählt ein Admin sich selbst, ist es sofort aktiv. Gilt dauerhaft, bis ein Admin es ändert/entfernt. Bedienung im Gruppen-Detail (Sponsor bestimmen über das Mitglieder-Menü oder „Ich zahle"; Annehmen/Ablehnen; entfernen). Im Sprech-Bildschirm zeigt ein Hinweis „Bezahlt von …" (für alle) und beim ERSTMALIGEN Reingehen einmalig ein Reminder. Admin (Verwaltung) und Zahler sind damit getrennt; der Begriff „Leader" bleibt für den späteren Navigationsmodus reserviert. In 5 Sprachen. Android + iOS.
- NEU: Bei aufgebrauchtem Kontingent zeigt die App eine verständliche Meldung „Kontingent aufgebraucht …" statt des allgemeinen Verbindungsfehlers.
- Backend: Token-Server und Abrechnungs-Webhook nutzen jetzt den Sponsor (sponsor_profile_id) als Zahler statt des alten pay_mode (schema.sql Abschnitt 15, in Supabase ausgeführt).

## 01.001.005
- FIX (Abrechnung): Doppelzählung der Verbindungsminuten behoben. Seit 01.001.004 liefert der Agora-Webhook echte Leave-Events (104) und verbucht die Zeit serverseitig. Die zusätzliche app-seitige Minuten-Meldung aus 00.001.018 (damals nur Fallback) ist jetzt deaktiviert, sonst wäre jede Tour doppelt gezählt worden. Der Webhook ist alleinige Abrechnungsquelle (zuverlässig auch bei App-Absturz, da Agora das Verbindungsende per Timeout meldet). Keine sichtbare Funktionsänderung. Android + iOS.

## 01.001.004
- FIX (Abrechnung/Webhook): Agora-Sprachkanäle nutzen jetzt das Profil **LiveBroadcasting** statt Communication. Grund: Agora-Support (Ticket #11991) hat bestätigt, dass die RTC-Channel-Event-Callbacks 103 (Beitritt) / 104 (Verlassen) / 112 NUR im LiveBroadcasting-Profil ausgelöst werden – im Communication-Profil kamen nie echte Events am Webhook an. Rolle bleibt Broadcaster, am Sprechverhalten ändert sich nichts. Damit kann die serverseitige Minutenverbuchung (agora-webhook) endlich echte Sessions zählen. Android + iOS.

## 01.001.003
- NEU: Abrechnungsansicht im Profil. Zeigt deine Stufe (Free/Pro/Mega), das Monats-Kontingent als Balken (verbraucht/übrig), eventuelle Zusatz-Minuten, das Reset-Datum sowie die letzten Touren (Datum, Gruppe, Dauer, wer bezahlt hat) und Käufe. Reine Leseansicht auf Basis der vorhandenen Abrechnungsdaten (my_billing + neue Lese-RPC my_usage_history, schema.sql Abschnitt 13 – muss in Supabase ausgeführt werden). In 5 Sprachen. Erreichbar über Profil → Abrechnung. Android + iOS.

## 01.001.002
- NEU: In-App-Hilfe. Über einen Hilfe-Knopf (Fragezeichen) in der Kopfzeile der Startseite UND im Profil öffnet sich die Anleitung als eingebettete Web-Ansicht (grevo.mclear.ch/hilfe.html). Vorteil: Die Hilfe wird online gepflegt und ist sofort aktuell – ohne neues App-Update. Paket `webview_flutter` ergänzt; bei fehlendem Internet erscheint ein Hinweis mit „Erneut versuchen“. App-Sprache wird der Seite als ?lang= mitgegeben. In 5 Sprachen (Hilfe/Help/Aide/Aiuto/Ajuda). Android + iOS.

## 01.001.001
- Grevo wird ab dieser Version offiziell auf BEIDEN Plattformen unterstuetzt: **Android UND iOS (iPhone/iPad)**. Beide laufen mit identischem Funktionsstand.
- ERSTE LAUFFAEHIGE VERSION auf allen Plattformen (Android + iOS). Hauptrelease auf 01 angehoben. WICHTIG/Lehre: Die iOS-Versionsanzeige 0.1.33 (033) war NIEDRIGER als das schon auf TestFlight verteilte 1.0.0 -> TestFlight wertete sie als Downgrade und bot den Build den internen Testern nicht zum Update an (nur 1.0.0 (6) war sichtbar). Build 6 (1.0.0) enthielt aber bereits den funktionierenden Iris-Fix. FIX: ab jetzt 01.001.001 -> Apple-Versionsname wird (via codemagic-Ableitung) `1.1.1` (>1.0.0, wird wieder als Update angeboten). Android: versionName 1.1.1, versionCode 1001001 (>2002, installiert sauber drueber). Keine Funktionsaenderung gegenueber 033 - reine Versions-/Verteilkorrektur.

## 00.001.033
- TestFlight-Versionsanzeige: codemagic.yaml leitet den Versionsnamen jetzt automatisch aus `lib/version.dart` ab (z.B. 00.001.033 -> `0.1.33`; Apple erlaubt keine fuehrenden Nullen, daher pro Segment auf Integer gekuerzt). Die Build-Nummer in Klammern bleibt der automatische, stetig steigende Zaehler. TestFlight zeigt damit `0.1.33 (N)` statt `1.0.0`. Einzige Pflegestelle bleibt appVersion in version.dart. Nur Anzeige/Bauweg - keine App-Funktionsaenderung.

## 00.001.032
- FIX iOS Live-Sprechen (2. Anlauf): Der `-force_load`-Versuch (030/031) griff nicht, App stuerzte weiter beim Agora-Init ab (`Iris_InitDartApiDL ... symbol not found`, per iPhone-Log bestaetigt). Ursache ist das statische Linken: Bei `use_frameworks! :linkage => :static` landet das nur zur Laufzeit per dlsym gesuchte Iris-Symbol nicht auffindbar in der App. FIX: statisches Linken entfernt -> normales `use_frameworks!` (dynamisch); der Agora-Iris-Wrapper laedt als Dylib, dlsym findet das Symbol. SPM ist weiterhin aus (loest den frueheren AgoraRtcWrapper-Header-Fehler), use_modular_headers! bleibt fuer Firebase. Nur iOS-Bauweg - Android unveraendert.

## 00.001.031
- HOTFIX Podfile: Der 00.001.030-Build scheiterte an `pod install` ("Invalid Podfile: syntax errors found") - beim Speichern war das Podfile abgeschnitten worden, der `post_install`-Block blieb offen. Podfile vollstaendig neu geschrieben und Syntax mit `ruby -c` geprueft (Syntax OK). Inhaltlich gleich wie 030 (`-force_load` der AgoraRtcWrapper-Binary gegen das fehlende Iris-Symbol). Nur iOS-Bauweg - Android unveraendert.

## 00.001.030
- FIX iOS Live-Sprechen (Ursache gefunden via iPhone-Geräte-Log am PC): Die App stürzte beim Agora-Init ab – `Failed to lookup symbol 'Iris_InitDartApiDL': dlsym(RTLD_DEFAULT, ...) symbol not found`. Grund: `use_frameworks! :linkage => :static` bindet Agora statisch ein, wodurch das nur zur Laufzeit gesuchte Iris-Symbol (in AgoraRtcWrapper) nicht in die App-Binary gelangte. FIX im ios/Podfile: `post_install` ergänzt `-force_load` für die AgoraRtcWrapper-Binary (offizielle Agora-Empfehlung), Pfad wird automatisch aus den Pods ermittelt (geräte-Slice ios-arm64). Damit bleibt das Symbol erhalten und der Kanal-Beitritt läuft. Nur iOS-Bauweg – Android unverändert. Wirkt ab dem nächsten TestFlight-Build.

## 00.001.029
- DIAGNOSE iOS-Verbindung: Auf dem iPhone schließt der Agora-Kanal-Beitritt nicht ab (Token kommt sauber, aber „Verbinde…" hängt). Eingebaut: (1) Agora-Fehler/Status werden festgehalten und nach 12 s ohne Beitritt als Klartext auf dem „Verbinde…"-Bildschirm angezeigt; (2) bei endgültigem Agora-„failed" sofortige Fehleranzeige mit Grund; (3) „Verlassen" reagiert jetzt immer (6-s-Zeitlimit beim Aufräumen), auch wenn der Beitritt hängt. Dient dazu, die genaue Ursache des iOS-Beitritts-Problems sichtbar zu machen. Android unverändert.

## 00.001.028
- FIX iOS-Mikrofon: `permission_handler`-Compile-Flag `PERMISSION_MICROPHONE=1` im ios/Podfile ergänzt. Ohne dieses Flag zeigte iOS beim Sprechen NIE den Mikrofon-System-Dialog (die Anfrage kam sofort als „abgelehnt" zurück), die App erschien nicht unter Einstellungen > Datenschutz > Mikrofon und Live-Sprechen war auf dem iPhone unmöglich. Nur iOS – Android unverändert. Wirkt ab dem nächsten TestFlight-Build.

## 00.001.027
- iOS: Export-Compliance dauerhaft hinterlegt (`ITSAppUsesNonExemptEncryption = false` in Info.plist). Grevo nutzt nur Standard-HTTPS/TLS – damit fragt TestFlight/App Store die Verschlüsselungs-Compliance bei künftigen Builds nicht mehr ab. Keine funktionale Änderung.

## 00.001.026
- iOS-Signierung **dauerhaft** gemacht: Distributions-Zertifikat „grevo_dist" einmalig in Codemagic erzeugt/gespeichert; codemagic.yaml nutzt jetzt den `ios_signing`-Block (distribution_type app_store), der Zertifikat + Profil automatisch holt und wiederverwendet. Vorher wurde pro Build ein neues Apple-Zertifikat erstellt → Apple-2er/3er-Limit → Signier-Fehler. Nur iOS-Bauweg – keine Änderung am Android-Verhalten.

## 00.001.025
- iOS-Build (Codemagic): **Swift Package Manager abgeschaltet** (`flutter config --no-enable-swift-package-manager`). Das neuere Flutter-stable zog Agora/Firebase über SPM, und die SPM-Variante von agora_rtc_engine 6.5.4 hat einen kaputten Header (`AgoraRtcWrapper/AgoraPIPController.h` nicht gefunden) → Build-Abbruch beim Archivieren. Mit CocoaPods (statt SPM) sind die Agora-Header korrekt und das eigene Podfile (00.001.024) greift. Nur iOS-Bauweg – keine Änderung am Android-Verhalten.

## 00.001.024
- iOS-Build (Codemagic): Eigenes `ios/Podfile` mit `use_frameworks! :linkage => :static` (Agora-Empfehlung) ergänzt, CocoaPods mit `--repo-update` (frische Agora-/Iris-Pods, behebt fehlenden Header `AgoraRtcWrapper/AgoraPIPController.h` beim Archivieren) und IPA-Build mit `--no-tree-shake-icons` (verhindert das Wegstrippen der Agora-Iris-Symbole). Nur iOS-Bauweg – keine Änderung am Android-Verhalten.

## 00.001.023
- iOS-Vorbereitung: **Hintergrund-Audio-Modus** (`UIBackgroundModes: audio`) ergänzt, damit das Sprechen auf dem iPhone auch bei gesperrtem Bildschirm / im Hintergrund weiterläuft (iOS-Pendant zum Android-Vordergrunddienst). Nur iOS – keine Änderung für Android. Wird mit dem ersten iOS-Build (Codemagic/TestFlight) aktiv.

## 00.001.022
- FIX: Absturz auf älteren **32-bit-Geräten** (z. B. manche Tablets) behoben. Die Wake-Word-Erkennung (sherpa-onnx) ist auf 32-bit-ARM technisch nicht lauffähig (stürzte beim Laden des Modells ab) und wird dort jetzt automatisch deaktiviert – die App läuft normal, „connect" geht per Knopf statt per Sprache. Auf 64-bit-Geräten unverändert mit Sprachwort.

## 00.001.021
- FIX: Im Sprech-Bildschirm waren auf kleineren Displays – vor allem im Sparmodus mit Reglern und Schaltern – die unteren Knöpfe (Stumm/Verlassen) abgeschnitten und nicht bedienbar. Die Ansicht ist jetzt scrollbar, alle Knöpfe sind erreichbar.

## 00.001.020
- NEU: kurzer **„Verbunden"-Ping** beim eigenen Verbinden (per Knopf oder Wort „connect"). So hört man, dass der Kanal offen ist, ohne aufs Handy zu schauen – besonders beim Fahren/im Sparmodus, wo die gesprochene Beitritts-Ansage aus ist. Spielt nicht, wenn man nur von anderen automatisch mit-hochgezogen wurde.

## 00.001.019
- Wake-Word „connect" von Vosk auf **sherpa-onnx** (k2-fsa) umgestellt. Vorteile: läuft jetzt **auch auf iOS** (vorher nur Android), kleineres Modell (~5 MB statt ~40 MB → schlankere App) und **ältere Android-Geräte werden wieder unterstützt** (minSdk 30 → 23, ab Android 6). Bedienung unverändert: im Sparmodus „connect" sagen öffnet den Kanal; der „Verbinden"-Knopf bleibt überall die Alternative. (Vorbereitung für die iOS-Version.)

## 00.001.018
- ABRECHNUNG (unsichtbar, Übergangslösung): Weil Agora die echten Channel-Events (Beitritt/Verlassen) derzeit nicht an unseren Server liefert – nur Test-Pings kommen an, ein Support-Ticket läuft – misst die App jetzt die Verbindungszeit zum Gruppen-Kanal SELBST und meldet die Minuten beim Verlassen an Supabase (neue RPC `app_report_usage`, Supabase-Abschnitt 12 muss ausgeführt werden). Jedes Gerät meldet seine eigene Zeit; im Sparmodus werden mehrere Verbindungs-Fenster zusammengezählt. Damit hängt die Minuten-Verbuchung nicht mehr an Agoras Webhook. Hinweis: Bei hartem App-Schließen (Absturz) kann eine Meldung ausfallen; sobald Agoras Webhook wieder liefert, ist das die verlässliche Quelle. Keine sichtbare Änderung für Tester.

## 00.001.017
- GRUNDLAGEN Abrechnung/Abo (unsichtbar, Vorbereitung): DB-Datenmodell für Kontingent, Stufen (Free/Pro/Mega, Platzhalter), Verbrauch, Zukäufe (einheitlicher Minuten-Topf) und Zahler-Modus pro Gruppe angelegt (Supabase Abschnitt 10). App vergibt beim Live-Sprechen jetzt eine FESTE Agora-uid je Nutzer (für die spätere Minuten-Zuordnung) statt einer Zufalls-uid; greift erst, wenn das Datenmodell in Supabase ausgeführt ist – sonst unverändert. Keine sichtbare Änderung für Tester.

## 00.001.016
- NEU: Akku-Schalter „Freihändig mit connect". Im Sprech-Bildschirm (unter dem Sparmodus-Schalter) lässt sich das „connect"-Lauschen ein-/ausschalten. Aus = nur der Verbinden-Knopf öffnet, dafür kein Dauer-Lauschen aufs Mikro → spart Akku. Standard: an. Pro Gerät gemerkt. Kurzanleitung um den Sparmodus/„connect"-Abschnitt ergänzt.

## 00.001.015
- FIX Absturz beim Live-Sprechen mit Sparmodus (00.001.014): Die Vosk-Bibliothek stürzte beim Start mit „Can't obtain peer field ID for class com.sun.jna.Pointer" ab, weil ihre native JNA-Bibliothek nicht aus der APK entpackt werden konnte. Native Libs werden jetzt wieder entpackbar gepackt (useLegacyPackaging) + Proguard-Regeln für JNA/Vosk ergänzt. Sprachwort „connect" sollte jetzt laufen.

## 00.001.014
- NEU (experimentell): Sprachwort „connect" im Sparmodus. Im Leerlauf lauscht die App freihändig auf das gesprochene Wort „connect" und öffnet damit den Kanal (gleiche Wirkung wie der Verbinden-Knopf) – ideal beim Fahren. Läuft komplett offline auf dem Gerät (Vosk, ~40 MB Modell, daher ist die App größer geworden). Anzeige „höre auf connect …" im Leerlauf. Erkennung ist experimentell: draußen/bei Wind springt es evtl. nicht immer an – der Knopf bleibt als sichere Alternative. Verlassen weiter per Knopf / nach 1 Min Stille.

## 00.001.013
- ÄNDERUNG Sparmodus: Der automatische Pegel-Trigger (Kanal öffnet bei jedem Geräusch) war unpraktisch und ist raus. Der Kanal wird jetzt BEWUSST per großem „Verbinden"-Knopf geöffnet. Danach bleibt er offen, solange geredet wird, und schließt nach 1 Minute Stille von selbst (Fenster einstellbar 5–120 s, Standard 60 s). Öffnet einer, werden die anderen automatisch mit-hochgezogen. Das Sprachwort „connect" zum freihändigen Öffnen folgt im nächsten Build.

## 00.001.012
- NEU (experimentell): Sparmodus im Sprech-Bildschirm. Der Sprachkanal ist nur offen, wenn wirklich geredet wird – Aufwecken automatisch per Stimme (lokale Mikro-Erkennung), danach bleibt der Kanal 15 s offen (einstellbar 5–60 s), dann schließt er. Spart Verbindungszeit. Schalter + Fenster-Regler live im Sprech-Bildschirm, Voreinstellung pro Gerät gemerkt; Privatmodus solange ausgeblendet. Hinweis: Die allererste Sekunde beim Aufwecken kann fehlen (Puffer-Variante folgt bei Bedarf), und draußen kann Wind den Kanal wecken (Schwelle justierbar).

## 00.001.011
- FIX Stummschalten: Auf manchen Geräten (Tablet) schaltete „Stumm" nicht nur das Mikro, sondern auch die Wiedergabe ab – man hörte selbst nichts mehr. Stummschalten läuft jetzt über die Aufnahme-Lautstärke (0 = stumm), die Audio-Sitzung bleibt aktiv; Hören bleibt unberührt. Wirkt auf beiden Geräten gleich.

## 00.001.010
- FIX Privatmodus (Empfänger): Das Privat-„Start"-Signal kam beim Empfänger als „broadcast" an, weil unser Feld „type" mit dem Supabase-Nachrichtentyp kollidierte und überschrieben wurde. Feld in „aktion" umbenannt – der Empfänger tritt dem Privatkanal jetzt korrekt bei (hört den Sender, Knopf wechselt auf „Privat beenden", beidseitiges Beenden funktioniert). Diagnose-Anzeigen wieder entfernt.

## 00.001.009
- Temporäre Diagnose (Privatmodus): Beim Empfang eines Privat-Signals erscheint jetzt ein FESTES Fenster (bleibt stehen bis OK) mit allen empfangenen Feldern (type, from, to, channel) und der Angabe, ob der Beitritt ausgelöst wird. Damit finden wir, warum der Empfänger nicht in den Privatkanal kommt. Wird danach wieder entfernt.

## 00.001.008
- Testdurchlauf der Release-Verteilung: prüft, ob der vollständige Versionsverlauf im Changelog sichtbar ist und ob frühere Versionen weiter zum Download bereitstehen. Keine inhaltliche Änderung (die Privatmodus-Diagnose von 00.001.007 bleibt aktiv).

## 00.001.007
- Temporäre Diagnose: Schlägt der Beitritt zum Privatkanal beim Empfänger fehl, wird jetzt der genaue Agora-Fehler als Popup angezeigt. Dient nur dazu, die Ursache zu finden; wird danach wieder entfernt.

## 00.001.006
- Fix Privatmodus: Verlässt der Partner die Gruppe/Runde, wird der Privatmodus jetzt zuverlässig auch beim anderen beendet (Knopf zurück auf „Privat sprechen") – robuster Agora-Fallback, falls das „beenden"-Signal nicht ankam.
- Temporäre Diagnose: Beim Empfang eines Privat-Signals erscheint ein kurzes Popup (zeigt, ob das Signal ankommt und ob es für das Gerät bestimmt ist). Dient nur dazu, den Empfänger-Fehler einzugrenzen; wird danach wieder entfernt.

## 00.001.005
- Fix Privatmodus: im Privatgespräch wird keine falsche/veraltete „X spricht"-Anzeige der Gruppe mehr eingeblendet.
- Fix Privatmodus: der Empfänger sieht sofort das Banner mit „Privat beenden" und kann den Privatmodus für beide beenden.

## 00.001.004
- Zweiter Testdurchlauf des automatischen Build-/Installations-Wegs, diesmal auf zwei Geräte (Galaxy A71 + Tablet SM-T515). Keine inhaltliche Änderung; bestätigt die neue Versionsnummer auf beiden Geräten.

## 00.001.003
- Testdurchlauf des automatischen Build-/Installations-Wegs (pub get → Release-APK → Gerät). Keine inhaltliche Änderung; dient nur dazu, die neue Versionsnummer am Handy sichtbar zu bestätigen.

## 00.001.002
- Fix Live-Bereich: „X spricht"-Anzeige flac