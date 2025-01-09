Zadanie:

Implementujte Warshallov algoritmus na výpočet tranzitívneho uzáveru orientovaného acyklického grafu. Algoritmus by mal byť implementovaný ako funkcia, ktorá prijíma maticu susednosti grafu a vracia maticu tranzitívneho uzáveru. Na overenie správnosti algoritmu použite príklad orientovaného grafu reprezentovaného maticou susednosti.

Testy:

Váš program bude vedieť načítať zadanú maticu zo súboru, vypočítať tranzitívny uzáver a ten vypísať na štandardný výstup. Rozumne malé kombinácie vstupov a výstupov sú:

### Vstup a výstup

**Vstup:**
```
0 1 1 0
0 0 1 0
0 0 0 1
0 0 0 0
```
**Uzáver:**
```
0 1 1 1
0 0 1 1
0 0 0 1
0 0 0 0
```

**Vstup:**
```
0 0 1 1 0
0 0 1 0 0
0 0 0 1 1
0 0 0 0 1
0 0 0 0 0
```
**Uzáver:**
```
0 0 1 1 1
0 0 1 1 1
0 0 0 1 1
0 0 0 0 1
0 0 0 0 0
```

**Vstup:**
```
0 0 0 0 1 1
0 0 1 0 1 1
0 0 0 1 0 0
0 0 0 0 0 1
0 0 0 0 0 1
0 0 0 0 0 0
```
**Uzáver:**
```
0 0 0 0 1 1
0 0 1 1 1 1
0 0 0 1 0 1
0 0 0 0 0 1
0 0 0 0 0 1
0 0 0 0 0 0
```
-- 


# Téma: Implementácia Kruskalovho algoritmu

## Cieľ:

Cieľom tejto práce na úlohe je implementovať Kruskalov algoritmus na nájdenie minimálneho kostrového stromu (MST) v neohodnotenom grafe. 


### Zadanie:

1. **Teoretická časť:**
   a) Vysvetlite, čo je minimálny kostrový strom (MST).
   - Pre vysvetlenie nie len Kruskalovho / Primovho algoritmu môžete využiť jedno z doučovaní algoritmov, ktoré sme realizovali na VŠB :
 - [Prvé doučovanie z algoritmov ](https://www.youtube.com/watch?v=yJjLqHZh9b0)
 - [Druhé doučovanie z algoritmov](https://www.youtube.com/watch?v=yJjLqHZh9b0)
   b) Popíšte princíp Kruskalovho algoritmu.  
   c) Aký je rozdiel medzi Kruskalovým a Primovým algoritmom?  

3. **Praktická časť:**
   Implementujte program vo vami preferovanej formy jazyka primárne konceptujte v C# avšak ako valídne riešenie beriem i python a c++ Kruskalov algoritmus pre graf zadaný ako zoznam hrán.

   **Podmienky:**


   - Vstupom je zoznam hrán grafu vo formáte: `[(u, v, w), ...]`, kde `u` a `v` sú vrcholy hrany a `w` je jej hmotnosť.
   - Graf môže obsahovať viac komponentov.
   - Použite triedenie na zoračenie hrán podľa hmotnosti.
   - Implementujte disjunktné množiny (Union-Find) s optimalizáciou cez kompresiu cesty a zjednocovanie podľa veľkosti.

4. **Testovanie:**

   a) Vstup:  
      Graf: `[(1, 2, 4), (1, 3, 1), (2, 3, 2), (2, 4, 5), (3, 4, 3)]`  
   b) Očakávaný výstup:  
      MST: `[(1, 3, 1), (2, 3, 2), (3, 4, 3)]`  
      Celková hmotnosť: `6`  
   c) Otestujte svoj program aj na vlastných číselných príkladoch s väčším počtom vrcholov.

6. **Bonusová úloha:**


   Implementujte vizualizáciu vstupného grafu a výsledného MST pomocou knižníc, ako je napríklad Matplotlib alebo NetworkX. Výstupom bude grafické znázorněnie.


**Poznámky:**  

Ak potrebujete pomôcť alebo konzultáciu, kontaktujte ma prostredníctvom discord, eduapage.
