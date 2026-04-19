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

**Inštrukcie k odovzdaniu:** Klonuj tento repozitár, vypĺňaj odpovede priamo do tohto súboru na označené miesta a odovzdaj repozitár hodnotiacej komisii.

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

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**c)** Aký je výsledok nasledujúcich výrazov? Zdôvodni (pozor na implicitné pretypovanie):

```csharp
int a = 7 / 2;                  // výsledok: ?
double b = 7.0 / 2;             // výsledok: ?
int c = (int)3.99;              // výsledok: ?
string s = "Číslo: " + 5 + 3;  // výsledok: ?
string t = "Číslo: " + (5 + 3);// výsledok: ?
```

> **Odpoveď:**
>
> *(Doplň výsledky a zdôvodnenie pre každý výraz.)*

---

### 1.2 – Riadenie toku a cykly

**a)** Napíš program, ktorý prečíta číslo `n` zo vstupu a vypíše násobilku od 1×n do 10×n. Ak je `n` záporné, program vypíše chybovú hlášku a skončí.

```cpp
// ===== TVOJE RIEŠENIE – násobilka =====



// =======================================
```

**b)** Prepíš nasledujúci `if-else` reťazec na `switch` príkaz a ekvivalentne na **ternárny operátor** (ak to je možné):

```csharp
if (skore >= 90) stupen = "A";
else if (skore >= 75) stupen = "B";
else if (skore >= 60) stupen = "C";
else stupen = "F";
```

```csharp
// ===== TVOJE RIEŠENIE – switch =====



// ====================================

// ===== TVOJE RIEŠENIE – ternárny operátor =====



// ===============================================
```

**c)** Čo je rozdiel medzi `while` a `do-while` cyklom? Napíš príklad, kde je `do-while` nevyhnutný.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

```cpp
// ===== TVOJE RIEŠENIE – príklad do-while =====



// =============================================
```

---

### 1.3 – Polia a kolekcie

**a)** Vysvetli rozdiel medzi **statickým poľom**, **dynamickým zoznamom (`List<T>`)**, **viacrozmerným poľom** a **jagged array**. Pre každé uveď jeden vhodný use-case.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Implementuj metódu `int[] OtocPole(int[] vstup)`, ktorá vráti nové pole s prvkami v obrátenom poradí — **bez použitia vstavaných metód**. Napíš aj `Main()`, ktorý ju otestuje.

```cpp
// ===== TVOJE RIEŠENIE – OtocPole =====



// =====================================
```

**c)** Napíš program, ktorý inicializuje maticu 3×3 hodnotami 1–9, vypíše ju naformátovane a vypočíta súčet diagonálnych prvkov (`riadok == stĺpec`).

```cpp
// ===== TVOJE RIEŠENIE – matica 3x3 =====



// ========================================
```

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

**Trieda `Klient`** — atribúty `kod` (int), `meno` (string); konštruktor, metóda `zobraz()`  
**Trieda `Ucet`** *(abstraktná)* — atribúty `cislo`, `zostatok`, `majitel`; virtuálna metóda `moznoVybrat(double suma)` → bool; metóda `vyber(double suma)`  
**Trieda `StandartnyUcet`** *(dedí od `Ucet`)* — `moznoVybrat()` vráti `true` ak `zostatok >= suma`  
**Trieda `UverUcet`** *(dedí od `Ucet`)* — pridáva `uverLimit`; `moznoVybrat()` povolí výber do mínusu do výšky limitu  
**Trieda `Banka`** — kolekcia `Ucet*`; metódy `pridajUcet()`, `spracujVybery(double suma)` *(demonštruj polymorfizmus)*

Povinné: destruktory kde treba (C++), UML diagram, heterogénna kolekcia v `Main()`.

```cpp
// ===== TVOJE RIEŠENIE – bankový systém =====



// ============================================
```

**UML diagram tried** (nakresli ASCII diagramom alebo popíš vzťahy):

```
===== UML DIAGRAM =====



=======================
```

---

### 2.2 – Statický čítač a správa pamäte

Implementuj triedu `Spojenie` so statickým čítačom aktívnych inštancií (inkrement v konštruktore, dekrement v destruktore) a statickou metódou `getAktivnych()`. Napíš `Main()` demonštrujúci správnosť.

```cpp
// ===== TVOJE RIEŠENIE – statický čítač =====



// ============================================
```

