# Tag 2

## Ihnalt des heutigen Tages
- systemctl
- Script
- Partitionierung
- Benutzerverwaltung


## systemctl

Deamon Verwaltungstool um Hintergrundprozesse zu verwalten. 

## Script 

```sh
script.sh &
#Skript läuft nun um Hintergrund
```

Das Skript kann auch in den Hintergrund gesetzt werden. 
Die Eingabe von `bg` setzt das Skript in den Background. 
Die Eingabe von`fg` setzt das Skript wieder in den Vordergrund. 

## Partitionierung

Dient underanderm dazu das Systemverzeichnisen nicht vollgemüllt werden

Mit dem Befehl `lsblk` werden alle Partitionen angezeigt. 

`pvs` zeigt das Physikalische Volume an. 

`vgs` zeigt die Grösse der Volume Gruppe an. 

```sh

[root@lx-server2021 ~]# lsblk
NAME            MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda               8:0    0   35G  0 disk 
├─sda1            8:1    0  500M  0 part /boot
└─sda2            8:2    0 34.5G  0 part 
  ├─vg01-root   253:0    0  500M  0 lvm  /
  ├─vg01-swap   253:1    0  956M  0 lvm  [SWAP]
  ├─vg01-usr    253:2    0  2.8G  0 lvm  /usr
  ├─vg01-tmp    253:3    0    1G  0 lvm  /tmp
  ├─vg01-srv    253:4    0    8M  0 lvm  /srv
  ├─vg01-home   253:5    0    8M  0 lvm  /home
  ├─vg01-opt    253:6    0    8M  0 lvm  /opt
  ├─vg01-var    253:7    0  1.9G  0 lvm  /var
  └─vg01-docker 253:8    0    5G  0 lvm  /var/lib/docker
sr0              11:0    1 1024M  0 rom  

```
**/dev/sda** entspricht dem ganzen Verzeichnis. 

**/dev/sda/sda1** entspricht einer Partition

### Erstellen einer Partition

Erstellend der Partition
```sh
lvcreate -L 1G --name lv01 vg01
#Logical volume "lv01" created.
```

Nun wird dem Volume ein Dateisystem hinzugefügt. 

```sh
mkfs.ext4 /dev/vg01/lv01 
```

Nun wird die Partition noch gemountet. 

```sh
 mount /dev/vg01/lv01  /lv01/
```
Vergrössern des Volumes.
```sh
lvextend  -L 2G /dev/vg01/lv01 
```

Nun wird das Filesystem auch noch angepasst. 

```sh
resize 2fs /dev/vg01/lv01 
```

## Benutzerverwaltung

Der Root user in Linux entspricht dem Windows Andminstrator

### Anzeigen

Die User & Gruppen können über den Befehl `id` angezeigt werden. 

```sh
[root@lx-server2021 ~]# id
uid=0(root) gid=0(root) groups=0(root) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023

```

Auch sind alle Benutzer im `/etc/passwd` file gespeichert. 

### Wesshalb Benutzer

Am besten wird für jeden Prozess ein eigener User erstellt. Dieser sollte keine Rootrechte haben. Somit kann dieser kaum Schaden anrichten auf dem Gerät. 

### Erstellen eines neuen Users
```sh
useradd -c "Hanslii" -m hansli01
# -c Kommentar
#-m Homeverzeichnis
```

### Userwechsel
```sh
su - hansli01
```

### Passwort

```sh
passwd hansli01
```
## Gruppen
Für jeden User wird auch eine Gruppe erstellt. 
