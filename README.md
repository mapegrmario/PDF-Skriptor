# PDF Skriptor

Ein PDF-Werkzeugkasten für Linux, der die Funktionen bündelt, die im
Büroalltag am häufigsten gebraucht werden – und die in der Linux-Welt
sonst nur verstreut oder gar nicht vorhanden sind.

## Funktionen

**Büroalltag-Kernmodule**
- **Organisieren**: PDFs zusammenfügen, in Einzelseiten trennen, Seiten
  drehen, einzelne Seiten löschen
- **Formulare**: PDF-Formularfelder direkt ausfüllen und speichern
- **Metadaten**: Titel, Autor, Betreff, Stichwörter einzeln oder für
  mehrere Dateien gleichzeitig bearbeiten (Batch-Modus)
- **Komprimieren**: Dateigröße verringern, mit Vorschau-Vergleich aller
  Qualitätsstufen vor dem Speichern
- **Sicherheit**: Passwortschutz mit Einschränkung von Druck- und
  Kopierrechten
- **Anmerkungen**: Freihand-Notizen (frei wählbare Farbe/Strichstärke),
  Hervorhebungen und wiederverwendbare Text-Stempel direkt auf der
  Seitenansicht; einzelne Anmerkungen per Radierer-Werkzeug gezielt
  wieder entfernen; Unterschrift einmalig zeichnen und beliebig oft
  platzieren
- **Lesezeichen**: Inhaltsverzeichnis anzeigen, Einträge hinzufügen/
  löschen/umsortieren, per Klick direkt zur Zielseite springen
- **Kopf-/Fußzeile**: Text mit Platzhaltern (Seitenzahl, Datum,
  Aktenzeichen) auf jede Seite anwenden, inkl. fortlaufender
  Aktenzeichen-Nummerierung mit Präfix und Startwert
- **Wasserzeichen**: Diagonaler Text (Farbe, Schriftgröße, Transparenz,
  Drehwinkel frei wählbar) auf jede Seite anwenden
- **PDF/A-Archivierung**: Umwandlung nach PDF/A-2b für die
  Langzeitarchivierung (z. B. GoBD-konforme Rechnungsablage)
- **Suche**: Volltextsuche im aktiven Dokument mit farbiger
  Trefferhervorhebung und Sprung zwischen Treffern (auch seitenübergreifend)
- **Seiten neu ordnen**: Seiten als Vorschaubilder per Drag & Drop in
  eine neue Reihenfolge bringen
