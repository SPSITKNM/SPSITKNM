# Zadanie projektov do predmetu PRO 2. polrok 2025/2026

---

## Obsah

1. [k-tá minimálna kostra grafu](#1-k-tá-minimálna-kostra-grafu)
2. [Minimálna cena prepravy tovaru](#2-minimálna-cena-prepravy-tovaru)
3. [Násobenie postupnosti matíc](#3-násobenie-postupnosti-matíc)
4. [Cesty jaskynným systémom](#4-cesty-jaskynným-systémom)
5. [Bipartitný graf](#5-bipartitný-graf)
6. [Optimalizácia rozvrhu úloh](#6-optimalizácia-rozvrhu-úloh)

---

## Deadline

> **Vypracované riešenie projektu je nutné odovzdať do:**
> - **4.AT, 4.BI, 4.CI – 4.4.2026 23:59**

---

## Všeobecné pokyny

- Každý študent si vyberie jeden projekt zo zoznamu nižšie
- Riešenie musí byť samostatná práca
- Kód musí byť čitateľný a dobre komentovaný
- Program musí správne spracovať všetky testovacie vstupy

---

## 1. k-tá minimálna kostra grafu

### Problém

V tomto zadaní budete hľadať špecifické kostry neorientovaného váženého grafu *G*. Nájdenie minimálnej kostry *K* grafu *G* je dobre známy problém, ktorého riešenie nie je nijako komplikované. Vašou úlohou ale bude nájsť postupnosť minimálnych kostier grafu *K₀ = K, K₁, K₂, ..., Kₘ*, kde *K₁* je druhá minimálna kostra grafu, *K₂* je tretia minimálna kostra grafu a tak ďalej, až *Kₘ* je maximálna kostra grafu.

Označme *w(Kᵢ)* súčet váh všetkých hrán v kostre *Kᵢ*, potom pre hodnoty *w(K₀), ..., w(Kₘ)* musí platiť:

```
w(K₀) ≤ w(K₁) ≤ ... ≤ w(Kₘ)
```

### Ukážkový príklad

Ukážkový graf *G* a jeho minimálna kostra *K₀* je zobrazená na obrázku 1, súčet váh hrán minimálnej kostry je *w(K₀) = 16*.

**Graf G (9 vrcholov: 0-8):**
```
Vrcholy: 0, 1, 2, 3, 4, 5, 6, 7, 8
Hrany s váhami:
  0-1: 2,  0-3: 1,  0-6: 5
  1-2: 5,  1-3: 5,  1-4: 1
  2-5: 5,  2-8: 1
  3-4: 5,  3-6: 1
  4-5: 5,  4-7: 4,  4-8: 4
  5-8: 5
  6-7: 4
  7-8: 3
```

Druhá minimálna kostra má dve varianty:
- **Prvá varianta:** hrana (2,4) s váhou 3 nahradená hranou (0,2) s váhou 4. Výsledok: *w(K₁) = w(K₀) - 3 + 4 = 17*
- **Druhá varianta:** hrana (6,8) s váhou 3 nahradená hranou (4,8) s váhou 4. Výsledok: *w(K₁) = 17*

Tretia minimálna kostra je už len jedna, vznikne nahradením zostávajúcej hrany (6,8) resp. (2,4) s váhou 3 hranou (4,8) resp. (0,2). Výsledný súčet váh je *w(K₂) = w(K₁) - 3 + 4 = 18*.

Maximálna kostra grafu je zobrazená na obrázku 4, kde *w(Kₘ) = 30*. Maximálna kostra existuje v niekoľkých variantách, ktoré sa líšia napojením vrcholov 3 a 4 k zostávajúcej časti kostry.

### Formát vstupu

Textový súbor obsahujúci maticu susednosti grafu:
- **Prvý riadok:** číslo *n* (počet vrcholov)
- **Ďalších *n* riadkov:** *n*-tica celých čísel predstavujúcich váhy hrán
- Ak je váha hrany rovná 0, hrana neexistuje

**Príklad vstupu (graf z obrázku 1):**
```
9
0 2 0 1 0 0 5 0 0
2 0 5 5 1 0 0 0 0
0 5 0 0 0 5 0 0 1
1 5 0 0 5 0 1 0 0
0 1 0 5 0 5 0 4 4
0 0 5 0 5 0 0 0 5
5 0 0 1 0 0 0 4 0
0 0 0 0 4 0 4 0 3
0 0 1 0 4 5 0 3 0
```

### Formát výstupu

Na štandardný výstup vypíšte postupne všetky kostry od minimálnej po maximálnu. Pre každú kostru vypíšte:
1. Poradové číslo kostry (K₀, K₁, ...)
2. Súčet váh hrán
3. Zoznam hrán kostry vo formáte `(u,v):váha`

### Testovacie prípady

#### Test 1: Malý graf (4 vrcholy)
**Vstup:**
```
4
0 1 4 3
1 0 2 0
4 2 0 5
3 0 5 0
```

**Očakávaný výstup:**
```
K0: w=6, hrany: (0,1):1, (1,2):2, (0,3):3
K1: w=8, hrany: (0,1):1, (0,2):4, (0,3):3
K2: w=9, hrany: (0,1):1, (1,2):2, (2,3):5
K3: w=10, hrany: (0,1):1, (0,2):4, (2,3):5
K4: w=12, hrany: (0,2):4, (0,3):3, (2,3):5
```

#### Test 2: Trojuholník (3 vrcholy)
**Vstup:**
```
3
0 2 3
2 0 4
3 4 0
```

**Očakávaný výstup:**
```
K0: w=5, hrany: (0,1):2, (0,2):3
K1: w=6, hrany: (0,1):2, (1,2):4
K2: w=7, hrany: (0,2):3, (1,2):4
```

#### Test 3: Lineárny graf (5 vrcholov)
**Vstup:**
```
5
0 1 0 0 0
1 0 2 0 0
0 2 0 3 0
0 0 3 0 4
0 0 0 4 0
```

**Očakávaný výstup:**
```
K0: w=10, hrany: (0,1):1, (1,2):2, (2,3):3, (3,4):4
```
*(Existuje len jedna kostra)*

---

## 2. Minimálna cena prepravy tovaru

### Problém

V tomto zadaní budete hľadať najlacnejšiu cestu pre prepravu tovaru v logistickej sieti. Máte k dispozícii graf miest spojených cestami s rôznymi cenami prepravy. Vašou úlohou je nájsť najlacnejšiu trasu z mesta *A* do mesta *B*.

**Zľava:** Pri preprave tovaru máte nárok na **50% zľavu na najdrahšiu hranu** v trase. To znamená, že ak nájdete najlacnejšiu trasu, cena so zľavou sa vypočíta tak, že najdrahšia hrana v tejto trase bude stáť len polovicu svojej pôvodnej ceny.

> **Pozor:** Optimálna trasa bez zľavy nemusí byť rovnaká ako optimálna trasa so zľavou! Niekedy sa oplatí ísť dlhšou trasou s jednou veľmi drahou hranou, pretože po aplikovaní zľavy bude celková cena nižšia.

### Formát vstupu

Textový súbor obsahujúci:
- **Prvý riadok:** číslo *n* (počet miest)
- **Ďalších *n* riadkov:** matica susednosti *n × n*

Hodnoty matice:
- **wᵢ,ⱼ = 0** pre *i = j* (cena z mesta do seba = 0)
- **wᵢ,ⱼ = -1** ak hrana neexistuje
- **wᵢ,ⱼ > 0** cena prepravy z mesta *i* do mesta *j*

- **Posledné dva riadky:** čísla *A* a *B* (počiatočné a koncové mesto)

**Príklad vstupu:**
```
4
0 -1 15 77
-1 0 8 38
15 8 0 -1
77 38 -1 0
0
3
```

### Formát výstupu

Na štandardný výstup vypíšte:
1. Cenu prepravy **bez zľavy** a trasu
2. Cenu prepravy **so zľavou** (50% na najdrahšiu hranu) a trasu
3. Ak trasa neexistuje, vypíšte `-1`

### Testovacie prípady

#### Test 1: Základný prípad
**Vstup:**
```
4
0 -1 15 77
-1 0 8 38
15 8 0 -1
77 38 -1 0
0
3
```

**Očakávaný výstup:**
```
Bez zľavy: 61, trasa: 0 -> 2 -> 1 -> 3
So zľavou: 42, trasa: 0 -> 2 -> 1 -> 3
Vysvetlenie: 15 + 8 + 38 = 61, najdrahšia hrana je 38, so zľavou: 15 + 8 + 19 = 42
```

#### Test 2: Priama vs. nepriama cesta
**Vstup:**
```
3
0 100 10
100 0 10
10 10 0
0
1
```

**Očakávaný výstup:**
```
Bez zľavy: 20, trasa: 0 -> 2 -> 1
So zľavou: 15, trasa: 0 -> 2 -> 1
Vysvetlenie: Priama cesta 0->1 stojí 100 (so zľavou 50), nepriama 0->2->1 stojí 20 (so zľavou 15)
```

#### Test 3: Neexistujúca cesta
**Vstup:**
```
4
0 5 -1 -1
5 0 -1 -1
-1 -1 0 3
-1 -1 3 0
0
3
```

**Očakávaný výstup:**
```
-1
```

#### Test 4: Zľava mení optimálnu trasu
**Vstup:**
```
4
0 10 50 -1
10 0 -1 10
50 -1 0 5
-1 10 5 0
0
3
```

**Očakávaný výstup:**
```
Bez zľavy: 25, trasa: 0 -> 1 -> 3 -> 2 -> 3 - NEPLATNÉ (trasa musí končiť v 3)
Bez zľavy: 20, trasa: 0 -> 1 -> 3
So zľavou: 15, trasa: 0 -> 1 -> 3
```

#### Test 5: Väčší graf
**Vstup:**
```
5
0 4 2 -1 -1
4 0 1 5 -1
2 1 0 8 10
-1 5 8 0 2
-1 -1 10 2 0
0
4
```

**Očakávaný výstup:**
```
Bez zľavy: 12, trasa: 0 -> 2 -> 1 -> 3 -> 4
So zľavou: 9.5, trasa: 0 -> 2 -> 1 -> 3 -> 4
Vysvetlenie: 2+1+5+2=10, so zľavou na hranu 5: 2+1+2.5+2=7.5... PREPOČÍTAŤ
```

---

## 3. Násobenie postupnosti matíc

### Problém

V tomto zadaní máte zadanú postupnosť *n + 1* prirodzených čísel *D = d₀, d₁, ..., dₙ*, kde všetky čísla *dᵢ > 0*. Dvojice čísel z postupnosti *D* predstavujú rozmery matíc *A₀, A₁, ..., Aₙ₋₁* tak, že matica *Aᵢ* má rozmery *dᵢ × dᵢ₊₁*.

Chceme vypočítať súčin všetkých matíc:

```
M = A₀ · A₁ · A₂ · ... · Aₙ₋₁
```

Keďže násobenie matíc je asociatívna operácia, môžeme do súčinu vložiť zátvorky a násobiť matice v rôznom poradí. Rôzne uzátvorkovania vedú k rôznemu počtu operácií násobenia.

**Vašou úlohou je implementovať algoritmus, ktorý nájde optimálne poradie násobenia matíc** - také, pri ktorom sa vykoná najmenší počet operácií násobenia prvkov matíc.

### Vzorec pre počet násobení

Pri násobení matice *A* rozmerov *p × q* s maticou *B* rozmerov *q × r* je počet násobení prvkov: **p × q × r**

### Príklad

Pre *n = 4* a postupnosť *D = 7, 5, 3, 6, 5*:

| Matica | Rozmery |
|--------|---------|
| A₀     | 7 × 5   |
| A₁     | 5 × 3   |
| A₂     | 3 × 6   |
| A₃     | 6 × 5   |

**Porovnanie uzátvorkovaní:**

| Uzátvorkovanie | Počet násobení |
|----------------|----------------|
| ((A₀ · A₁) · A₂) · A₃ | 441 |
| **(A₀ · A₁) · (A₂ · A₃)** | **300** (optimum) |
| (A₀ · (A₁ · A₂)) · A₃ | 510 |
| A₀ · ((A₁ · A₂) · A₃) | 415 |
| A₀ · (A₁ · (A₂ · A₃)) | 340 |

### Formát vstupu

Textový súbor, kde každý riadok obsahuje jednu postupnosť čísel *D* oddelených medzerami.

### Formát výstupu

Pre každý riadok vstupu vypíšte:
1. Optimálne uzátvorkovanie
2. Minimálny počet násobení

### Testovacie prípady

#### Test 1: Základný príklad
**Vstup:**
```
7 5 3 6 5
```

**Očakávaný výstup:**
```
(A0 * A1) * (A2 * A3) = 300
```

#### Test 2: Dve matice
**Vstup:**
```
7 5 3
```

**Očakávaný výstup:**
```
(A0 * A1) = 105
```

#### Test 3: Jedna matica (žiadne násobenie)
**Vstup:**
```
7 5
```

**Očakávaný výstup:**
```
A0 = 0
```

#### Test 4: Viacero riadkov
**Vstup:**
```
40 20 30 10 30
2 3 5 8 13 21 34
10 20 30
```

**Očakávaný výstup:**
```
((A0 * A1) * A2) * A3 = 26000
... (optimálne uzátvorkovanie pre druhý riadok)
(A0 * A1) = 6000
```

#### Test 5: Rovnaké rozmery
**Vstup:**
```
10 10 10 10 10
```

**Očakávaný výstup:**
```
((A0 * A1) * A2) * A3 = 4000
alebo
(A0 * A1) * (A2 * A3) = 4000
(Všetky uzátvorkovania majú rovnaký počet násobení)
```

#### Test 6: Veľký rozdiel v rozmeroch
**Vstup:**
```
1 100 1 100 1
```

**Očakávaný výstup:**
```
(A0 * (A1 * A2)) * A3 = 300
```

---

## 4. Cesty jaskynným systémom

### Problém

V tomto zadaní budete hľadať cesty v jaskynnom labyrinte. Labyrint sa skladá z jaskýň spojených chodbami. Jaskyne môžu byť dvoch typov:
- **Veľké jaskyne** - označené VEĽKÝMI písmenami (napr. A, B, C)
- **Malé jaskyne** - označené malými písmenami (napr. a, b, c, start, end)

Vašou úlohou je nájsť všetky možné cesty daným labyrintom, ktoré:

1. **Začínajú** vždy v jaskyni `start`
2. **Končia** vždy v jaskyni `end`
3. **Malé jaskyne** navštívia **najviac jedenkrát**
4. **Veľké jaskyne** môžu navštíviť **ľubovoľne veľakrát**

**Na štandardný výstup vypíšte počet nájdených ciest.**

### Formát vstupu

Súbor, kde každý riadok obsahuje dvojicu názvov jaskýň spojených pomlčkou: `jaskyna1-jaskyna2`

### Formát výstupu

Jedno číslo - počet nájdených ciest. (Voliteľne môžete vypísať aj samotné cesty.)

### Testovacie prípady

#### Test 1: Základný príklad
**Vstup:**
```
start-A
start-b
A-c
A-b
b-d
A-end
b-end
```

**Očakávaný výstup:**
```
10
```

**Všetky cesty:**
```
start,A,b,A,c,A,end
start,A,b,A,end
start,A,b,end
start,A,c,A,b,A,end
start,A,c,A,b,end
start,A,c,A,end
start,A,end
start,b,A,c,A,end
start,b,A,end
start,b,end
```

#### Test 2: Jednoduchý príklad
**Vstup:**
```
start-A
A-end
```

**Očakávaný výstup:**
```
1
```
*(Jediná cesta: start -> A -> end)*

#### Test 3: Len malé jaskyne
**Vstup:**
```
start-a
a-b
b-end
a-end
```

**Očakávaný výstup:**
```
2
```
*(Cesty: start->a->b->end, start->a->end)*

#### Test 4: Väčší systém
**Vstup:**
```
start-A
start-B
A-c
A-B
B-d
B-end
A-end
c-B
```

**Očakávaný výstup:**
```
10
```

#### Test 5: Veľká jaskyňa ako hub
**Vstup:**
```
start-HUB
HUB-a
HUB-b
HUB-c
a-end
b-end
c-end
```

**Očakávaný výstup:**
```
3
```
*(Cesty: start->HUB->a->end, start->HUB->b->end, start->HUB->c->end)*

#### Test 6: Komplexný príklad s cyklami
**Vstup:**
```
start-A
A-B
B-C
C-A
A-end
B-end
C-end
start-x
x-A
```

**Očakávaný výstup:**
```
14
```

---

## 5. Bipartitný graf

### Problém

V tomto zadaní máte implementovať metódu `IsBipartite`, ktorá pre daný graf *G* vráti:
- **true** - ak je graf *G* bipartitný
- **false** - ak graf *G* nie je bipartitný

### Čo je bipartitný graf?

Graf je **bipartitný**, ak je možné jeho vrcholy rozdeliť do dvoch disjunktných množín *U* a *V* tak, že každá hrana grafu spája vrchol z *U* s vrcholom z *V*. Inými slovami, žiadna hrana nespája dva vrcholy z tej istej množiny.

**Ekvivalentná definícia:** Graf je bipartitný práve vtedy, keď neobsahuje cyklus nepárnej dĺžky.

**Tip:** Graf je bipartitný, ak ho je možné ofarbiť dvomi farbami tak, že žiadne dva susedné vrcholy nemajú rovnakú farbu.

> **Odporúčanie:** Prejdite si článok na Wikipédii v angličtine: https://en.wikipedia.org/wiki/Bipartite_graph

### Formát vstupu

- **Prvý riadok:** číslo *n* (počet vrcholov)
- **Ďalších *n* riadkov:** *n*-tica číslic 0 a 1 (matica susednosti)
  - `1` = hrana existuje
  - `0` = hrana neexistuje

### Formát výstupu

Jedno slovo: `true` alebo `false`

### Testovacie prípady

#### Test 1: Bipartitný graf (4 vrcholy - štvorec)
**Vstup:**
```
4
0101
1010
0101
1010
```

**Očakávaný výstup:**
```
true
```
*(Rozdelenie: U={0,2}, V={1,3})*

#### Test 2: Nebipartitný graf (trojuholník)
**Vstup:**
```
3
011
101
110
```

**Očakávaný výstup:**
```
false
```
*(Trojuholník obsahuje cyklus dĺžky 3 - nepárny)*

#### Test 3: Bipartitný graf (9 vrcholov)
**Vstup:**
```
9
000001000
001010010
010000000
000001000
010000000
100100000
000000001
010000000
000000100
```

**Očakávaný výstup:**
```
true
```

#### Test 4: Izolované vrcholy
**Vstup:**
```
4
0000
0000
0000
0000
```

**Očakávaný výstup:**
```
true
```
*(Graf bez hrán je vždy bipartitný)*

#### Test 5: Kompletný graf K4
**Vstup:**
```
4
0111
1011
1101
1110
```

**Očakávaný výstup:**
```
false
```
*(Kompletný graf Kn pre n>2 nie je bipartitný)*

#### Test 6: Hviezda (bipartitný)
**Vstup:**
```
5
01111
10000
10000
10000
10000
```

**Očakávaný výstup:**
```
true
```
*(Hviezda je vždy bipartitná: U={0}, V={1,2,3,4})*

#### Test 7: Pentagon (5-cyklus)
**Vstup:**
```
5
01001
10100
01010
00101
10010
```

**Očakávaný výstup:**
```
false
```
*(Cyklus dĺžky 5 je nepárny)*

#### Test 8: Hexagon (6-cyklus)
**Vstup:**
```
6
010001
101000
010100
001010
000101
100010
```

**Očakávaný výstup:**
```
true
```
*(Cyklus dĺžky 6 je párny)*

---

## 6. Optimalizácia rozvrhu úloh

### Problém

V tomto zadaní budete implementovať algoritmus pre optimálne rozvrhovanie úloh. Máte zadaných *n* úloh, kde každá úloha *i* je charakterizovaná tromi parametrami:
- **sᵢ** - čas začiatku
- **eᵢ** - čas konca
- **pᵢ** - zisk (profit), ktorý získame pri dokončení úlohy

**Dve úlohy sa prekrývajú**, ak existuje časový okamih, kedy sú obe úlohy aktívne. Formálne: úlohy *i* a *j* sa prekrývajú, ak platí *sᵢ < eⱼ* a *sⱼ < eᵢ*.

**Vašou úlohou je nájsť takú podmnožinu neprekrývajúcich sa úloh, ktorá maximalizuje celkový zisk.**

### Formát vstupu

- **Prvý riadok:** číslo *n* (počet úloh)
- **Ďalších *n* riadkov:** tri celé čísla oddelené medzerou: *sᵢ eᵢ pᵢ*

### Formát výstupu

- Maximálny možný zisk
- (Voliteľne) zoznam vybraných úloh

### Testovacie prípady

#### Test 1: Základný príklad
**Vstup:**
```
4
1 4 5
2 4 6
3 5 5
4 6 7
```

**Očakávaný výstup:**
```
13
Vybrané úlohy: 2, 4
```
*(Úlohy 2 a 4 sa neprekrývajú: 6 + 7 = 13)*

#### Test 2: Všetky sa prekrývajú
**Vstup:**
```
3
1 10 5
2 8 10
3 6 3
```

**Očakávaný výstup:**
```
10
Vybraná úloha: 2
```

#### Test 3: Žiadne sa neprekrývajú
**Vstup:**
```
3
1 2 5
3 4 10
5 6 3
```

**Očakávaný výstup:**
```
18
Vybrané úlohy: 1, 2, 3
```

#### Test 4: Jedna úloha
**Vstup:**
```
1
5 10 100
```

**Očakávaný výstup:**
```
100
```

#### Test 5: Väčší príklad
**Vstup:**
```
6
1 3 5
2 5 6
4 6 5
6 7 4
5 8 11
7 9 2
```

**Očakávaný výstup:**
```
17
Vybrané úlohy: 1, 5 (alebo iná optimálna kombinácia)
```

#### Test 6: Sekvenčné úlohy
**Vstup:**
```
5
1 2 1
2 3 2
3 4 3
4 5 4
5 6 5
```

**Očakávaný výstup:**
```
15
Vybrané úlohy: 1, 2, 3, 4, 5
```
*(Všetky úlohy na seba nadväzujú)*

#### Test 7: Veľa malých vs. jedna veľká
**Vstup:**
```
4
1 2 3
2 3 3
3 4 3
1 4 8
```

**Očakávaný výstup:**
```
9
Vybrané úlohy: 1, 2, 3
```
*(Tri malé úlohy: 3+3+3=9 > jedna veľká: 8)*

#### Test 8: Zložitejší prípad
**Vstup:**
```
8
1 4 3
3 5 4
0 6 2
5 7 4
3 8 5
5 9 6
6 10 3
8 11 4
```

**Očakávaný výstup:**
```
13
```

---

## Hodnotenie

Projekty budú hodnotené podľa:
- **Správnosť riešenia** na testovacích vstupoch
- **Efektivita algoritmu** (časová a pamäťová zložitosť)
- **Kvalita kódu** (čitateľnosť, komentáre, štruktúra)
- **Dodržanie termínu** odovzdania

---

*Zadanie projektov PRO 2. polrok 2025/2026*

**Autor:** Tomáš Mucha
