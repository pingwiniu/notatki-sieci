# Steps 6-11: Detailed Linux File Manipulation Tasks

## Step 6: Creating Duplicated Names File
```bash
# Duplicate the contents of imiona file twice
cat ~/imiona ~/imiona > ~/imiona2
```

### Expected Result
```
Arek
Szymon
Jakub
Iga
Ala
Mela
Ola
Marcin
Piotr
Patrycja
Kinga
Alan
Arek
Szymon
Jakub
Iga
Ala
Mela
Ola
Marcin
Piotr
Patrycja
Kinga
Alan
```

## Step 7: Sorting and Unique Names
```bash
# Sort names alphabetically and remove duplicates
sort ~/imiona2 | uniq
```

### Expected Output
```
Alan
Ala
Arek
Iga
Jakub
Kinga
Marcin
Mela
Ola
Patrycja
Piotr
Szymon
```

## Step 8: Counting Files and Errors
```bash
# Count files matching "imiona*"
find / -name "imiona*" | wc -l

# Count generation of errors
find / -name "imiona*" 2>&1 | wc -l
```

### Alternative Error Counting Method
```bash
# Redirect errors to a file and count
find / -name "imiona*" 2> error_log
wc -l error_log
```

## Step 9: Using tee Command
```bash
# Display first 5 lines of passwd and save to file
head -n 5 /etc/passwd | tee ~/uzytkownicy

# Verify file contents
cat ~/uzytkownicy
```

### Uppercase Name Transformation
```bash
# Convert names to uppercase, display and save
cat ~/imiona | tr '[:lower:]' '[:upper:]' | tee ~/IMIONA
```

## Step 10: Creating Directories and Archives
```bash
# Create directory structure
mkdir -p ~/Ksiazki/Podreczniki ~/Ksiazki/Literatura

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
```

## Step 11: Multiple Archive Formats
```bash
# Create 7z archive
7z a ~/Ksiazki.7z ~/Ksiazki

# Remove original directory
rm -rf ~/Ksiazki

# Extract 7z archive
7z x ~/Ksiazki.7z

# Create zip archive
zip -r ~/Ksiazki.zip ~/Ksiazki

# Unzip archive
unzip ~/Ksiazki.zip

# List contents to verify
ls ~/Ksiazki
```

## Step 12: Additional File Listing
```bash
# Create file with detailed directory listing
ls -ali > ~/pliki.txt
```
