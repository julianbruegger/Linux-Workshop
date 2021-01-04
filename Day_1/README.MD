# Erster Tag des LINUX-Workshops

## Ihnalt des heutigen Tages
- Einführung und überblick über Linux
- Befehle
-

## Befehle 
|Befehl |Argumente  |Funktion   |
|------ |--------   |-          |
|cd     |           | wechsel des verzeichnises|
|ls     | -l, -ls, -la           |Auflistung der Verzeichnisse|
|cat    |-less (seitenweise)|Damit können Dateien direkt im Terminal angezeigt werden           |
|tail   | -f (liveausgabe)           |Ausgabe der letzten 7 linien des files|
|grep   |       | Suche nach etwas in file `grep "root" /etc/passwd`         |
|netstat|    |      Zeigt alle offenen Ports btw. Netzwerkverbindungen|
|rm| -r (rekursiv)    |      löscht das ausgewählte File|
|top| |      prozessübersicht|
|free|-m (mega), -g (giga)|Freier Arbeitsspeicher|



### Verbinden von Befehlen mittels Pipe

Mit einer Pipe `|` können Outputs in ein neues Programm weitergegeben werden. 

```sh

cat /etc/passwd | grep "root"

```

## vi editor

Zum Schreben im Editor muss der "INSERT" modus verwendet werden. Dieser wird über die `insert` Taste gestartet. Über `Esc` kann der Modus beendet werden. 

Im Standartmodus kann über `dd` ganze Zahlen gelöscht werden.

Der vi kann mit `:x` & `ENTER` beendet werden. 

Im standartmodus können elemente mit `yy` kopiert werden, diese können dann mit `pp` gepastet werden. 



|Befehl     |Funktion           |
|:------:   |:-----             |
|yy         |Kopieren der Zeile |
|pp         |Einfügen der Zeile |
|dd         |löschen der Zeile  |
|:x         |Exit & Save        |
|:q!        |Exit & Dump        |