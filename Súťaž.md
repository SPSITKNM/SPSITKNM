
# Advent of Code – Deň 4: Upratovanie tábora

Skôr než môžu byť z lodí vyložené posledné zásoby, je potrebné uvoľniť miesto. Preto bolo niekoľkým škriatkom pridelené upratovanie určitých častí tábora. Každá sekcia má jedinečné ID číslo a každý škriatok má pridelený rozsah ID sekcií.

Keď si však škriatkovia začali porovnávať svoje pridelenia, všimli si, že mnohé z týchto sekcií sa prekrývajú. Aby rýchlo zistili, kde dochádza k prekrývaniu a znížili duplicitu, škriatkovia vytvorili zoznam dvojíc s pridelenými sekciami (váš vstupný problém).

Napríklad nasledujúci zoznam obsahuje dvojice pridelených sekcií:

```
2-4,6-8
2-3,4-5
5-7,7-9
2-8,3-7
6-6,4-6
2-6,4-8
```

Tento zoznam znamená:

- V prvej dvojici mal prvý škriatok pridelené sekcie 2–4 (sekcie 2, 3 a 4) a druhý škriatok sekcie 6–8 (sekcie 6, 7 a 8).
- V druhej dvojici mal každý škriatok pridelené dve sekcie.
- V tretej dvojici mal prvý škriatok sekcie 5, 6 a 7, zatiaľ čo druhý škriatok mal tiež 7, ale navyše 8 a 9.

Tento zoznam používa jednociferné ID sekcií pre zjednodušenie znázornenia; váš zoznam môže obsahovať väčšie čísla. Vizualizácia priradenia sekcií pre jednotlivé dvojice vyzerá takto:

```
.234.....  2-4
.....678.  6-8

.23......  2-3
...45....  4-5

....567..  5-7
......789  7-9

.2345678.  2-8
..34567..  3-7

.....6...  6-6
...456...  4-6

.23456...  2-6
...45678.  4-8
```

Niektoré dvojice zistili, že jedno z ich priradení úplne obsahuje to druhé. Napríklad 2–8 úplne obsahuje 3–7 a 6–6 je úplne obsiahnuté v 4–6. V takýchto dvojiciach je jeden škriatok pridelený na upratovanie sekcií, ktoré už jeho partner upratuje, čo naznačuje, že je potrebné tieto dvojice prehodnotiť. V tomto príklade sú takéto dvojice dve.

**Koľko dvojíc priradení obsahuje jeden rozsah, ktorý úplne zahŕňa druhý?**

---

### Prihláste sa na hranie pomocou jednej z týchto služieb:

- [GitHub](#)
- [Google](#)
- [Twitter](#)
- [Reddit](#)

[Ako funguje autentifikácia?](#)
