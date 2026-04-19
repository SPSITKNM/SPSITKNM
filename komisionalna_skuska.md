# Komisionálna skúška – SGX (SMART technológie)
**Škola:** Stredná priemyselná škola informačných technológií, Kysucké Nové Mesto  
**Predmet:** SGX – SMART technológie  
**Ročník:** 4.  
**Meno a priezvisko:** _______________  
**Trieda:** _______________  
**Dátum:** _______________

---

## Pokyny pre študenta

Táto komisionálna skúška pokrýva celé preberané učivo predmetu **SGX – SMART technológie** za školský rok. Predmet je zameraný na moderné technológie v oblasti vývoja softvéru, správy systémov, virtualizácie, kontajnerizácie, verzovacích systémov, monitoringu a AI-asistovaného vývoja, vrátane teoretických základov programovania, objektovo-orientovaného prístupu a algoritmizácie.

Vypracovanie nemá stanovené časové ani nástrojové obmedzenia. Študent je oprávnený zvoliť si programovací jazyk (C++ alebo C#, pokiaľ nie je stanovené inak), prostredie a formu záznamu riešenia podľa vlastného uváženia. Hodnotí sa správnosť riešenia, hĺbka pochopenia prezentovaných princípov a schopnosť komplexne obhájiť každé rozhodnutie obsiahnuté v odovzdanom vypracovaní. Komisia je oprávnená požiadať o ústne vysvetlenie ľubovoľnej časti riešenia.

**Dva piliere výučby**, z ktorých vychádzajú všetky okruhy tejto skúšky:

- **Repozitáre** (primárny zdroj poznámok, príkladov a zadaní):
  - https://github.com/SPSITKNM/SPSITKNM
  - https://github.com/SPSITKNM/oop_opakovanie
  - https://github.com/SPSITKNM/SXG

- **Videosériál** (výkladové videá ku všetkým témam skúšky, od základov jazyka cez algoritmizáciu až po pokročilé systémové témy):  
  https://youtube.com/playlist?list=PLJW-oHbyRDeJt24tw-RaHJwxbXUCh3GrQ

---

## OKRUH 1 – Základy jazyka, dátové typy a riadenie toku
*(Repozitár: `SPSITKNM` → `poznamky.md`)*

---

### 1.1 – Dátové typy a pamäť

**a)** Doplň tabuľku dátových typov v C# (alebo ich ekvivalenty v C++):

| Typ | Veľkosť | Rozsah / Popis | Príklad literálu |
|---|---|---|---|
| `byte` | 1 B | 0 až 255 | |
| `int` | | | `42` |
| `long` | | | |
| `float` | 4 B | | `3.14f` |
| `double` | | | |
| `bool` | | `true` / `false` | |
| `char` | | | `'A'` |
| `string` | | | |

**b)** Vysvetli rozdiel medzi **Stack** a **Heap** pamäťou. Kde sa alokujú lokálne premenné a kde objekty vytvorené cez `new`? Čo je **garbage collector** v C# a prečo ho C++ nemá?

**c)** Aký je výsledok nasledujúcich výrazov? Zdôvodni (pozor na implicitné pretypovanie):
```csharp
int a = 7 / 2;           // výsledok: ?
double b = 7.0 / 2;      // výsledok: ?
int c = (int)3.99;        // výsledok: ?
string s = "Číslo: " + 5 + 3;  // výsledok: ?
string t = "Číslo: " + (5 + 3); // výsledok: ?
```

---

### 1.2 – Riadenie toku a cykly

**a)** Napíš program, ktorý prečíta číslo `n` zo vstupu a vypíše násobilku od 1×n do 10×n. Ak je `n` záporné, program vypíše chybovú hlášku a skončí.

**b)** Prepíš nasledujúci `if-else` reťazec na `switch` príkaz a ekvivalentne na **ternárny operátor** (ak to je možné):
```csharp
if (skore >= 90) stupen = "A";
else if (skore >= 75) stupen = "B";
else if (skore >= 60) stupen = "C";
else stupen = "F";
```

**c)** Čo je rozdiel medzi `while` a `do-while` cyklom? Napíš príklad, kde je `do-while` nevyhnutný (situácia, kde telo musí vykonať aspoň raz).

---

### 1.3 – Polia a kolekcie

**a)** Vysvetli rozdiel medzi **statickým poľom**, **dynamickým zoznamom (`List<T>`)**, **viacrozmerným poľom** a **jagged array**. Pre každé uveď jeden vhodný use-case.

**b)** Implementuj metódu `int[] OtocPole(int[] vstup)`, ktorá vráti nové pole s prvkami v obrátenom poradí — **bez použitia vstavaných metód** (`Array.Reverse` a podobné sú zakázané). Napíš aj `Main()`, ktorý ju otestuje.

**c)** Napíš program, ktorý inicializuje maticu 3×3 celých čísel hodnotami od 1 do 9 a vypíše ju naformátovane do konzoly. Potom vypočíta a vypíše súčet diagonálnych prvkov (prvky kde `riadok == stĺpec`).

---

