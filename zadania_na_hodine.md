# Git a GitHub od nuly: základy verziovania

**Typ:** cvičenie na hodinu, samostatne a vo dvojiciach
**Čas:** 2 × 45 minút
**Cieľ:** naučiť sa základnú prácu s verziovacím systémom **Git** a platformou **GitHub**: založiť repozitár, ukladať zmeny, vracať sa v histórii, pracovať s vetvami, spolupracovať cez pull request a vyriešiť konflikt.

Poznámky, na ktoré sa môžeš pozrieť: [GitHub_vs_GitLab.md](https://github.com/SPSITKNM/SPSITKNM/blob/main/GitHub_vs_GitLab.md) (príkazy, vetvy, konflikty, SSH a PAT).

---

## Čo budeš vedieť po tejto hodine
- vysvetliť rozdiel medzi **Gitom** a **GitHubom**,
- vytvoriť repozitár, urobiť **commit** a pozrieť históriu,
- vrátiť nechcenú zmenu (`restore`, `revert`),
- odoslať prácu na GitHub (`push`) a stiahnuť cudziu (`clone`, `pull`),
- pracovať s **vetvami** a spájať ich (`merge`),
- otvoriť **pull request** a spraviť **review** práce spolužiaka,
- vyriešiť **konflikt** pri zlučovaní,
- nepridať do repozitára to, čo tam nepatrí (`.gitignore`).

## Základné pojmy

| Pojem | Význam |
|---|---|
| **Git** | program v tvojom počítači, ktorý si pamätá históriu zmien súborov |
| **GitHub** | web, na ktorom sa Git repozitáre ukladajú a zdieľajú (Git funguje aj bez neho) |
| **repozitár** | priečinok, ktorého históriu Git sleduje |
| **commit** | uložená verzia (snímka) súborov s popisom |
| **staging area** | „košík“, do ktorého dáš zmeny (`git add`) pred commitom |
| **vetva (branch)** | samostatná línia zmien, hlavná sa volá `main` |
| **remote / origin** | vzdialený repozitár (napr. na GitHube), `origin` je jeho štandardné meno |
| **clone** | stiahnutie celého repozitára aj s históriou |
| **push / pull** | odoslanie commitov na server / stiahnutie a zlúčenie nových |
| **fork** | tvoja vlastná kópia cudzieho repozitára na GitHube |
| **pull request (PR)** | žiadosť o zlúčenie tvojej vetvy do cudzieho repozitára, s diskusiou a reviewom |
| **konflikt** | dvaja zmenili to isté miesto a Git nevie sám určiť, ktorá verzia platí |

## Pravidlá
- **Nikdy** nikomu nedávaj svoje heslo, **token** (PAT) ani SSH kľúč a nevkladaj ich do repozitára.
- Commit správa je **krátka veta v rozkazovacom spôsobe** (napr. `Pridaj sekciu O mne`), nie `fix` alebo `zmeny`.
- Pred každým `git add` sa pozri na `git status`.
- Výstupy príkazov v zadaní sú v angličtine a **hashe commitov budú u teba iné**. Ak máš systém v slovenčine, niektoré texty sa môžu líšiť.

---

# Príprava (asi 10 minút)

## 1. Účet na GitHube
Ak ešte nemáš účet, založ si ho na github.com. Meno účtu si zvoľ rozumne, budeš ho odovzdávať učiteľovi.

## 2. Nainštalovaný Git
Skontroluj verziu (potrebuješ **2.23 alebo novšiu**):

```bash
git --version
```

Očakávaný výstup (číslo sa môže líšiť):

```
git version 2.50.1
```

## 3. Základné nastavenie
Git musí vedieť, kto robí zmeny. Spusti (nahraď svojím menom a e-mailom, ktorý máš na GitHube):

```bash
git config --global user.name "Jana Novakova"
git config --global user.email "jana@example.com"
git config --global init.defaultBranch main
git config --global pull.rebase false
```

Kontrola:

```bash
git config --global --list
```

```
user.name=Jana Novakova
user.email=jana@example.com
init.defaultbranch=main
pull.rebase=false
```

- `init.defaultBranch main` zabezpečí, že hlavná vetva sa bude volať `main`.
- `pull.rebase false` nastaví, že `git pull` bude pri zlučovaní robiť **merge** (potrebujeme to v časti 5).

## 4. Prihlásenie na GitHub
Pri `git push` cez HTTPS GitHub **nechce heslo**, ale **Personal Access Token (PAT)**, alebo prihlásenie cez program `gh` či GitHub Desktop. Postup nastavenia (PAT, SSH) je v poznámkach `GitHub_vs_GitLab.md`. Nastav si ho pred hodinou, kým ho budeš potrebovať v časti 3.

- [ ] účet na GitHube existuje
- [ ] `git --version` ukazuje 2.23 alebo novšiu
- [ ] `git config --global --list` ukazuje moje meno a e-mail
- [ ] viem sa prihlásiť na GitHub z príkazového riadka (PAT, `gh` alebo SSH)

---

# Časť 1: Tvoj prvý repozitár (3 body)

**Úloha:** Vytvor lokálny repozitár, pridaj do neho súbor `README.md` a ulož prvý commit.

## Postup

1. Vytvor priečinok a vojdi doňho:

```bash
mkdir git-zaklady
cd git-zaklady
```

2. Zmeň priečinok na Git repozitár:

```bash
git init
```

```
Initialized empty Git repository in .../git-zaklady/.git/
```

3. Pozri sa na stav. Zatiaľ nie je čo ukladať:

```bash
git status
```

```
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

4. Vytvor súbor `README.md` s takýmto obsahom (v ľubovoľnom editore):

```
# Moj prvy repozitar

Ahoj svet!
```

5. Súbor je zatiaľ **neverzovaný** (untracked):

```bash
git status
```

```
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README.md

nothing added to commit but untracked files present (use "git add" to track)
```

6. Pridaj ho do staging area a skontroluj:

```bash
git add README.md
git status
```

```
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   README.md
```

7. Ulož commit:

```bash
git commit -m "Pridaj README"
```

```
[main (root-commit) 16e3a71] Pridaj README
 1 file changed, 3 insertions(+)
 create mode 100644 README.md
```

8. Pozri históriu:

```bash
git log --oneline
```

```
16e3a71 Pridaj README
```

## Tri miesta, kde môže byť súbor
Zapamätaj si tok zmien:

```
pracovný priečinok  ──git add──►  staging area  ──git commit──►  história (repozitár)
```

## Kontrola
- [ ] `git log --oneline` ukazuje jeden commit s mojou správou
- [ ] `git status` hovorí, že nie je čo commitovať

**Otázka:** Čo by sa stalo, keby si namiesto `git add README.md` hneď spravil `git commit -m "..."`? (Odpoveď: nič, commit by ohlásil, že nie je čo ukladať, lebo staging area je prázdna.)

---

# Časť 2: História a vracanie zmien (3 body)

**Úloha:** Vyskúšaj, ako zistiť, čo si zmenil, ako zmenu zahodiť a ako vrátiť už uložený commit.

## Postup

1. Zmeň v `README.md` riadok `Ahoj svet!` na `Ahoj svet, tu je zmena!` a pozri, čo Git vidí:

```bash
git diff
```

```
--- a/README.md
+++ b/README.md
@@ -1,3 +1,3 @@
 # Moj prvy repozitar
 
-Ahoj svet!
+Ahoj svet, tu je zmena!
```

Riadok s `-` je pôvodný, riadok s `+` nový.

2. Zmenu **zahoď** (vráti súbor do stavu posledného commitu):

```bash
git restore README.md
git status
```

```
On branch main
nothing to commit, working tree clean
```

3. Pridaj do `README.md` nový riadok `Druhy riadok.` na koniec, ulož commit jedným príkazom (`-a` pridá zmeny už sledovaných súborov):

```bash
git commit -am "Pridaj druhy riadok"
```

4. Teraz si uvedomíš, že ten commit nechceš. Namiesto mazania histórie vytvor **nový commit, ktorý ho vráti**:

```bash
git revert HEAD --no-edit
git log --oneline
```

```
e54f2b3 Revert "Pridaj druhy riadok"
110095d Pridaj druhy riadok
16e3a71 Pridaj README
```

`HEAD` je označenie posledného commitu. História ostala zachovaná, len pribudol commit, ktorý zmenu zrušil.

## Rozdiel medzi `restore` a `revert`

| Príkaz | Čo robí | Kedy |
|---|---|---|
| `git restore súbor` | zahodí **neuložené** zmeny v súbore | zmena ešte nie je v commite |
| `git revert commit` | vytvorí **nový commit**, ktorý zruší starý | commit už existuje (najmä ak je odoslaný na server) |

## Kontrola
- [ ] `git log --oneline` ukazuje 3 commity, posledný je `Revert ...`
- [ ] `README.md` je v pôvodnom stave (tri riadky, bez `Druhy riadok.`)

---

# Časť 3: GitHub (4 body)

**Úloha:** Vytvor repozitár na GitHube, pripoj ho k lokálnemu, odošli commity a stiahni ho druhýkrát do iného priečinka.

## Postup

1. Na github.com klikni na **New repository**. Meno: `git-zaklady`. Nezaškrtávaj *Add a README*, *.gitignore* ani *licenciu* (repozitár musí byť prázdny). Klikni **Create repository**.

2. V lokálnom priečinku pripoj vzdialený repozitár (nahraď `TVOJE-MENO` menom svojho účtu):

```bash
git remote add origin https://github.com/TVOJE-MENO/git-zaklady.git
git remote -v
```

```
origin	https://github.com/TVOJE-MENO/git-zaklady.git (fetch)
origin	https://github.com/TVOJE-MENO/git-zaklady.git (push)
```

3. Odošli commity. `-u` nastaví, že vetva `main` bude odteraz sledovať `origin/main`:

```bash
git push -u origin main
```

```
To https://github.com/TVOJE-MENO/git-zaklady.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

4. Otvor stránku repozitára v prehliadači. Vidíš súbor `README.md` a históriu commitov?

5. Stiahni repozitár **do iného priečinka** (ako keby si bol druhý človek). Odíď z priečinka `git-zaklady` a spusti:

```bash
cd ..
git clone https://github.com/TVOJE-MENO/git-zaklady.git kamarat-kopia
```

```
Cloning into 'kamarat-kopia'...
```

6. V tejto kópii nastav jej **vlastné** meno (len pre tento repozitár, bez `--global`):

```bash
cd kamarat-kopia
git config user.name "Kamarat"
git config user.email "kamarat@example.com"
```

Kópiu `kamarat-kopia` použiješ v časti 5 na simuláciu druhého programátora.

## Kontrola
- [ ] na GitHube vidím repozitár `git-zaklady` s `README.md` a tromi commitmi
- [ ] priečinok `kamarat-kopia` existuje a obsahuje `README.md`

---

# Časť 4: Vetvy (3 body)

**Úloha:** Vytvor vetvu, urob v nej zmenu a zlúč ju do `main`.

Vráť sa do pôvodného priečinka (`cd ../git-zaklady`).

## Postup

1. Vytvor novú vetvu a prepni sa na ňu:

```bash
git switch -c feature/o-mne
```

```
Switched to a new branch 'feature/o-mne'
```

2. Pridaj na koniec `README.md`:

```
## O mne
Ja som Jana.
```

(pred `## O mne` nech je prázdny riadok) a ulož commit:

```bash
git add README.md
git commit -m "Pridaj sekciu O mne"
```

3. Vráť sa na `main` a zlúč vetvu:

```bash
git switch main
git merge feature/o-mne
```

```
Updating e54f2b3..b7a9c41
Fast-forward
 README.md | 3 +++
 1 file changed, 3 insertions(+)
```

`Fast-forward` znamená, že `main` sa len posunul dopredu, lebo sa medzitým nezmenil.

4. Zmaž zlúčenú vetvu a odošli zmeny:

```bash
git branch -d feature/o-mne
git branch
git push
```

```
Deleted branch feature/o-mne (was b7a9c41).
* main
```

## Prečo vetvy
Na vetve sa robí nová funkcia alebo oprava **oddelene**, aby si nepokazil funkčný `main`. Zlúči sa až keď je hotová.

## Kontrola
- [ ] `git branch` ukazuje len `main`
- [ ] na GitHube je v `README.md` sekcia „O mne“

---

# Časť 5: Pull request a review od spolužiaka (5 bodov)

**Úloha:** Vo dvojici si navzájom navrhnite zmeny cez **pull request** a zreviewujte ich.

Práca vo dvojici (A a B). **A je vlastník repozitára**, **B navrhuje zmenu** cez fork a pull request a A ju kontroluje. Potom sa role vymenia, takže každý vyskúša autora aj revieweru.

## Autor (B), ktorý navrhuje zmenu do cudzieho repozitára

1. Otvor v prehliadači repozitár `git-zaklady` **spolužiaka A** a klikni **Fork** (vpravo hore) a **Create fork**. Vznikne tvoja kópia `TVOJE-MENO/git-zaklady`.

2. Stiahni **svoj fork** a vytvor vetvu:

```bash
git clone https://github.com/TVOJE-MENO/git-zaklady.git git-zaklady-fork
cd git-zaklady-fork
git switch -c feature/pozdrav-b
```

3. Pridaj do `README.md` riadok o sebe (napr. `Pozdravuje Peter.`), ulož commit a odošli vetvu:

```bash
git add README.md
git commit -m "Pridaj pozdrav od Petra"
git push -u origin feature/pozdrav-b
```

4. Na stránke svojho forku na GitHube sa objaví žltý pás **Compare & pull request**. Klikni naň, napíš **názov** a stručný **popis** (čo si zmenil a prečo) a klikni **Create pull request**.

## Reviewer (A), ktorý kontroluje

1. Na stránke svojho repozitára otvor záložku **Pull requests** a otvor PR od spolužiaka.
2. Otvor záložku **Files changed**. Uvidíš zmeny podobne ako pri `git diff`.
3. Pridaj aspoň **jeden komentár** k riadku (klikni na modré `+` pri riadku).
4. Klikni **Review changes**, vyber **Comment**, **Approve** alebo **Request changes** a **Submit review**.
5. Ak je všetko v poriadku, klikni **Merge pull request** a **Confirm merge**.

## Autor po zlúčení
Autor si nemusí nič sťahovať. Vlastník repozitára (A) si stiahne zmeny do svojho lokálneho repozitára:

```bash
git pull
```

Potom si **vymeňte role** a urobte to isté v druhom smere.

## Čo dobrý review obsahuje
- konkrétny komentár k riadku, nie iba „ok“,
- návrh, čo zmeniť a prečo,
- slušný tón.

> Názvy tlačidiel na GitHube sa môžu časom mierne zmeniť. Ak niečo nenájdeš, opýtaj sa vo dvojici alebo učiteľa.

## Kontrola
- [ ] otvoril som PR do repozitára spolužiaka a mám jeho odkaz
- [ ] zreviewoval som PR spolužiaka aspoň jedným komentárom a zlúčil som ho
- [ ] `git log --oneline` u vlastníka ukazuje zlúčený commit spolužiaka

---

# Časť 6: Konflikt (4 body)

**Úloha:** Vyrob konflikt a vyrieš ho. Konflikt vzniká, keď dvaja zmenia **to isté miesto** súboru. Nie je to chyba, je to bežná situácia.

Použi druhý priečinok `kamarat-kopia` z časti 3 ako druhého programátora. (Ak ho nemáš, stiahni si repozitár znova.) Predtým v ňom spusti `git pull`, aby mal aktuálny stav.

## Postup

**Kamarát** (v priečinku `kamarat-kopia`):

1. Zmeň riadok `Ahoj svet!` v `README.md` na `Ahoj svet, Kamarat!`.
2. Ulož a odošli:

```bash
git commit -am "Kamarat: pozdrav"
git push
```

**Ty** (v priečinku `git-zaklady`), **bez** predchádzajúceho `git pull`:

3. Zmeň **ten istý riadok** na `Ahoj svet, Jana!`, ulož commit:

```bash
git commit -am "Jana: pozdrav"
```

4. Skús odoslať. Git odmietne, lebo server má novšie zmeny:

```bash
git push
```

```
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to '...'
hint: Updates were rejected because the remote contains work that you do not
hint: have locally. ...
hint: 'git pull' before pushing again.
```

5. Stiahni zmeny. Git sa pokúsi zlúčiť a narazí na konflikt:

```bash
git pull
```

```
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

6. Pozri sa na stav:

```bash
git status
```

```
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)
	both modified:   README.md
