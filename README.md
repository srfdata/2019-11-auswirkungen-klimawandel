# 2019-11-auswirkungen-klimawandel

## Vorbemerkungen

Dieses Dokument beschreibt die Vorprozessierung und explorative Analyse des Datensatzes, der Grundlage des auf srf.ch veröffentlichten Artikel [XYZ](https://www.srf.ch/data) ist.

SRF Data legt Wert darauf, dass die Datenvorprozessierung und -Analyse nachvollzogen und überprüft werden kann. SRF Data glaubt an das Prinzip offener Daten, aber auch offener und nachvollziehbarer Methoden. Zum anderen soll es Dritten ermöglicht werden, auf dieser Vorarbeit aufzubauen und damit weitere Auswertungen oder Applikationen zu generieren. 

Die Endprodukte des vorliegenden Scripts, neben der vorliegenden explorativen Analyse, sind JSON-Dateien zu den Klimaszenarien für jede Gemeinde und ein JSON-File mit allen Metainformationen zu den Gemeinden. (Datenbeschreibung siehe unten):

* `output/climate_projections_bfsId.json`: Das Skript generiert 2212 Dateien, für jede Gemeinde eine Datei. Die Dateien tragen jeweils die Gemeindenummer des Bundesamts für Statistik (BfS) im Dateinamen. In den Dateien sind alle Klimavariablen enthalten, zwei simulierte Szenarien, alle drei Zeitperioden und alle drei Schätzungen.

* `output/municipalities.json`: Metainformationen zu allen Gemeinden, Gemeindestand 1. Januar 2019.

### R-Script & Daten

Die Vorprozessierung und Analyse wurde im Statistikprogramm R vorgenommen. Das zugrunde liegende Script sowie die prozessierten Daten können unter [diesem Link](https://srfdata.github.io/`r project_name`/rscript.zip) heruntergeladen werden. Durch Ausführen von `main.Rmd` kann der hier beschriebene Prozess nachvollzogen und der für den Artikel verwendete Datensatz generiert werden. Dabei werden Daten aus dem Ordner `input` eingelesen und Ergebnisse in den Ordner `output` geschrieben. 

SRF Data verwendet das [rddj-template](https://github.com/grssnbchr/rddj-template) von Timo Grossenbacher als Grundlage für seine R-Scripts.  Entstehen bei der Ausführung dieses Scripts Probleme, kann es helfen, die Anleitung von [rddj-template](https://github.com/grssnbchr/rddj-template) zu studieren. 

Debug-Informationen: *This report was generated on `r Sys.time()`. R version: `r paste0(version$major, ".", version$minor)` on `r version$platform`. For this report, CRAN packages as of `r package_date` were used.*

### GitHub

Der Code für die vorliegende Datenprozessierung ist auf [https://github.com/srfdata/`r project_name`](https://github.com/srfdata/`r project_name`) zur freien Verwendung verfügbar. 


### Lizenz

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons Lizenzvertrag" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Dataset" property="dct:title" rel="dct:type">`r project_name`</span> von <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/srfdata/`r project_name`" property="cc:attributionName" rel="cc:attributionURL">SRF Data</a> ist lizenziert unter einer <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Namensnennung - Weitergabe unter gleichen Bedingungen 4.0 International Lizenz</a>.

### Weitere Projekte

Code & Daten von [SRF Data](https://srf.ch/data) sind unter [https://srfdata.github.io](https://srfdata.github.io) verfügbar.

### Haftungsausschluss

Die veröffentlichten Informationen sind sorgfältig zusammengestellt, erheben aber keinen Anspruch auf Aktualität, Vollständigkeit oder Richtigkeit. Es wird keine Haftung übernommen für Schäden, die  durch die Verwendung dieses Scripts oder der daraus gezogenen Informationen entstehen. Dies gilt ebenfalls für Inhalte Dritter, die über dieses Angebot zugänglich sind.

### Datenbeschreibung

#### `output/climate_projections_bfsId.json`

Für jede, der 2212 Gemeinden wird eine JSON-Datei generiert mit allen nötigen Klimavariablen, Szenarien, Perioden und Schätzungen.

| Attribut | Typ | Beschreibung |
|-------|------|-----------------------------------------------------------------------------|
| bfs_id | Number | Gemeindenummer |
| key | String | Klimavariable (FD, snowdays, ID, SD, HD, TN, tas und pr) |
| period | String  | Zeitpunkt, den die Simulation abbiulden soll (1981-2010, 2035, 2060, 2085) |
| estimate | String | Schätzwerte für die Berechnungen, q5, q50 und q95 |
| rcp | String | Unterschiedliche Klimaszenarios (obs, RCP2.6, RCP8.5) |
| season | String | Wert für die Jahreszeit, nur vorhanden bei den Variablen pr und tas |


#### `output/municipality.json`

| Attribut | Typ | Beschreibung |
|-------|------|-----------------------------------------------------------------------------|
| bfs_id | Number | Gemeindenummer |
| name | String | Gemeindename |
| altitude | String  | Höhenlage der Gemeinde |
| region | String | Grossregion der Gemeinde |
| urban | Boolean | Grosstadt oder Agglomeration |


### Originalquelle

Die «Klimaszenarien CH2018» sind Simulationen mit insgesamt 21 verschiedenen Computermodellen, die am EURO-CORDEX («Coordinated Regional Climate Downscaling Experiment – European Domain») betrieben werden. Das Projekt wird vom Weltklimaforschungsprogramm (WRCP) gesponsert.
Die regionalen Klimasimulationen berücksichtigen drei verschiedene Szenarien, je nach Entwicklung der Treibhausgasemissionen:

Die regionalen Klimasimulationen berücksichtigen drei verschiedene Szenarien, je nach Entwicklung der Treibhausgasemissionen:

* Kein Klimaschutz (RCP8.5): Die klimawirksamen Emissionen nehmen stetig zu (hier verwendet als «pessimistisches Szenario»)

* Konsequenter Klimaschutz (RCP2.6): Der Anstieg der Treibhausgase in der Atmosphäre kann bis in 20 Jahren gestoppt werden (hier verwendet als «optimistisches Szenario»)

* Begrenzter Klimaschutz (RCP4.5): Eine mittlere Entwicklung mit begrenztem Klimaschutz (hier nicht verwendet)

Die Klimaszenarien CH2018 beziehen sich jeweils auf einen Mittelwert der geschätzten klimatischen Verhältnisse über einen längeren Zeitraum. Wenn es im Text «2035» heisst, bezieht sich das auf die nahe Zukunft von 2020-2049. Ist die Rede von «2060», geht es um die Mitte des Jahrhunderts (2045-2074) und «2085» bezieht sich auf das Ende des Jahrhunderts (2070-2099). Als Referenzperiode gilt der Zeitraum von 1981 bis 2010. Werte von «heute» sind also gemittelte Messwerte über diesen Zeitraum.

Diese Projektionen der Klimamodelle sind jedoch nicht exakt, sondern streuen immer über einen gewissen Bereich. Der Median davon entspricht am ehesten dem absehbaren Wert und wird als «erwartetes» Ergebnis behandelt.

##### Gitternetz-Daten der Klimaszenarien 2018
Die Daten wurden im Dateiformat [netCDF](https://www.unidata.ucar.edu/software/netcdf/docs/netcdf_introduction.html) geliefert. Für jede Klimavariable gibt es einen Ordner.

&rarr; `input/FD_obs_CH2018`

In diesem Ordner befinden sich die Dateien zu den Frosttagen.

&rarr; `input/HD_obs_CH2018`

In diesem Ordner befinden sich die Dateien zu den Hitzetagen

&rarr; `input/ID_obs_CH2018`

In diesem Ordner befinden sich die Dateien zu den Eistagen.

&rarr; `input/SD_obs_CH2018`

In diesem Ordner befinden sich die Dateien zu den Sommertagen.

&rarr; `input/snowdays_obs_CH2018`

In diesem Ordner befinden sich die Dateien zu den Schneetagen.

&rarr; `input/TN_obs_CH2018`

In diesem Ordner befinden sich die Dateien zu den Tropennächten.

&rarr; `input/tas_obs_CH2018`

In diesem Ordner befinden sich die Dateien zu den Tagesmittelwerten für die Temperatur nach Jahreszeit.

&rarr; `input/pr_obs_CH2018`

In diesem Ordner befinden sich die Dateien zu den Tagesmittelwerten für Niederschlag nach Jahreszeit.


#### Klimatische Regionen
&rarr; `input/climate_regions`

In diesem Ordner befinden sich die Dateien aufgeteilt und gemittelet nach Region. In jeder Datei sind alle Klimavariablen, Szenarien etc. vorhanden. Das Dateiformat ist ebenfalls netCDF.

#### Gemeindegrenzen
&rarr; `input/gd-b-00.03-875-gg17`

Die Shapedateien für die Gemeinden und Kantonen können hier runtergeladen werden: [Generalisierte Gemeindegrenzen](https://www.bfs.admin.ch/bfs/de/home/dienstleistungen/geostat/geodaten-bundesstatistik/administrative-grenzen/generalisierte-gemeindegrenzen.assetdetail.1902553.html).

#### Grossregionen

&rarr; `input/Grossregionen`
Die Shapedatei zu den Grossregionen bildet die regionale Einteiung ab, die MeteoSchweiz für die Bewertung der Risiken und Chancen verwendet hat.