> **Mohlo by sa hodiť**
>
> *Konvencie pomenovania identifikátorov:*
> ```
> camelCase       → lokálne premenné, parametre:  mojePremenná
> PascalCase      → triedy, metódy, vlastnosti:   MojaTrieda
> snake_case      → konštanty v C++:              max_hodnota
> SCREAMING_SNAKE → globálne konštanty:           MAX_HODNOTA
> ```
>
> *Pretypovanie a reťazenie:*
> Operátor `+` pri `string` je ľavosmerný — výraz sa vyhodnocuje zľava doprava.
> `"text" + 5 + 3` → `"text5" + 3` → `"text53"` (nie `"text8"`!)

---

## OKRUH 2 – Objektovo-orientované programovanie
*(Repozitáre: `SPSITKNM`, `oop_opakovanie`)*

---

### 2.1 – Implementácia hierarchie tried

Navrhni a implementuj bankový systém podľa nasledujúcej špecifikácie:

**Trieda `Klient`**
- Atribúty: `kod` (int), `meno` (string)
- Konštruktor, metóda `zobraz()`

**Trieda `Ucet`** *(abstraktná alebo s virtuálnou metódou)*
- Atribúty: `cislo` (string), `zostatok` (double), `majitel` (Klient)
- Konštruktor, metóda `zobraz()`
- **Virtuálna / abstraktná** metóda `moznoVybrat(double suma)` → `bool`
- Metóda `vyber(double suma)` — ak je výber povolený, odčíta ho; inak vypíše chybové hlásenie

**Trieda `StandartnyUcet`** *(dedí od `Ucet`)*
- `moznoVybrat()` vráti `true` ak `zostatok >= suma`

**Trieda `UverUcet`** *(dedí od `Ucet`)*
- Pridáva `uverLimit` (double)
- `moznoVybrat()` povolí výber do mínusu — maximálne do výšky `uverLimit`

**Trieda `Banka`**
- Uchováva kolekciu ukazateľov `Ucet*` (alebo references)
- Metóda `pridajUcet(Ucet*)`
- Metóda `spracujVybery(double suma)` — zavolá `vyber()` na každom účte *(demonštruj polymorfizmus)*

**Povinné požiadavky:**
1. V C++: implementuj destruktory tam, kde je potrebné; zdôvodni kde nie
2. Nakresli **UML diagram** tried s vyznačením IS-A, HAS-A a viditeľnosťou členov
3. V `Main()` vytvor heterogénnu kolekciu (`StandartnyUcet` aj `UverUcet`) a zavolaj `spracujVybery()`

---

### 2.2 – Statický čítač a správa pamäte

Implementuj triedu `Spojenie` (napr. databázové spojenie), ktorá:
- Statickým atribútom sleduje počet **aktívnych** inštancií (inkrementuje v konštruktore, dekrementuje v destruktore)
- Poskytuje statickú metódu `getAktivnych()` → int
- V C++: správne implementuje destruktor a uvoľňuje prípadné dynamicky alokované zdroje

Napíš `Main()`, kde vytvoríš 3 objekty, jeden zrušíš (`delete` v C++ alebo pomocou scope v C#) a overíš správnosť počítadla.

---

### 2.3 – Analytické otázky

**a)** Vysvetli **Liskovej substitučný princíp (LSP)**. Napíš príklad triedy, ktorá **porušuje** LSP, a vysvetli, aký problém to spôsobí za behu programu.

**b)** Porovnaj **dedičnosť (IS-A)** a **kompozíciu (HAS-A)**. Uveď konkrétny príklad z praxe, kde by použitie dedičnosti bolo nesprávne (napr. kde vzťah nie je skutočne IS-A) a kompozícia by bola správnym riešením.

**c)** Aké problémy prináša **hlboká dedičnostná hierarchia** (5+ úrovní)? Prečo sa v modernom vývoji uprednostňuje kompozícia a rozhrania (interfaces) pred hlbokou dedičnosťou?

**d)** Prečo je **zapuzdrenie** základom udržiavateľného kódu? Popíš konkrétny scenár, kde verejné atribúty namiesto getterov/setterov spôsobia skrytú chybu pri rozširovaní systému.

---

> **Mohlo by sa hodiť**
>
> *UML diagram tried — notácia:*
> ```
> ┌─────────────────┐
> │    <<abstract>> │
> │      Ucet       │
> ├─────────────────┤
> │ - cislo: string │   ← private
> │ # zostatok: dbl │   ← protected (prístupné potomkom)
> ├─────────────────┤
> │ + zobraz()      │
> │ + vyber()       │
> │ {abstract}      │
> │ + moznoVybrat() │
> └───────┬─────────┘
>         △  ← dedičnosť (IS-A)
>   ┌─────┴──────┐
>   │            │
> StandartnyUcet  UverUcet
>
> Banka ──◆── Ucet*   (HAS-A, agregácia)
> Ucet  ──◆── Klient  (HAS-A, kompozícia)
> ```
>
> *LSP jednoducho:* Kdekoľvek použiješ `Ucet*`, musí korektne fungovať `UverUcet*` aj `StandartnyUcet*` bez nutnosti testovať konkrétny typ (`instanceof` / `dynamic_cast` v produkčnom kóde = zápach).

---

## OKRUH 3 – Algoritmizácia: zložitosť a lineárne dátové štruktúry
*(Repozitár: `SPSITKNM` → `algoritmizacia.md`, YouTube playlist)*