---

### 2.3 – Analytické otázky

**a)** Vysvetli **Liskovej substitučný princíp (LSP)**. Napíš príklad triedy, ktorá LSP **porušuje**, a vysvetli, aký problém to spôsobí za behu.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

```cpp
// ===== PRÍKLAD porušenia LSP =====



// ==================================
```

**b)** Porovnaj **dedičnosť (IS-A)** a **kompozíciu (HAS-A)**. Uveď konkrétny príklad z praxe, kde by dedičnosť bola nesprávna a kompozícia správna.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**c)** Aké problémy prináša **hlboká dedičnostná hierarchia** (5+ úrovní)? Prečo sa v modernom vývoji uprednostňuje kompozícia a rozhrania?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**d)** Prečo je **zapuzdrenie** základom udržiavateľného kódu? Popíš scenár, kde verejné atribúty spôsobia skrytú chybu pri rozširovaní systému.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

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
> │ # zostatok: dbl │   ← protected
> ├─────────────────┤
> │ + zobraz()      │
> │ {abstract}      │
> │ + moznoVybrat() │
> └───────┬─────────┘
>         △  ← dedičnosť (IS-A)
>   ┌─────┴──────┐
>   │            │
> StandartnyUcet  UverUcet
>
> Banka ──◆── Ucet*   (HAS-A)
> Ucet  ──◆── Klient  (HAS-A)
> ```
>
> *LSP jednoducho:* Kdekoľvek použiješ `Ucet*`, musí korektne fungovať aj `UverUcet*` — inak je návrh hierarchie chybný.

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

> ** Odpoveď – zložitosti a zdôvodnenia:**
>
> (a) Zložitosť: ___ — Zdôvodnenie: *(Sem vpíš.)*
>
> (b) Zložitosť: ___ — Zdôvodnenie: *(Sem vpíš.)*
>
> (c) Zložitosť: ___ — Zdôvodnenie: *(Sem vpíš.)*
>
> (d) Zložitosť: ___ — Zdôvodnenie: *(Sem vpíš.)*

**Analytická otázka:** Prečo sa `O(n² + n)` zjednodušuje na `O(n²)`? Je toto zjednodušenie vždy správne?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

### 3.2 – Implementácia: Singly Linked List

Implementuj v C++ triedu `LinkedList` so všetkými nasledujúcimi metódami. Uzly alokuj dynamicky, v destruktore pamäť uvoľni.

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

```cpp
// ===== TVOJE RIEŠENIE – LinkedList =====



// ========================================
```

> ** Odpoveď – analytické doplnenie:**
>
> Prečo je `deleteLast()` O(n) a ako to rieši DLL?
> *(Sem vpíš.)*
>
> Rozdiel medzi DLL a circular LL, kedy je každý vhodný?
> *(Sem vpíš.)*

---

### 3.3 – Implementácia: Stack — overenie zátvorkového výrazu

Implementuj `bool jeVyvazeny(string vyraz)` pomocou **vlastnej implementácie Stack** (nie `std::stack`). Spracuj kombináciu `()`, `[]`, `{}`.

Príklady: `"{[()]}"` → `true` | `"{[(])}"` → `false` | `"((("` → `false` | `""` → `true`

```cpp
// ===== TVOJE RIEŠENIE – Stack + jeVyvazeny() =====



// =================================================
```

---

### 3.4 – Implementácia: Queue — simulácia frontu

Implementuj simuláciu frontu tlačových úloh s vlastnou triedou `Queue`. Trieda `TlacovaUloha`: atribúty `id`, `nazov`, `pocetStran`. Trieda `TlacovaFronta`: operácie `enqueue()`, `dequeue()`, `peek()`, `isEmpty()`. V `Main()` pridaj 5 úloh a postupne ich spracuj — demonštruj FIFO.

```cpp
// ===== TVOJE RIEŠENIE – Queue + tlačový front =====



