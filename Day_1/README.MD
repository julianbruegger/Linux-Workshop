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

### Verbinden von Befehlen mittels Pipe

Mit einer Pipe `|` können Outputs in ein neues Programm weitergegeben werden. 

```sh

cat /etc/passwd | grep "root"

```