---

### 3.1 – Analýza časovej zložitosti

Urči Big O zložitosť každého úseku a **písomne zdôvodni** — nestačí uviesť len výsledok:

```cpp
// (a) — čo sa deje s j?
for (int i = 0; i < n; i++)
    for (int j = i; j < n; j++)
        cout << i + j;

// (b)
int x = n;
while (x > 1)
    x = x / 2;

// (c) — dve rôzne vstupné premenné
void f(int a, int b) {
    for (int i = 0; i < a; i++) cout << i;
    for (int j = 0; j < b; j++) cout << j;
}

// (d) — vnorené na rôznych premenných
for (int i = 0; i < a; i++)
    for (int j = 0; j < b; j++)
        cout << i * j;
```

**Analytická otázka:** Prečo sa výraz `O(n² + n)` zjednodušuje na `O(n²)`? Je toto zjednodušenie vždy správne, alebo existujú situácie kde na nezanedbávanom člene záleží?

---

### 3.2 – Implementácia: Spájaný zoznam (Singly Linked List)

Implementuj v C++ triedu `LinkedList` so všetkými nasledujúcimi metódami. Každý uzol alokuj dynamicky (`new`), v destruktore pamäť uvoľni.

| Metóda | Zložitosť | Poznámka |
|---|---|---|
| `append(int val)` | O(1) | Pridaj na koniec |
| `prepend(int val)` | O(1) | Pridaj na začiatok |
| `deleteFirst()` | O(1) | Odstráň prvý uzol |
| `deleteLast()` | O(n) | Odstráň posledný uzol |
| `get(int index)` | O(n) | Vráť ukazateľ na uzol |
| `set(int index, int val)` | O(n) | Nastav hodnotu uzla |
| `insert(int index, int val)` | O(n) | Vlož uzol na pozíciu |
| `deleteNode(int index)` | O(n) | Zmaž uzol na pozícii |
| `reverse()` | O(n) | Obrať zoznam in-place |
| `print()` | O(n) | Vypíš celý zoznam |

Po implementácii písomne odpovedz:
- Prečo je `deleteLast()` O(n) pri jednoduchom LL a ako to rieši **dvojito spájaný zoznam (DLL)**?
- Aký je rozdiel medzi **DLL** a **kruhovým spájaným zoznamom (circular LL)**? Kedy je každý vhodný?

---

### 3.3 – Implementácia: Stack — overenie zátvorkového výrazu

Implementuj funkciu `bool jeVyvazeny(string vyraz)`, ktorá pomocou **vlastnej implementácie Stack** (nie `std::stack`) overí, či je zátvorkový výraz správne uzavretý. Funkcia musí spracovať kombináciu `()`, `[]`, `{}`.

Príklady vstupu a očakávaného výstupu:
- `"{[()]}"` → `true`
- `"{[(])}"` → `false`  
- `"((("` → `false`
- `""` → `true`

---

### 3.4 – Implementácia: Queue — simulácia frontu

Implementuj program simulujúci **front tlačových úloh** s vlastnou triedou `Queue`:
- `TlacovaUloha`: atribúty `id`, `nazov`, `pocetStran`
- `TlacovaFronta`: operácie `enqueue()`, `dequeue()`, `peek()`, `isEmpty()`
- `Main()`: pridaj 5 úloh, postupne ich spracuj (vypíš poradie) — demonštruj FIFO správanie

---

### 3.5 – Analytická otázka

Pole (`std::vector`) umožňuje prístup k prvku v O(1), spájaný zoznam len v O(n). Napriek tomu existujú scenáre, kde je spájaný zoznam výhodnejší. Uveď **dva konkrétne scenáre** s odôvodnením, prečo je tu LL lepší než pole.

---

> **Mohlo by sa hodiť**
>
> *Vizualizácia uzla a zoznamov:*
> ```
> Singly LL:   head → [10|•] → [20|•] → [30|/] ← tail
>
> DLL:         head → [/|10|•] ⇄ [•|20|•] ⇄ [•|30|/] ← tail
>
> Circular LL: head → [10|•] → [20|•] → [30|•] ──┐
>                └──────────────────────────────────┘
> ```
>
> *Algoritmus `reverse()` — three-pointer technika:*
> ```cpp
> Node *prev = nullptr, *curr = head, *next = nullptr;
> while (curr != nullptr) {
>     next = curr->next;   // ulož nasledovníka
>     curr->next = prev;   // otočíš šípku
>     prev = curr;         // posuň prev
>     curr = next;         // posuň curr
> }
> head = prev;
> ```
>
> *Rastová tabuľka zložitostí (n = 1000):*
> ```
> O(1)      →         1 op.
> O(log n)  →        10 op.
> O(n)      →     1 000 op.
> O(n log n)→    10 000 op.
> O(n²)     → 1 000 000 op.
> ```

---

## OKRUH 4 – Algoritmizácia: pokročilé dátové štruktúry a triediace algoritmy
*(Repozitár: `SPSITKNM` → `zadania_na_domacu_pracu.md`, `opravne_ulohy.md`, YouTube playlist)*

---

### 4.1 – Binary Search Tree (BST)

**a)** Vysvetli invariant BST: aká podmienka musí platiť pre každý uzol (vzťah k ľavému a pravému podstromu)?

