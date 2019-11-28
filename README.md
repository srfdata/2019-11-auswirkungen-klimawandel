# 2019-11-auswirkungen-klimawandel

## Vorbemerkungen

Dieses Dokument beschreibt die Vorprozessierung und explorative Analyse des Datensatzes, der Grundlage des auf srf.ch veröffentlichten Artikel [XYZ](https://www.srf.ch/data) ist.

SRF Data legt Wert darauf, dass die Datenvorprozessierung und -Analyse nachvollzogen und überprüft werden kann. SRF Data glaubt an das Prinzip offener Daten, aber auch offener und nachvollziehbarer Methoden. Zum anderen soll es Dritten ermöglicht werden, auf dieser Vorarbeit aufzubauen und damit weitere Auswertungen oder Applikationen zu generieren. 

Die Endprodukte des vorliegenden Scripts, neben der vorliegenden explorativen Analyse, sind JSON-Dateien zu den Klimaszenarien für jede Gemeinde und ein JSON-File mit allen Metainformationen zu den Gemeinden.

* `output/climate_projections_bfsId.json`: Das Skript generiert 2212 Dateien, für jede Gemeinde eine Datei. Die Dateien tragen jeweils die Gemeindenummer des Bundesamts für Statistik (BfS) im Dateinamen. In den Dateien sind alle Klimavariablen enthalten, zwei simulierte Szenarien, alle drei Zeitperioden und alle drei Schätzungen.

* `output/municipalities.json`: Metainformationen zu allen Gemeinden, Gemeindestand 1. Januar 2019.

### R-Script & Daten

Die Vorprozessierung und Analyse wurde im Statistikprogramm R vorgenommen. Das zugrunde liegende Script sowie die prozessierten Daten können unter [diesem Link](https://srfdata.github.io/2019-11-auswirkungen-klimawandel/rscript.zip) heruntergeladen werden. Durch Ausführen von `main.Rmd` kann der hier beschriebene Prozess nachvollzogen und der für den Artikel verwendete Datensatz generiert werden. Dabei werden Daten aus dem Ordner `input` eingelesen und Ergebnisse in den Ordner `output` geschrieben. 

SRF Data verwendet das [rddj-template](https://github.com/grssnbchr/rddj-template) von Timo Grossenbacher als Grundlage für seine R-Scripts.  Entstehen bei der Ausführung dieses Scripts Probleme, kann es helfen, die Anleitung von [rddj-template](https://github.com/grssnbchr/rddj-template) zu studieren. 

### GitHub

Der Code für die vorliegende Datenprozessierung ist auf [https://github.com/srfdata/2019-11-auswirkungen-klimawandel](https://github.com/srfdata/2019-11-auswirkungen-klimawandel) zur freien Verwendung verfügbar. 


### Lizenz

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons Lizenzvertrag" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Dataset" property="dct:title" rel="dct:type">2019-11-auswirkungen-klimawandel</span> von <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/srfdata/2019-11-auswirkungen-klimawandel" property="cc:attributionName" rel="cc:attributionURL">SRF Data</a> ist lizenziert unter einer <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Namensnennung - Weitergabe unter gleichen Bedingungen 4.0 International Lizenz</a>.

### Weitere Projekte

Code & Daten von [SRF Data](https://srf.ch/data) sind unter [https://srfdata.github.io](https://srfdata.github.io) verfügbar.

### Haftungsausschluss

Die veröffentlichten Informationen sind sorgfältig zusammengestellt, erheben aber keinen Anspruch auf Aktualität, Vollständigkeit oder Richtigkeit. Es wird keine Haftung übernommen für Schäden, die  durch die Verwendung dieses Scripts oder der daraus gezogenen Informationen entstehen. Dies gilt ebenfalls für Inhalte Dritter, die über dieses Angebot zugänglich sind.