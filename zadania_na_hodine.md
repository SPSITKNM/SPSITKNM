Zadání:

Implementujte Warshalův algoritmus pro výpočet transitivního uzávěru orientovaného acyklického grafu. Algoritmus by měl být implementován jako funkce, která přijímá matici sousednosti grafu a vrací matici transitivního uzávěru. Pro ověření správnosti algoritmu použijte příklad orientovaného grafu reprezentovaného maticí sousednosti.

Testy:

Váš program bude umět načíst zadanou matici ze souboru, spočítat transitivní uzávěr a ten vypsat na standardní výstup. Rozumně malé kombinace vstupů a výstupů jsou:

### Vstup a výstup

**Vstup:**
```
0 1 1 0
0 0 1 0
0 0 0 1
0 0 0 0
```
**Uzávěr:**
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
**Uzávěr:**
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
**Uzávěr:**
```
0 0 0 0 1 1
0 0 1 1 1 1
0 0 0 1 0 1
0 0 0 0 0 1
0 0 0 0 0 1
0 0 0 0 0 0
```

