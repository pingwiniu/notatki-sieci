# Adresacja IP - materiały do kartkówki

## 1. Podział adresów IP na klasy

### Klasa A
- Zakres: 0.0.0.0 - 127.255.255.255
- Pierwszy oktet: 0-127
- Domyślna maska: 255.0.0.0 (/8)
- Format: N.H.H.H (N-sieć, H-host)

### Klasa B
- Zakres: 128.0.0.0 - 191.255.255.255
- Pierwszy oktet: 128-191
- Domyślna maska: 255.255.0.0 (/16)
- Format: N.N.H.H

### Klasa C
- Zakres: 192.0.0.0 - 223.255.255.255
- Pierwszy oktet: 192-223
- Domyślna maska: 255.255.255.0 (/24)
- Format: N.N.N.H

### Klasa D (multicast)
- Zakres: 224.0.0.0 - 239.255.255.255
- Pierwszy oktet: 224-239

### Klasa E (zarezerwowana)
- Zakres: 240.0.0.0 - 255.255.255.255
- Pierwszy oktet: 240-255

## 2. Adresy prywatne vs publiczne

### Adresy prywatne
- 10.0.0.0 - 10.255.255.255 (klasa A)
- 172.16.0.0 - 172.31.255.255 (klasa B)
- 192.168.0.0 - 192.168.255.255 (klasa C)

### Adresy publiczne
- Wszystkie pozostałe adresy IP, które nie należą do zakresów prywatnych
- Używane w internecie
- Muszą być unikalne w skali globalnej

## 3. Zapisy maski podsieci

### Notacja dziesiętno-kropkowa
Przykłady:
- 255.0.0.0
- 255.255.0.0
- 255.255.255.0
- 255.255.255.128
- 255.255.255.192

### Notacja CIDR (prefiksowa)
- /8  = 255.0.0.0
- /16 = 255.255.0.0
- /24 = 255.255.255.0
- /25 = 255.255.255.128
- /26 = 255.255.255.192

## 4. Przykład obliczania adresów

Dla adresu IP: 192.168.1.100/24

1. Adres sieci:
   - Wykonaj AND logiczny między IP a maską
   - 192.168.1.100 AND 255.255.255.0
   - Wynik: 192.168.1.0

2. Adres rozgłoszeniowy:
   - Zamień wszystkie bity hosta na 1
   - Wynik: 192.168.1.255

3. Zakres adresów hostów:
   - Od: adres sieci + 1 (192.168.1.1)
   - Do: adres rozgłoszeniowy - 1 (192.168.1.254)