// ==================================================
```

---

### 3.5 – Analytická otázka

Pole umožňuje prístup v O(1), spájaný zoznam len v O(n). Napriek tomu existujú scenáre kde je LL výhodnejší. Uveď **dva konkrétne scenáre** s odôvodnením.

> **Odpoveď:**
>
> Scenár 1: *(Sem vpíš.)*
>
> Scenár 2: *(Sem vpíš.)*

---

> **Mohlo by sa hodiť**
>
> *Vizualizácia:*
> ```
> Singly LL:   head → [10|•] → [20|•] → [30|/] ← tail
> DLL:         head → [/|10|•] ⇄ [•|20|•] ⇄ [•|30|/] ← tail
> Circular LL: head → [10|•] → [20|•] → [30|•] ──┐
>                └──────────────────────────────────┘
> ```
>
> *Three-pointer reverse:*
> ```cpp
> Node *prev = nullptr, *curr = head, *next = nullptr;
> while (curr != nullptr) {
>     next = curr->next;
>     curr->next = prev;
>     prev = curr;
>     curr = next;
> }
> head = prev;
> ```
>
> *Rastová tabuľka (n = 1000):*
> ```
> O(1) → 1 op. | O(log n) → 10 | O(n) → 1 000 | O(n²) → 1 000 000
> ```

---

## OKRUH 4 – Algoritmizácia: pokročilé dátové štruktúry a triediace algoritmy
*(Repozitár: `SPSITKNM` → `zadania_na_domacu_pracu.md`, `opravne_ulohy.md`, YouTube playlist)*

---

### 4.1 – Binary Search Tree (BST)

**a)** Vysvetli invariant BST — aká podmienka musí platiť pre každý uzol?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Implementuj triedu `BST` s metódami `insert(int val)`, `contains(int val)` → bool, `inorderTraversal()` (vzostupný výpis, rekurzia).

```cpp
// ===== TVOJE RIEŠENIE – BST =====



// ================================
```

**c)** Vlož do BST čísla `50, 30, 70, 20, 40, 60, 80`. Nakresli výsledný strom a popiš postup `inorderTraversal()`.

```
===== DIAGRAM – BST strom =====



================================
```

> ** Odpoveď – postup inorderTraversal:**
>
> *(Popíš poradie navštívených uzlov.)*

**d)** Čo je **degenerovaný BST**, kedy k nemu dôjde a ako sa rieši (uveď pojem)?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

### 4.2 – Hash Tabuľka

**a)** Vysvetli pojmy **hash funkcia**, **bucket**, **kolízia** a riešenie kolízií metódou **separate chaining**.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Implementuj jednoduchú hash tabuľku s metódami `set(string key, int value)`, `get(string key)` → int, `keys()`.

```cpp
// ===== TVOJE RIEŠENIE – HashTable =====



// ========================================
```

**c)** Implementuj `bool maSpolognyPrvok(int[] a, int[] b)` v čase **O(n)** (nie O(n²)) pomocou hash tabuľky alebo `unordered_set`.

```cpp
// ===== TVOJE RIEŠENIE – maSpolognyPrvok =====



// ============================================
```

**d)** Prečo je priemerná zložitosť `get()` O(1), ale v najhoršom prípade O(n)? Kedy nastáva najhorší prípad?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

### 4.3 – Graf a BFS

**a)** Vysvetli rozdiel medzi **orientovaným** a **neorientovaným** grafom. Čo je **adjacency list** a prečo sa preferuje pred **adjacency matrix** pri riedkych grafoch?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Implementuj triedu `Graf` (neorientovaný, adjacency list: `unordered_map<string, vector<string>>`) s metódami `addVertex()`, `addEdge()`, `removeEdge()`, `removeVertex()`.

```cpp
// ===== TVOJE RIEŠENIE – Graf =====



// ==================================
```

**c)** Implementuj `bfsTraversal(string start)` — BFS prehľadávanie s využitím Queue.

```cpp
// ===== TVOJE RIEŠENIE – BFS =====



// =================================
```

**d)** Prečo BFS využíva Queue a nie Stack? Čo by sme dostali so Stackom?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

### 4.4 – Triediace algoritmy

Doplň tabuľku:

| Algoritmus | Princíp (stručne) | Best case | Average | Worst case | Priestor |
|---|---|---|---|---|---|
| **Bubble Sort** | | | | | |
| **Quick Sort** | | | | | |
| **Merge Sort** | | | | | |

**Implementačná úloha:** Implementuj **Merge Sort** pre pole celých čísel. Nakresli diagram postupu delenia a spájania pre vstup `{38, 27, 43, 3, 9, 82, 10}`.

```cpp
// ===== TVOJE RIEŠENIE – Merge Sort =====