**b)** Implementuj triedu `BST` s nasledujúcimi metódami:
- `insert(int val)` — vloží hodnotu na správne miesto, O(log n) priemerný prípad
- `contains(int val)` → bool — vyhľadá hodnotu
- `inorderTraversal()` — vypíše všetky hodnoty **vzostupne** (využi rekurziu)

**c)** Vlož do BST (v tomto poradí) čísla: `50, 30, 70, 20, 40, 60, 80`. Nakresli výsledný strom a popiš postup `inorderTraversal()` — v akom poradí sa uzly navštívia?

**d)** Analytická otázka: Čo je **degenerovaný BST** a kedy k nemu dôjde? Aká je jeho časová zložitosť a ako ho možno riešiť (uveď pojem, nie implementáciu)?

---

### 4.2 – Hash Tabuľka

**a)** Vysvetli princíp hash tabuľky: čo je **hash funkcia**, **bucket** a **kolízia**? Ako sa kolízie riešia metódou **separate chaining**?

**b)** Implementuj jednoduchú hash tabuľku v C++ s metódami:
- `set(string key, int value)` — uloží dvojicu kľúč-hodnota (zvládni kolízie)
- `get(string key)` → int — vráti hodnotu pre daný kľúč (-1 ak neexistuje)
- `keys()` → vypíše všetky unikátne kľúče

**c)** Implementuj funkciu `bool maSpolognyPrvok(int[] a, int[] b)`, ktorá zistí, či majú dve polia spoločný prvok — **v čase O(n)** (nie O(n²)). Využi hash tabuľku alebo `unordered_set`.

**d)** Analytická otázka: Prečo je priemerná zložitosť operácie `get()` v hash tabuľke O(1), ale v najhoršom prípade O(n)? Kedy nastáva najhorší prípad?

---

### 4.3 – Graf a BFS

**a)** Vysvetli rozdiel medzi **orientovaným** a **neorientovaným** grafom. Čo je **adjacency list** a prečo sa preferuje pred **adjacency matrix** pri riedkych grafoch?

**b)** Implementuj triedu `Graf` reprezentujúcu neorientovaný graf pomocou adjacency listu (`unordered_map<string, vector<string>>`):
- `addVertex(string nazov)`
- `addEdge(string od, string do)`
- `removeEdge(string od, string do)`
- `removeVertex(string nazov)` — odstráni aj všetky hrany

**c)** Implementuj metódu `bfsTraversal(string start)`, ktorá vypíše všetky uzly dosiahnuteľné z `start` pomocou **prehľadávania do šírky (BFS)**. Použij `Queue` ako pomocnú štruktúru.

**d)** Analytická otázka: Prečo BFS využíva Queue a nie Stack? Čo by sa stalo, ak by sme Stack použili namiesto Queue (aký algoritmus by sme dostali)?

---

### 4.4 – Triediace algoritmy

Pre každý algoritmus:
1. Vysvetli princíp (slovne alebo pseudokódom)
2. Uveď časovú zložitosť (best / average / worst case)
3. Uveď priestorovú zložitosť

| Algoritmus | Princíp | Best | Average | Worst | Priestor |
|---|---|---|---|---|---|
| **Bubble Sort** | | | | | |
| **Quick Sort** | | | | | |
| **Merge Sort** | | | | | |

**Implementačná úloha:** Implementuj **Merge Sort** pre pole celých čísel. Demonštruj funkčnosť na poli `{38, 27, 43, 3, 9, 82, 10}` — nakresli diagram postupu delenia a spájania.

**Analytická otázka:** Prečo je Merge Sort preferovaný pred Quick Sort pre triedenie **spájaných zoznamov**? (Nápoveda: myslí na prístup k pamäti.)

---

### 4.5 – Makefile

**a)** Vysvetli štruktúru Makefile pravidla: čo je **target**, **dependency** a **command**? Prečo musí command začínať TABulátorom?

**b)** Napíš `Makefile` pre C++ projekt s týmito súbormi: `main.cpp`, `LinkedList.cpp`, `LinkedList.h`. Makefile musí:
- Skompilovať každý `.cpp` zvlášť na `.o` (objektový súbor)
- Linkovať objektové súbory do spustiteľného súboru `app`
- Obsahovať target `clean` na zmazanie `.o` súborov a `app`
- Používať premenné `CC = g++` a `CFLAGS = -Wall -std=c++17`

**c)** Aký je rozdiel medzi `make` a `make clean`? Čo robí automatická premenná `$@` a `$^`?

---

> **Mohlo by sa hodiť**
>
> *BST invariant vizuálne:*
> ```
>         50
>        /  \
>       30   70
>      / \  / \
>     20 40 60 80
>
> Inorder: 20 → 30 → 40 → 50 → 60 → 70 → 80  (vzostupne!)
> ```
>
> *BFS postup — využíva Queue:*
> ```
> Začiatok: Queue = [A]
> Spracuj A → pridaj susedov B, C → Queue = [B, C]
> Spracuj B → pridaj susedov D, E → Queue = [C, D, E]
> ...
> ```
>
> *Merge Sort diagram:*
> ```
> [38,27,43,3]   →  [38,27] + [43,3]
> [38,27]        →  [38] + [27]  →  merge → [27,38]
> [43,3]         →  [43] + [3]   →  merge → [3,43]
> final merge    →  [3,27,38,43]
> ```
>
> *Makefile — základná štruktúra:*
> ```makefile
> CC = g++
> CFLAGS = -Wall -std=c++17
>
> app: main.o LinkedList.o
> 	$(CC) $(CFLAGS) -o $@ $^
>
> %.o: %.cpp
> 	$(CC) $(CFLAGS) -c $<
>
> clean:
> 	rm -f *.o app
> ```

