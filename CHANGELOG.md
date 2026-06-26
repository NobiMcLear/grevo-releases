# Grevo – Änderungsliste

Schema der Version: **Hauptrelease.Versionszähler.Iteration** (z.B. 00.001.001).
Iteration steigt bei jedem Änderungsdurchlauf, der Versionszähler bei jeder fertigen Funktion.

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
