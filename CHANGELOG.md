# Grevo – Änderungsliste

Schema der Version: **Hauptrelease.Versionszähler.Iteration** (z.B. 00.001.001).
Iteration steigt bei jedem Änderungsdurchlauf, der Versionszähler bei jeder fertigen Funktion.

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
- Fix Live-Bereich: „X spricht"-Anzeige flackerte weg, weil Agoras lokale Lautstärke-Meldung die Sprecherliste leerte – jetzt steuert nur die Remote-Meldung die Anzeige.
- Fix Live-Bereich: Namen verschwanden, wenn ein Gerät in den Hintergrund ging (Bildschirm aus). Namensliste wird jetzt zwischengespeichert und erst entfernt, wenn Agora die Person wirklich als offline meldet.

## 00.001.001
- Erste Versionierung; Versionsbalken unten auf jeder Maske eingeführt.
- Sammelstand der bis dahin uncommitteten Tagesarbeit: Privatmodus-Fix (gleichzeitiger Start), gesprochene Ansagen (Privat-Modus / -aus, Gruppe beigetreten/verlassen) mit weiblicher/männlicher Stimme und An/Aus im Profil, Android-Hintergrund-Service (Mikro bei aus-Bildschirm), Kurzanleitung aktualisiert.