---

## OKRUH 5 – Git, GitHub, GitLab a CI/CD
*(Repozitáre: `SPSITKNM` → `GitHub_vs_GitLab.md`, `SXG` → `git_github_gitlab.md`)*

---

### 5.1 – Feature branch workflow: presné príkazy

Pre každý krok nasledujúceho scenára napíš presný git príkaz (alebo sériu príkazov):

1. Inicializuj lokálny repozitár a pripoj ho k vzdialenému originu `https://gitlab.com/skola/projekt.git`
2. Vytvor vetvu `feature/user-auth` a prepni sa na ňu
3. Pridaj všetky zmenené súbory do staging area a vytvor commit so správou `"feat: add JWT authentication"`
4. Odošli vetvu na vzdialený server (prvý push novej vetvy)
5. Na vetve `main` nastala zmena; integruj ju do svojej feature vetvy **bez vytvorenia merge commitu**
6. Pri zlúčení nastane konflikt v súbore `auth.cpp` — popiš postup riešenia krok po kroku
7. Po schválení merge requestu zmaž lokálnu aj vzdialenú vetvu `feature/user-auth`

---

### 5.2 – Návrh CI/CD pipeline

Napíš funkčný `.gitlab-ci.yml` pre C++ projekt s týmito požiadavkami:
- **Fáza `build`:** skompilovanie projektu pomocou `make`
- **Fáza `test`:** spustenie testov (napr. `./run_tests.sh`)
- **Fáza `deploy`:** spustí sa **iba na vetve `main`**; nasadí artefakt (môže byť symbolické)
- Nastav image `gcc:latest`
- Artefakty z `build` fázy (skompilovaný binárny súbor) odovzdaj do `test` fázy

---

### 5.3 – Identifikácia anti-patterns

V nasledujúcom git workflow sú **3 závažné chyby**. Identifikuj každú a vysvetli, prečo je problematická a ako ju opraviť:

```bash
git checkout main
# ... vývojár upravuje súbory ...
git add .
git commit -m "fix"
git push origin main

# Kolega sa pokúša synchronizovať a nastane konflikt:
git reset --hard origin/main   # zahodí vlastné zmeny
git push --force origin main   # prepíše vzdialenú históriu
```

---

### 5.4 – Analytické otázky

**a)** `git merge` vs `git rebase` — vysvetli rozdiel vo výslednej git histórii. Uveď **konkrétnu situáciu** pre každý príkaz, kde je jeho použitie optimálne.

**b)** Čo je **CI/CD** a aký **business benefit** prináša oproti manuálnemu nasadzovaniu — argumentuj nie len technicky, ale z pohľadu organizácie/biznisu.

**c)** `git fetch` stiahne zmeny zo vzdialeného repozitára, ale neaplikuje ich. `git pull` stiahne a okamžite aplikuje. V akej situácii je `git fetch` + manuálny `git merge` bezpečnejšia voľba ako `git pull`?

---

> **Mohlo by sa hodiť**
>
> *Git flow schéma:*
> ```
> main     ──●──────────────────────────●── (merge commit)
>             \                        /
> feature      ●──●──●──●──●──●──●──●
> ```
>
> *`.gitlab-ci.yml` — základná kostra:*
> ```yaml
> stages:
>   - build
>   - test
>   - deploy
>
> build-job:
>   stage: build
>   image: gcc:latest
>   script:
>     - make
>   artifacts:
>     paths:
>       - app
>
> deploy-job:
>   stage: deploy
>   rules:
>     - if: '$CI_COMMIT_BRANCH == "main"'
> ```

---

## OKRUH 6 – Operačné systémy a Linux
*(Repozitár: `SXG` → `Uvod_do_operacnych_systemov.md`, `Linux Commands Cheat Sheet.md`, `fedora_commands.md`)*

---

### 6.1 – Implementácia: fork() a pipe() v jazyku C

Napíš kompletný program v **jazyku C**, ktorý:
1. Vytvorí komunikačný kanál (`pipe()`)
2. Zavolá `fork()` na vytvorenie potomka
3. **Rodič** zapíše do pipe správu vo formáte `"Správa od rodiča PID=<PID>"` a zatvorí write-end
4. **Potomok** prečíta správu z pipe, vypíše ju na `stdout` a zatvorí read-end
5. **Rodič** počká na ukončenie potomka (`wait()`) a vypíše jeho návratový kód

Program musí korektne zatvárať neupotrené file descriptory a ošetriť zlyhanie `fork()`.

**Po implementácii odpovedz:** Čo je **zombie proces**? Ako vzniká a akú rolu hrá `wait()` pri jeho prevencii?

---

### 6.2 – Stavový diagram procesu

