Die PDF-Datei enthält die Präsentation von der Konferenz als auch die Folien des Workshops. Die Folien enthalten alle Informationen darüber, wie man das Starter-Projekt zum Entwickeln von JavaScript-Projekten für FileMaker benutzen kann. Im Folgenden eine Kurzanleitung, wie man vorgehen kann.

## Voraussetzungen

- installiertes Node.js [https://nodejs.org/](https://nodejs.org/)
- installiertes git-System
  - unter MacOS ist es bereits vorhanden
  - unter Windows muss es von [https://git-scm.com/downloads](https://git-scm.com/downloads) heruntergeladen und installiert werden
- ein Editor wie VSCode [https://code.visualstudio.com/](https://code.visualstudio.com/)

## Kurzanleitung für die Nutzung des CLI-Tools

Im Terminal kann man mit folgendem Befehl ein CLI-Tool herunterladen, welches man zum Initialisieren eines Starter-Projektes nutzen kann.

```bash
npm i -g @agametis/create-app-for-fm
```

Nach der Installation kann man in jedem Verzeichnis mit folgendem Befehl ein neues Projekt initiieren.

```bash
create-app-for-fm
```

Das Starter-Projekt ist das erste (fm-starter-vite) in der Liste der zur Auswahl stehenden Projekte.

**Alternativ:** falls es bei der Installation zu Problemen mit Zugriffsrechten kommt, kann man das Tool mit dem folgenden Befehl auch temporär nutzen:

```bash
npx @agametis/create-app-for-fm
```

Eine Lösung für die Zugriffsrechte-Problematik kann unter anderem unter dem Link [https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally) gefunden werden.

### Nutzung des Projektes

Wenn man ein Projekt initialisiert hat, befindet sich im Stammverzeichnis des Projektes ein Beispiel Node.js-Projekt inklusive einer FileMaker-Datei. In der `README.md`-Datei gibt es weitere Hinweise zum Projekt.

Mit `npm run dev` startet man im Terminal den Enticklungserver. Mit `q+enter` oder `ctrl+c` kann man den Server wieder stoppen.

Nachfolgend noch ein paar Anmerkungen zu Problemen, die während des Workshops aufgetreten sind.

## Troubleshooting

### JS-Bibliotheken noch nicht installiert

Falls man das Starter-Projekt direkt von [https://github.com/agametis/fm-starter-vite](https://github.com/agametis/fm-starter-vite) per Zip oder `git clone` heruntergeladen hat, muss nach dem Entpacken/Herunteladen der Befehl `npm install` im Installationsverzeichnis ausgeführt werden. Dieser stellt sicher, dass alle JavaScript-Bibliotheken im Projekt lokal vorhanden sind. Mit diesem Befehl wird das Verzeichnis `node_modules` erstellt, in dem sich alle Bibliotheken befinden. Bei der Nutzung des CLI-Tools von oben entfällt dieser Schritt, weil das Tool sich darum kümmert, die JavaScript-Bibliotheken zu installieren.

### Port des lokalen Webservers ist nicht 5173

Falls das Ausführen des Skriptes `npm run dev` den Server nicht auf Port 5173 laufen lässt, bedeutet das, dass im Hintergrund ein anderer Dienst diesen Port verwendet. Um das zu beheben, muss entweder der Dienst auf Port 5173 beendet werden oder wenn er nicht beendet werden kann oder darf, Nutzt `npm run dev` in der Regel den nächsten freien Port. Das kann zum Beispiel der Port 5174 sein. Der neuer Port muss entsprechend das FileMaker-Skript `Aktualisiere WebViewer` angepasst werden.

### Projekt wird im Browser geöffnet

Wenn man die Adresse `http://localhost:5173/` direkt im Browser öffnet, funktioniert das Projekt nicht so, wie man es erwartet. Das liegt daran, dass im Kontext des Browsers das FileMaker-Element, mit der Funktion `PerformScriptWithOptions()` nicht verfügbar ist. Sobald man das Projekt in einem FileMaker-Layout im WebViewer nutzt, ist das FileMaker-Element verfügbar.