// ========================================
```

```
===== DIAGRAM – Merge Sort delenie/spájanie =====



=================================================
```

**Analytická otázka:** Prečo je Merge Sort preferovaný pred Quick Sort pre triedenie **spájaných zoznamov**?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

### 4.5 – Makefile

**a)** Vysvetli štruktúru Makefile pravidla: čo je **target**, **dependency**, **command**? Prečo musí command začínať TABulátorom?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Napíš `Makefile` pre projekt s `main.cpp`, `LinkedList.cpp`, `LinkedList.h` — kompilácia po `.o`, linkovanie do `app`, target `clean`, premenné `CC` a `CFLAGS`.

```makefile
# ===== TVOJE RIEŠENIE – Makefile =====



# ========================================
```

**c)** Čo robí automatická premenná `$@` a `$^`?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

> **Mohlo by sa hodiť**
>
> *BST vizuálne:*
> ```
>         50
>        /  \
>       30   70
>      / \  / \
>     20 40 60 80
> Inorder: 20→30→40→50→60→70→80
> ```
>
> *BFS — Queue postup:*
> ```
> Queue=[A] → spracuj A, pridaj B,C → Queue=[B,C] → spracuj B...
> ```
>
> *Merge Sort:*
> ```
> [38,27,43,3] → [38,27]+[43,3] → [27,38]+[3,43] → [3,27,38,43]
> ```
>
> *Makefile kostra:*
> ```makefile
> CC=g++
> CFLAGS=-Wall -std=c++17
> app: main.o LinkedList.o
> 	$(CC) $(CFLAGS) -o $@ $^
> %.o: %.cpp
> 	$(CC) $(CFLAGS) -c $<
> clean:
> 	rm -f *.o app
> ```

---

## OKRUH 5 – Git, GitHub, GitLab a CI/CD
*(Repozitáre: `SPSITKNM` → `GitHub_vs_GitLab.md`, `SXG` → `git_github_gitlab.md`)*

---

### 5.1 – Feature branch workflow: presné príkazy

Pre každý krok nasledujúceho scenára napíš presný git príkaz (alebo sériu príkazov):

```bash
# Krok 1 – inicializuj lokálny repozitár a pripoj k https://gitlab.com/skola/projekt.git


# Krok 2 – vytvor vetvu feature/user-auth a prepni sa na ňu


# Krok 3 – pridaj všetky zmeny do staging area, commit "feat: add JWT authentication"


# Krok 4 – odošli vetvu na vzdialený server (prvý push)


# Krok 5 – integruj zmeny z main do feature vetvy BEZ merge commitu


# Krok 6 – nastane konflikt v auth.cpp; popiš postup riešenia krok po kroku:
# (a)
# (b)
# (c)


# Krok 7 – zmaž lokálnu aj vzdialenú vetvu feature/user-auth


```

---

### 5.2 – Návrh CI/CD pipeline

Napíš funkčný `.gitlab-ci.yml` pre C++ projekt: fázy `build` (make), `test` (./run_tests.sh), `deploy` (len na `main`); image `gcc:latest`; artefakty z build do test.

```yaml
# ===== TVOJE RIEŠENIE – .gitlab-ci.yml =====



# ============================================
```

---

### 5.3 – Identifikácia anti-patterns

V nasledujúcom git workflow sú **3 závažné chyby**. Identifikuj každú, vysvetli prečo je problematická a ako ju opraviť:

```bash
git checkout main
git add .
git commit -m "fix"
git push origin main
# Kolega dostane konflikt:
git reset --hard origin/main
git push --force origin main
```

> **Odpoveď:**
>
> Chyba 1: *(Sem vpíš — čo je zlé a prečo.)*
>
> Chyba 2: *(Sem vpíš.)*
>
> Chyba 3: *(Sem vpíš.)*

---

### 5.4 – Analytické otázky

**a)** `git merge` vs `git rebase` — vysvetli rozdiel vo výslednej histórii. Uveď konkrétnu situáciu pre každý príkaz, kde je optimálny.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Čo je **CI/CD** a aký **business benefit** prináša oproti manuálnemu nasadzovaniu?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**c)** V akej situácii je `git fetch` + manuálny `git merge` bezpečnejšia voľba ako `git pull`?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

> **Mohlo by sa hodiť**
>
> *Git flow schéma:*
> ```
> main    ──●──────────────────────────●── (merge commit)
>            \                        /
> feature     ●──●──●──●──●──●──●──●
> ```
>
> *`.gitlab-ci.yml` kostra:*
> ```yaml
> stages: [build, test, deploy]
> build-job:
>   stage: build
>   image: gcc:latest
>   script: [make]
>   artifacts:
>     paths: [app]
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