```

7. Otvor `README.md`. Git v ňom označil sporné miesto:

```
# Moj prvy repozitar

<<<<<<< HEAD
Ahoj svet, Jana!
=======
Ahoj svet, Kamarat!
>>>>>>> 2d5e0b8

## O mne
Ja som Jana.
```

Čítanie značiek:

| Značka | Význam |
|---|---|
| `<<<<<<< HEAD` | začiatok **tvojej** verzie |
| `=======` | oddeľovač |
| `>>>>>>> ...` | koniec verzie **z servera** (od kamaráta) |

8. **Vyrieš konflikt**: zmaž všetky tri značky a nechaj výsledný text, na ktorom sa dohodneš (môžeš spojiť obe verzie):

```
# Moj prvy repozitar

Ahoj svet, Jana a Kamarat!

## O mne
Ja som Jana.
```

9. Označ konflikt za vyriešený, ulož a odošli:

```bash
git add README.md
git commit -m "Vyries konflikt v README"
git push
```

10. Pozri si históriu ako graf:

```bash
git log --oneline --graph
```

```
*   c93e1a7 Vyries konflikt v README
|\
| * 2d5e0b8 Kamarat: pozdrav
* | 8a4f6d2 Jana: pozdrav
|/
* b7a9c41 Pridaj sekciu O mne
* e54f2b3 Revert "Pridaj druhy riadok"
* 110095d Pridaj druhy riadok
* 16e3a71 Pridaj README
```

Vidíš, ako sa dve línie zmien spojili do jedného commitu.

## Ak sa zľakneš
Kým konflikt nevyriešiš, môžeš zlučovanie **zrušiť** a vrátiť sa do stavu pred `git pull`:

```bash
git merge --abort
```

## Kontrola
- [ ] v `README.md` nie sú žiadne značky `<<<<<<<`, `=======`, `>>>>>>>`
- [ ] `git log --oneline --graph` ukazuje spojenie dvoch línií
- [ ] `git status` hovorí `nothing to commit, working tree clean` a `git push` prešiel

---

# Časť 7: `.gitignore` a bezpečnosť (2 body)

**Úloha:** Zabráň tomu, aby sa do repozitára dostali súbory, ktoré tam nepatria (preložené programy, systémové súbory, heslá).

## Postup

1. Vytvor dva „zbytočné“ súbory (napr. skompilovaný program a systémový súbor macOS):

```bash
touch a.out .DS_Store
git status --short
```

```
?? .DS_Store
?? a.out
```

2. Vytvor súbor `.gitignore` s obsahom:

```
a.out
.DS_Store
```

```bash
git status --short
```

```
?? .gitignore
```

Súbory `a.out` a `.DS_Store` Git prestal ponúkať. Vidí už len `.gitignore`.

3. Ulož `.gitignore` do repozitára:

```bash
git add .gitignore
git commit -m "Pridaj .gitignore"
git push
```

## Dôležité pravidlá
- **`.gitignore` neodstráni súbory, ktoré už Git sleduje.** Ak si súbor omylom commitol, treba ho z Gitu vyradiť (súbor ostane na disku):

```bash
git rm --cached a.out
git commit -m "Odstran a.out z Gitu"
```

Potom pridaj `a.out` do `.gitignore`.

- **Nikdy nepushuj heslá, tokeny ani súbory typu `.env`.** Aj keď ich neskôr zmažeš, ostanú v **histórii**. Ak sa to stane, heslo alebo token okamžite **zruš a vygeneruj nový**.
- Predtým než použiješ `git add .`, pozri `git status`. Príkaz pridá **všetko**.
- Nikdy nepoužívaj `git push --force` do spoločnej vetvy, prepíšeš cudziu prácu.

## Kontrola
- [ ] `git status --short` po vytvorení `.gitignore` nezobrazuje `a.out` ani `.DS_Store`
- [ ] viem vysvetliť, prečo nestačí zmazať heslo, ktoré som už commitol

---

# Bonus (+2 body)

## Rozpracovaná práca: `git stash`
Ak potrebuješ rýchlo prepnúť vetvu a nechceš commitovať nedokončenú zmenu:

```bash
echo "rozpracovane" >> README.md
git stash
git status --short
git stash pop
```

```
Saved working directory and index state WIP on main: 2f7c0e1 Pridaj .gitignore
```

`git stash` odloží zmeny do „šuplíka“ a pracovný priečinok je čistý. `git stash pop` ich vráti. Na záver zmenu zahoď (`git restore README.md`), aby si ju nenechal v repozitári.

## Značky: `git tag`
Označ dôležitý bod histórie (napr. odovzdanú verziu):

```bash
git tag v1.0
git log --oneline --decorate -3
```

```
2f7c0e1 (HEAD -> main, tag: v1.0) Pridaj .gitignore
```

Značku odošleš príkazom `git push origin v1.0`.

## Nájdi, čo sa zmenilo
Skús `git log --oneline --graph --all` a `git show HEAD`. Vysvetli spolužiakovi, čo vidíš.

---

# Rýchly prehľad príkazov

| Chcem... | Príkaz |
|---|---|
| vytvoriť repozitár | `git init` |
| stiahnuť cudzí repozitár | `git clone URL` |
| zistiť stav | `git status` |
| pridať súbor do staging area | `git add súbor` |
| uložiť commit | `git commit -m "správa"` |
| pozrieť históriu | `git log --oneline` |
| vidieť neuložené zmeny | `git diff` |
| zahodiť neuloženú zmenu | `git restore súbor` |
| vrátiť commit novým commitom | `git revert HEAD` |
| pripojiť vzdialený repozitár | `git remote add origin URL` |
| odoslať commity | `git push` |
| stiahnuť a zlúčiť zmeny | `git pull` |
| vytvoriť vetvu a prepnúť sa | `git switch -c názov` |
| prepnúť vetvu | `git switch názov` |
| zlúčiť vetvu do aktuálnej | `git merge názov` |
| zrušiť zlučovanie s konfliktom | `git merge --abort` |
| odložiť rozpracované zmeny | `git stash` a `git stash pop` |

# Najčastejšie chyby
- **Zabudnuté `git add`**: commit neobsahuje zmenu. Pozri `git status` pred commitom.
- **Commit správa `fix`, `zmeny`, `asdf`**: nikto sa v tom nevyzná. Píš vety.
- **`git push` odmietnutý** (`fetch first`): najprv `git pull`, potom `git push`.
- **Commit súborov, ktoré tam nepatria** (`a.out`, `.DS_Store`, heslá): `.gitignore` a `git rm --cached`.
- **Práca priamo na `main` bez vetvy** v tíme: mení sa cez vetvu a pull request.
- **Strach z konfliktu**: je normálny. Postup nájdeš v časti 6, prípadne `git merge --abort`.

---

# Odovzdanie
Do zadania na EduPage vlož:
1. odkaz na tvoj repozitár `git-zaklady` na GitHube,
2. odkaz na **pull request, ktorý si otvoril** (do repozitára spolužiaka),
3. odkaz na **pull request, ktorý si zreviewoval**,
4. snímku obrazovky výstupu `git log --oneline --graph` (musia byť vidieť obe línie z konfliktu).

# Hodnotenie (25 bodov)

| Časť | Body |
|---|---|
| 1. Prvý repozitár | 3 |
| 2. História a vracanie zmien | 3 |
| 3. GitHub | 4 |
| 4. Vetvy | 3 |
| 5. Pull request a review | 5 |
| 6. Konflikt | 4 |
| 7. `.gitignore` a bezpečnosť | 2 |
| Kvalita commit správ a poriadok v repozitári | 1 |
| **Spolu** | **25** |
| Bonus (`stash`, `tag`, `--graph`) | +2 |

# Kontrolné otázky
1. Aký je rozdiel medzi Gitom a GitHubom?
2. Čo robí `git add` a čo `git commit`? Prečo sú to dva kroky?
3. Aký je rozdiel medzi `git restore` a `git revert`?
4. Prečo `git push` občas skončí chybou `fetch first` a čo treba urobiť?
5. Čo je vetva a prečo sa v tíme nepracuje priamo na `main`?
6. Čo je pull request a čo má obsahovať dobrý review?
7. Kedy vzniká konflikt a ako vyzerá v súbore?
8. Prečo nestačí zmazať heslo, ktoré si omylom commitol?

**Odpovede:**
1. Git je program na správu verzií súborov (funguje lokálne), GitHub je služba na ukladanie a zdieľanie Git repozitárov.
2. `git add` vyberie zmeny do staging area, `git commit` ich uloží do histórie. Dva kroky umožňujú commitovať len časť zmien.
3. `restore` zahodí neuložené zmeny, `revert` vytvorí nový commit, ktorý zruší starý (história ostane).
4. Na serveri sú novšie commity, ktoré lokálne nemáš. Treba `git pull` a potom `git push`.
5. Vetva je samostatná línia zmien. Rozpracovaná práca nepokazí funkčný `main` a zlúči sa až po kontrole.
6. Pull request je žiadosť o zlúčenie vetvy s diskusiou. Dobrý review má konkrétny komentár, návrh a slušný tón.
7. Keď dvaja zmenia to isté miesto súboru. V súbore sú značky `<<<<<<<`, `=======`, `>>>>>>>`.
8. Heslo ostane v histórii (v starých commitoch). Treba ho zrušiť a vygenerovať nové.

---

# AI Workshop - Pracovný list

> Prejdite si materiály a doplňte chýbajúce časti. Tento "pracovný list" vám pomôže pochopiť kľúčové koncepty práce s AI asistentmi.

### Primárne zdroje

| Zdroj | Odkaz |
|-------|-------|
| PDF dokument | **AI_Workshop.pdf** |
| YouTube playlist | [Claude Code Workshop](https://youtube.com/playlist?list=PLJW-oHbyRDeL62yOcaqjex7cKnzcEYQXi&si=JUX_Bc2piFMk1NwJ) |
| GitHub dokumentácia | [github.com/Kames003/Claude-](https://github.com/Kames003/Claude-) |

---

## Úvod: Čo je AI Asistent?

### Architektúra

```
+-------------+     +------------------+     +-------------+
| POUZIVATEL  | <-> |   AI ASISTENT    | <-> |     LLM     |
|             |     |   (interface)    |     |   (model)   |
+-------------+     +------------------+     +-------------+
     Ty                 Prostredník            "Mozog"
