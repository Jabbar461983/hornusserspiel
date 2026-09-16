# Abschlag ins Ries — Einbau in ClubDesk

Zwei Varianten, beide ohne externe Abhängigkeiten ausser den Schriften von Google Fonts.

## Variante A — schlankste HTML-Datei (empfohlen)

Ordner `clubdesk/`:

    spiel.html          37 kB   die ganze Seite samt Spiellogik
    bilder/             77 kB   Emblem, Beachflag, vier Sponsorenlogos

Beide Teile in dieselbe Ebene der ClubDesk-Dateiablage laden, so dass `bilder/` ein
Unterordner von `spiel.html` bleibt. Anschliessend verlinken oder einbetten:

    <iframe src="pfad/zu/spiel.html" style="width:100%;height:900px;border:0"
            title="Hornusser Minispiel"></iframe>

## Variante B — eine einzige Datei

`hornusser-einzeldatei.html` (140 kB) enthält die Bilder eingebettet. Nur eine Datei
hochladen, keine Ordnerstruktur nötig. Nimm diese Variante, wenn ClubDesk keine
Unterordner zulässt.

## Was gegenüber der Arbeitsversion entfallen ist

Die Arbeitsversion (`Hornusser Minispiel.dc.html`) war mit allem Drum und Dran
1084 kB gross. Weggefallen sind:

- React und die Komponentenbibliothek des Design Systems — die vier Bildschirme sind
  jetzt gewöhnliches HTML, die Logik ist einfaches JavaScript
- die eingebetteten Schriftdateien — die drei Schriften kommen über einen
  `<link>` von Google Fonts
- die Design-System-Stylesheets — die benötigten Farben, Schriftrollen und Abstände
  stehen als knapp 40 Zeilen CSS im Kopf der Datei
- Bildgrössen: Emblem 162 kB → 29 kB (JPEG, 360 px), Beachflag 91 kB → 14 kB,
  Sponsorenlogos je 12–15 kB → 8–10 kB

Unverändert sind Spielmechanik, Grafik, Masken und Rangliste.

## Grenzen

Die Rangliste liegt im Browser-Speicher des einzelnen Geräts
(`localStorage`, Schlüssel `ehf2027-hornusser-rangliste`). Sie ist damit pro Besucher,
nicht gemeinsam, und die Newsletter-Anmeldung wird nirgends versandt. Für eine
gemeinsame Rangliste und den Versand braucht es eine Server-Schnittstelle; im Quelltext
ist die Stelle der Klick auf «Abschicken» (`el('send')`).