- **Digitale Signatur**: Kryptographische Signatur (PKCS#7) mit
  selbstsigniertem oder vorhandenem Zertifikat erzeugen; Signaturen
  beliebiger PDF-Dateien auf Unversehrtheit prüfen

**Alleinstellungsmodule** (in der Linux-Welt selten oder gar nicht vorhanden)
- **OCR**: Durchsuchbare PDFs aus Scans erzeugen (Deutsch/Englisch)
- **Vergleich**: Zwei PDF-Versionen Seite für Seite vergleichen, mit
  farbig markierten Änderungen
- **Redaction**: Inhalte dauerhaft entfernen – per Textsuche oder
  manuell markierter Bereich (kein bloßer schwarzer Balken)
- **Konvertierung**: PDF → Markdown/Text mit automatischer
  Tabellenerkennung
- **Batch-Pipeline**: Werkzeuge zu einer Kette verbinden und auf alle
  PDFs eines Ordners anwenden (z. B. „alle Rechnungen: komprimieren →
  Passwort setzen")

## Bedienung

PDF Skriptor orientiert sich am Aufbau eines Schreibprogramms: Das
Dokument steht permanent im Zentrum des Fensters - egal welches
Werkzeug gerade gewählt ist, bleibt die Dokumentenansicht unverändert
sichtbar (inklusive Seitennavigation und Zoom). Werkzeug-spezifische
Optionen erscheinen in einer schmaleren Spalte rechts daneben.

Die Dokumentenansicht lässt sich stufenlos zoomen (40–400 %): über die
„−"/„+"-Knöpfe unterhalb der Seite, per Strg+Mausrad, oder durch einen
Klick auf die Prozentanzeige, um auf 100 % zurückzusetzen.

Diese rechte Spalte zeigt zugleich die **einzige Navigation** der
Anwendung: eine Übersicht mit Begrüßung und Schnellzugriffs-Kacheln zu
allen Werkzeugen (inklusive Einstellungen, Hilfe und Über-dieses-
Programm) - ein Klick auf eine Kachel springt direkt zum jeweiligen
Modul. Über den „☰ Menü"-Knopf in der kompakt gehaltenen Werkbank
gelangt man von jedem Werkzeug aus wieder zu dieser Übersicht zurück.

Alle geladenen Dateien erscheinen oben in der Werkbank als anklickbare
Chips - bei vielen Dateien wird der Bereich automatisch scrollbar
(Mausrad oder Scrollbalken). Dateien lassen sich per **Drag & Drop**
von einem beliebigen Dateimanager aus irgendwo im Fenster ablegen,
oder über „Dateien auswählen" laden. Ein Klick auf einen Chip macht
die Datei zur **aktive Datei** - mit ihr arbeitet das gerade gewählte
Werkzeug, und sie erscheint sofort in der zentralen Dokumentenansicht.
Über das „×" an einem Chip lässt sich eine einzelne Datei gezielt
wieder entfernen.

Bei den Werkzeugen **Anmerkungen** und **Redaction (manuell)** wird
direkt auf der zentralen Dokumentenansicht gezeichnet bzw. markiert -
es gibt keine separate, doppelte Seitenansicht mehr dafür.

## Systemvoraussetzungen

Getestet unter Debian-basierten Distributionen (Ubuntu, Linux Mint,
LMDE, MX Linux) sowie Fedora, openSUSE und Arch Linux.

- Python 3.10 oder neuer
- Ghostscript (für die Komprimierungsfunktion und die PDF/A-Archivierung)
- ocrmypdf + Tesseract mit deutschen/englischen Sprachdaten (für OCR)

## Installation

**Automatisch (empfohlen):**

```bash
chmod +x install.sh
./install.sh
```

Das Skript erkennt die Distribution, installiert alle Systempakete
(Ghostscript, ocrmypdf, Tesseract, python3-tk) über den passenden
Paketmanager, legt die virtuelle Python-Umgebung an, installiert die
Python-Abhängigkeiten und richtet einen **Startmenü-Eintrag** ein
(„PDF Skriptor" erscheint danach im Anwendungsmenü der Distribution,
z. B. unter „Büro").

**Manuell:**

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

Systempakete dann je nach Distribution manuell installieren (siehe
Tabelle unten).

| Distribution | Befehl |
|---|---|
| Ubuntu / Linux Mint / MX Linux | `sudo apt install ghostscript ocrmypdf tesseract-ocr-deu tesseract-ocr-eng python3-tk` |
| Fedora | `sudo dnf install ghostscript ocrmypdf tesseract-langpack-deu tesseract-langpack-eng` |
| openSUSE | `sudo zypper install ghostscript ocrmypdf tesseract-ocr-traineddata-deu` |
| Arch Linux | `sudo pacman -S ghostscript ocrmypdf tesseract-data-deu tesseract-data-eng` |

Fehlt Ghostscript oder ocrmypdf, weist die Anwendung beim Start darauf hin.

## Start

Nach der Installation über das Startmenü („PDF Skriptor") oder:

```bash
./run.sh
```

Alternativ manuell:

```bash
source venv/bin/activate
python3 main.py
```

## Analyse/Diagnose

Bei Problemen (z. B. eine Funktion meldet einen Fehler) hilft das
Analyse-Script, ohne die GUI starten zu müssen:

```bash
./analyse.sh
```

Es prüft die installierten Systemabhängigkeiten (Ghostscript, ocrmypdf,
Tesseract, qpdf), freien Speicherplatz in `/tmp` und im Ausgabeordner
(relevant bei OCR-Problemen), zeigt die aktuellen Einstellungen, gibt
einen Überblick über die Dateien im Ausgabeordner und zeigt die
letzten Einträge aus `fehler.log`. Optionen:

```bash
./analyse.sh --help
./analyse.sh --output-dir=/pfad/zum/ordner
./analyse.sh --log-lines=50
./analyse.sh --full-log
```

## Einstellungen und Protokolle

- Einstellungen werden unter `~/.config/pdf-skriptor/` gespeichert.
- Fehler werden in `fehler.log` im Programmordner protokolliert.
- Details zu Architektur und Testergebnissen stehen in `analyse.md`.

## Autor

Mario Peeß, Großenhain
E-Mail: mapegr@mailbox.org

## Haftungsausschluss

Dieses Programm wurde mit größter Sorgfalt entwickelt. Für Datenverlust
oder Schäden, die durch die Nutzung dieser Software entstehen, wird
keine Haftung übernommen. Bitte erstellen Sie vor wichtigen
Bearbeitungen stets eine Sicherungskopie Ihrer Dokumente.

## Verwendete Drittanbieter-Software

- CustomTkinter (MIT-Lizenz)
- pypdf (BSD-Lizenz)
- pikepdf / qpdf (MPL 2.0 / Apache-Lizenz)
- PyMuPDF / MuPDF (AGPL-Lizenz)
- Pillow (HPND-Lizenz)
- pyHanko / pyhanko-certvalidator (MIT-Lizenz)
- cryptography (Apache-2.0- oder BSD-3-Clause-Lizenz)
- Ghostscript (AGPL-Lizenz, externes Systemprogramm)
- ocrmypdf / Tesseract OCR (MPL 2.0 / Apache-Lizenz, externe Systemprogramme)