```

**LLM (Large Language Model)** je samotný jazykový model - "mozog", ktorý generuje odpovede. Príklady: GPT-4, Claude, Gemini, Llama...

**AI Asistent** je vrstva medzi tebou a LLM. Je to softvér, ktorý:
- Prijíma tvoje požiadavky
- Pridáva kontext (systémové inštrukcie, informácie o projekte)
- Posiela to do LLM
- Prijíma odpoveď a môže vykonávať akcie (editovať súbory, spúšťať príkazy)

### Prečo potrebujeme AI Asistenta?

Samotný LLM je len "textový generátor". AI Asistent mu dáva:

| Schopnosť | Popis |
|-----------|-------|
| **Nástroje (Tools)** | Možnosť čítať/písať súbory, spúšťať príkazy |
| **Kontext** | Informácie o tvojom projekte, pravidlá |
| **Pamäť** | Uchovávanie histórie konverzácie |
| **Bezpečnosť** | Systém povolení, sandbox |

### Coding AI Asistenti

Existuje viacero coding AI asistentov:
- **CLI nástroje** (príkazový riadok) - napr. Claude Code, Aider, Cursor CLI
- **IDE rozšírenia** - napr. GitHub Copilot, Cursor, Windsurf
- **Webové rozhrania** - napr. ChatGPT, Claude.ai

Koncepty, ktoré sa naučíš v tomto workshope, sú **univerzálne** a aplikovateľné na väčšinu z nich.

---

# ČASŤ 1: Setup a základy

## 1. CLI vs GUI

Mnoho AI asistentov funguje ako **CLI** nástroj.

**CLI** znamená _________________________ a znamená to, že s nástrojom komunikujeme cez _________________________.

**GUI** znamená _________________________ - klasické okná, tlačidlá, myš.

### Výhody CLI pre programátorov

Doplň výhody:
- Rýchlejšie pre skúsených používateľov
- Ľahko sa _________________________ (automatizácia)
- Funguje cez _________________________ (SSH)
- Menej náročné na _________________________

---

## 2. Sessions - konverzácie s AI

AI asistent si pamätá konverzáciu v tzv. **session** (sedenie/relácia).

### Čo je session?

Session = jedna súvislá konverzácia s AI asistentom. Obsahuje:
- Tvoje správy (prompty)
- Odpovede AI
- Vykonané akcie
- Zdieľaný kontext

### Správa sessions

| Akcia | Čo to znamená |
|-------|---------------|
| Nová session | Začínam "s čistým stolom" - AI nevie nič o predošlej práci |
| Pokračovanie v session | AI si pamätá celú predošlú konverzáciu |
| Vymazanie session | Zahodím históriu a začnem odznova |

### Kedy začať novú session?

Napíš 2 dôvody, prečo by si chcel začať novú session:

1. _________________________________________________________________

2. _________________________________________________________________

---

# ČASŤ 2: Base usage a IDE integrácia

## 3. Konfigurácia AI Asistentov

Väčšina AI asistentov má viacero úrovní nastavení.

### Hierarchia nastavení (od najnižšej po najvyššiu prioritu)

```
+----------------------------------------+
|  3. LOKÁLNE (najvyššia priorita)       |  <- Moje osobné nastavenia
+----------------------------------------+
|  2. PROJEKTOVÉ                         |  <- Zdieľané v tíme
+----------------------------------------+
|  1. GLOBÁLNE (najnižšia priorita)      |  <- Platí všade
+----------------------------------------+
```

### Prečo existujú lokálne nastavenia?

Lokálne nastavenia typicky **nie sú** súčasťou Git repozitára.

Je to preto, lebo: _________________________________________________________________

---

## 4. Context Window a Tokeny

### Čo je context window?

Context window = maximálne množstvo textu (tokenov), ktoré LLM "vidí" naraz.

```
+-----------------------------------------------------------+
|                    CONTEXT WINDOW                         |
|  +-----------------------------------------------------+  |
|  | System prompt (inštrukcie pre AI)                   |  |
|  +-----------------------------------------------------+  |
|  | Informácie o nástrojoch                             |  |
|  +-----------------------------------------------------+  |
|  | História konverzácie                                |  |
|  +-----------------------------------------------------+  |
|  | Tvoj aktuálny prompt                                |  |
|  +-----------------------------------------------------+  |
|  | [REZERVA pre odpoveď AI]                            |  |
|  +-----------------------------------------------------+  |
+-----------------------------------------------------------+
```

### Tokeny

**Token** nie je to isté ako slovo. Token je jednotka, ktorú LLM spracováva.

Približne: **1 token = cca 4 znaky** alebo **100 tokenov = cca 75 slov**

### Compaction (komprimácia)

Keď konverzácia presiahne limit, AI asistent vykoná **compaction**:

**Compaction** = _________________________

**Výhoda:** AI môže pokračovať v práci

**Nevýhoda:** _________________________ (niektoré detaily sa stratia)

---

## 5. IDE Integrácie

Mnoho AI asistentov má integrácie s IDE (napr. VS Code).

### Čo poskytujú?

| Funkcia | Popis |
|---------|-------|
| Diff viewer | Porovnanie zmien pred/po |
| Inline akceptácia | Schválenie zmien priamo v editore |
| Sync | Synchronizácia medzi CLI a IDE |

### Prečo ich používať?

Ľahšie sa _________________________ zmeny pred ich akceptovaním.

---

# ČASŤ 3: Advance Permissions Management

## 6. Permissions - bezpečnosť

AI asistent má prístup k tvojmu súborovému systému. To je **mocné, ale nebezpečné**.

### Typy akcií podľa rizika

| Riziko | Príklad akcie | Vyžaduje povolenie? |
|--------|---------------|---------------------|
| Nízke | Čítanie súborov | Nie |
| Stredné | Editovanie súborov v projekte | Záleží na nastavení |
| Vysoké | Spúšťanie shell príkazov | Áno |
| Kritické | Git operácie (push, reset) | Áno |

### Auto-accept módy

**Čo typicky môže AI robiť bez pýtania:**
- Čítať súbory
- Editovať súbory v projekte

**Čo stále vyžaduje povolenie:**
- _________________________
- _________________________
- Operácie mimo projekt

---

## 7. Dangerous Mode

Niektorí asistenti ponúkajú režim, ktorý preskočí všetky povolenia.

**Riziká:**
- AI môže _________________________ git históriu
- AI môže _________________________ súbory
- AI môže spustiť _________________________ skripty

### Kedy by sa to mohlo hodiť?

Pri použití v kombinácii so _________________________ prostredím.

---

## 8. Sandbox - izolované prostredie

**Sandbox** = izolované prostredie, kde AI môže pracovať bez rizika poškodenia systému.

### Typy sandboxov

| Typ | Popis |
|-----|-------|
| Docker sandbox | Beh v Docker kontajneri |
| Natívny sandbox | Vstavaný v AI asistentovi |

Predstav si sandbox ako: _________________________________________________________________

---

# ČASŤ 4: Version Control a Undo

## 9. Vracanie zmien

### Prečo je Git dôležitý pri práci s AI?

1. _________________________________________________________________

2. _________________________________________________________________

### Možnosti vrátenia zmien

| Metóda | Popis |
|--------|-------|
| Git revert/reset | Klasické git príkazy |
| IDE diff nástroje | Porovnanie "pred" a "po" |
| Zabudované undo | Vlastný mechanizmus asistenta |

### Dôležité

Pred väčšími zmenami je **VŽDY** dobré urobiť _________________________.

---

# ČASŤ 5: Plan Mode

## 10. Plan Mode

**Plan Mode** = plánovací režim pred implementáciou.

### Ako to funguje?

```
+-----------------------------------------------------------+
|                     PLAN MODE                             |
|                                                           |
|  1. AI analyzuje požiadavku                               |
|  2. Kladie upresňujúce otázky                             |
|  3. Navrhuje plán riešenia                                |
|  4. Čaká na tvoje schválenie                              |
|  5. AŽ POTOM začne implementovať                          |
|                                                           |
|  POZOR: V Plan Mode AI NEMÔŽE robiť zmeny!                |
+-----------------------------------------------------------+
```

### Kedy použiť Plan Mode?

- Pri _________________________ úlohách
- Keď si _________________________ výsledkom
- Pri úlohách ovplyvňujúcich _________________________

### Výhody

1. Predídeš zbytočným _________________________
2. Môžeš ovplyvniť riešenie _________________________ než je implementované
3. AI lepšie _________________________ tvoje požiadavky

---

# ČASŤ 6: Context Engineering a projektové inštrukcie

## 11. Špecifické inštrukcie a SPEC.md

### Čo je SPEC.md?

SPEC.md = dokument so špecifikáciou projektu/funkcionality.

### Rozdiel medzi inštrukciami a špecifikáciou

| Súbor | Účel | Veľkosť |
|-------|------|---------|
| Inštrukcie (CLAUDE.md) | Pravidlá pre AI | Stručný |
| SPEC.md | Detailný popis funkcionality | Môže byť dlhší |

### Stratégia použitia

V inštrukciách môžeš napísať:
```
Keď implementuješ novú funkcionalitu, pozri sa do @SPEC.md
```

**Prečo je to lepšie?** _________________________________________________________________

---

## 12. Projektové inštrukcie (CLAUDE.md)

Väčšina AI asistentov podporuje súbor s inštrukciami (napr. `CLAUDE.md`, `.cursorrules`).

### Čo obsahuje?

```markdown
# Názov projektu
Stručný popis...

