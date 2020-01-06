# Churchtools-PDF Erstellung bei Domainfactory

Folgende Schritte sind notwendig um in Churchtools die PDF-Erstellung zu aktivieren, wenn Churchtools bei Domainfactory gehostet ist.
Für die Durchführung ist ein SSH-Zugang notwendig. Viele Anregung stammen aus folgendem Forum: https://forum.church.tools/topic/4377/datenauskunft-pdf-export-f%C3%BCr-self-hoster-auf-gehostetem-webspace

## pdfgen anstelle von phantomjs

Da bei DF phantomjs nicht installiert ist und auch nicht lauffähig ist, hat Joachim Meyer ein Script geschrieben, welches die PDF-Erstellung anstelle von phantomjs übernimmt. 
**Vielen Dank an "Joachim Meyer"!** Siehe auch https://forum.church.tools/user/fodinabor

* Im Hauptordner (darin befindet sich die index.php) von Churchtools ein Unterordner "bin" anlegen
* Die Dateien "composer.json", "pdfgen.php", ".htacess" und "phantomjs" in den bin Ordner kopieren. 
* Die Dateien pdfgen.php und phantomjs müssen ausführbar gemacht werden.
```
$ chmod 0755 pdfgen.php
$ chmod 0755 phantomjs
```

## Composer installieren

* Im Home-Verzeichnis (/kunden/XXXXXX_XXXXX) die Datei .bashrc zum Ändern öffnen: 
```
$ nano .bashrc
```
* Folgende Zeilen am Ende anhängen:
```
alias php7cli='/usr/local/bin/php7.2.23-cli'
alias composer='php7cli ~/composer.phar'
alias php='/usr/local/bin/php7.2.23-cli'
```
* SSH-Konsole schließen und erneut öffnen (damit die neuen Alias-Einstellungen geladen werden)
* Composer installieren
```
curl -sS https://getcomposer.org/installer | php7cli
```
* Installation überprüfen
```
$ composer -V
```

## Notwendige Abhängigkeiten installieren

* Composer mit install im ordner bin (in dem Ordner muss die composer.json liegen) ausführen
```
$ composer install
```

Das war's nun muss die PDF-Erstellung funktionieren!