Napíš kompletný program v **jazyku C**: vytvor pipe, zavolaj `fork()`; rodič zapíše `"Správa od rodiča PID=<PID>"` a zatvorí write-end; potomok prečíta, vypíše a zatvorí read-end; rodič počká cez `wait()` a vypíše návratový kód. Ošetri zlyhanie `fork()` a zbytočne otvorené fd.

```c
// ===== TVOJE RIEŠENIE – fork() + pipe() =====



// =============================================
```

> ** Odpoveď – zombie proces:**
>
> Čo je zombie proces, ako vzniká a akú rolu hrá `wait()`?
> *(Sem vpíš.)*

---

### 6.2 – Stavový diagram procesu

Nakresli stavový diagram so stavmi `NEW → READY → RUNNING → WAITING → TERMINATED`. Pre každý prechod uveď konkrétnu udalosť.

```
===== DIAGRAM – stavový diagram procesu =====



=============================================
```

> ** Odpoveď – PCB a context switch:**
>
> Čo obsahuje PCB (min. 5 položiek) a prečo ho OS potrebuje pri context switch?
> *(Sem vpíš.)*

---

### 6.3 – Linux príkazy: scenáre

Doplň príkaz pre každý scenár:

| Scenár | Príkaz |
|---|---|
| Zobraz bežiace procesy: PID, USER, CPU%, MEM%, CMD | |
| Nájdi všetky riadky s `ERROR` v `system.log` a ulož ich do `chyby.txt` | |
| Sleduj koniec `system.log` v reálnom čase | |
| Rekurzívne nájdi všetky súbory `.conf` v `/etc` | |
| Nastav práva `deploy.sh` na `rwxr-xr--` (octal) | |
| Zobraz aktívne sieťové rozhrania a IP adresy | |
| Ukonči proces s názvom `nginx` bez znalosti PID | |
| Zoraď riadky `data.csv` podľa druhého stĺpca (oddelovač `,`) | |
| Skopíruj adresár `projekt/` na `192.168.1.10:/home/admin/` | |
| Zobraz veľkosť adresárov v `/var/log` od najväčšieho | |

---

### 6.4 – Analytické otázky

**a)** Porovnaj **pipe** a **zdieľanú pamäť (shared memory)** ako IPC mechanizmy — výhody, nevýhody, typické use-cases.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Čo sú file descriptory 0, 1, 2? Čo sa stane ak program uzavrie `stdout` (`close(1)`) a otvorí nový súbor?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**c)** Prečo `fork()` kopíruje adresný priestor rodiča a aký mechanizmus OS používa na optimalizáciu tejto operácie?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

> **Mohlo by sa hodiť**
>
> *Kostra fork() + pipe():*
> ```c
> int pipefd[2];   // [0]=read, [1]=write
> pipe(pipefd);
> pid_t pid = fork();
> if (pid == 0) { close(pipefd[1]); /* čítaj */ }
> else          { close(pipefd[0]); /* píš */ wait(NULL); }
> ```
>
> *File descriptory:* `0=stdin` `1=stdout` `2=stderr`
>
> *Octal práva:* `rwxr-xr-- = 754` (r=4, w=2, x=1)

---

## OKRUH 7 – Virtualizácia: VirtualBox, KVM a Docker
*(Repozitár: `SXG` → `VirtualBox Guide.md`, `kvm.md`, `docker.md`)*

---

### 7.1 – Dockerfile pre produkčnú aplikáciu

Napíš `Dockerfile` pre Python Flask API: base image `python:3.11-slim`, workdir `/app`, skopíruj `requirements.txt` a inštaluj závislosti **pred** kódom, skopíruj kód, nastav `FLASK_ENV=production`, exponuj port `5000`, spusti `flask run --host=0.0.0.0`.

```dockerfile
# ===== TVOJE RIEŠENIE – Dockerfile =====



# ========================================
```

> ** Odpoveď – layer cache:**
>
> Prečo kopírovať `requirements.txt` pred zvyšným kódom?
> *(Sem vpíš.)*

