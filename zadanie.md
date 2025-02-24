

### 3. User Account Setup
```bash
sudo useradd -m -g users -G wheel DominikaX12
sudo passwd DominikaX12
sudo usermod -aG wheel DominikaX12
```

## Task 1: File Creation and Manipulation

### Create Initial Names File
```bash
cat > ~/imiona << EOF
Arek
Szymon
Jakub
Iga
Ala
Mela
Ola
Marcin
Piotr
EOF
```

### Append Additional Names
```bash
echo "Patrycja" >> ~/imiona
echo "Kinga" >> ~/imiona
echo "Alan" >> ~/imiona
```

### Verify File Contents
```bash
cat ~/imiona
```

## Task 2: File Search and Error Redirection

### Find Files with Error Handling
```bash
# Find and redirect errors
find / -name "imiona" 2> ~/errors
more ~/errors

# Redirect stdout and stderr
find / -name "imiona" 2>/dev/null 1>~/findResult
cat ~/findResult

# Combine stdout and stderr
find / -name "imiona" >& ~/findResultsErrors
```

### Filter Search Results
```bash
cat ~/findResultsErrors | grep "/sys/"
```

## Task 3: File Duplication and Sorting

### Create Duplicated Names File
```bash
cat ~/imiona ~/imiona > ~/imiona2
```

### Sort and Remove Duplicates
```bash
sort ~/imiona2 | uniq
```

## Task 4: File Counting and Transformation

### Count Files and Errors
```bash
# Count found files
find / -name "imiona*" | wc -l

# Count errors
find / -name "imiona*" 2>&1 | wc -l
```

### Text Transformation
```bash
# Display first 5 lines of passwd
head -n 5 /etc/passwd | tee ~/uzytkownicy

# Convert names to uppercase
cat ~/imiona | tr '[:lower:]' '[:upper:]' | tee ~/IMIONA
```

## Task 5: Archiving and Compression

### Create Directory Structure
```bash
mkdir -p ~/Ksiazki/Podreczniki ~/Ksiazki/Literatura
```

### Create and Manage Archives
```bash
# Create tar archive
tar -cvf ~/Ksiazki.tar ~/Ksiazki

# List archive contents
tar -tvf ~/Ksiazki.tar

# Compress with gzip
gzip ~/Ksiazki.tar
mv ~/Ksiazki.tar.gz ~/Ksiazki.tar.gz

# Decompress
gunzip ~/Ksiazki.tar.gz
tar -xvf ~/Ksiazki.tar

# Create 7z archive
7z a ~/Ksiazki.7z ~/Ksiazki

# Create zip archive
zip -r ~/Ksiazki.zip ~/Ksiazki

# Unzip
unzip ~/Ksiazki.zip
```

### Create LS Output File
```bash
ls -ali > ~/pliki.txt
```



