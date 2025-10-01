# Linux Commands Cheat Sheet

## Základné navigačné príkazy

### pwd (Print Working Directory)
Zobrazí aktuálnu cestu k adresáru, v ktorom sa nachádzate.
```bash
pwd
```

### cd (Change Directory)
Presun medzi adresármi.
```bash
cd Desktop/C++          # Presun do konkrétneho adresára
cd .                    # Zostať v aktuálnom adresári
cd ..                   # Presun o úroveň vyššie
cd ~                    # Presun do domovského adresára
```

## Práca s adresármi

### mkdir (Make Directory)
Vytvorenie nového adresára.
```bash
mkdir test                      # Vytvorí adresár "test"
mkdir test/hello                # Vytvorí adresár "hello" v adresári "test"
mkdir -p random/middle/hello    # Vytvorí celú cestu adresárov naraz
```

### ls (List)
Zobrazenie obsahu adresára.
```bash
ls                      # Základné zobrazenie súborov a adresárov
ls -a                   # Zobrazí aj skryté súbory (začínajúce s .)
ls -l                   # Detailné zobrazenie s právami a informáciami
ls -al                  # Kombinácia -a a -l
ls -R                   # Rekurzívne zobrazenie aj podadresárov
```

## Práca so súbormi

### touch
Vytvorenie prázdneho súboru.
```bash
touch names.txt              # Vytvorí súbor "names.txt"
touch test/houses.txt        # Vytvorí súbor v adresári "test"
```

### cat (Concatenate)
Zobrazenie, vytvorenie a spájanie súborov.
```bash
cat file.txt                 # Zobrazí obsah súboru
cat > file.txt               # Vytvorí súbor a umožní písanie (ukončenie: Ctrl+C)
cat file.txt two.txt > total.txt    # Spoji obsah dvoch súborov do tretieho
```

### cp (Copy)
Kopírovanie súborov a adresárov.
```bash
cp file.txt copy_file.txt    # Skopíruje súbor
cp -R test random            # Rekurzívne kopírovanie adresára
```

### mv (Move)
Presun a premenovanie súborov a adresárov.
```bash
mv names.txt random          # Presunie súbor do adresára
mv file.txt newName.txt      # Premenuje súbor
mv names.txt ../newNames.txt # Presunie a premenuje súbor
```

### rm (Remove)
Vymazávanie súborov a adresárov.
```bash
rm file.txt                  # Vymaže súbor
rm -R folder                 # Vymaže adresár rekurzívne
rm -rf folder                # Vynútené vymazanie bez potvrdenia
```

## Textové operácie

### echo
Zobrazenie textu alebo zápis do súboru.
```bash
echo "hello world"           # Vypíše text
echo "banzai" > file.txt     # Zapíše text do súboru
```

### tr (Translate)
Preklad znakov.
```bash
cat file.txt | tr a-z A-Z > upper.txt    # Prevedie malé písmená na veľké
```

### head a tail
Zobrazenie začiatku alebo konca súboru.
```bash
head -n 4 file.txt           # Zobrazí prvé 4 riadky
tail -n 4 file.txt           # Zobrazí posledné 4 riadky
```

### cut
Vyrezávanie častí riadkov.
```bash
cut -c 1-2 file.txt          # Zobrazí prvé 2 znaky z každého riadku
```

## Vyhľadávanie

### find
Vyhľadávanie súborov a adresárov.
```bash
find . -type f               # Nájde všetky súbory v aktuálnom adresári
find . -type d               # Nájde všetky adresáre
find . -type f -name "*.txt" # Nájde všetky .txt súbory
find . -type f -iname "*.txt"        # Vyhľadávanie bez rozlišovania veľkosti písmen
find . -type f -mmin -20     # Súbory zmenené za posledných 20 minút
find . -type f -mmin +2 -mmin -10    # Súbory zmenené medzi 2-10 minútami dozadu
find . -type f -maxdepth 1   # Vyhľadávanie len v aktuálnej úrovni
find . -size +1k             # Súbory väčšie ako 1KB
find . -empty                # Prázdne súbory
find . -perm 777             # Súbory s konkrétnymi právami
find . -type f -name "*.txt" -exec rm -rf {} +   # Vymaže všetky nájdené .txt súbory
```

### locate
Rýchle vyhľadávanie súborov.
```bash
locate "*.txt"               # Nájde všetky .txt súbory (nemusí fungovať na macOS)
```

