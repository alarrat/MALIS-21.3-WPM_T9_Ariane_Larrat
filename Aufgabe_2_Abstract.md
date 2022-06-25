# Aufbereitung einer digitalen Bildsammlung als Webcontent (Python Script)

## Abstract

In dieser Aufgabe 2 soll der Versuch unternommen werden, den in Aufgabe 1 dargelegten optimierten Prozess teilweise umzusetzen. Ziel dieses Vorgehens ist es in erster Linie, einen Probedatensatz an Bilddateien als Web Content aufzubereiten und die dafür erforderlichen #UmsetzungsSchritte durchzuführen.

### Zum Probedatensatz

Der Probedatensatz enthält insg. 27 Bilddateien, davon 9 Dateien im Format .png und 18 Dateien im Format .jpeg. 
Bei ersteren handelt es sich um Wordpress Logo-Bilder mit einer Größe von ca. 200 x 200 px und bei letzteren um sog. WordPress Blogpost-Bilder mit einer Größe von ca. 1200 x 630 px (Bei WordPress handelt es sich um das verwendete CMS, in dem das Bildmaterial als Webcontent zur Verfügung gestellt werden soll). Die Dateien liegen gesammelt bisher in einem Verzeichnis "data" vor.


## Ziele

Vorrangiges Ziel der Aufbereitung der Bilddateien als Webcontent ist es, die Performance und UX im CMS zu verbessern, die unstrukturierte Ablagestruktur und Benennung zu organisieren und dabei das Potential der vorhandenen Metadaten zu nutzen.


## Umsetzungsschritte

Umd die o. g. Ziele zu erreichen, sollen die folgenden Umsetzungsschritte erfolgen:

### A. Dateiumbenennung mit Metdaten der Bilddateien und Suffix

Teilziel dieser Umsetzung ist es, alle .jpeg-Bilddateien mit der Benennung YYYYMMDD_hhmmss_header und alle .png-Billdateien mit der Benennung YYYYMMDD_hhmmss_thumbnail auszuzeichnen. In diesem Schritt sollen zunächst alle Bilder im Ursprungsverzeichnis "data" adressiert werden. Anschließend soll das Bearbeitungsdatum (modification date) aus den Metadaten der Bilddateien ausgelesen werden. Es wird das modification date verwendet, da dieses ausschlaggebend für den Redaktionsprozess in der Bildredaktion ist, da es angibt, wann die Bilder zuletzt modifiziert wurden. Der ausgelesene UNIX timestamp soll anschließend in die menschenlesbare UTC time umgewandelt werden mit der entsprechenden Ansetzungsform nach ISO 8601. Als letztes sollen die Bilddateien umbenannt werden mit den entsprechenden Suffix "Header" und "Thumbnail".

### B. Modifikation der Header-Bilder (Grautöne und Skalierung)

Damit die Header-Bilder in das Visual Design der Website mit dem CMS WordPress passen, soll der RGB-Farbraum der Bilder in Grautöne umgewandelt werden. Ferner werden die Blogpost-Bilder mit einer derzeitigen Größe von 1200 x 630 px auf eine Größe von 1048 x 550 px skaliert, um sie als Header-Bilder verwenden zu können.


### C. Modifikation der Thumbnail-Bilder (nur Skalierung)

Damit die Thumbnail-Bilder als solche verwendet werden können, müssen diese von einer Größe von 200 x 200 px auf eine Größe von 150 x 150 px skaliert werden. Hierfür soll das Skript zur Modifikation der Header-Bilder nachgenutzt werden.


### D. Konvertierung als WebP-Dateien

Die vorhandenen Bilddateien in den Formaten .png und .jpeg bieten einige Herausforderung im Handling im WordPress CMS, insb. die Performance betreffend. Um die Bilddateien in ihrer Größe zu reduzieren und anschließend für das Web nutzen zu können, sollen diese als WebP-Grafiken konvertiert werden. Dabei sollen die Bilddateien aus dem ursprünglichen Verzeichnis beibehalten werden und in einem neuen Ordner mit der Bezeichnung "WebP" abgelegt werden.

### E. Speicherung in zwei Ordnern 

In einem letzten Schritt werden die in den Schritten A-D modifzierten Bilddateien in eine neue Ordnerstruktur überführt. Alle .jpeg-Dateien sollen in einem Ordner data_webp_header und alle .png-Dateien in einem Ordner data_webp_thumbnails abgelegt werden.