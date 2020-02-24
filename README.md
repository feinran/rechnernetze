
# Internet-Schichtenmodell:

- Host-to-Network (Ethernet, WLAN 802.11b, PPP, DSL)
- Vermittlungsschicht (IPv4, IPv6)
- Transportschicht (TCP, UDP)
- Anwendungsschicht (SMTP, HTTP, FTP, SSL)

Router:
- Vermittlungsschicht
- Host-to-Network


# ISO/OSI Refernezmodell

Alle deutschen Studenten trinke verschieden Sorten Bier.

- Bitübertragung (Strom, Licht)
- Sicherung (CRC, CSMA, MAC)
- Vermittlung (IPvX, Wireguard)
- Transport (TCP, UDP, Multiplexing, Flusskontrolle)
- Sitzung (RTCP, SMPP)
- Darstellung (Telnet, ICA)
- Anwendung (SMTP, HTTP, FTP, SSL)

Router:
- Bitübertragung
- Sicherung
- Vermittlung


# Multiplexverfahren

1. Raummultiplexverfahren
2. Frequenz-
3. Codierung-
4. Zeit-


# CRC

Irreduziebles Polynom: Ein Polynom, dass kein Vielfaches eines kleineren Polynoms ist.
(x^4 + 1) ist reduzibel: (x^2 + 1)(x^2 - 1)

Man kann eine Nachricht leicht veränden, ohne dass die CRC-Summe (Prüfsumme) sich ändert.
Dazu addiert man einfach die CRC-Summe irgendwo zur Nachricht (nicht zur Prüfsumme selbst!)

Aufgabe: Berechnen Sie mit CRC eine 4-Bit Kontrollsume der Eingabe
0101 1011 1101 0010 für das Generatorpolynom x^5 + x^4 + x^2 + 1

Verfahren:
1. Eingabe + 0 * Grad des Generatorpolynoms
2. Führende Nullen kann man wegstreichen
3. Generatorpolynom umwandeln (hier: 110101)
4. Rechnung durchführen:
   
```
010110111101001000000 : 110101
 110101
 ------
  1100011101001000000
  110101
  ------
     1001101001000000
     110101
     ------
      100111001000000
      110101
      ------
       10010001000000
       110101
       ------
        1000101000000
        110101
        ------
         101111000000
         110101
         ------
          11010000000
          110101
          ------
               100000
               110101
               ------
                10101
```

5. Ergebins ist dann Eingabe + CRC (hier: 0101 1011 1101 0010 10101)
   

# Datenbanken

SELECT(Projektion: pi) FROM(Verbund: ><) WHERE(Selektion: o)

Gleiche Reihen fallen in der Mathematischen schreibweise oder mit "Select Distinct" raus,
wegen der Definition von Mengen (Jedes Element unique)


# Flag Bits

FLAG + NACHRICHT + FLAG

Eine gute achtstellige FLAG-Bit-Sequenz ist 0111 1110 oder 1000 0001.
Dann muss man nur nach jeder 5. 1/0 eine 0/1 stopfen.


# HTTP

TCP Pakete bei einem HTTP Request:

```
   TCP Verbindungsaufbau ->
<- Acknowledgment
   HTTP Request + Ack    ->
<- HTTP Response
   Acknowledgment + Fin   ->
<- Acknowledgment + Fin
   Acknowledgment
```

Jetzt ist die Connection 2 half closed


# TCP Stauvermeidung

Tahoe:
- Wenn timeout ist der threshhold die hälfte
- Anfang mit slowstart (exp) bis threshhold
- Bei threshhold additive increase

Tahoe:
- Wenn timeout ist der threshhold die hälfte
- Anfang bei threshhold
- Bei threshhold additive increase

# Hamming Distanz

Code-Buch:
- A 0000 0000
- B 0100 0011
- C 0011 1001
- D 1110 0101
- E 1010 1111

Hamming Distanz ist die Anzahl der unterschiedlichen Bits:
```
d(A, B) = 3
d(A, E) = 6
d(B, C) = 4
```

Hamming Distanz eines Code-Buches ist der kleinste abstand zwischen zwei Codewörtern im Buch.
```
d = d(A, B) = 3
```

`d - 1 = 2` Bitfehler können *erkannt* werden  
`(d - 1) / 2 = 1` Bitfehler können *korrigiert* werden

0100 0000 wird zu A korrigiert weil nur ein Bit sich von A unterscheidet.


# Dämpfung

In Dezibell: 10log_10(Seendeenergie / Empfangsenergie)

- Allgemeine Dämpfung (Tunnel)
- Frequenzverlust (WLAN 2.4/5GHz)
- Frequenzabhängige Dämpfung (Langes Kabel schlecht für hohe Frequenzen)
- Störung und Verzerrung (Meherere Sender auf der gleichen Frequenz)
- Rauschen (Mikrofon + Handy)


# Kodierungen

Manchester Code:
```
Wechsel von hoch zu niedrig = 1
Wechsel von niedrig zu hoch = 0
```

Selbstaktender Code hat bei jedem Gesendeten Bit einen Spannungswechsel, damit kann man sicher
sein immer synchronisiert zu sein und ratet auch bei vielen aufeinanderfolgenden 0en oder 1en nich aus dem Takt.


# QAM

Große Amplitude -> Äußerer Ring
Kleine Amplitude -> Innerer Ring

Phase wird immer Zum vorhereigen Verschoben.

```
3/4 | 1/4
---------
5/4 | 7/4
```


# CDMA

Multiplexverfahren kein Verschlüsselungsverfaheren.

Symbolkodierungen sind immer Vektoren orthogonal zueinander.  
```
Sender A: 1 = (1, 1), 0 = (-1, -1)  
Sender B: 1 = (1, -1), 0 = (-1, 1)

Empfangen: (0, 2)
Sender A: (1, 1) * (0, 2) > 0 => 1
Sender B: (1, -1) * (0, 2) < 0 => 0
```

