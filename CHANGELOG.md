## 01.001.010
- FIX: Beendet der Sponsor sein Sponsoring im Gruppen-Detail (oder ohne in der Sprechrunde zu sein), merken es jetzt ALLE Verbundenen zuverlaessig (Supabase-Realtime) und werden gefragt.
- FIX: Nach dem Verlassen der Sprechrunde wird die Gruppen-Detailseite neu geladen (kein veraltetes Bezahlt von... mehr). Android + iOS.

## 01.001.009
- NEU: Der Sponsor kann sein Sponsoring selbst beenden (auch ohne Admin) - Sponsoring beenden im Sprech-Bildschirm und im Gruppen-Detail. Danach zahlt die Gruppe wieder selbst.
- NEU: Beendet der Sponsor waehrend einer laufenden Runde, werden die Verbundenen gefragt: auf eigene Kosten weiter (Ja) oder trennen (Nein / keine Antwort nach ca. 20s).
- VERBESSERT: Gruppen-Uebersicht frischt die Verbindungsanzahl regelmaessig automatisch auf. Android + iOS.

# Grevo – Änderungsliste

Schema der Version: **Hauptrelease.Versionszähler.Iteration** (z.B. 00.001.001).
Iteration steigt bei jedem Änderungsdurchlauf, der Versionszähler bei jeder fertigen Funktion.

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