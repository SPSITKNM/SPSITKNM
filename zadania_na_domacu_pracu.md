Robot začína v ľavom hornom rohu hracej dosky s rozmermi \( n \times m \). Hracia doska obsahuje mince, pričom každá minca je umiestnená na pozícii s hodnotou 1, pozície s hodnotou 0 sú prázdne.

Vašou úlohou je napísať program na výpočet maximálneho počtu mincí, ktoré môže robot nazbierať, ak sa pohybuje iba doprava a nadol smerom k pravému dolnému rohu hracej dosky.

Prístup a algoritmus je popísaný v knihe *Introduction to the Design and Analysis of Algorithms* od Levitina, na strane 288 (Príklad 3). *Nájdete na našom discorde v sekci učebné materiály*

## Testovacie dáta

### Matica s výsledkom 7:

```cpp
vector<vector<int>> board = {
    {1, 0, 1, 0, 1},
    {1, 1, 0, 0, 0},
    {0, 1, 1, 0, 1},
    {1, 0, 1, 1, 0}
};
```

### Matica s výsledkom 7:


```cpp
vector<vector<int>> board = {
    {0, 0, 0, 0, 1, 0, 1, 0, 0, 1},
    {1, 0, 1, 0, 0, 0, 0, 0, 0, 0},
    {0, 1, 0, 0, 1, 0, 0, 0, 1, 1},
    {0, 1, 1, 1, 0, 1, 1, 0, 0, 1},
    {1, 1, 1, 0, 0, 1, 1, 1, 1, 0},
    {0, 1, 0, 0, 0, 0, 1, 1, 1, 1},
    {0, 0, 1, 1, 1, 1, 0, 1, 1, 0},
    {1, 1, 1, 0, 0, 1, 1, 1, 1, 1},
    {1, 1, 0, 0, 0, 0, 1, 1, 0, 1},
    {0, 0, 0, 0, 1, 1, 0, 0, 0, 1},
    {1, 1, 1, 0, 1, 1, 1, 1, 0, 0},
    {0, 1, 1, 0, 1, 0, 1, 0, 0, 1},
    {1, 0, 1, 1, 1, 1, 0, 0, 1, 0},
    {1, 1, 1, 1, 0, 1, 1, 1, 1, 1},
    {0, 0, 1, 0, 0, 1, 0, 0, 1, 0},
    {1, 0, 1, 1, 0, 1, 0, 1, 0, 1},
    {0, 1, 0, 0, 0, 1, 1, 1, 1, 0},
    {1, 0, 1, 1, 0, 0, 1, 0, 1, 1},
    {1, 1, 1, 0, 1, 1, 0, 1, 1, 1},
    {0, 0, 0, 1, 1, 0, 1, 1, 0, 0},
    {0, 0, 0, 0, 1, 0, 1, 0, 1, 1},
    {1, 0, 0, 1, 1, 1, 0, 1, 0, 0},
    {1, 0, 1, 1, 0, 0, 1, 0, 0, 1},
    {1, 1, 0, 1, 1, 0, 1, 1, 0, 0},
    {1, 0, 1, 0, 0, 1, 1, 1, 0, 1},
    {1, 1, 0, 1, 1, 0, 0, 0, 0, 1}
};
```
