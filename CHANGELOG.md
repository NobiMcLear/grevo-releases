# Grevo – Änderungsliste

Schema der Version: **Hauptrelease.Versionszähler.Iteration** (z.B. 00.001.001).
Iteration steigt bei jedem Änderungsdurchlauf, der Versionszähler bei jeder fertigen Funktion.

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
