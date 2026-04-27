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

## Edwards curves für SSH
- Konfiguration: `ssh-keygen -t ed25519` Danach wie gewohnt mit `ssh-copy-id` übertragen.
- Vorteile:
  - Sicherer weil keine bekannte Schwachstelle oder Hintertüren
  - Schneller weil die Berechnungen sind CPU schonender
  - Der Schlüssel ist viel kürzer als ein 4096-Bit RSA Key
 
## Windows Login

Windows mit ssh verbinden ohne passwort zu nutzen

**Windows Powershell öffnen:**
```sh
ssh-keygen

cat ~/.ssh/id_ed25519.pub | ssh denis.velic@10.10.10.11 "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >>  ~/.ssh/authorized_keys"
```
wenn ich jetzt eingebe `ssh denis.velic@10.10.10.11` kann ich mich direkt verbinden mit ssh ohne Passwort