Nakresli stavový diagram procesu so stavmi `NEW → READY → RUNNING → WAITING → TERMINATED`. Pre každý prechod (šípku) uveď **konkrétnu udalosť**, ktorá ho spôsobuje.

Doplň: Čo obsahuje **PCB (Process Control Block)** a prečo ho OS potrebuje pri **prepínaní kontextu (context switch)**? Vymenuj minimálne 5 položiek PCB.

---

### 6.3 – Linux príkazy: scenáre

Pre každý scenár napíš presný príkaz (prípadne reťazec pomocou `|`):

| Scenár | Príkaz |
|---|---|
| Zobraz bežiace procesy: PID, USER, CPU%, MEM%, CMD | |
| Nájdi všetky riadky s `ERROR` v `system.log` a ulož ich do `chyby.txt` | |
| Sleduj koniec `system.log` v reálnom čase (nové záznamy) | |
| Rekurzívne nájdi všetky súbory `.conf` v `/etc` | |
| Nastav práva `deploy.sh` na `rwxr-xr--` (octal) | |
| Zobraz aktívne sieťové rozhrania a IP adresy | |
| Ukonči proces s názvom `nginx` bez znalosti PID | |
| Zoraď riadky `data.csv` podľa druhého stĺpca (oddelovač `,`) | |
| Skopíruj adresár `projekt/` na vzdialený server `192.168.1.10:/home/admin/` | |
| Zobraz veľkosť adresárov v `/var/log` od najväčšieho | |

---

### 6.4 – Analytické otázky

**a)** Porovnaj **pipe** a **zdieľanú pamäť (shared memory)** ako dva IPC mechanizmy — výhody, nevýhody, typické use-cases.

**b)** Čo sú **file descriptory** 0, 1, 2? Čo sa stane ak program uzavrie `stdout` (`close(1)`) a následne otvorí nový súbor — aký file descriptor dostane a prečo?

**c)** Prečo je `fork()` v Unixe navrhnutý tak, aby skopíroval celý adresný priestor rodiča? Aký mechanizmus operačný systém využíva na optimalizáciu tejto kopírovej operácie (`copy-on-write`)?

---

> **Mohlo by sa hodiť**
>
> *Kostra programu s `fork()` a `pipe()`:*
> ```c
> #include <unistd.h>
> #include <sys/wait.h>
> #include <stdio.h>
> #include <string.h>
>
> int main() {
>     int pipefd[2];           // [0]=read end, [1]=write end
>     pipe(pipefd);
>     pid_t pid = fork();
>     if (pid < 0)  { /* chyba */ }
>     else if (pid == 0) {
>         close(pipefd[1]);    // potomok nepíše
>         // read(pipefd[0], ...)
>     } else {
>         close(pipefd[0]);    // rodič nečíta
>         // write(pipefd[1], ...)
>         wait(NULL);
>     }
> }
> ```
>
> *File descriptory:*
> ```
> 0 = stdin   (klávesnica)
> 1 = stdout  (terminál)
> 2 = stderr  (chybový výstup)
> ```
>
> *Práva a octal:*
> ```
> rwxr-xr-- = 754
> r=4, w=2, x=1  →  rwx=7, r-x=5, r--=4
> ```

---

## OKRUH 7 – Virtualizácia: VirtualBox, KVM a Docker
*(Repozitár: `SXG` → `VirtualBox Guide.md`, `kvm.md`, `docker.md`)*

---

### 7.1 – Dockerfile pre produkčnú aplikáciu

Napíš `Dockerfile` pre **Python Flask API** s týmito požiadavkami:
- Základný image: `python:3.11-slim`
- Pracovný adresár: `/app`
- Skopíruje `requirements.txt` a nainštaluje závislosti **pred** kopírovaním zdrojového kódu
- Skopíruje celý zdrojový kód
- Nastaví premennú prostredia `FLASK_ENV=production`
- Exponuje port `5000`
- Spustí: `flask run --host=0.0.0.0`

**Po implementácii vysvetli:** Prečo je výhodné kopírovať `requirements.txt` **pred** zvyšným kódom? (Súvisí s Docker layer cache.)

---

### 7.2 – Docker Compose: viacservisná aplikácia

Napíš `docker-compose.yml` pre systém:
- Služba `web`: tvoj Flask image (port 5000 → host 8080)
- Služba `db`: `postgres:15` s premennými `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_DB`
- Obidve v spoločnej sieti `backend-net`
- Dáta DB sú perzistentné cez named volume `pgdata`
- `web` čaká na `db` (`depends_on`)

---

### 7.3 – VBoxManage automatizácia

Napíš sekvenciu `VBoxManage` príkazov, ktorá automatizovane:
1. Vytvorí VM `TestVM` (typ Linux, variant Ubuntu_64)
2. Nastaví 2048 MB RAM a 2 CPU
3. Vytvorí dynamicky alokovaný VDI disk 20 GB a pripojí ho
4. Nastaví sieťový adaptér na bridged režim
5. Spustí VM v headless režime

---

### 7.4 – KVM konfigurácia

Napíš príkazy (jeden riadok každý), ktoré:
1. Overia podporu HW virtualizácie (VT-x / AMD-V)
2. Skontrolujú načítanie KVM kernel modulov
3. Overia vhodnosť systému pre QEMU/KVM hosting
4. Nastavia optimalizačný profil `virtual-host`

