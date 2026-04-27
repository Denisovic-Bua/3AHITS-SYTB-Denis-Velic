# 📑 SSH Private Key Bericht


![Student](https://img.shields.io/badge/Student-Denis%20VELIC-lightblue?style=for-the-badge&logo=github)
![Klasse](https://img.shields.io/badge/Klasse-3AHITS-blue?style=for-the-badge&logo=googleclassroom&logoColor=white)
![Datum](https://img.shields.io/badge/Datum-27.04.2026-darkblue?style=for-the-badge&logo=googlecalendar&logoColor=white)

## 👤 Basisinformationen
| **Thema** | [0802_ssh_private_key_ue01](https://github.com/HTL-Braunau-probst/ITSE-3-LAB-AHITS23/blob/main/0802_ssh_private_key_ue01.md)

| **Fach** | ITSE 


---

## Theorie
In der Bash ist die Doppelklammer-Arithmetik (( )) der neuste und schnellste Standard für Ganzzahlberechnungen im **C Schreib Stil** Während `let` und `expr` ältere Alternativen sind, ermöglichen die Klammern eine saubere Syntax mit Leerzeichen und direkten Variablenzuweisungen ohne das $-Zeichen zu benutzen



## 1. Übung Multiplizierer

Erstelle ein Skript das 2 Zahlen als Kommandozeilenargumente übernimmt. Multipliziere diese Zahlen und gib das Ergebnis aus, verwende jede der 3 besprochenen Methoden.

**multi.sh:**
```sh
#!/bin/bash

# Zahlen aus den Argumenten holen
Zahl1=$1
Zahl2=$2

# 1.Methode "let"

let Ergebnis1=$Zahl1*$Zahl2
echo "let: $Ergebnis1"

# 2. Methode "expr"

Ergebnis2=$(expr $Zahl1 \* $Zahl2)
echo "expr: $Ergebnis2"

# 3. Methode "Doppelklammer(())"

Ergebnis3=$(( Zahl1 * Zahl2))
echo "(()): $Ergebnis3"
```
**Ausgabe:**
```sh
./multi.sh 5 6
let: 30
expr: 30
(()): 30
```
Bei expr musst man das `\*` schreiben damit die Shell nicht denkt du meinst alle Dateien im Ordner.

Bei der Doppelklammer kannst du innerhalb der Klammern das $-Zeichen weglassen

## 2. Übung Werkstatt Summe

Schreibe ein shell Script dass die Summe aller Beträge in klassenkassa.csv mit dem Text Werkstatt in ermittelt.

**werkstatt.sh:**
```sh
#!/bin/bash

# grep sucht "Werkstatt" cut holt Spalte 3. zweites cut entfernt Nachkommastellen 
# paste verbindet alles mit +
ausdruck=$(grep "Werkstatt" klassenkassa.csv | cut -d',' -f3 | cut -d'.' -f1 | paste -sd+ -)

# 2. Berechnung 
ergebnis=$((ausdruck))

# 3. Ausgabe
echo "Der Ausdruck: $ausdruck"
echo "Die Summe: $ergebnis" (GANZZAHL)
```
**Augabe:**
```sh
./werkstatt.sh
Der Ausdruck: 15+13+42+23+33+5+25+7+15+18+6+10+15+8+14+18+12+14+12+13+6+8
Die Summe: 322
```
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

