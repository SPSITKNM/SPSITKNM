# Praktické úlohy na triediace algoritmy

Súbor praktických úloh zameraných na rôzne triediace algoritmy. Každá úloha obsahuje zadanie, návrh riešenia a analýzu algoritmickej zložitosti.

---

## 1. Bubble Sort - Organizácia knižnice

### Zadanie

V školskej knižnici máte 8 kníh, ktoré sú rozložené v nesprávnom poradí podľa ISBN čísla. Knihy máte v tomto poradí:

```
[423, 156, 789, 234, 567, 123, 890, 345]
```

### Úloha

1. Použite **Bubble Sort** na zoradenie kníh vzostupne podľa ISBN
2. Vypíšte stav poľa po každom kompletnom prechode (každom vonkajšom cykle)
3. Spočítajte, koľko porovnaní a koľko výmen ste vykonali

### Analýza zložitosti

- Odhadnite (vypočítajte) **časovú zložitosť** v najhoršom, priemernom a najlepšom prípade
- Slovne zdôvodnite, prečo má algoritmus túto zložitosť

---

## 2. Selection Sort - Výber najlepších študentov

### Zadanie

Máte zoznam študentov s ich priemernými známkami:

```
Študent: [Anna: 2.5, Bob: 1.8, Cyril: 3.2, Dana: 1.5, Eva: 2.1, Filip: 1.9]
```

### Úloha

1. Použite **Selection Sort** na zoradenie študentov podľa priemeru (od najlepšieho)
2. Pri každom kroku vysvetlite, prečo ste vybrali práve daného študenta
3. Nakresľte schému, ktorá ukazuje pozície minimu v každej iterácii

### Analýza zložitosti

- Odhadnite (vypočítajte) **časovú zložitosť** algoritmu
- Prečo má Selection Sort vždy rovnakú zložitosť bez ohľadu na vstup?
- Koľko výmen ste vykonali? Je to lepšie alebo horšie ako pri Bubble Sort?
- Kedy by ste preferovali Selection Sort pred Bubble Sort?

---

## 3. Insertion Sort - Zoraďovanie kariet

### Zadanie

Hráte karty a postupne vyberáte karty z balíčka. Karty máte v tomto poradí:

```
[7♠, 3♥, 9♦, 2♣, 8♠, 4♥, 6♦, 5♣]
```

### Úloha

1. Použite **Insertion Sort** - simulujte, ako by ste zoraďovali karty v ruke
2. Po vybraní každej novej karty popíšte, kam ju vložíte a prečo
3. Nakresľte grafickú reprezentáciu každého kroku

### Analýza zložitosti

- Odhadnite (vypočítajte) **časovú zložitosť** v najlepšom a najhoršom prípade
- V akom prípade bude Insertion Sort najrýchlejší? Uveďte príklad vstupu.
- V akom prípade bude najpomalší? Uveďte príklad vstupu.
- Prečo je Insertion Sort efektívny pre malé polia alebo takmer zoradené dáta?
- Zdôvodnite slovne, prečo je jeho najlepší prípad O(n) a najhorší O(n²)

---

## 4. Quick Sort - Rozdelenie študentov na skupiny

### Zadanie

Máte 12 študentov s rôznym vekom, ktorých potrebujete zoradiť:

```
[19, 22, 18, 21, 20, 23, 18, 19, 22, 20, 21, 19]
```

### Úloha

1. Použite **Quick Sort** s pivotom ako prostredným prvkom
2. Nakresľte strom rekurzívnych volaní
3. Pri každom delení ukážte, ako sa pole rozdelilo na menšie a väčšie hodnoty

### Analýza zložitosti

- Odhadnite (vypočítajte) **časovú zložitosť** v priemernom a najhoršom prípade
- Vypočítajte hĺbku rekurzie pre váš prípad
- Vysvetlite slovne, prečo je priemerná zložitosť O(n log n)
- Čo sa stane v najhoršom prípade? Aký vstup by to spôsobil?

---

## 5. Merge Sort - Spájanie výsledkov testov

### Zadanie

Dvaja učitelia opravovali testy nezávisle a každý má svoj zoradený zoznam bodov. Potrebujete ich spojiť do jedného zoradeného zoznamu:

