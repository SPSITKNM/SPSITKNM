
# Git vs GitLab – Komplexné Poznámky

## Základné rozdiely

### Git
- **Command line tool** na správu verzií (version control).
- Umožňuje **lokálne** sledovať zmeny v kóde.
- Pracuješ s vetvami, commitmi, spájaním zmien atď.
- Vytvára lokálny **snapshot** aplikácie.
- Každý commit má jedinečný ID hash.
- Predvolená vetva po inicializácii je `master` alebo `main`.

### GitLab
- **Webová platforma** postavená nad Gitom.
- Umožňuje **centrálne hostovanie** Git repozitárov.
- Podporuje **spoluprácu v tíme**, **CI/CD pipeline**, **issue tracking**, **wiki**, a **merge requesty**.
- Hosting na: `https://gitlab.com/`, prípadne na firemnom servery (napr. `gitlab.railsformers.com`).

---

## Lokálna práca s Gitom

```bash
# Zobrazenie vetvy
git branch

# Pridanie súboru na commitovanie
git add alpha.txt

# Pridanie všetkých zmien v priečinku
git add .

# Uloženie zmien do histórie repozitára
git commit -m "Tvoja správa"

# Skombinovanie git add + commit pre už sledované súbory
git commit -a -m "updated echo"

# Prehľad commitov
git log --oneline
git log --all --oneline --decorate --graph
```

---

## Vzdialený repozitár (origin)

```bash
# Pridanie zmien do vzdialeného repozitára
git push

# Načítanie zmien od iných členov tímu
git pull

# Zobrazenie URL repozitára
git remote -v
```

`origin` = názov vzdialeného servera (napr. GitLab).

---

## Fetch vs Pull

- `git fetch` = Stiahne dáta zo vzdialeného servera, ale **neaplikuje** ich hneď.
- `git merge` = Aplikuje zmeny z fetchnutého obsahu do tvojej aktuálnej vetvy.
- `git pull` = Kombinácia `fetch` + `merge`.

---

## Reset a história

```bash
# Vracia do stavu určitého commitu a vymaže zmeny
git reset --hard <commit_hash>

# Vrátenie posledného commitu
git reset --hard

# Zistenie histórie referencií
git reflog
```

Pozor: po `--hard` resete môžu byť commity **nenávratne stratené**, pokiaľ nie sú uložené vzdialene.

---

## Cherry-pick

```bash
# Skopíruje konkrétny commit z inej vetvy do aktuálnej
git cherry-pick <commit_hash>
```

---

## Práca s vetvami

```bash
# Vytvorenie novej vetvy
git branch dev

# Prepnutie na vetvu
git switch dev
# Alebo: git checkout dev

# Vytvorenie a prepnutie naraz
git switch -c dev

# Zoznam vetiev
git branch --list
```

### Vizuálne zobrazenie:
```
* 35ca233 (HEAD -> master) this is the fourth commit
| * 3f5b5a8 (dev) third one
| * 572057b third one
|/  
* c2f80a7 First commit
```

---

## Merge vs Rebase

- **Merge**: Spája vetvy a zachováva **históriu**.
- **Rebase**: Prepisuje históriu a vkladá commity "ako keby" vznikli na novej báze.

---

## Práca so súbormi

```bash
# Vytvorenie súboru (alebo update timestampu ak už existuje)
touch example.txt
```

---

## SSH prihlásenie (bez zadávania hesla)

```bash
# Vygenerovanie kľúča
ssh-keygen -t ed25519 -C "tomasmucha@railsformers.com"

# Zobrazenie public key
cat ~/.ssh/id_ed25519.pub
```

➡️ Tento public key pridaj do GitLab:
- GitLab → Settings → SSH Keys → vlož tam výstup z `cat`.

---

## Ďalšie tipy

- Ukončenie editoru `nano`: `CTRL + X`
- Ukončenie `vim`: `ESC`, potom `:q!` alebo `:wq`

---

## Push projektu do GitLab

```bash
git init
git remote add origin https://gitlab.railsformers.com/tomas.mucha/my-project.git
git add .
git commit -m "initial commit"
git push -u origin main
```

---

## PAT – Personal Access Token

Používa sa namiesto hesla pri HTTPS prístupe do GitLab, najmä ak je dvojfaktorová autentifikácia zapnutá.

---

**Poznámka**: `origin/main` alebo `origin/master` je názov vetvy vo vzdialenom repozitári.

--- 

git init = bude zaznamenavat všetko 

git log --all --graph = prehladny log = ukoncenie q

git checkout <nazov_filu> 

--- 

# Git -- Merge a Konflikty

### Čo znamená merge?

-   Keď mergujeme dva branche, výsledok pôjde **do tej branche, na
    ktorej aktuálne pracujeme**.\
-   Master branch (alebo main) funguje ako hlavná vetva, na ktorej sa
    stavia všetko ostatné.

**Príklad:**\
Ak sme v `master` a spustíme príkaz:

``` bash
git merge feature1
```

tak sa zmeny z `feature1` spoja do `master`.

------------------------------------------------------------------------

### Merge conflicts

-   Nastanú, keď git nevie rozhodnúť, ktorú zmenu si máme vybrať.\
-   Vtedy sa nás spýta, aby sme vybrali zmenu manuálne.\
-   Merge conflict teda znamená, že medzi dvomi branchmi sú
    **nezlučiteľné rozdiely**.

**Príklad logu:**

    CONFLICT (content): Merge conflict in feature
    Automatic merge failed; fix conflicts and then commit the result.

-   V editore bude zvýraznené, kde vznikol konflikt.\
-   Ako vývojár si musíme vy


# Git -- Merge Conflicts a Pipelines

### Merge conflicts v editore

-   V editore bude vždy poukázané, o aký problém sa jedná.\
-   Git branch conflict funguje v štýle: máme `branch1` a `branch2`, a
    **vývojár rozhoduje, ktorá zmena sa má implementovať**.

------------------------------------------------------------------------

### Feature branches

-   Slúžia na vývoj nových funkcií mimo hlavnej vetvy (`master` /
    `main`).\
-   Po dokončení sa mergujú späť do hlavnej vetvy.

------------------------------------------------------------------------

# CI / CD a Pipelines

### Ako konštruovať pipelines?

-   Jobs, ktoré sú podobne veľké, je vhodné spúšťať paralelne.\
-   Pipeline má na starosti build, testovanie a nasadenie aplikácie.

------------------------------------------------------------------------

### AWS tipy

-   Pri ťahaní image je potrebné **vždy špecifikovať tag**.

------------------------------------------------------------------------

### Maskovanie a ochrana premenných

-   **Protect variables** -- ak je zapnuté, premenné budú dostupné len
    pre **protected branches**.\
-   **Mask variables** -- predvolene vypnuté, ak je zapnuté, premenné sa
    nebudú zobrazovať v logoch.

------------------------------------------------------------------------

### Synchronizácia dát so S3

-   Potrebujeme zabezpečiť, že všetko, čo máme vo foldri, je
    zosynchronizované do S3 bucketu.

------------------------------------------------------------------------

### Pipeline a default branch

-   Ak máme iba jeden pipeline, **default branch sa automaticky
    updatuje**.

------------------------------------------------------------------------

### Post-deployment testing

-   Znamená testovanie aplikácie po jej nasadení.\
-   Slúži na overenie, že nasadená verzia funguje podľa očakávania.

------------------------------------------------------------------------

# CI / CD -- Definícia

-   **CI (Continuous Integration):** neustála integrácia kódu,
    automatické testovanie a build.\
-   **CD (Continuous Delivery / Continuous Deployment):**
    -   *Delivery* = zmeny sú pripravené na nasadenie.\
    -   *Deployment* = zmeny sa automaticky nasadzujú do produkcie.

------------------------------------------------------------------------

### Staging environment

-   Neprodukčné, neverejné prostredie veľmi podobné produkcii.\
-   Ak pipeline zlyhá, chyba neovplyvní produkciu.

------------------------------------------------------------------------

### Reusing of configuration

-   Opätovné využívanie častí konfigurácie na zjednodušenie a zrýchlenie
    CI/CD pipelines.

------------------------------------------------------------------------

# Continuous Delivery Pipeline

### Docker in Docker (DinD)

-   Spúšťanie dockeru vo vnútri dockeru pre **čistotu systému**.\
-   Používa sa najmä v CI/CD pipelines.

------------------------------------------------------------------------

### Config file -- potenciálne problémy

-   Problém môže byť v samotnom koncepte nastavenia.

------------------------------------------------------------------------

# Otázky a problémy s Docker build

### Veci, ktoré komplikovali docker build:

-   `debug` gem sa pokúšal načítať v produkčnom prostredí, aj keď bol
    vylúčený z inštalácie.\
-   V `Dockerfile` bola inštalácia Ruby gems bez development/test
    skupín.

#### Inštalácia Ruby gems bez development/test skupín:

``` dockerfile
RUN bundle config set --local deployment 'true' &&     bundle config set --local without 'development test' &&     bundle install --jobs $(nproc) --retry 3
```

#### Zabránenie načítaniu debug gem-u v produkčnom prostredí (`application.rb`):

``` ruby
if Rails.env.production?
  config.debug_exception_response_format = :api
end
```

------------------------------------------------------------------------

# Potrebné balíky pre virtualizáciu (Linux)

``` bash
sudo dnf install -y qemu-kvm libvirt virt-install virt-manager virt-viewer edk2-ovmf swtpm qemu-img guestfs-tools libosinfo libosinfo-tools tuned
```

------------------------------------------------------------------------

# Testovanie aplikácie

``` bash
curl http://localhost:8080/
curl http://localhost:8080/libraries
curl http://localhost:8080/health
```

