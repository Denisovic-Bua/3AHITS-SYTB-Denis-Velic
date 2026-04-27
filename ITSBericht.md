# 📑 SSH Private Key Bericht


![Student](https://img.shields.io/badge/Student-Denis%20VELIC-lightblue?style=for-the-badge&logo=github)
![Klasse](https://img.shields.io/badge/Klasse-3AHITS-blue?style=for-the-badge&logo=googleclassroom&logoColor=white)
![Datum](https://img.shields.io/badge/Datum-27.04.2026-darkblue?style=for-the-badge&logo=googlecalendar&logoColor=white)

## 👤 Basisinformationen
| **Thema** | [0802_ssh_private_key_ue01](https://github.com/HTL-Braunau-probst/ITSE-3-LAB-AHITS23/blob/main/0802_ssh_private_key_ue01.md)

| **Fach** | ITSE 


---

## SSH Key 

### Kali 2 ( Server ) Konfigurieren

Die Anleitung auf [GeeksForGeeks](https://www.geeksforgeeks.org/linux-unix/how-to-enable-and-start-ssh-on-kali-linux/)

**Shell**
```sh
sudo apt update 

sudo apt install openssh-server

sudo systemctl start ssh

sudo systemctl enable ssh
```

Jetzt Probier auf **Kali 1** dich mit SSH auf **Kali 2** zu verbinden
```sh
ssh kali@192.168.11.53
```

### Kali 1

```sh
ssh-keygen

ssh-copy-id kali@192.168.11.53

ssh kali@192.168.11.53
```
Jetzt solltest du dich ohne Passwort einloggen können

**Datein am Server ( Kali 2) nach `ssh-copy ip kali@192.168.11.53`:**
- **Datei**: `~/.ssh/authorized_keys` wurde generiert
- Der Public key wurde geändert
- Das Verzeichnis .ssh 700, die Datei 600

**Dateien am Kali 1:**
- Die Datei `known_hosts` wurde aktualisiert

## 3. Übung Zeitmessung
Schreibe 2 Skripts: time_start.sh und time_stop.sh. Bei Aufruf von `time_stop.sh` wird die Anzahl der Sekunden ausgegeben die seit dem letzten Aufruf von `time_start.sh` vergangen sind.

**time_start.sh:**

```sh
#!/bin/bash

# Aktuelle UNIX-Zeit ermitteln
start_zeit=$(date +%s)

# Zeit temporär speichern
echo $start_zeit > /tmp/start_zeit.txt

```

**time_stop.sh:**

```sh
#!/bin/bash

# Startzeit aus der Datei lesen
start_zeit=$(cat /tmp/start_zeit.txt)

# Aktuelle Zeit ermitteln
stop_zeit=$(date +%s)

# Differenz rechnen
vergangen=$((stop_zeit - start_zeit))

# Ergebnis 
echo "$vergangen Sekunden sind vergangen."
```

**Ausgabe:**
```sh
./time_start.sh
# Paar sekunden warten
./time_stop.sh
5
```

