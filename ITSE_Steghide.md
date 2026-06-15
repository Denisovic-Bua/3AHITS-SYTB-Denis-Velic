
# 📑 SSH Private Key Bericht


![Student](https://img.shields.io/badge/Student-Denis%20VELIC-lightblue?style=for-the-badge&logo=github)
![Klasse](https://img.shields.io/badge/Klasse-3AHITS-blue?style=for-the-badge&logo=googleclassroom&logoColor=white)
![Datum](https://img.shields.io/badge/Datum-15.06.2026-darkblue?style=for-the-badge&logo=googlecalendar&logoColor=white)

## 👤 Basisinformationen
| **Thema** | [1001_steganographie_ue01](https://github.com/HTL-Braunau-probst/ITSE-3-LAB-AHITS23/blob/main/1001_steganographie_ue01.md)

| **Fach** | ITSE 


---

## Was ist Steghide?
**Steghide** ist ein OpenSource Tool für **Sternographie**, das heißt es versteckt geheim Daten in einem Bild- oder Audiodatei, ohne das es sich vom Original optisch oder akustisch verändert.

- **Unterstütze Formate:**
  - JPEG, BMP, WAV und AU-Dateien

 Es arbeitet mit dem Verschlüsselungsverfahren AES-128

## Sternographie Anwenden:
**Bild zum Sternographieren:**
<img width="360" height="360" alt="freakbob" src="https://github.com/user-attachments/assets/0dccd2ec-d53c-4c40-aa7b-602ea63b7765" />

Dann in der Shell:
```sh

echo "ja würde ich" > geheim.txt

steghide embed -ef geheim.txt -cf freakbob.jpg -sf stego_bild.jpg

# Dann muss man halt den Passphrase eingeben
```
Wenn man das Bild jetzt jemanden schickt + Passphrase dazu:
```sh
steghide extract -sf stego_bild.jpg 
Enter passphrase: 
the file "geheim.txt" does already exist. overwrite ? (y/n) y
wrote extracted data to "geheim.txt".
```

**Bild verändert:**


<img width="360" height="360" alt="stego_bild" src="https://github.com/user-attachments/assets/b92275a6-84bb-4470-94f5-62233a05dc0c" />
