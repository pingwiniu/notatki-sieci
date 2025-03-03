# Ćwiczenia z Metasymboli Powłoki Linux - Wyjaśnienie

## Informacje o Uczniu
- **Imię i Nazwisko**: Dominika Kuklińska
- **Numer w Dzienniku**: 12
- **Konto**: dominika12

## Ćwiczenia z Dopasowywania Wzorców

### Które pliki pasują do następujących wzorców:

`ls *.doc`
- Dopasowuje wszystkie pliki z rozszerzeniem .doc: pictures.doc, ebook1.doc

`echo file[0-9].txt`
- Dopasowuje pliki o nazwach od file0.txt do file9.txt

`touch \*\?`
- Tworzy plik o nazwie dosłownej "*?"

`echo .*`
- Dopasowuje wszystkie ukryte pliki: .bash_history oraz inne ukryte pliki w katalogu

### Polecenia ze Zmiennymi Powłoki:

```bash
sciezka=`pwd`
echo $sciezka
```
- Ustawia zmienną `sciezka` na ścieżkę bieżącego katalogu roboczego
- Wyświetla ścieżkę bieżącego katalogu

```bash
echo "* mój katalog to $HOME"
```
- Wyświetla: * mój katalog to /home/dominika12

```bash
echo 'mój katalog to $HOME *.*'
```
- Wyświetla dosłownie: mój katalog to $HOME *.*
- (Pojedyncze cudzysłowy zapobiegają rozwinięciu zmiennej)

```bash
cd "~"
```
- Próbuje przejść do katalogu o nazwie dosłownej "~", prawdopodobnie spowoduje błąd
- (Nie jest to katalog domowy, ponieważ ~ musi być bez cudzysłowów, aby nastąpiło rozwinięcie)

### Tworzenie Plików i Dopasowywanie Wzorców:

Utworzone pliki:
```bash
touch .bash_history pictures.doc pic1.jpg pic2.jpg pic3.jpg prace.txt "file1?" "File2?" ebook1.doc ebook1.pdf gzp3 text
```

Dopasowania wzorców:
1. `.*`
   - Dopasowanie: .bash_history

2. `p??[123]*`
   - Dopasowanie: pic1.jpg, pic2.jpg, pic3.jpg

3. `?ile?\?`
   - Dopasowanie: file1?, File2?

4. `*1.*`
   - Dopasowanie: pic1.jpg, file1?, ebook1.doc, ebook1.pdf

5. `ebook*`
   - Dopasowanie: ebook1.doc, ebook1.pdf

6. `???[a-z]`
   - Dopasowanie: text

## Przetwarzanie Tekstu za Pomocą grep

Zawartość pliku "slowa":
```
od wtorku do soboty
od soboty do niedzieli
nie ma dnia wolnego
dla komputera naszego
pracuje od rana do wieczora
wiec szacunek dla naszego procesora
```

1. Linie zawierające "do":
```bash
cat slowa | grep "do"
```
- Wynik:
  - od wtorku do soboty
  - od soboty do niedzieli
  - pracuje od rana do wieczora

2. Linie zaczynające się od "od":
```bash
cat slowa | grep "^od"
```
- Wynik:
  - od wtorku do soboty
  - od soboty do niedzieli

3. Linie kończące się słowem "soboty":
```bash
cat slowa | grep "soboty$"
```
- Wynik:
  - od wtorku do soboty

4. Linie niezawierające "do":
```bash
cat slowa | grep -v "do"
```
- Wynik:
  - nie ma dnia wolnego
  - dla komputera naszego
  - wiec szacunek dla naszego procesora

5. Liczba linii zawierających "bot":
```bash
cat slowa | grep -c "bot"
```
- Wynik: 1

## Przykłady Użycia Polecenia find

1. Znajdź wszystkie pliki .jpg w całym systemie plików:
```bash
find / -name "*.jpg" 2>/dev/null
```

2. Znajdź wszystkie foldery w /home zawierające "bash":
```bash
find /home -type d -name "*bash*" 2>/dev/null
```

3. Znajdź wszystkie puste foldery należące do użytkownika root w /etc:
```bash
find /etc -type d -empty -user root 2>/dev/null
```

4. Znajdź wszystkie pliki z uprawnieniami 777 w /home:
```bash
find /home -type f -perm 777 2>/dev/null
```

5. Znajdź wszystkie pliki z numerem i-węzła 1:
```bash
find / -inum 1 2>/dev/null
```

## Dodatkowe Polecenia

1. Wypisz polecenia w /usr/bin z podziałem na strony:
```bash
ls /usr/bin | more
```

2. Konwersja małych liter na duże przy użyciu tr:
```bash
cat mojePliki.txt | tr '[a-z]' '[A-Z]' > MOJEPLIKI.TXT
```

3. Użycie tee do wyświetlenia i zapisania zalogowanych użytkowników:
```bash
who | tee zalogowani
```