---

### 7.2 – Docker Compose: viacservisná aplikácia

Napíš `docker-compose.yml`: služba `web` (Flask, port 5000→8080), služba `db` (postgres:15, premenné prostredia), spoločná sieť `backend-net`, named volume `pgdata`, `web` čaká na `db`.

```yaml
# ===== TVOJE RIEŠENIE – docker-compose.yml =====



# ================================================
```

---

### 7.3 – VBoxManage automatizácia

Napíš sekvenciu `VBoxManage` príkazov:

```bash
# 1 – vytvor VM TestVM (Linux, Ubuntu_64)

# 2 – nastav 2048 MB RAM a 2 CPU

# 3 – vytvor dynamicky alokovaný VDI disk 20 GB a pripoj ho

# 4 – nastav sieťový adaptér na bridged

# 5 – spusti VM v headless režime

```

---

### 7.4 – KVM konfigurácia

```bash
# 1 – over podporu HW virtualizácie (VT-x / AMD-V)

# 2 – skontroluj načítanie KVM kernel modulov

# 3 – over vhodnosť systému pre QEMU/KVM hosting

# 4 – nastav optimalizačný profil virtual-host

```

---

### 7.5 – Analytické otázky

**a)** Porovnaj **kontajner (Docker)** a **virtuálny stroj (VM)** z hľadiska: izolácie, výkonnostného overheadu, vhodného use-case.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Vysvetli Docker **layer caching** — ako Docker rozhoduje, ktoré vrstvy rebuildiť? Prečo `COPY . .` na začiatku je anti-pattern?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**c)** Prečo sa KVM preferuje pred VirtualBoxom na produkčných serveroch? Uveď aspoň 2 technické dôvody.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**d)** Aké sú **4 sieťové režimy VirtualBoxu**? Pre každý uveď typický scenár použitia.

> **Odpoveď:**
>
> NAT: *(Sem vpíš.)*
>
> NAT Network: *(Sem vpíš.)*
>
> Bridged: *(Sem vpíš.)*
>
> Host-only: *(Sem vpíš.)*

---