---

### 7.5 – Analytické otázky

**a)** Porovnaj **kontajner (Docker)** a **virtuálny stroj (VM)** z hľadiska: (1) izolácie, (2) výkonnostného overheadu, (3) vhodného use-case.

**b)** Vysvetli Docker **layer caching** — ako Docker rozhoduje, ktoré vrstvy rebuildiť? Prečo `COPY . .` na začiatku Dockerfile je anti-pattern?

**c)** Prečo sa KVM preferuje pred VirtualBoxom na produkčných serveroch? Uveď aspoň 2 technické dôvody súvisiace s typom hypervisora.

**d)** Aké sú **4 sieťové režimy VirtualBoxu** (NAT, NAT Network, Bridged, Host-only)? Pre každý uveď typický scenár použitia.

---

> **Mohlo by sa hodiť**
>
> *Docker architektúra:*
> ```
> Docker CLI ──(REST API)──► Docker Daemon
>                              ├── Images   (read-only vrstvy)
>                              ├── Containers (bežiace inštancie)
>                              └── Volumes  (perzistentné úložisko)
> ```
>
> *Dockerfile — layer cache princíp:*
> ```
> COPY requirements.txt .   ← invaliduje cache len ak sa zmení requirements.txt
> RUN pip install ...        ← reexekvuje len ak predchádzajúca vrstva je nová
> COPY . .                   ← invaliduje cache pri každej zmene kódu
> ```
>
> *KVM príkazy:*
> ```bash
> lscpu | grep -i virtualization
> lsmod | grep kvm
> virt-host-validate qemu
> tuned-adm profile virtual-host
> ```

---

## OKRUH 8 – Monitoring a OpenTelemetry
*(Repozitár: `SXG` → `otel.md`)*

---

### 8.1 – Návrh observability stratégie

Máš trojvrstvovú webovú aplikáciu: `frontend (React)` → `api (Python REST)` → `databaza (PostgreSQL)`.

Navrhni komplexnú observability stratégiu s využitím OpenTelemetry. Pre každú vrstvu uveď:
- Čo budeš sledovať pomocou **Traces** a prečo práve traces (nie metriky)?
- Aké konkrétne **Metrics** nastavíš pre vrstvu `api` (min. 3 metriky s popisom čo merajú)
- Aké udalosti budú zaznamenávané ako **Logs** a na akej severity úrovni (`INFO`, `WARN`, `ERROR`)

Každé rozhodnutie zdôvodni.

---

### 8.2 – Analýza trace diagramu

```
[HTTP Request] ─────────────────────────────────── 850ms ─┐
  ├─[span: api.authenticate]          12ms                 │
  ├─[span: api.getUserData]          780ms  ◄── !          │
  │    └─[span: db.query_user]       775ms  ◄── !          │
  └─[span: api.renderResponse]        55ms                 │
                                                           ┘
```

**a)** Kde nastáva bottleneck? Zdôvodni na základe čísel v trace.

**b)** Aké sú **aspoň 3 hypotézy**, prečo `db.query_user` trvá 775ms?

**c)** Aké metriky na databázovej vrstve by si monitoroval, aby si tieto hypotézy potvrdil alebo vyvrátil?

---

### 8.3 – Analytické otázky

**a)** Kedy použiješ **auto-instrumentáciu** a kedy **manuálnu instrumentáciu**? Porovnaj development effort vs. granularitu dát.

**b)** Prečo nestačí samotné logovanie (Logs) na diagnostiku výkonnostných problémov v distribuovanom systéme? Čo Traces pridávajú navyše?

**c)** Vysvetli mechanizmus **context propagation** — ako distribuovaný trace prepája spany naprieč viacerými službami a procesmi?

---

> **Mohlo by sa hodiť**
>
> *Tri piliere observability — kedy ktorý:*
> ```
> Traces  → Prečo je požiadavka pomalá? Kde je bottleneck?
> Metrics → Ako sa mení trend v čase? Rastie počet chýb?
> Logs    → Čo presne sa stalo? Aká bola chybová správa?
> ```
>
> *Schéma distribuovaného trace:*
> ```
> request → [frontend span]
>                │ HTTP header: traceparent
>                ▼
>           [api span]
>                │ DB connection
>                ▼
>           [db span]
> ```
>
> *Nástroje ekosystému:*
> Prometheus (scraping), Grafana (vizualizácia), Jaeger / Zipkin (trace UI),
> Datadog (all-in-one komerčné), OpenTelemetry Collector (agregácia + routing)

---

## OKRUH 9 – AI-asistovaný vývoj (Claude Code)
*(Repozitár: `SPSITKNM` → `zadania_na_hodine.md`)*

---

### 9.1 – Základné koncepty

**a)** Vysvetli rozdiel medzi **CLI** a **GUI** rozhraním AI asistenta. Uveď aspoň 2 výhody CLI prístupu pri práci s kódom (napr. automatizácia, SSH).

**b)** Čo je **context window** (kontextové okno)? Čo je **compaction** a aká je jeho nevýhoda pri dlhých konverzáciách?