### grep
Vyhľadávanie textu v súboroch.
```bash
grep "ahoj" file.txt         # Nájde riadky obsahujúce "ahoj"
grep -i "ahoj" file.txt      # Vyhľadávanie bez rozlišovania veľkosti písmen
grep -w "ahoj" file.txt      # Vyhľadávanie celého slova
grep -B 3 "ahoj" file.txt    # Zobrazí 3 riadky pred nájdeným textom
grep -win "ahoj" ./*.txt     # Kombinácia flagov pre všetky .txt súbory
grep -wirl "ahoj" .          # Zobrazí len názvy súborov s nájdeným textom
```

## Oprávnenia súborov

### chmod (Change Mode)
Zmena oprávnení súborov.

**Oprávnenia:**
- r (read) = 4 - čítanie
- w (write) = 2 - písanie
- x (execute) = 1 - spustenie

**Používatelia:**
- u (user) - vlastník
- g (group) - skupina
- o (others) - ostatní
- a (all) - všetci

```bash
chmod u+x script.sh          # Pridá právo spustenia pre vlastníka
chmod g-w file.txt           # Odoberie právo písania pre skupinu
chmod a+r file.txt           # Pridá právo čítania pre všetkých
chmod 777 file.txt           # Nastaví všetky práva pre všetkých (rwxrwxrwx)
chmod u=rwx,g=rx,o=r file.txt    # Nastaví konkrétne práva pre každú skupinu
```

## Systémové informácie

### whoami
Zobrazí meno aktuálneho používateľa.
```bash
whoami
```

### df (Disk Free)
Zobrazí využitie diskového priestoru.
```bash
df                           # Základné informácie
df -h                        # Ľudsky čitateľný formát
df -hg                       # Formát v gigabajtoch
```

### du (Disk Usage)
Zobrazí využitie priestoru adresármi.
```bash
du                           # Využitie priestoru
du -h                        # Ľudsky čitateľný formát
```

### uname
Systémové informácie.
```bash
uname -o                     # Operačný systém
uname -m                     # Architektúra procesora
uname -r                     # Verzia jadra
```

### id
Informácie o používateľovi.
```bash
id -G                        # Zobrazí ID všetkých skupín
```

## Správa procesov

### top
Zobrazí bežiace procesy v reálnom čase.
```bash
top
```

### ps
Zobrazí aktuálne bežiace procesy.
```bash
ps aux                       # Detailný zoznam všetkých procesov
```

### kill
Ukončenie procesu.
```bash
kill [process_id]            # Ukončí proces s daným ID
```

## História príkazov

### history
Zobrazí históriu použitých príkazov.
```bash
history                      # Zobrazí celú históriu
history | grep "ls"          # Vyhľadá v histórii príkazy obsahujúce "ls"
```

## Porovnávanie súborov

### diff
Porovná súbory riadok po riadku.
```bash
diff file1.txt file2.txt     # Zobrazí rozdiely medzi súbormi
```

## Archivovanie

### zip/unzip
Vytvorenie a extrahovanie archívov.
```bash
zip archive.zip file1.txt file2.txt    # Vytvorí archív
unzip archive.zip                       # Extrahuje archív
```

## Užitočné skratky

- **Ctrl+A** - Presun na začiatok riadku
- **Ctrl+C** - Ukončenie aktuálneho príkazu
- **Tab** - Automatické dopĺňanie príkazov a názvov súborov
- **q** - Ukončenie man stránok

## Sudo
Vykonanie príkazu s administrátorskými právami.
```bash
sudo command                 # Vykoná príkaz ako superuser
```

## Man (Manual)
Zobrazenie manuálových stránok pre príkazy.
```bash
man echo                     # Zobrazí manuál pre príkaz echo
man tr                       # Zobrazí manuál pre príkaz tr
```

## Reťazenie príkazov

### Pipe (|)
Presmeruje výstup jedného príkazu na vstup druhého.
```bash
cat file.txt | tr a-z A-Z    # Zobrazí obsah súboru s veľkými písmenami
history | grep "ls"          # Vyhľadá v histórii príkazy s "ls"
```

### Sekvenčné vykonávanie
```bash
echo "first" && echo "second"    # Vykoná druhý príkaz len ak prvý uspeje
```

---

*Tento cheat sheet obsahuje základné Linux príkazy potrebné pre prácu v príkazovom riadku. Pre viac informácií o konkrétnom príkaze použite `man [názov_príkazu]`.*