```
Učiteľ A: [45, 67, 78, 89, 92]
Učiteľ B: [52, 68, 73, 85, 91, 95]
```

### Úloha

1. Najprv spojte tieto dva zoradené zoznamy pomocou merge operácie
2. Potom zoberťe nezoradené pole `[64, 34, 25, 12, 22, 11, 90, 88]` a zoraďte ho pomocou **Merge Sort**
3. Nakresľte kompletný strom delení a spájaní

### Analýza zložitosti

- Odhadnite (vypočítajte) **časovú zložitosť** algoritmu
- Prečo je časová zložitosť vždy O(n log n) bez ohľadu na vstup?
- Slovne zdôvodnite, ako ste došli k tomuto výsledku
- Porovnajte Merge Sort a Quick Sort - kedy použijete ktorý?

---

## 6. Heap Sort - Prioritný systém úloh

### Zadanie

Máte systém úloh s rôznou prioritou (čím vyššie číslo, tým dôležitejšia úloha):

```
Úlohy: [3, 8, 5, 1, 9, 2, 7, 4, 6]
```

### Úloha

1. Najprv vytvorte **max-heap** z daných priorít
2. Nakresľte heap ako binárny strom
3. Použite **Heap Sort** na zoradenie úloh zostupne (od najdôležitejšej)
4. Pri každom kroku ukážte, ako sa heap mení

### Analýza zložitosti

- Odhadnite (vypočítajte) **časovú zložitosť** vytvorenia heap-u (heapify)
- Odhadnite (vypočítajte) **časovú zložitosť** extrakcie prvkov z heap-u
- Aká je celková časová zložitosť Heap Sort?
- Slovne zdôvodnite svoj výpočet

---

## 7. Porovnávacia úloha - Experimentálne meranie

### Zadanie

Máte tri rôzne typy vstupných polí (každé veľkosti 10):

**a) Takmer zoradené:**
```
[1, 2, 3, 4, 5, 7, 6, 8, 9, 10]
```

**b) Úplne náhodné:**
```
[47, 12, 89, 3, 56, 23, 91, 8, 34, 67]
```

**c) Zoradené opačne:**
```
[10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
```

### Úloha

1. Zoraďte každé pole pomocou **troch rôznych algoritmov** (napríklad Bubble, Insertion, Quick Sort)
2. Pre každý algoritmus a každý typ vstupu spočítajte:
   - Počet porovnaní
   - Počet výmen/presunov
   - Počet krokov
3. Vytvorte tabuľku s výsledkami

### Analýza

- Odhadnite (vypočítajte) **časovú zložitosť** pre každý prípad
- Ktorý algoritmus bol najrýchlejší pre každý typ vstupu?
- Ktorý algoritmus mal najkonzistentnejšie výsledky?
- Zdôvodnite svoje pozorovania pomocou teoretickej zložitosti

---

## Bonusová úloha - Stabilita algoritmov

### Zadanie

Máte študentov s rovnakými známkami, ale rôznymi menami:

```
[(Anna, 2.0), (Bob, 1.5), (Cyril, 2.0), (Dana, 1.5), (Eva, 2.0)]
```

### Úloha

1. Zoraďte študentov pomocou **Bubble Sort**, **Merge Sort** a **Quick Sort**
2. Sledujte, či študenti s rovnakými známkami ostali v pôvodnom poradí

### Otázky

- Ktoré algoritmy sú stabilné (zachovávajú poradie rovnakých prvkov)?
- Prečo je stabilita dôležitá v praxi?
- Ako by ste upravili nestabilný algoritmus, aby bol stabilný?

---

## Návod na vypracovanie | zdroje 

**Úvod do algoritmizácie** : https://youtu.be/lN-TrkF8WHQ?si=tLIDFgyVPZnAqp5f
**Sorting algorithms** : https://youtu.be/bxXmgMqjGwM?si=gLsM7p7bVrW7yOp-
Skriptá : https://github.com/SPSITKNM/SPSITKNM

Držím palce pri riešení 

S pozdravom, 

Tomáš 🪰.
