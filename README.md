# Lorentz Labor – eigenes Hosting

Dieses Paket läuft unabhängig von ChatGPT und benötigt keine Anmeldung, keine API-Schlüssel und keinen Build-Schritt. Die 3D-Bibliothek ist enthalten. Die Hosting-Version verwendet Systemschriften statt externer Google Fonts.

## 1. Eigener Webspace / Schulserver
Den INHALT dieses Ordners in einen öffentlich erreichbaren Ordner hochladen, z. B. public_html/lorentz/. Die Struktur einschließlich vendor/ beibehalten. Dann https://DEINE-DOMAIN/lorentz/ aufrufen.
Voraussetzungen: statisches HTTPS-Hosting; .js-Dateien müssen mit einem JavaScript-MIME-Typ ausgeliefert werden. PHP, Node.js und eine Datenbank werden nicht benötigt. GitHub-Workflow, netlify.toml und Anleitung müssen nicht mit hochgeladen werden.

## 2. Netlify
Bei Netlify anmelden. Unter https://app.netlify.com/drop den entpackten Ordner mit index.html hineinziehen. Netlify erzeugt eine eigene öffentliche URL. Alternativ ein Git-Repository mit diesen Dateien importieren: Build-Befehl leer lassen; Publish-Verzeichnis: .
Die beiliegende netlify.toml konfiguriert das Publish-Verzeichnis. Keine kostenpflichtigen Zusatzdienste erforderlich; die aktuellen Anbieterbedingungen beachten.

## 3. GitHub Pages
1. Ein neues Repository im eigenen GitHub-Konto anlegen (für kostenlose Pages-Nutzung gewöhnlich öffentlich).
2. Alle Dateien einschließlich .github/workflows/pages.yml ins Repository-Root übernehmen und auf den Standardbranch pushen. Keine Zugangsdaten hochladen.
3. Unter Settings → Pages → Build and deployment als Source „GitHub Actions“ wählen.
4. Unter Actions den Workflow „Deploy Lorentz Labor to Pages“ manuell starten. Nach Erfolg steht die öffentliche URL in Settings → Pages. Spätere Pushes auf den Standardbranch veröffentlichen automatisch.
Die relativen Asset-Pfade funktionieren auch unter https://BENUTZER.github.io/REPOSITORY/.

## Lokal ausprobieren
Im entpackten Ordner ausführen:
python3 -m http.server 8000
Dann http://localhost:8000 öffnen. Das direkte Öffnen von index.html per Doppelklick funktioniert wegen JavaScript-Modulen nicht zuverlässig.

## Modell und Technik
Leiterlänge 0,10 m, Masse 0,040 kg, Pendellänge 0,65 m. Schwerkraft, Lorentzkraft und lineare Dämpfung bestimmen die Bewegung; Annahmen stehen in „Die Physik dahinter“ in der Simulation.
Ein aktueller Browser mit WebGL ist erforderlich. Simulation und Daten bleiben im Browser. Three.js r170: MIT-Lizenz, siehe THREE-LICENSE.txt.

Die Dateien und der GitHub-Pages-Workflow sind in diesem Repository eingerichtet. Aktiviere unter Settings → Pages die Quelle „GitHub Actions“ und starte bei Bedarf den Workflow. Netlify und eigener Webspace benötigen noch die Einrichtung im jeweiligen Konto.