**c)** Prečo sa lokálne nastavenia Claude (napr. `settings.local.json`) **nezahŕňajú do git repozitára**? Aké riziká by to prinieslo?

---

### 9.2 – Permissions a bezpečnosť

**a)** Aké typy akcií v Claude Code **stále vyžadujú manuálne potvrdenie** napriek udeleniam oprávnení? (Uveď aspoň 2 príklady.)

**b)** Čo je **sandbox** v kontexte Claude Code? S čím ho možno prirovnať z bežného IT sveta?

**c)** Čo môže AI urobiť s git históriou a súbormi v tzv. **dangerous / dangerouslySkipPermissions** režime? Prečo je tento režim rizikový?

---

### 9.3 – Plan Mode a Context Engineering

**a)** Na aké typy úloh je vhodné použiť **Plan Mode** (režim plánovania)? Uveď aspoň 3 scenáre, kedy ho má vývojár aktivovať pred tým, ako AI začne robiť zmeny.

**b)** Čo je `CLAUDE.md` a prečo je výhodné do neho zahrnúť iba referenciu na `SPEC.md` namiesto priameho kopírovania obsahu?

**c)** Vysvetli 2 princípy **Context Engineering** pri práci s AI:
- Čo sa myslí pod „poskytni relevantnú informáciu"?
- Prečo je stručnosť (`brevity`) dôležitá pri práci s kontextovým oknom?

---

### 9.4 – Pokročilé funkcie

**a)** Čo sú **MCP (Model Context Protocol) servery** a aký typ funkcionality umožňujú AI asistentovi, ktorý by bez nich nemal?

**b)** Čo sú **Hooks** v Claude Code? Uveď príklad udalosti, ktorá hook spúšťa, a príklad akcie, ktorú hook vykoná.

**c)** Vysvetli koncept **Feedback Loop** pri AI-asistovanom vývoji. Prečo je dôležité používať nástroje ako **Playwright** na verifikáciu výsledkov? Aká je hlavná nevýhoda feedback loop prístupu?

**d)** Čo je **Multi-Agent systém (Ralph Loop)**? Pre aký typ pracovného zaťaženia (`workload`) je najvhodnejší a aký aspekt kontroly sa pri ňom znižuje?

---

### 9.5 – Analytická otázka

Na základe všetkého, čo si sa naučil o AI-asistovanom vývoji:

**a)** Aké sú **3 najväčšie výhody** integrácie AI asistenta do vývojového procesu?

**b)** Aké sú **3 najväčšie riziká** — technické, bezpečnostné alebo organizačné?

**c)** Prečo je **verzovací systém (Git)** obzvlášť dôležitý pri práci s AI asistentom, ktorý môže robiť rozsiahle zmeny v kóde?

---

> **Mohlo by sa hodiť**
>
> *Kľúčové pojmy a ich prepojenie:*
> ```
> CLAUDE.md  → projektové inštrukcie (súčasť kontextu každej konverzácie)
> SPEC.md    → špecifikácia projektu (referovaná z CLAUDE.md)
> Plan Mode  → AI navrhuje, človek schvaľuje pred vykonaním
> Hooks      → shell príkazy spúšťané automaticky pri udalostiach
> MCP        → rozšírenia umožňujúce AI prístup k externým systémom
> ```
>
> *Prečo Git + AI = nevyhnutnosť:*
> AI môže urobiť rozsiahle zmeny v desiatich súboroch naraz.
> Bez commitu pred zmenou nie je možnosť vrátiť sa k predchádzajúcemu stavu.
> `git commit` pred AI akciou = záchranná sieť.

---

## Hodnotiace kritériá

| Okruh | Téma | Praktické | Analytické | Max. bodov |
|---|---|---|---|---|
| 1 | Základy jazyka a dátové typy | 15 | 5 | 20 |
| 2 | OOP | 15 | 5 | 20 |
| 3 | Algoritmizácia – lineárne štruktúry | 20 | 5 | 25 |
| 4 | Algoritmizácia – pokročilé štruktúry | 20 | 5 | 25 |
| 5 | Git / GitLab / CI-CD | 10 | 5 | 15 |
| 6 | OS a Linux | 15 | 5 | 20 |
| 7 | Virtualizácia | 10 | 5 | 15 |
| 8 | OpenTelemetry | 5 | 5 | 10 |
| 9 | AI-asistovaný vývoj | 5 | 5 | 10 |
| **Celkom** | | **115** | **45** | **160** |

*(Bodovanie je orientačné — komisia môže upraviť váhu jednotlivých úloh.)*

**Klasifikačná stupnica:**
| Percentá | Klasifikácia |
|---|---|
| 90 – 100 % | 1 – výborný |
| 75 – 89 % | 2 – chválitebný |
| 55 – 74 % | 3 – dobrý |
| 35 – 54 % | 4 – dostatočný |
| 0 – 34 % | 5 – nedostatočný |

---

*Autor: Tomáš Mucha | Predmet: SGX – SMART technológie | SPSIT KNM*  
*Repozitáre: github.com/SPSITKNM/{SPSITKNM, oop\_opakovanie, SXG}*  
*Videosériál (oba piliere výučby): https://youtube.com/playlist?list=PLJW-oHbyRDeJt24tw-RaHJwxbXUCh3GrQ*
