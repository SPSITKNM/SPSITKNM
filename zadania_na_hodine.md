# Zadanie: Program na vykreslenie geometrických tvarov do `20.9.2025`

## Popis

Vašou úlohou je vytvoriť program, ktorý bude vedieť vypísať rôzne geometrické tvary na výstup. Pri spustení program načíta zo štandardného vstupu tri čísla (obrazec, A, B). V závislosti od hodnoty čísla obrazec program vykreslí daný geometrický tvar, ktorý bude ovplyvnený hodnotami parametrov **A** (šírka) a **B** (výška).

### Typy obrazcov

Nižšie nájdete zoznam obrazcov, ktoré by mal váš program podporovať:

### 0 - Plný obdĺžnik
Ak má **obrazec** hodnotu `0`, program by mal vypísať plný obdĺžnik s šírkou **A** a výškou **B**.

#### Ukážkový výstup pre vstup: 
```plaintext
0 3 5
```
```plaintext
XXX
XXX
XXX
XXX
XXX
```

### 1 - Dutinový obdĺžnik

Ak má obrazec hodnotu 1, program by mal vypísať dutý obdĺžnik s šírkou A a výškou B. Dutý obdĺžnik obsahuje X po svojom obvode, ale vo vnútri je prázdny (vypíše sa medzera).

#### Ukážkový výstup pre vstup: 

```plaintext
1 4 5
```

```plaintext
XXXX
X  X
X  X
X  X
XXXX
```

### 2 - Číselný obdĺžnik

Ak má obrazec hodnotu 2, program by mal vypísať obdĺžnik s šírkou A a výškou B, ktorý bude mať v strede číselný vzor. Čísla začínajú od nuly a zvyšujú sa o jednotku. Pri prekročení hodnoty 9 sa čísla "prelejú" na nulu. Číselný vzor je uprostred, s okrajom z písmen X.

```plaintext
2 6 7
```

```plaintext
XXXXXX
X0123X
X4567X
X8991X
X2345X
X6789X
XXXXXX
```

### 3 - Diagonála

Ak má obrazec hodnotu 3, program by mal vypísať diagonálu smerujúcu doprava dole, ktorá obsahuje A bodov. Parameter B je v tomto prípade ignorovaný.

```plaintext
3 5 0
```

```plaintext
X    
 X   
  X  
   X 
    X
```

### 6 - Písmeno T 

Ak má obrazec hodnotu 6, program by mal vykresliť písmeno T, ktoré bude mať šírku A bodov a výšku B bodov. Môžete predpokladať, že hodnota A bude vždy nepárna, aby bolo možné písmeno T vycentrovať.

```plaintext
6 5 4
```

```plaintext
XXXXX
  X  
  X  
  X  
```

### 9 - Číselný obdĺžnik po stĺpcoch 

Ak má obrazec hodnotu 9, program by mal vypísať obdĺžnik s šírkou A a výškou B, ktorý bude mať v strede číselný vzor. Čísla sa budú zvyšovať po stĺpcoch. Čísla začínajú od nuly a zvyšujú sa o jednotku. Pri prekročení hodnoty 9 sa čísla "prelejú" na nulu.

```plaintext
9 5 6
```


```plaintext
XXXXX
X048X
X159X
X260X
X371X
XXXXX
```
