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