> **Mohlo by sa hodiť**
>
> *Docker architektúra:*
> ```
> Docker CLI ──► Docker Daemon
>                  ├── Images (read-only vrstvy)
>                  ├── Containers (bežiace inštancie)
>                  └── Volumes (perzistentné úložisko)
> ```
>
> *Layer cache — logika:*
> ```
> COPY requirements.txt .  ← cache miss len pri zmene requirements.txt
> RUN pip install ...
> COPY . .                 ← cache miss pri každej zmene kódu
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

Máš trojvrstvovú aplikáciu: `frontend (React)` → `api (Python REST)` → `databaza (PostgreSQL)`. Navrhni komplexnú observability stratégiu — pre každú vrstvu uveď čo sledovať cez Traces, aké Metrics (min. 3 pre `api`) a aké Logs (s úrovňou INFO/WARN/ERROR). Každé rozhodnutie zdôvodni.

> **Odpoveď:**
>
> **Frontend:**
> - Traces: *(Sem vpíš.)*
> - Logs: *(Sem vpíš.)*
>
> **API:**
> - Traces: *(Sem vpíš.)*
> - Metrics (min. 3): *(Sem vpíš.)*
> - Logs: *(Sem vpíš.)*
>
> **Databáza:**
> - Traces: *(Sem vpíš.)*
> - Metrics: *(Sem vpíš.)*
> - Logs: *(Sem vpíš.)*

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

**a)** Kde nastáva bottleneck? Zdôvodni číslami.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Uveď **aspoň 3 hypotézy**, prečo `db.query_user` trvá 775ms.

> **Odpoveď:**
>
> 1. *(Sem vpíš.)*
>
> 2. *(Sem vpíš.)*
>
> 3. *(Sem vpíš.)*

**c)** Aké metriky by si monitoroval na DB vrstve na potvrdenie/vyvrátenie týchto hypotéz?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

### 8.3 – Analytické otázky

**a)** Kedy použiješ **auto-instrumentáciu** a kedy **manuálnu**? Porovnaj development effort vs. granularitu dát.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Prečo samotné Logs nestačia na diagnostiku výkonnostných problémov v distribuovanom systéme? Čo Traces pridávajú?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**c)** Vysvetli mechanizmus **context propagation** — ako trace prepája spany naprieč viacerými službami?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

> **Mohlo by sa hodiť**
>
> *Tri piliere — kedy ktorý:*
> ```
> Traces  → Kde je bottleneck? Prečo je požiadavka pomalá?
> Metrics → Aký je trend? Rastie počet chýb?
> Logs    → Čo presne sa stalo? Aká bola chybová správa?
> ```
>
> *Schéma context propagation:*
> ```
> request → [api span] ──traceparent header──► [db span]
> ```
>
> *Nástroje:* Prometheus, Grafana, Jaeger, Zipkin, Datadog, OTel Collector

---

## OKRUH 9 – AI-asistovaný vývoj (Claude Code)
*(Repozitár: `SPSITKNM` → `zadania_na_hodine.md`)*

---

### 9.1 – Základné koncepty

**a)** Vysvetli rozdiel medzi **CLI** a **GUI** rozhraním AI asistenta. Uveď aspoň 2 výhody CLI prístupu pri práci s kódom.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Čo je **context window**? Čo je **compaction** a aká je jeho nevýhoda?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**c)** Prečo sa lokálne nastavenia (`settings.local.json`) nezahŕňajú do git repozitára?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

### 9.2 – Permissions a bezpečnosť

**a)** Aké akcie v Claude Code stále vyžadujú manuálne potvrdenie? Uveď aspoň 2 príklady.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Čo je **sandbox** v kontexte Claude Code? S čím ho možno prirovnať?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**c)** Čo môže AI urobiť v **dangerous** režime a prečo je to rizikové?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

### 9.3 – Plan Mode a Context Engineering

**a)** Na aké typy úloh je vhodné použiť **Plan Mode**? Uveď aspoň 3 scenáre.

> **Odpoveď:**
>
> 1. *(Sem vpíš.)*
>
> 2. *(Sem vpíš.)*
>
> 3. *(Sem vpíš.)*

**b)** Čo je `CLAUDE.md` a prečo je výhodné zahrnúť referenciu na `SPEC.md` namiesto kopírovania obsahu?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**c)** Vysvetli 2 princípy **Context Engineering**: čo znamená „poskytni relevantnú informáciu" a prečo je stručnosť dôležitá?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

### 9.4 – Pokročilé funkcie

**a)** Čo sú **MCP servery** a akú funkcionalitu umožňujú AI asistentovi?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**b)** Čo sú **Hooks**? Uveď príklad udalosti, ktorá hook spúšťa, a príklad akcie, ktorú vykoná.

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**c)** Vysvetli **Feedback Loop**. Prečo je dôležité používať nástroje ako Playwright na verifikáciu? Aká je hlavná nevýhoda?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

**d)** Čo je **Multi-Agent systém (Ralph Loop)**? Pre aký typ workloadu je najvhodnejší a čo sa znižuje?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

### 9.5 – Analytická otázka

**a)** Aké sú **3 najväčšie výhody** integrácie AI asistenta do vývojového procesu?

> **Odpoveď:**
>
> 1. *(Sem vpíš.)*  2. *(Sem vpíš.)*  3. *(Sem vpíš.)*

**b)** Aké sú **3 najväčšie riziká** — technické, bezpečnostné alebo organizačné?

> **Odpoveď:**
>
> 1. *(Sem vpíš.)*  2. *(Sem vpíš.)*  3. *(Sem vpíš.)*

**c)** Prečo je **Git** obzvlášť dôležitý pri práci s AI asistentom, ktorý môže robiť rozsiahle zmeny?

> **Odpoveď:**
>
> *(Sem vpíš svoju odpoveď.)*

---

> **Mohlo by sa hodiť**
>
> *Kľúčové pojmy:*
> ```
> CLAUDE.md  → projektové inštrukcie (v kontexte každej konverzácie)
> SPEC.md    → špecifikácia projektu (referovaná z CLAUDE.md)
> Plan Mode  → AI navrhuje, človek schvaľuje pred vykonaním zmien
> Hooks      → shell príkazy spúšťané automaticky pri udalostiach
> MCP        → rozšírenia umožňujúce AI prístup k externým systémom
> ```
>
> *Git + AI:* AI môže zmeniť 10 súborov naraz. `git commit` pred AI akciou = záchranná sieť.

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