# Pravidlá
- Používaj TypeScript
- Píš testy pre každú funkciu

# Architektúra
- /src - zdrojové súbory
- /tests - testy
```

### Kedy sa načíta?

Tento súbor sa **automaticky načíta** pri každej session a stáva sa súčasťou _________________________.

### Prečo má byť stručný?

_________________________________________________________________

### Vnorené inštrukcie

```
projekt/
  CLAUDE.md           <- načíta sa vždy
  frontend/
    CLAUDE.md         <- načíta sa len pri práci vo frontend/
  backend/
    CLAUDE.md         <- načíta sa len pri práci v backend/
```

---

## 13. Context Engineering

**Context Engineering** = umenie poskytnúť AI správny kontext.

### Základné princípy

| Princíp | Vysvetlenie |
|---------|-------------|
| Relevantnosť | Pridávaj len _________________________ informácie |
| Stručnosť | Šetri _________________________ |
| Štruktúra | Používaj formátovanie pre _________________________ |

### XML tagy pre štruktúru

```xml
<error>
TypeError: Cannot read property 'map' of undefined
    at UserList.js:15
</error>
```

**Prečo je to lepšie?** _________________________________________________________________

---

# ČASŤ 7: Nástroje a rozšírenia

## 14. Nástroje (Tools)

AI asistenti môžu mať prístup k rôznym nástrojom:

### Základné nástroje

| Nástroj | Čo robí |
|---------|---------|
| File Read | Číta obsah súborov |
| File Write | Zapisuje/upravuje súbory |
| Shell/Bash | Spúšťa terminálové príkazy |
| Web Search | Vyhľadáva na internete |
| Web Fetch | Načítava obsah webových stránok |

---

## 15. Thinking Mode

**Thinking Mode** = režim, kde AI "premýšľa nahlas" a ukazuje svoj myšlienkový proces.

### Výhody a nevýhody

| Výhody | Nevýhody |
|--------|----------|
| Vidíš ako AI uvažuje | Spotrebuje viac _________________________ |
| Kvalitnejšie odpovede | _________________________ odpoveď |
| Odhalíš chyby v uvažovaní | |

### Kedy ho vypnúť?

Pri _________________________ úlohách, kde nepotrebujeme detailné uvažovanie.

---

## 16. Práca s dokumentáciou

AI asistenti môžu pristupovať k externej dokumentácii:

| Spôsob | Popis |
|--------|-------|
| Web search | AI vyhľadá na internete |
| Web fetch | AI načíta konkrétnu URL |
| MCP servery | Špecializované nástroje |
| Copy-paste | Manuálne vložíš do promptu |

### Tip: Markdown dokumentácia

Väčšina dokumentácií ponúka Markdown verziu. Je lepšia, pretože:
- Menej "šumu"
- Šetrí _________________________
- Lepšie sa _________________________

---

## 17. MCP - Model Context Protocol

**MCP** = štandard pre pridávanie nových nástrojov a zdrojov pre AI asistentov.

Príklad: MCP server pre dokumentáciu umožňuje AI ľahšie _________________________.

### Ako funguje?

```
+------------------+     +------------------+     +------------------+
|   AI ASISTENT    | <-> |   MCP SERVER     | <-> |  EXTERNÝ ZDROJ   |
+------------------+     +------------------+     +------------------+
```

---

# ČASŤ 8: Skills a Custom Commands

## 18. Skills

**Skills** = rozšírené schopnosti AI asistenta pre špecifické úlohy.

### Čo sú skills?

Skills sú v podstate "balíčky" obsahujúce:
- Špecifické inštrukcie
- Definované nástroje
- Workflow pre konkrétnu úlohu

### Ako fungujú?

AI asistent ich môže:
- Automaticky objaviť a použiť keď sú potrebné
- Spustiť na základe tvojej výzvy

### Third-party skills

Existujú platformy so zdieľanými skills (napr. skills.sh).

**Výhoda používania hotových skills:** _________________________________________________________________

---

## 19. Custom Commands

**Custom Commands** = znovu použiteľné prompty, ktoré si vytvoríš sám.

### Prečo ich používať?

Predstav si, že často robíš code review s rovnakým promptom. Namiesto opakovania môžeš vytvoriť command.

### Štruktúra custom command

```yaml
description: Popis čo command robí
allowed-tools: [Read]  # Obmedzenie nástrojov
---
Tvoj prompt tu...
$ARGUMENTS  # Placeholder pre argumenty
```

### Príklad použitia

Command `/review` s argumentom:
```
/review src/components/Button.js
```

### Kde ich uložiť?

- **Lokálne** - v projekte (zdieľané s tímom)
- **Globálne** - na tvojom počítači (osobné)

---

# ČASŤ 9: Hooks a Plugins

## 20. Hooks

**Hooks** = automatické reakcie na udalosti AI asistenta.

### Ako fungujú?

```
+------------------+     +------------------+     +------------------+
|  AI VYKONÁ       | --> |     HOOK SA      | --> |   SPUSTÍ SA      |
|  AKCIU           |     |    AKTIVUJE      |     |   TVOJ KÓD       |
+------------------+     +------------------+     +------------------+
```

### Typy hookov

| Typ | Kedy sa spustí |
|-----|----------------|
| PreToolUse | Pred použitím nástroja |
| PostToolUse | Po použití nástroja |

### Príklad použitia

Po každej úprave súboru automaticky spustiť formátovač kódu.

**Hook sa spustí po:** _________________________

**Vykoná:** _________________________

---

## 21. Plugins

**Plugins** = hotové balíčky rozširujúce funkcionalitu AI asistenta.

### Čo môžu obsahovať?

- MCP servery
- Custom commands
- Skills
- Hooks

### Kde ich nájsť?

- Oficiálny marketplace
- Interné firemné repozitáre
- GitHub

**Výhoda:** Nemusíš všetko nastavovať od začiatku - použiješ hotové riešenie.

---

# ČASŤ 10: Feedback Loops a Multi-Agent systémy

## 22. Feedback Loops

**Feedback Loop** = mechanizmus, kde AI sama overuje svoju prácu.

### Prečo je to dôležité?

AI môže robiť chyby. Feedback loop jej umožňuje:
1. Vykonať zmenu
2. _________________________ výsledok
3. Opraviť chyby
4. Opakovať

### Typy feedback loops

| Typ | Popis |
|-----|-------|
| Unit testy | AI spustí testy a opraví zlyhania |
| Browser testing | AI otvorí prehliadač a skontroluje UI |
| Linting | AI skontroluje kvalitu kódu |

### Príklad: Playwright

Playwright umožňuje AI otvoriť prehliadač a _________________________ webstránku.

**Nevýhoda feedback loops:** Vyššia spotreba _________________________

### Pozor na testy písané AI

AI má tendenciu písať testy, ktoré _________________________.

Preto je dobré testy buď písať pred implementáciou alebo ich _________________________.

---

## 23. Multi-Agent systémy (Ralph Loops)

**Multi-Agent systém** = viacero AI agentov pracujúcich spoločne alebo AI bežiaca v slučke.

### Ralph Loop - koncept

```
+-----------------------------------------------------------+
|                      RALPH LOOP                           |
|                                                           |
|  while (tasks_remaining && iterations < MAX):             |
|      1. Agent si vyberie task zo zoznamu                  |
|      2. Implementuje riešenie                             |
|      3. Spustí testy                                      |
|      4. Označí task ako hotový                            |
|      5. Pokračuje na ďalší task                           |
|                                                           |
+-----------------------------------------------------------+
```

### Ako to funguje?

1. Vytvoríš zoznam úloh (napr. v PRD súbore)
2. Spustíš agenta v slučke
3. Agent si vyberá a plní úlohy automaticky
4. Ty len kontroluješ výsledky

### Výhody

- Menej manuálnej práce
- Vhodné pre _________________________

### Nevýhody

- Menšia _________________________ nad procesom
- Agent sa môže "zaseknúť"
- Stále potrebuješ dobrý _________________________ a jasné úlohy

### Čo je potrebné pre úspešný Ralph Loop?

1. Dobre definované _________________________
2. Funkčné _________________________
3. Sandbox prostredie pre _________________________
4. Kvalitný project _________________________

---

# Zhrnutie

## 24. Prehľad konceptov

Spoj pojem s definíciou:

| Pojem | | Definícia |
|-------|---|-----------|
| Context Window | | A. Automatická kompresia konverzácie |
| Compaction | | B. Izolované bezpečné prostredie |
| Sandbox | | C. Maximálna kapacita "pamäte" LLM |
| Skills | | D. Znovu použiteľné prompty |
| Custom Commands | | E. Rozšírené schopnosti pre špecifické úlohy |
| Hooks | | F. Automatické reakcie na udalosti |
| Feedback Loop | | G. AI overuje svoju vlastnú prácu |
| Ralph Loop | | H. Agent pracujúci v automatickej slučke |

---

## Reflexia

**Čo ťa z workshopu najviac zaujalo alebo prekvapilo?**

_________________________________________________________________

_________________________________________________________________

**Aké sú podľa teba najväčšie výhody používania AI asistentov?**

_________________________________________________________________

_________________________________________________________________

**Aké sú podľa teba najväčšie riziká?**

_________________________________________________________________

_________________________________________________________________

**Ako by si mohol využiť tieto koncepty vo svojich projektoch?**

_________________________________________________________________

_________________________________________________________________

---

# Prehľad všetkých otázok

> Klikni na otázku pre presmerovanie na príslušnú sekciu v dokumente.

---

## ČASŤ 1: Setup a základy

### [1. CLI vs GUI](#1-cli-vs-gui)
- [ ] Čo znamená CLI?
- [ ] Cez čo komunikujeme s CLI nástrojom?
- [ ] Čo znamená GUI?
- [ ] Ako sa CLI ľahko... (automatizácia)?
- [ ] Cez čo funguje CLI vzdialene?
- [ ] Na čo je CLI menej náročné?

### [2. Sessions](#2-sessions---konverzácie-s-ai)
- [ ] Dva dôvody, prečo začať novú session

---

## ČASŤ 2: Base usage a IDE integrácia

### [3. Konfigurácia](#3-konfigurácia-ai-asistentov)
- [ ] Prečo lokálne nastavenia nie sú v Git repozitári?

### [4. Context Window a Tokeny](#4-context-window-a-tokeny)
- [ ] Čo je compaction?
- [ ] Aká je nevýhoda compaction?

### [5. IDE Integrácie](#5-ide-integrácie)
- [ ] Prečo používať IDE integrácie? (ľahšie sa...)

---

## ČASŤ 3: Advance Permissions Management

### [6. Permissions](#6-permissions---bezpečnosť)
- [ ] Čo stále vyžaduje povolenie? (2 odpovede)

### [7. Dangerous Mode](#7-dangerous-mode)
- [ ] Čo môže AI urobiť s git históriou?
- [ ] Čo môže AI urobiť so súbormi?
- [ ] Aké skripty môže AI spustiť?
- [ ] S akým prostredím sa dangerous mode kombinuje?

### [8. Sandbox](#8-sandbox---izolované-prostredie)
- [ ] Ako si predstaviť sandbox? (prirovnanie)

---

## ČASŤ 4: Version Control a Undo

### [9. Vracanie zmien](#9-vracanie-zmien)
- [ ] Dva dôvody, prečo je Git dôležitý pri práci s AI
- [ ] Čo je dobré urobiť pred väčšími zmenami?

---

## ČASŤ 5: Plan Mode

### [10. Plan Mode](#10-plan-mode)
- [ ] Pri akých úlohách použiť Plan Mode?
- [ ] Kedy si... výsledkom?
- [ ] Aké úlohy ovplyvňujú...?
- [ ] Čomu predídeš zbytočným...?
- [ ] Kedy môžeš ovplyvniť riešenie?
- [ ] Čo AI lepšie...?

---

## ČASŤ 6: Context Engineering a projektové inštrukcie

### [11. SPEC.md](#11-špecifické-inštrukcie-a-specmd)
- [ ] Prečo je lepšie odkazovať na SPEC.md z CLAUDE.md?

### [12. Projektové inštrukcie](#12-projektové-inštrukcie-claudemd)
- [ ] Súčasťou čoho sa stáva CLAUDE.md pri načítaní?
- [ ] Prečo má byť CLAUDE.md stručný?

### [13. Context Engineering](#13-context-engineering)
- [ ] Aké informácie pridávať? (relevantnosť)
- [ ] Čo šetríme stručnosťou?
- [ ] Prečo používať formátovanie?
- [ ] Prečo sú XML tagy lepšie?

---

## ČASŤ 7: Nástroje a rozšírenia

### [15. Thinking Mode](#15-thinking-mode)
- [ ] Čo spotrebuje thinking mode viac?
- [ ] Aká je odpoveď s thinking mode?
- [ ] Pri akých úlohách ho vypnúť?

### [16. Práca s dokumentáciou](#16-práca-s-dokumentáciou)
- [ ] Čo šetrí Markdown dokumentácia?
- [ ] Ako sa lepšie... Markdown?

### [17. MCP](#17-mcp---model-context-protocol)
- [ ] Čo umožňuje MCP server pre dokumentáciu?

---

## ČASŤ 8: Skills a Custom Commands

### [18. Skills](#18-skills)
- [ ] Výhoda používania hotových skills?

---

## ČASŤ 9: Hooks a Plugins

### [20. Hooks](#20-hooks)
- [ ] Po čom sa hook spustí? (príklad)
- [ ] Čo hook vykoná? (príklad)

---

## ČASŤ 10: Feedback Loops a Multi-Agent systémy

### [22. Feedback Loops](#22-feedback-loops)
- [ ] Čo robí AI v kroku 2 feedback loop?
- [ ] Čo umožňuje Playwright?
- [ ] Aká je nevýhoda feedback loops? (spotreba)
- [ ] Aké testy má AI tendenciu písať?
- [ ] Čo robiť s testami písanými AI?

### [23. Multi-Agent systémy](#23-multi-agent-systémy-ralph-loops)
- [ ] Pre čo sú Ralph Loops vhodné?
- [ ] Čo je menšie pri Ralph Loops? (kontrola)
- [ ] Čo stále potrebuješ? (plán)
- [ ] 4 veci potrebné pre úspešný Ralph Loop

---

## Zhrnutie

### [24. Prehľad konceptov](#24-prehľad-konceptov)
- [ ] Spoj 8 pojmov s definíciami (A-H)

### [Reflexia](#reflexia)
- [ ] Čo ťa najviac zaujalo/prekvapilo?
- [ ] Najväčšie výhody AI asistentov?
- [ ] Najväčšie riziká?
- [ ] Ako využiť vo svojich projektoch?

---


*AI Workshop | SPSIT | Tom. Muc.*
