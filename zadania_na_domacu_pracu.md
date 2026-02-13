# Algoritmy a Dátové štruktúry - Cvičebné úlohy (C++)

*Developed by Tomáš Mucha*

## Obsah

### Grafové algoritmy
1. [Kruskalov algoritmus](#úloha-1-kruskalov-algoritmus---minimálna-kostra-grafu)
2. [Primov algoritmus](#úloha-2-primov-algoritmus---iný-prístup-ku-koste)
3. [Dijkstrov algoritmus](#úloha-3-dijkstrov-algoritmus---najkratšie-cesty)

### Dátové štruktúry
4. [Hash Mapy](#úloha-4-hash-mapy---rýchle-vyhľadávanie)

### Stromové štruktúry
- [**ÚVOD: Od Linked Listu k Stromu**](#úvod-od-linked-listu-k-stromu) ← **Začni tu ak si nerobil stromy!**
5. [Binárny strom](#úloha-5-binárny-strom---základná-stromová-štruktúra)
6. [Binárny vyhľadávací strom (BST)](#úloha-6-binárny-vyhľadávací-strom-bst---efektívne-vyhľadávanie)
7. [AVL stromy](#úloha-7-avl-stromy---samovyvažujúce-binárne-stromy)
8. [B-stromy](#úloha-8-b-stromy---stromy-pre-databázy)

### Algoritmy na prehľadávanie
9. [DFS - Prehľadávanie do hĺbky](#úloha-9-dfs---prehľadávanie-do-hĺbky)
10. [BFS - Prehľadávanie do šírky](#úloha-10-bfs---prehľadávanie-do-šírky)
11. [Binárne vyhľadávanie](#úloha-11-binárne-vyhľadávanie---rýchle-hľadanie-v-zoradenom-poli)

### Kompresia
12. [Huffmanovo kódovanie](#úloha-12-huffmanovo-kódovanie---kompresia-dát)

### Pomocné sekcie
- [Cheat Sheet - Rýchle zopakovanie](#cheat-sheet---rýchle-zopakovanie-pred-skúškou)
- [Kontrolné otázky](#kontrolné-otázky---over-si-či-rozumieš)
- [Sebahodnotenie](#sebahodnotenie-pred-skúškou)

---

## Ako používať tento materiál

### Pre koho je tento materiál?

Tento materiál je určený pre študentov, ktorí:
- Poznajú základy C++ (premenné, funkcie, triedy, ukazovatele)
- Robili **linked listy** alebo podobné štruktúry
- Rozumejú základom **rekurzie**
- Stromové štruktúry nerobili alebo ich potrebujú zopakovať

---

### Odporúčané poradie štúdia

**Ak si nerobil stromy**, nasleduj toto poradie:

```
╔══════════════════════════════════════════════════════════════════════════════╗
║  FÁZA 1: ZÁKLADY STROMOV (začni tu!)                                         ║
║  ──────────────────────────────────────────────────────────────────────────  ║
║                                                                              ║
║  [Úvod: Od Linked Listu k Stromu] ──→ [Úloha 5: Binárny strom]              ║
║           (1-2 hodiny)                      (2 hodiny)                       ║
║                                                                              ║
║  Naučíš sa: Čo je strom, základné pojmy, rozdiel oproti linked listu        ║
╚══════════════════════════════════════════════════════════════════════════════╝
                                    ↓
╔══════════════════════════════════════════════════════════════════════════════╗
║  FÁZA 2: PREHĽADÁVANIE STROMOV                                               ║
║  ──────────────────────────────────────────────────────────────────────────  ║
║                                                                              ║
║  [Úloha 9: DFS] ──────────────────→ [Úloha 10: BFS]                         ║
║   (2 hodiny)                           (1.5 hodiny)                          ║
║                                                                              ║
║  Naučíš sa: Ako prechádzať stromy, rekurzia vs iterácia, stack vs queue     ║
╚══════════════════════════════════════════════════════════════════════════════╝
                                    ↓
╔══════════════════════════════════════════════════════════════════════════════╗
║  FÁZA 3: VYHĽADÁVACIE STROMY                                                 ║
║  ──────────────────────────────────────────────────────────────────────────  ║
║                                                                              ║
║  [Úloha 6: BST] ──→ [Úloha 11: Binárne vyhľadávanie] ──→ [Úloha 7: AVL]     ║
║   (2.5 hodiny)            (1.5 hodiny)                      (3 hodiny)       ║
║                                                                              ║
║  Naučíš sa: Efektívne vyhľadávanie, O(log n), vyvažovanie stromov           ║
╚══════════════════════════════════════════════════════════════════════════════╝
                                    ↓
╔══════════════════════════════════════════════════════════════════════════════╗
║  FÁZA 4: POKROČILÉ TÉMY                                                      ║
║  ──────────────────────────────────────────────────────────────────────────  ║
║                                                                              ║
║  [Úloha 8: B-stromy] ──→ [Úloha 12: Huffman] ──→ [Úloha 4: Hash Mapy]       ║
║    (2 hodiny)              (2 hodiny)              (2 hodiny)                ║
║                                                                              ║
║  Naučíš sa: Databázové stromy, kompresia, hash tabuľky                      ║
╚══════════════════════════════════════════════════════════════════════════════╝
                                    ↓
╔══════════════════════════════════════════════════════════════════════════════╗
║  FÁZA 5: GRAFOVÉ ALGORITMY (vyžaduje predošlé znalosti)                      ║
║  ──────────────────────────────────────────────────────────────────────────  ║
║                                                                              ║
║  [Úloha 1: Kruskal] ──→ [Úloha 2: Prim] ──→ [Úloha 3: Dijkstra]             ║
║    (2.5 hodiny)          (2 hodiny)           (2.5 hodiny)                   ║
║                                                                              ║
║  Naučíš sa: Minimálna kostra, najkratšie cesty, Union-Find                  ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

---

### Prerekvizity pre každú tému

| Úloha | Potrebuješ vedieť | Odhadovaný čas |
|-------|-------------------|----------------|
| **Úvod: Od Linked Listu k Stromu** | Linked list, ukazovatele | 1-2 hod |
| **5. Binárny strom** | Úvod, rekurzia | 2 hod |
| **9. DFS** | Binárny strom, stack | 2 hod |
| **10. BFS** | Binárny strom, queue | 1.5 hod |
| **6. BST** | Binárny strom, DFS | 2.5 hod |
| **11. Binárne vyhľadávanie** | Základy algoritmov | 1.5 hod |
| **7. AVL** | BST (dôležité!) | 3 hod |
| **8. B-stromy** | BST, AVL koncept | 2 hod |
| **12. Huffman** | Binárny strom, priority queue | 2 hod |
| **4. Hash Mapy** | Základy C++ | 2 hod |
| **1. Kruskal** | Grafy, Union-Find, triedenie | 2.5 hod |
| **2. Prim** | Grafy, priority queue | 2 hod |
| **3. Dijkstra** | Grafy, priority queue, BFS koncept | 2.5 hod |

**Celkový odhadovaný čas:** ~25 hodín (vrátane cvičení)

---

### Tipy na efektívne učenie algoritmov

#### 1. NIKDY nekopíruj kód bez pochopenia

```
ZLE:   Skopírujem kód -> spustím -> funguje -> hotovo

DOBRE: Prečítam teóriu -> nakreslím si príklad na papier
       -> napíšem kód sám -> debugujem -> pochopím
```

#### 2. Kresli, kresli, kresli!

Stromy a grafy sú **vizuálne** štruktúry. Vždy si nakresli:
- Stav pred operáciou
- Každý krok algoritmu
- Stav po operácii

```
Príklad: Vkladanie 15 do BST

PRED:          KROK 1:        KROK 2:        PO:
   [10]         [10]           [10]           [10]
   /  \    →    /  \      →    /  \      →    /  \
 [5]  [20]    [5]  [20]      [5]  [20]      [5]  [20]
              15>10,         15<20,              /
              idem vpravo    idem vľavo       [15]
```

#### 3. Používaj "rubber duck debugging"

Vysvetli algoritmus nahlas (aj gumenej kačičke). Ak nevieš vysvetliť jednoducho, nerozumieš tomu.

#### 4. Testuj na okrajových prípadoch

```cpp
// Vždy testuj:
// 1. Prázdny vstup (nullptr, prázdne pole)
// 2. Jeden prvok
// 3. Dva prvky
// 4. Veľa prvkov
// 5. Duplikáty
// 6. Už zoradené / obrátene zoradené
```

#### 5. Porovnávaj časové zložitosti

Pred každým algoritmom sa spýtaj:
- Aká je časová zložitosť?
- Dá sa to urobiť rýchlejšie?
- Aká je priestorová zložitosť?

#### 6. Implementuj najprv jednoducho, potom optimalizuj

```
Krok 1: Fungujúce riešenie (aj keď pomalé)
Krok 2: Testy prechádzajú
Krok 3: Optimalizácia (ak je potrebná)
```

---

### Ako témy súvisia

```
                    ┌─────────────────┐
                    │  LINKED LIST    │
                    │  (základ)       │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  BINÁRNY STROM  │
                    │  (Úloha 5)      │
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
     ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
     │    DFS      │  │    BFS      │  │    BST      │
     │  (Úloha 9)  │  │  (Úloha 10) │  │  (Úloha 6)  │
     └──────┬──────┘  └──────┬──────┘  └──────┬──────┘
            │                │                │
            │                │         ┌──────┴──────┐
            │                │         ▼             ▼
            │                │   ┌──────────┐  ┌──────────┐
            │                │   │   AVL    │  │ Binárne  │
            │                │   │(Úloha 7) │  │vyhľadáv. │
            │                │   └────┬─────┘  │(Úloha 11)│
            │                │        │        └──────────┘
            │                │        ▼
            │                │   ┌──────────┐
            │                │   │ B-stromy │
            │                │   │(Úloha 8) │
            │                │   └──────────┘
            │                │
            ▼                ▼
     ┌─────────────────────────────────┐
     │         GRAFOVÉ ALGORITMY       │
     │  Kruskal, Prim, Dijkstra        │
     │  (Úlohy 1, 2, 3)                │
     └─────────────────────────────────┘
            │
            ▼
     ┌─────────────────┐      ┌─────────────────┐
     │   HASH MAPY     │      │    HUFFMAN      │
     │   (Úloha 4)     │      │   (Úloha 12)    │
     └─────────────────┘      └─────────────────┘
```

---

### Časté chyby začiatočníkov

| Chyba | Prečo je to problém | Riešenie |
|-------|---------------------|----------|
| Preskočím úvod o stromoch | Nepochopím základy, potom sa trápim | Začni od Úvodu! |
| Nekontroluj nullptr | Segmentation fault | Vždy `if (node == nullptr)` |
| Zamieňam výšku a hĺbku | Nesprávne výpočty | Pozri si definície v Úvode |
| Nekreslím si príklady | Nevidím čo sa deje | Papier a ceruzka sú povinné |
| Kopírujem bez pochopenia | Na skúške neviem nič | Píš kód sám |

---

### Ako vieš, že si tému pochopil?

Pre každú tému by si mal vedieť:

1. **Vysvetliť** algoritmus vlastnými slovami (bez kódu)
2. **Nakresliť** príklad na papier
3. **Napísať** kód od nuly (bez pozerania)
4. **Analyzovať** časovú zložitosť
5. **Identifikovať** kedy použiť tento algoritmus

**Ak nevieš jedno z týchto, vráť sa k téme!**

---

# ČASŤ 1: GRAFOVÉ ALGORITMY

## Úloha 1: Kruskalov algoritmus - Minimálna kostra grafu

**Čo sa naučíš:** Ako nájsť minimálnu kostru grafu pomocou Kruskalovho algoritmu v C++

### Teória - Čo je to minimálna kostra?

**Graf** = množina vrcholov (uzlov) spojených hranami  
**Kostra grafu** = podmnožina hrán, ktorá spája všetky vrcholy bez cyklov  
**Minimálna kostra** = kostra s najmenším súčtom váh hrán

**Kruskalov algoritmus:**

1. Zoraď všetky hrany podľa váhy (od najmenšej)
2. Postupne pridávaj hrany, ktoré nevytvoria cyklus
3. Skonči, keď máš n-1 hrán (pre n vrcholov)

**Analógia:** Staviaš sieť ciest medzi mestami. Chceš spojiť všetky mestá s čo najmenšími nákladmi, bez zbytočných okružných ciest.

### Vizualizácia grafu

```
        1
    (0)-----(1)
    /|       |\
   2 |       | 4
  /  |       |  \
(2)  |3      |   (3)
  \  |       |  /
   6 |       | 5
    \|       |/
    (4)-----(5)
        9

Graf s 6 vrcholmi a 9 hranami.
Hrany: 0-1(1), 0-2(2), 1-2(3), 1-3(4), 2-3(5), 2-4(6), 3-4(7), 3-5(8), 4-5(9)
```

**Výsledná minimálna kostra:**
```
        1
    (0)-----(1)
    /         \
   2           4
  /             \
(2)             (3)
  \               \
   6               8
    \               \
    (4)             (5)

MST hrany: 0-1(1), 0-2(2), 1-3(4), 2-4(6), 3-5(8)
Celková váha: 21
```

---

### Krok za krokom

#### Krok 1: Union-Find (Disjoint Set) štruktúra

Najprv potrebujeme dátovú štruktúru na detekciu cyklov:

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

/**
 * Union-Find (Disjoint Set Union) štruktúra.
 * Slúži na efektívnu kontrolu, či pridanie hrany vytvori cyklus.
 */
class UnionFind {
private:
    vector<int> parent;  // parent[i] = rodič vrcholu i
    vector<int> rank;    // rank[i] = "hĺbka" stromu zakoreneného vo vrchole i

public:
    UnionFind(int n) {
        parent.resize(n);
        rank.resize(n, 0);

        // Na začiatku je každý vrchol sám svojím rodičom
        for (int i = 0; i < n; i++) {
            parent[i] = i;
        }
    }

    /**
     * Nájdi koreň (reprezentanta) množiny, do ktorej patrí x.
     * Používa path compression - optimalizácia.
     */
    int find(int x) {
        if (parent[x] != x) {
            // Path compression: pripoj x priamo ku koreňu
            parent[x] = find(parent[x]);
        }
        return parent[x];
    }

    /**
     * Spoj dve množiny obsahujúce x a y.
     * Vráti true, ak boli v rôznych množinách (spojenie prebehlo).
     * Vráti false, ak už boli v rovnakej množine (vytvoril by sa cyklus).
     */
    bool unite(int x, int y) {
        int rootX = find(x);
        int rootY = find(y);

        // Už sú v rovnakej množine - vytvoril by sa cyklus
        if (rootX == rootY) {
            return false;
        }

        // Union by rank - pripoj menší strom pod väčší
        if (rank[rootX] < rank[rootY]) {
            parent[rootX] = rootY;
        } else if (rank[rootX] > rank[rootY]) {
            parent[rootY] = rootX;
        } else {
            parent[rootY] = rootX;
            rank[rootX]++;
        }

        return true;
    }
};
```

**Vysvetlenie:**

- `parent[i]` udržiava "reprezentanta" množiny pre vrchol i
- `find(x)` nájde koreň stromu (reprezentanta množiny)
- `unite(x, y)` spojí dve množiny
- Union by rank a path compression = optimalizácie pre rýchlosť

---

#### Krok 2: Štruktúra pre hranu

```cpp
/**
 * Štruktúra reprezentujúca hranu grafu.
 */
struct Edge {
    int u, v;      // Vrcholy, ktoré hrana spája
    int weight;    // Váha hrany

    // Konštruktor
    Edge(int u, int v, int weight) : u(u), v(v), weight(weight) {}

    // Operátor na porovnávanie (pre triedenie)
    bool operator<(const Edge& other) const {
        return weight < other.weight;
    }
};
```

---

#### Krok 3: Implementácia Kruskalovho algoritmu

```cpp
/**
 * Kruskalov algoritmus na nájdenie minimálnej kostry grafu.
 *
 * Parametre:
 *   n: počet vrcholov (očíslované 0 až n-1)
 *   edges: vektor hrán
 *
 * Vracia:
 *   pair<vector<Edge>, int>: minimálna kostra a jej celková váha
 */
pair<vector<Edge>, int> kruskal(int n, vector<Edge>& edges) {
    // KROK 1: Zoraď hrany podľa váhy (od najmenšej)
    sort(edges.begin(), edges.end());

    cout << "Zoradene hrany podla vahy:" << endl;
    for (const auto& e : edges) {
        cout << "   " << e.u << " -- " << e.v
             << " (vaha: " << e.weight << ")" << endl;
    }
    cout << endl;

    // KROK 2: Inicializuj Union-Find štruktúru
    UnionFind uf(n);

    // KROK 3: Vyber hrany pre minimálnu kostru
    vector<Edge> mst;      // Minimálna kostra
    int totalCost = 0;

    cout << "Budovanie minimalnej kostry:" << endl;

    for (const auto& edge : edges) {
        // Skús pridať hranu - ak nevytvori cyklus
        if (uf.unite(edge.u, edge.v)) {
            mst.push_back(edge);
            totalCost += edge.weight;
            cout << "   [+] Pridavam: " << edge.u << " -- " << edge.v
                 << " (vaha: " << edge.weight << ")" << endl;
        } else {
            cout << "   [-] Preskakujem: " << edge.u << " -- " << edge.v
                 << " (vytvori cyklus)" << endl;
        }

        // Optimalizácia: ak máme n-1 hrán, máme kostru
        if (mst.size() == n - 1) {
            cout << "   Kostra kompletna!" << endl;
            break;
        }
    }

    cout << endl;
    return {mst, totalCost};
}
```

**Vysvetlenie krokov:**

1. **Triedenie:** O(E log E), kde E = počet hrán
2. **Prechádzanie hrán:** Pre každú hranu skontroluj, či nevytvori cyklus
3. **Union-Find:** Rýchla kontrola cyklov (takmer O(1) amortizovane)

---

#### Krok 4: Hlavný program - príklad použitia

```cpp
int main() {
    // Definícia grafu
    // Graf má 6 vrcholov (0-5)
    int n = 6;
    vector<Edge> edges;

    // Pridanie hrán vo formáte: Edge(vrchol1, vrchol2, váha)
    edges.push_back(Edge(0, 1, 1));
    edges.push_back(Edge(0, 2, 2));
    edges.push_back(Edge(1, 2, 3));
    edges.push_back(Edge(1, 3, 4));
    edges.push_back(Edge(2, 3, 5));
    edges.push_back(Edge(2, 4, 6));
    edges.push_back(Edge(3, 4, 7));
    edges.push_back(Edge(3, 5, 8));
    edges.push_back(Edge(4, 5, 9));

    // Spustenie algoritmu
    cout << "==================================================" << endl;
    cout << "KRUSKALOV ALGORITMUS - Minimalna kostra grafu" << endl;
    cout << "==================================================" << endl;
    cout << endl;

    auto [mst, totalCost] = kruskal(n, edges);

    // Výpis výsledku
    cout << "==================================================" << endl;
    cout << "VYSLEDOK:" << endl;
    cout << "==================================================" << endl;
    cout << "Minimalna kostra obsahuje " << mst.size() << " hran:" << endl;
    for (const auto& e : mst) {
        cout << "  " << e.u << " -- " << e.v
             << " (vaha: " << e.weight << ")" << endl;
    }
    cout << endl;
    cout << "Celkova vaha kostry: " << totalCost << endl;
    cout << "==================================================" << endl;

    return 0;
}
```

**Očakávaný výstup:**

```
==================================================
KRUSKALOV ALGORITMUS - Minimalna kostra grafu
==================================================

Zoradene hrany podla vahy:
   0 -- 1 (vaha: 1)
   0 -- 2 (vaha: 2)
   1 -- 2 (vaha: 3)
   1 -- 3 (vaha: 4)
   2 -- 3 (vaha: 5)
   2 -- 4 (vaha: 6)
   3 -- 4 (vaha: 7)
   3 -- 5 (vaha: 8)
   4 -- 5 (vaha: 9)

Budovanie minimalnej kostry:
   [+] Pridavam: 0 -- 1 (vaha: 1)
   [+] Pridavam: 0 -- 2 (vaha: 2)
   [-] Preskakujem: 1 -- 2 (vytvori cyklus)
   [+] Pridavam: 1 -- 3 (vaha: 4)
   [-] Preskakujem: 2 -- 3 (vytvori cyklus)
   [+] Pridavam: 2 -- 4 (vaha: 6)
   [-] Preskakujem: 3 -- 4 (vytvori cyklus)
   [+] Pridavam: 3 -- 5 (vaha: 8)
   Kostra kompletna!

==================================================
VYSLEDOK:
==================================================
Minimalna kostra obsahuje 5 hrán:
  0 -- 1 (vaha: 1)
  0 -- 2 (vaha: 2)
  1 -- 3 (vaha: 4)
  2 -- 4 (vaha: 6)
  3 -- 5 (vaha: 8)

Celkova vaha kostry: 21
==================================================
```

---

### Časová zložitosť

| Operácia              | Zložitosť      |
| --------------------- | -------------- |
| Triedenie hrán        | O(E log E)     |
| Union-Find operácie   | O(E · α(V))\*  |
| **Celková zložitosť** | **O(E log E)** |

\*α(V) je inverzná Ackermannova funkcia - prakticky konštanta

**Pre E = O(V²):** O(E log E) = O(V² log V)

---

### Kompilácia a spustenie

```bash
# Kompilácia
g++ -std=c++17 -o kruskal kruskal.cpp

# Spustenie
./kruskal
```

---

### Čo si sa naučil?

- **Kruskalov algoritmus** hľadá minimálnu kostru grafu
- **Union-Find** efektívne detekuje cykly
- Algoritmus je **chamtivý** (greedy) - vždy vyberie najlacnejšiu hranu
- Časová zložitosť: **O(E log E)**
- Funguje na **súvislých** grafoch

---

### Časté chyby a ako sa im vyhnúť

| Chyba | Prečo nastáva | Riešenie |
|-------|---------------|----------|
| Zabudnuté triedenie hrán | Študent preskočí `sort()` | Vždy triediť pred hlavnou slučkou |
| Nesprávny Union-Find | Chýba path compression alebo union by rank | Použiť obe optimalizácie |
| Off-by-one v počte hrán | MST má `n-1` hrán, nie `n` | Kontrola: `mst.size() == n - 1` |
| Zabudnuté obojsmerné hrany | Pri neorientovanom grafe | Pridať hranu len raz do zoznamu |
| Nesúvislý graf | Algoritmus skončí s menej ako n-1 hranami | Skontrolovať, či `mst.size() == n - 1` |

**Typické bugs v kóde:**

```cpp
// CHYBA: Zabudnuté triedenie
for (const auto& edge : edges) {  // hrany nie sú zoradené!
    if (uf.unite(edge.u, edge.v)) { ... }
}

// SPRÁVNE:
sort(edges.begin(), edges.end());  // najprv zoradiť
for (const auto& edge : edges) { ... }
```

```cpp
// CHYBA: Porovnanie váh namiesto indexov v Union-Find
bool unite(int x, int y) {
    if (x == y) return false;  // porovnávame hodnoty, nie korene!
}

// SPRÁVNE:
bool unite(int x, int y) {
    int rootX = find(x);  // nájdi koreň
    int rootY = find(y);
    if (rootX == rootY) return false;  // porovnaj korene
}
```

---

### Tipy na testovanie

**1. Manuálna kontrola na malom grafe:**
```cpp
// Trojuholník s váhami 1, 2, 3
// Očakávaný MST: hrany s váhami 1 a 2, celková váha = 3
edges = {{0,1,1}, {1,2,2}, {0,2,3}};
auto [mst, cost] = kruskal(3, edges);
assert(cost == 3);
assert(mst.size() == 2);
```

**2. Edge cases na testovanie:**
```cpp
// Test 1: Jeden vrchol (žiadne hrany)
assert(kruskal(1, {}).second == 0);

// Test 2: Dva vrcholy, jedna hrana
assert(kruskal(2, {{0,1,5}}).second == 5);

// Test 3: Nesúvislý graf - malo by vrátiť menej ako n-1 hrán
vector<Edge> disconnected = {{0,1,1}};  // vrchol 2 izolovaný
auto [mst, cost] = kruskal(3, disconnected);
assert(mst.size() < 2);  // graf nie je súvislý
```

**3. Kontrolné otázky pred odovzdaním:**
- [ ] Sú hrany zoradené pred spracovaním?
- [ ] Má výsledná kostra presne n-1 hrán?
- [ ] Je celková váha minimálna (porovnaj s ručným výpočtom)?
- [ ] Funguje algoritmus aj pre graf s jedným vrcholom?

---

### Skús sám - Doplň chýbajúci kód

```cpp
pair<vector<Edge>, int> kruskal_student(int n, vector<Edge>& edges) {
    // TODO 1: Zoraď hrany podľa váhy
    // Hint: použij sort() a operator< v štruktúre Edge
    _________________________________

    UnionFind uf(n);
    vector<Edge> mst;
    int totalCost = 0;

    for (const auto& edge : edges) {
        // TODO 2: Skontroluj, či pridanie hrany vytvori cyklus
        // Hint: použij metódu unite() z UnionFind
        if (_________________________________) {
            mst.push_back(edge);
            totalCost += edge.weight;
        }

        // TODO 3: Zastav, keď máme dostatočný počet hrán
        // Hint: koľko hrán má mať kostra?
        if (mst.size() == _________________________________) {
            break;
        }
    }

    return {mst, totalCost};
}
```

<details>
<summary>Riešenie (klikni pre zobrazenie)</summary>

```cpp
// TODO 1:
sort(edges.begin(), edges.end());

// TODO 2:
if (uf.unite(edge.u, edge.v))

// TODO 3:
if (mst.size() == n - 1)
```
</details>

---

### Praktické úlohy

#### Úloha 1.1: Základná implementácia

Implementuj Kruskalov algoritmus pre nasledujúci graf:

- 5 vrcholov (0-4)
- Hrany: (0-1, 10), (0-2, 6), (0-3, 5), (1-3, 15), (2-3, 4)

**Očakávaný výsledok:** Celková váha MST = 19

#### Úloha 1.2: Detekcia nesúvislého grafu

Uprav implementáciu tak, aby detekovala, či je graf súvislý. Ak nie je, vypíš chybovú hlášku.

**Hint:** Ak MST nemá n-1 hrán, graf nie je súvislý.

#### Úloha 1.3: Vstup zo súboru

Uprav program tak, aby čítal graf zo súboru:

```
6 9
0 1 1
0 2 2
1 2 3
...
```

Prvý riadok: počet vrcholov, počet hrán  
Ďalšie riadky: u v váha

---

## Úloha 2: Primov algoritmus - Iný prístup ku kostre

**Čo sa naučíš:** Alternatívny spôsob hľadania minimálnej kostry v C++

### Teória - Rozdiel medzi Kruskal a Prim

**Kruskalov algoritmus:**

- Triedi HRANY
- Buduje "les" stromov, ktoré spája
- Lepší pre riedke grafy

**Primov algoritmus:**

- Začína od jedného VRCHOLU
- Postupne pridává najbližšie vrcholy
- Lepší pre husté grafy
- Vždy má jeden súvislý strom

**Analógia:**

- **Kruskal** = staviaš viacero mostov súčasne a potom ich spájaš
- **Prim** = staviaš mesto od centra a postupne pridávaš nové štvrte

### Vizualizácia - Ako Prim rastie

```
Štart z vrcholu 0:

Krok 1: Začíname          Krok 2: Pridaj 0-1(1)     Krok 3: Pridaj 0-2(2)
     [0]                       [0]---[1]                 [0]---[1]
                                                         /
                                                       [2]

Krok 4: Pridaj 1-3(4)     Krok 5: Pridaj 2-4(6)     Krok 6: Pridaj 3-5(8)
     [0]---[1]                 [0]---[1]                 [0]---[1]
     /      \                  /      \                  /      \
   [2]      [3]              [2]      [3]              [2]      [3]
                              |                         |        \
                             [4]                       [4]       [5]

Výsledok: MST s váhou 21
```

**Kľúčový rozdiel oproti Kruskalovi:** Prim vždy udržiava jeden súvislý strom, zatiaľ čo Kruskal môže mať viacero komponentov, ktoré postupne spája.

---

### Krok za krokom

#### Krok 1: Reprezentácia grafu

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <climits>
using namespace std;

/**
 * Graf reprezentovaný ako zoznam susedov.
 * Vhodný pre Primov algoritmus.
 */
class Graph {
private:
    int V;  // Počet vrcholov
    vector<vector<pair<int, int>>> adj;  // adj[u] = {(v, váha), ...}

public:
    Graph(int vertices) : V(vertices) {
        adj.resize(V);
    }

    /**
     * Pridaj neorientovanú hranu medzi u a v s váhou weight.
     */
    void addEdge(int u, int v, int weight) {
        adj[u].push_back({v, weight});
        adj[v].push_back({u, weight});
    }

    /**
     * Vypíš graf.
     */
    void printGraph() {
        cout << "Reprezentacia grafu:" << endl;
        for (int u = 0; u < V; u++) {
            cout << "   Vrchol " << u << ": ";
            bool first = true;
            for (auto [v, w] : adj[u]) {
                if (!first) cout << " -> ";
                cout << v << "(vaha:" << w << ")";
                first = false;
            }
            cout << endl;
        }
        cout << endl;
    }

    // Getter pre Primov algoritmus
    int getV() const { return V; }
    const vector<pair<int, int>>& getNeighbors(int u) const {
        return adj[u];
    }
};
```

---

#### Krok 2: Štruktúra pre hranu v MST

```cpp
/**
 * Štruktúra pre hranu v minimálnej kostre.
 */
struct MSTEdge {
    int u, v, weight;

    MSTEdge(int u, int v, int weight) : u(u), v(v), weight(weight) {}
};
```

---

#### Krok 3: Implementácia Primovho algoritmu

```cpp
/**
 * Primov algoritmus na nájdenie minimálnej kostry.
 *
 * Parametre:
 *   graph: graf reprezentovaný ako zoznam susedov
 *   start: počiatočný vrchol (default 0)
 *
 * Vracia:
 *   pair<vector<MSTEdge>, int>: MST a celková váha
 */
pair<vector<MSTEdge>, int> prim(const Graph& graph, int start = 0) {
    int V = graph.getV();
    vector<bool> visited(V, false);  // Označí už pridané vrcholy
    vector<MSTEdge> mst;             // Minimálna kostra
    int totalCost = 0;

    // Prioritná fronta: (váha, aktuálny_vrchol, predošlý_vrchol)
    // Min-heap - najmenšia váha na vrchu
    priority_queue<tuple<int, int, int>,
                   vector<tuple<int, int, int>>,
                   greater<tuple<int, int, int>>> pq;

    // Začíname od 'start' vrcholu s váhou 0
    pq.push({0, start, -1});  // -1 znamená žiadny predošlý vrchol

    cout << "Budovanie MST pomocou Primovho algoritmu:" << endl;
    cout << "   Zaciname od vrcholu " << start << endl << endl;

    int iteration = 0;

    while (!pq.empty() && mst.size() < V - 1) {
        // Vyber hranu s najmenšou váhou
        auto [weight, u, parent] = pq.top();
        pq.pop();

        // Ak už je vrchol pridaný, preskoč
        if (visited[u]) continue;

        // Označ vrchol ako pridaný
        visited[u] = true;
        iteration++;

        // Pridaj hranu do MST (okrem prvého vrcholu)
        if (parent != -1) {
            mst.push_back(MSTEdge(parent, u, weight));
            totalCost += weight;
            cout << "   Iteracia " << iteration << ": ";
            cout << "[+] Pridavam: " << parent << " -- " << u
                 << " (vaha: " << weight << ")" << endl;
        } else {
            cout << "   Iteracia " << iteration << ": ";
            cout << "Pociatocny vrchol: " << u << endl;
        }

        // Pridaj všetkých susedov aktuálneho vrcholu do fronty
        for (auto [v, w] : graph.getNeighbors(u)) {
            if (!visited[v]) {
                pq.push({w, v, u});
            }
        }
    }

    cout << endl;
    return {mst, totalCost};
}
```

**Vysvetlenie:**

1. **Prioritná fronta (heap):** Udržiava hrany zoradené podľa váhy
2. **Visited pole:** Zabráni opätovnému pridaniu vrcholu
3. **Greedy výber:** Vždy vyberieme najlacnejšiu hranu do nového vrcholu

---

#### Krok 4: Hlavný program - príklad použitia

```cpp
int main() {
    // Vytvor ten istý graf ako pri Kruskalovi
    Graph g(6);

    g.addEdge(0, 1, 1);
    g.addEdge(0, 2, 2);
    g.addEdge(1, 2, 3);
    g.addEdge(1, 3, 4);
    g.addEdge(2, 3, 5);
    g.addEdge(2, 4, 6);
    g.addEdge(3, 4, 7);
    g.addEdge(3, 5, 8);
    g.addEdge(4, 5, 9);

    cout << "==================================================" << endl;
    cout << "PRIMOV ALGORITMUS - Minimalna kostra grafu" << endl;
    cout << "==================================================" << endl;
    cout << endl;

    g.printGraph();

    auto [mst, totalCost] = prim(g, 0);

    cout << "==================================================" << endl;
    cout << "VYSLEDOK:" << endl;
    cout << "==================================================" << endl;
    cout << "Minimalna kostra obsahuje " << mst.size() << " hran:" << endl;
    for (const auto& e : mst) {
        cout << "  " << e.u << " -- " << e.v
             << " (vaha: " << e.weight << ")" << endl;
    }
    cout << endl;
    cout << "Celkova vaha kostry: " << totalCost << endl;
    cout << "==================================================" << endl;

    return 0;
}
```

**Očakávaný výstup:**

```
==================================================
PRIMOV ALGORITMUS - Minimalna kostra grafu
==================================================

Reprezentacia grafu:
   Vrchol 0: 1(vaha:1) -> 2(vaha:2)
   Vrchol 1: 0(vaha:1) -> 2(vaha:3) -> 3(vaha:4)
   Vrchol 2: 0(vaha:2) -> 1(vaha:3) -> 3(vaha:5) -> 4(vaha:6)
   Vrchol 3: 1(vaha:4) -> 2(vaha:5) -> 4(vaha:7) -> 5(vaha:8)
   Vrchol 4: 2(vaha:6) -> 3(vaha:7) -> 5(vaha:9)
   Vrchol 5: 3(vaha:8) -> 4(vaha:9)

Budovanie MST pomocou Primovho algoritmu:
   Zaciname od vrcholu 0

   Iteracia 1: Pociatocny vrchol: 0
   Iteracia 2: [+] Pridavam: 0 -- 1 (vaha: 1)
   Iteracia 3: [+] Pridavam: 0 -- 2 (vaha: 2)
   Iteracia 4: [+] Pridavam: 1 -- 3 (vaha: 4)
   Iteracia 5: [+] Pridavam: 2 -- 4 (vaha: 6)
   Iteracia 6: [+] Pridavam: 3 -- 5 (vaha: 8)

==================================================
VYSLEDOK:
==================================================
Minimalna kostra obsahuje 5 hrán:
  0 -- 1 (vaha: 1)
  0 -- 2 (vaha: 2)
  1 -- 3 (vaha: 4)
  2 -- 4 (vaha: 6)
  3 -- 5 (vaha: 8)

Celkova vaha kostry: 21
==================================================
```

---

### Časová zložitosť

**S prioritnou frontou (binary heap):**

| Implementácia    | Zložitosť        |
| ---------------- | ---------------- |
| S binary heap    | O((V + E) log V) |
| S Fibonacci heap | O(E + V log V)   |

**Kedy použiť ktorý algoritmus?**

| Vlastnosť               | Kruskal        | Prim          |
| ----------------------- | -------------- | ------------- |
| Riedky graf (málo hrán) | Lepší       | Pomalší    |
| Hustý graf (veľa hrán)  | Pomalší     | Lepší      |
| Jednoduchosť            | Jednoduchší | Zložitejší |
| Paralelizácia           | Možná       | Ťažšia     |

---

### Kompilácia a spustenie

```bash
# Kompilácia
g++ -std=c++17 -o prim prim.cpp

# Spustenie
./prim
```

---

### Čo si sa naučil?

- **Primov algoritmus** rastie od jedného vrcholu
- Používa **prioritnú frontu** pre výber najlacnejšej hrany
- Vhodný pre **husté grafy**
- Časová zložitosť: **O((V + E) log V)**
- Dáva **rovnaký výsledok** ako Kruskal

---

### Časté chyby a ako sa im vyhnúť

| Chyba | Prečo nastáva | Riešenie |
|-------|---------------|----------|
| Opätovné pridanie vrcholu | Chýba kontrola `visited` | Vždy skontrolovať `if (visited[u]) continue;` |
| Nesprávny typ fronty | Použitie max-heap namiesto min-heap | Použiť `greater<>` v priority_queue |
| Zabudnutý počiatočný vrchol | Nepridanie štartu do fronty | `pq.push({0, start, -1})` na začiatku |
| Spracovanie zastaraných hrán | Vo fronte zostávajú staré záznamy | Kontrola `if (currentDist > dist[u]) continue;` |

**Typické bugs v kóde:**

```cpp
// CHYBA: Max-heap namiesto min-heap
priority_queue<tuple<int, int, int>> pq;  // default je max-heap!

// SPRÁVNE: Min-heap pomocou greater<>
priority_queue<tuple<int, int, int>,
               vector<tuple<int, int, int>>,
               greater<tuple<int, int, int>>> pq;
```

```cpp
// CHYBA: Chýbajúca kontrola visited
auto [weight, u, parent] = pq.top();
pq.pop();
// rovno pridávame do MST - môže pridať duplicitne!

// SPRÁVNE: Najprv skontroluj
auto [weight, u, parent] = pq.top();
pq.pop();
if (visited[u]) continue;  // preskočíme už spracované
visited[u] = true;
```

---

### Tipy na testovanie

**1. Porovnanie s Kruskalom:**
```cpp
// Oba algoritmy musia dať rovnakú celkovú váhu
auto [mst_kruskal, cost_kruskal] = kruskal(n, edges);
auto [mst_prim, cost_prim] = prim(graph, 0);
assert(cost_kruskal == cost_prim);  // váhy sa musia rovnať
```

**2. Test nezávislosti na štartovacom vrchole:**
```cpp
// Celková váha MST nezávisí od štartovacieho vrcholu
for (int start = 0; start < n; start++) {
    auto [mst, cost] = prim(graph, start);
    assert(cost == expected_cost);
}
```

**3. Kontrolný checklist:**
- [ ] Je prioritná fronta min-heap (nie max-heap)?
- [ ] Kontrolujem `visited` pred spracovaním vrcholu?
- [ ] Pridávam všetkých susedov do fronty?
- [ ] Má výsledná MST presne n-1 hrán?

---

### Skús sám - Doplň chýbajúci kód

```cpp
pair<vector<MSTEdge>, int> prim_student(const Graph& graph, int start) {
    int V = graph.getV();
    vector<bool> visited(V, false);
    vector<MSTEdge> mst;
    int totalCost = 0;

    // TODO 1: Aký typ fronty potrebujeme? (min-heap alebo max-heap?)
    // Hint: chceme najmenšiu váhu na vrchu
    priority_queue<tuple<int, int, int>,
                   vector<tuple<int, int, int>>,
                   _________________________________> pq;

    pq.push({0, start, -1});

    while (!pq.empty() && mst.size() < V - 1) {
        auto [weight, u, parent] = pq.top();
        pq.pop();

        // TODO 2: Kedy máme preskočiť tento vrchol?
        if (_________________________________) continue;

        visited[u] = true;

        if (parent != -1) {
            mst.push_back(MSTEdge(parent, u, weight));
            totalCost += weight;
        }

        // TODO 3: Ktorých susedov pridáme do fronty?
        for (auto [v, w] : graph.getNeighbors(u)) {
            if (_________________________________) {
                pq.push({w, v, u});
            }
        }
    }

    return {mst, totalCost};
}
```

<details>
<summary>Riešenie (klikni pre zobrazenie)</summary>

```cpp
// TODO 1: Min-heap
greater<tuple<int, int, int>>

// TODO 2: Preskočíme už navštívené
if (visited[u])

// TODO 3: Pridáme nenavštívených susedov
if (!visited[v])
```
</details>

---

### Praktické úlohy

#### Úloha 2.1: Začni od iného vrcholu

Spusti Primov algoritmus od vrcholu 3 namiesto 0. Zmenila sa celková váha MST?

#### Úloha 2.2: Matica susednosti

Uprav Primov algoritmus tak, aby pracoval s maticou susednosti namiesto zoznamu susedov.

**Hint:** Použite 2D pole `int adj[MAX][MAX]`, kde `adj[i][j]` = váha hrany alebo INF.

#### Úloha 2.3: Počet hrán vo fronte

Pridaj počítadlo, ktoré sleduje maximálny počet prvkov v prioritnej fronte počas behu algoritmu.

---

## Úloha 3: Dijkstrov algoritmus - Najkratšie cesty

**Čo sa naučíš:** Ako nájsť najkratšiu cestu z jedného vrcholu do všetkých ostatných v C++

> **Prerekvizity:** Grafy (reprezentácia) • Priority queue • [BFS koncept](#úloha-10-bfs---prehľadávanie-do-šírky)
>
> **Súvisiace témy:** [Prim (podobný algoritmus pre MST)](#úloha-2-primov-algoritmus---iný-prístup-ku-koste) • [BFS (najkratšia cesta bez váh)](#úloha-10-bfs---prehľadávanie-do-šírky)

### Teória - Čo je Dijkstrov algoritmus?

**Problém:** Máš mapu miest a vzdialenosti medzi nimi. Chceš vedieť najkratšiu cestu z tvojho mesta do všetkých ostatných.

**Dijkstrov algoritmus:**

- Začína od zdrojového vrcholu
- Postupne "relaxuje" hrany (zlepšuje odhady vzdialeností)
- Používa prioritnú frontu pre výber najbližšieho nenavštíveného vrcholu
- **Funguje len pre nezáporné váhy!**

**Analógia:** GPS navigácia - postupne objavuješ kratšie cesty, kým nenájdeš tie optimálne.

### Vizualizácia - Ako Dijkstra objavuje cesty

```
Graf:                          Vzdialenosti počas behu:

    (0)--4-->(1)               Krok 0: [0, ∞, ∞, ∞, ∞, ∞]  štart
     |        |                Krok 1: [0, 4, 1, ∞, ∞, ∞]  spracuj 0
     1        1                Krok 2: [0, 3, 1, 6, ∞, ∞]  spracuj 2 (cez 2->1 kratšie!)
     v        v                Krok 3: [0, 3, 1, 4, ∞, ∞]  spracuj 1 (cez 1->3 kratšie!)
    (2)--2-->(1)               Krok 4: [0, 3, 1, 4, 7, ∞]  spracuj 3
     |        |                Krok 5: [0, 3, 1, 4, 7, 9]  spracuj 4
     5        |
     v        v
    (3)<------+                Výsledné najkratšie cesty z 0:
     |                         0->1: 3 (cez 2)
     3                         0->2: 1 (priamo)
     v                         0->3: 4 (cez 2,1)
    (4)--2-->(5)               0->4: 7 (cez 2,1,3)
                               0->5: 9 (cez 2,1,3,4)
```

**Kľúčový insight:** Dijkstra vždy spracuje vrchol s najmenšou známou vzdialenosťou. Preto nefunguje pre záporné váhy - spracovaný vrchol už nemôže byť "zlepšený".

---

### Krok za krokom

#### Krok 1: Reprezentácia grafu a základné štruktúry

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <climits>
#include <algorithm>
using namespace std;

/**
 * Graf reprezentovaný ako zoznam susedov.
 */
class Graph {
private:
    int V;
    vector<vector<pair<int, int>>> adj;  // {sused, váha}

public:
    Graph(int vertices) : V(vertices) {
        adj.resize(V);
    }

    void addEdge(int u, int v, int weight) {
        adj[u].push_back({v, weight});
    }

    int getV() const { return V; }
    const vector<pair<int, int>>& getNeighbors(int u) const {
        return adj[u];
    }

    void printGraph() {
        cout << "Graf:" << endl;
        for (int u = 0; u < V; u++) {
            if (!adj[u].empty()) {
                cout << "   " << u << ": ";
                bool first = true;
                for (auto [v, w] : adj[u]) {
                    if (!first) cout << ", ";
                    cout << v << "(vaha:" << w << ")";
                    first = false;
                }
                cout << endl;
            }
        }
        cout << endl;
    }
};
```

---

#### Krok 2: Dijkstrov algoritmus

```cpp
/**
 * Dijkstrov algoritmus na nájdenie najkratších ciest.
 *
 * Parametre:
 *   graph: orientovaný/neorientovaný graf
 *   start: zdrojový vrchol
 *
 * Vracia:
 *   pair<vector<int>, vector<int>>: vzdialenosti a predchodcovia
 */
pair<vector<int>, vector<int>> dijkstra(const Graph& graph, int start) {
    int V = graph.getV();

    // Inicializácia
    vector<int> dist(V, INT_MAX);  // Vzdialenosti (∞ na začiatku)
    vector<int> pred(V, -1);       // Predchodcovia na ceste
    dist[start] = 0;

    // Prioritná fronta: (vzdialenosť, vrchol)
    priority_queue<pair<int, int>,
                   vector<pair<int, int>>,
                   greater<pair<int, int>>> pq;

    pq.push({0, start});

    cout << "Hladame najkratsie cesty z vrcholu " << start << endl;
    cout << "Pociatocne vzdialenosti: ";
    for (int i = 0; i < V; i++) {
        if (dist[i] == INT_MAX) cout << "∞ ";
        else cout << dist[i] << " ";
    }
    cout << endl << endl;

    int iteration = 0;

    while (!pq.empty()) {
        // Vyber vrchol s najmenšou vzdialenosťou
        auto [currentDist, u] = pq.top();
        pq.pop();

        // Ak sme už našli kratšiu cestu, preskoč
        if (currentDist > dist[u]) continue;

        iteration++;
        cout << "--- Iteracia " << iteration << " ---" << endl;
        cout << "Spracovavam vrchol: " << u
             << " (vzdialenosť: " << currentDist << ")" << endl;

        // Relax všetkých susedov
        for (auto [v, weight] : graph.getNeighbors(u)) {
            int newDist = currentDist + weight;

            // Ak je nová cesta kratšia, aktualizuj
            if (newDist < dist[v]) {
                int oldDist = dist[v];
                dist[v] = newDist;
                pred[v] = u;
                pq.push({newDist, v});

                cout << "   [+] " << u << " -> " << v << ": ";
                if (oldDist == INT_MAX) cout << "∞";
                else cout << oldDist;
                cout << " → " << newDist;
                if (oldDist != INT_MAX)
                    cout << " (zlepsenie o " << (oldDist - newDist) << ")";
                cout << endl;
            } else {
                cout << "   [-] " << u << " -> " << v << ": "
                     << newDist << " nie je lepšie ako " << dist[v] << endl;
            }
        }

        cout << "   Aktualne vzdialenosti: ";
        for (int i = 0; i < V; i++) {
            if (dist[i] == INT_MAX) cout << "∞ ";
            else cout << dist[i] << " ";
        }
        cout << endl << endl;
    }

    return {dist, pred};
}
```

---

#### Krok 3: Rekonštrukcia cesty

```cpp
/**
 * Rekonštruuj najkratšiu cestu zo start do end.
 */
vector<int> reconstructPath(const vector<int>& pred, int start, int end) {
    vector<int> path;

    // Prechádzaj spätne cez predchodcov
    for (int v = end; v != -1; v = pred[v]) {
        path.push_back(v);
    }

    // Otočenie cesty (bola sme ju stavali od konca)
    reverse(path.begin(), path.end());

    // Skontroluj, či cesta naozaj začína vo start
    if (path.empty() || path[0] != start) {
        return {};  // Neexistuje cesta
    }

    return path;
}
```

---

#### Krok 4: Hlavný program - príklad použitia

```cpp
int main() {
    // Vytvor graf
    Graph g(6);

    // Orientovaný graf
    g.addEdge(0, 1, 4);
    g.addEdge(0, 2, 1);
    g.addEdge(1, 3, 1);
    g.addEdge(2, 1, 2);
    g.addEdge(2, 3, 5);
    g.addEdge(3, 4, 3);
    g.addEdge(4, 5, 2);

    cout << "============================================================" << endl;
    cout << "DIJKSTROV ALGORITMUS - Najkratsie cesty" << endl;
    cout << "============================================================" << endl;
    cout << endl;

    g.printGraph();

    // Spusti algoritmus
    int startVertex = 0;
    auto [distances, predecessors] = dijkstra(g, startVertex);

    cout << "============================================================" << endl;
    cout << "VYSLEDOK:" << endl;
    cout << "============================================================" << endl;
    cout << endl;
    cout << "Najkratsie vzdialenosti z vrcholu " << startVertex << ":" << endl;

    for (int v = 0; v < g.getV(); v++) {
        cout << "   " << startVertex << " -> " << v << ": ";

        if (distances[v] == INT_MAX) {
            cout << "nedostupny" << endl;
        } else {
            cout << distances[v];

            // Rekonštruuj cestu
            vector<int> path = reconstructPath(predecessors, startVertex, v);

            if (!path.empty()) {
                cout << " (cesta: ";
                for (size_t i = 0; i < path.size(); i++) {
                    if (i > 0) cout << " -> ";
                    cout << path[i];
                }
                cout << ")";
            }
            cout << endl;
        }
    }

    cout << "============================================================" << endl;

    return 0;
}
```

**Očakávaný výstup:**

```
============================================================
DIJKSTROV ALGORITMUS - Najkratsie cesty
============================================================

Graf:
   0: 1(vaha:4), 2(vaha:1)
   1: 3(vaha:1)
   2: 1(vaha:2), 3(vaha:5)
   3: 4(vaha:3)
   4: 5(vaha:2)

Hladame najkratsie cesty z vrcholu 0
Pociatocne vzdialenosti: 0 ∞ ∞ ∞ ∞ ∞

--- Iteracia 1 ---
Spracovavam vrchol: 0 (vzdialenosť: 0)
   [+] 0 -> 1: ∞ → 4
   [+] 0 -> 2: ∞ → 1
   Aktualne vzdialenosti: 0 4 1 ∞ ∞ ∞

--- Iteracia 2 ---
Spracovavam vrchol: 2 (vzdialenosť: 1)
   [+] 2 -> 1: 4 → 3 (zlepsenie o 1)
   [+] 2 -> 3: ∞ → 6
   Aktualne vzdialenosti: 0 3 1 6 ∞ ∞

--- Iteracia 3 ---
Spracovavam vrchol: 1 (vzdialenosť: 3)
   [+] 1 -> 3: 6 → 4 (zlepsenie o 2)
   Aktualne vzdialenosti: 0 3 1 4 ∞ ∞

--- Iteracia 4 ---
Spracovavam vrchol: 3 (vzdialenosť: 4)
   [+] 3 -> 4: ∞ → 7
   Aktualne vzdialenosti: 0 3 1 4 7 ∞

--- Iteracia 5 ---
Spracovavam vrchol: 4 (vzdialenosť: 7)
   [+] 4 -> 5: ∞ → 9
   Aktualne vzdialenosti: 0 3 1 4 7 9

--- Iteracia 6 ---
Spracovavam vrchol: 5 (vzdialenosť: 9)
   Aktualne vzdialenosti: 0 3 1 4 7 9

============================================================
VYSLEDOK:
============================================================

Najkratsie vzdialenosti z vrcholu 0:
   0 -> 0: 0 (cesta: 0)
   0 -> 1: 3 (cesta: 0 -> 2 -> 1)
   0 -> 2: 1 (cesta: 0 -> 2)
   0 -> 3: 4 (cesta: 0 -> 2 -> 1 -> 3)
   0 -> 4: 7 (cesta: 0 -> 2 -> 1 -> 3 -> 4)
   0 -> 5: 9 (cesta: 0 -> 2 -> 1 -> 3 -> 4 -> 5)
============================================================
```

---

### Časová zložitosť

| Operácia     | Zložitosť |
| ------------ | --------- |
| Vyhľadávanie | O(log n)  |
| Vkladanie    | O(log n)  |
| Mazanie      | O(log n)  |

**S rôznymi implementáciami:**

| Implementácia  | Zložitosť        |
| -------------- | ---------------- |
| Pole (naive)   | O(V²)            |
| Binary heap    | O((V + E) log V) |
| Fibonacci heap | O(E + V log V)   |

**Priestorová zložitosť:** O(V)

---

### Prečo nefunguje pre záporné váhy?

```cpp
// Príklad grafu so zápornou váhou
// Graf:
// 0 -> 1 (váha 1)
// 0 -> 2 (váha 4)
// 1 -> 2 (váha -5)

// Dijkstra by našiel cestu 0 -> 2 s váhou 4
// Ale kratšia cesta je 0 -> 1 -> 2 s váhou 1 + (-5) = -4
// Dijkstra túto cestu nenájde, lebo už označil vrchol 2 ako "hotový"
```

**Pre záporné váhy použite Bellman-Ford algoritmus!**

---

### Kompilácia a spustenie

```bash
# Kompilácia
g++ -std=c++17 -o dijkstra dijkstra.cpp

# Spustenie
./dijkstra
```

---

### Čo si sa naučil?

- **Dijkstrov algoritmus** nájde najkratšie cesty z jedného vrcholu
- Používa **greedy prístup** s prioritnou frontou
- **Nefunguje** pre záporné váhy
- Časová zložitosť: **O((V + E) log V)**
- Vhodný pre **mapy, navigácie, siete**

---

### Časté chyby a ako sa im vyhnúť

| Chyba | Prečo nastáva | Riešenie |
|-------|---------------|----------|
| Použitie so zápornými váhami | Dijkstra predpokladá nezáporné | Použiť Bellman-Ford pre záporné váhy |
| Nesprávna inicializácia | `dist[start]` nie je 0 | `dist[start] = 0` na začiatku |
| Chýbajúca relaxácia | Neaktualizovanie kratšej cesty | `if (newDist < dist[v]) dist[v] = newDist` |
| Spracovanie zastaraných záznamov | Vo fronte sú duplicitné položky | `if (currentDist > dist[u]) continue;` |
| Integer overflow | `dist[u] + weight` pretečie | Kontrola pred sčítaním alebo `long long` |

**Typické bugs v kóde:**

```cpp
// CHYBA: Zabudnutá inicializácia štartu
vector<int> dist(V, INT_MAX);
// dist[start] = 0;  <- CHÝBA!
pq.push({0, start});  // vkladáme 0, ale dist[start] je stále INT_MAX

// SPRÁVNE:
vector<int> dist(V, INT_MAX);
dist[start] = 0;
pq.push({0, start});
```

```cpp
// CHYBA: Integer overflow pri sčítaní
int newDist = dist[u] + weight;  // ak dist[u] == INT_MAX, pretečie!

// SPRÁVNE: Kontrola pred sčítaním
if (dist[u] == INT_MAX) continue;
int newDist = dist[u] + weight;

// ALEBO: použiť long long
vector<long long> dist(V, LLONG_MAX);
```

```cpp
// CHYBA: Chýbajúca kontrola zastaraných záznamov
auto [currentDist, u] = pq.top();
pq.pop();
// Rovno relaxujeme susedov - aj keď sme tento vrchol už spracovali!

// SPRÁVNE:
auto [currentDist, u] = pq.top();
pq.pop();
if (currentDist > dist[u]) continue;  // zastaraný záznam
```

---

### Tipy na testovanie

**1. Jednoduchý test - priama cesta:**
```cpp
// 0 -> 1 -> 2, váhy 3 a 4
// Očakávané: dist[2] = 7
Graph g(3);
g.addEdge(0, 1, 3);
g.addEdge(1, 2, 4);
auto [dist, pred] = dijkstra(g, 0);
assert(dist[2] == 7);
```

**2. Test kratšej nepriamej cesty:**
```cpp
// Priama: 0->2 s váhou 10
// Nepriama: 0->1->2 s váhami 3+4=7
Graph g(3);
g.addEdge(0, 2, 10);
g.addEdge(0, 1, 3);
g.addEdge(1, 2, 4);
auto [dist, pred] = dijkstra(g, 0);
assert(dist[2] == 7);  // nie 10!
```

**3. Test nedosiahnuteľného vrcholu:**
```cpp
// Vrchol 2 nie je dosiahnuteľný z 0
Graph g(3);
g.addEdge(0, 1, 5);
// žiadna hrana do 2
auto [dist, pred] = dijkstra(g, 0);
assert(dist[2] == INT_MAX);
```

**4. Kontrolný checklist:**
- [ ] Je `dist[start] = 0` na začiatku?
- [ ] Kontrolujem `currentDist > dist[u]` pred spracovaním?
- [ ] Sú všetky váhy nezáporné?
- [ ] Môže dôjsť k integer overflow?

---

### Skús sám - Doplň chýbajúci kód

```cpp
pair<vector<int>, vector<int>> dijkstra_student(const Graph& graph, int start) {
    int V = graph.getV();

    // TODO 1: Akou hodnotou inicializujeme vzdialenosti?
    vector<int> dist(V, _________________________________);
    vector<int> pred(V, -1);

    // TODO 2: Akú vzdialenosť má štartovací vrchol?
    dist[start] = _________________________________;

    priority_queue<pair<int, int>,
                   vector<pair<int, int>>,
                   greater<pair<int, int>>> pq;

    pq.push({0, start});

    while (!pq.empty()) {
        auto [currentDist, u] = pq.top();
        pq.pop();

        // TODO 3: Kedy preskočíme tento záznam?
        if (_________________________________) continue;

        for (auto [v, weight] : graph.getNeighbors(u)) {
            int newDist = currentDist + weight;

            // TODO 4: Kedy aktualizujeme vzdialenosť?
            if (_________________________________) {
                dist[v] = newDist;
                pred[v] = u;
                pq.push({newDist, v});
            }
        }
    }

    return {dist, pred};
}
```

<details>
<summary>Riešenie (klikni pre zobrazenie)</summary>

```cpp
// TODO 1: Nekonečno (maximálna hodnota)
INT_MAX

// TODO 2: Nula - štart je od seba vzdialený 0
0

// TODO 3: Ak máme lepšiu cestu, preskočíme
currentDist > dist[u]

// TODO 4: Ak je nová cesta kratšia
newDist < dist[v]
```
</details>

---

### Praktické úlohy

#### Úloha 3.1: Neorientovaný graf

Uprav implementáciu tak, aby fungovala s neorientovanými grafmi.

**Hint:** Pri `addEdge(u, v, w)` pridaj aj `addEdge(v, u, w)`.

#### Úloha 3.2: Len jedna cesta

Uprav algoritmus tak, aby sa zastavil hneď, ako nájde cestu k zadanému cieľovému vrcholu.

#### Úloha 3.3: Všetky najkratšie cesty

Uprav implementáciu tak, aby našla všetky najkratšie cesty (môže ich byť viac s rovnakou dĺžkou).

**Hint:** Namiesto jedného predchodcu ulož zoznam predchodcov pre každý vrchol.

---

## Úloha 4: Hash Mapy - Rýchle vyhľadávanie

**Čo sa naučíš:** Ako fungujú hash tabuľky a prečo sú také rýchle v C++

### Teória - Čo je Hash Mapa?

**Hash Mapa** (hash table, dictionary) = dátová štruktúra pre rýchle vyhľadávanie párov kľúč-hodnota.

**Princíp:**

1. **Hash funkcia** premení kľúč na index v poli
2. Hodnota sa uloží na tento index
3. Vyhľadávanie, vkladanie, mazanie = O(1) priemerne!

**Analógia:** Slovník - nalistujete slovo podľa prvého písmena (hash), nie postupne od začiatku.

### Vizualizácia - Ako funguje hash mapa

```
Vkladanie: "apple"->5, "banana"->8, "cherry"->12, "date"->3

Hash funkcia: súčet ASCII hodnôt % veľkosť_tabuľky

"apple"  = 97+112+112+108+101 = 530 % 5 = 0
"banana" = 98+97+110+97+110+97 = 609 % 5 = 4
"cherry" = 99+104+101+114+114+121 = 653 % 5 = 3
"date"   = 100+97+116+101 = 414 % 5 = 4  <- KOLÍZIA s "banana"!

Separate Chaining:                    Linear Probing:
+-------+                             +-------+
| 0 | -> ["apple":5]                  | 0 | "apple":5
+-------+                             +-------+
| 1 | -> []                           | 1 | [prázdny]
+-------+                             +-------+
| 2 | -> []                           | 2 | [prázdny]
+-------+                             +-------+
| 3 | -> ["cherry":12]                | 3 | "cherry":12
+-------+                             +-------+
| 4 | -> ["banana":8] -> ["date":3]   | 4 | "banana":8
+-------+                             +-------+
                                      | 5 | "date":3  <- posunuté!
                                      +-------+
```

**Vyhľadávanie "date":**
- Separate Chaining: hash("date")=4, prejdi zoznam na indexe 4
- Linear Probing: hash("date")=4, index 4 má "banana", skús 5 -> nájdené!

---

### Krok za krokom

#### Krok 1: Jednoduchá hash funkcia

```cpp
#include <iostream>
#include <vector>
#include <list>
#include <string>
using namespace std;

/**
 * Jednoduchá hash funkcia pre reťazce.
 * Sčíta ASCII hodnoty znakov a urobí modulo size.
 */
int simpleHash(const string& key, int size) {
    int hashValue = 0;
    for (char c : key) {
        hashValue += static_cast<int>(c);
    }
    int index = hashValue % size;
    cout << "   Hash(\"" << key << "\") = "
         << hashValue << " % " << size << " = " << index << endl;
    return index;
}
```

---

#### Krok 2: Riešenie kolízií - Separate Chaining

```cpp
/**
 * Hash mapa s riešením kolízií pomocou separate chaining.
 * Každý slot obsahuje linked list (zoznam) párov.
 */
template<typename K, typename V>
class HashMapChaining {
private:
    int size;
    int count;
    vector<list<pair<K, V>>> table;  // Každý slot = linked list

    int hash(const K& key) {
        // Pre string
        if constexpr (is_same_v<K, string>) {
            int hashValue = 0;
            for (char c : key) {
                hashValue += static_cast<int>(c);
            }
            return hashValue % size;
        }
        // Pre int
        else {
            return key % size;
        }
    }

public:
    HashMapChaining(int tableSize = 10) : size(tableSize), count(0) {
        table.resize(size);
        cout << "Vytvorena hash mapa s velkostou " << size << endl;
    }

    /**
     * Vlož pár (kľúč, hodnota).
     */
    void put(const K& key, const V& value) {
        int index = hash(key);

        // Skontroluj, či kľúč už existuje
        for (auto& [k, v] : table[index]) {
            if (k == key) {
                V oldValue = v;
                v = value;
                cout << "   [~] Aktualizovane: '" << key << "' na indexe "
                     << index << " (" << oldValue << " -> " << value << ")" << endl;
                return;
            }
        }

        // Pridaj nový pár
        table[index].push_back({key, value});
        count++;
        int collisions = table[index].size() - 1;
        cout << "   [+] Pridane: '" << key << "': " << value
             << " na index " << index << " (kolizie: " << collisions << ")" << endl;
    }

    /**
     * Získaj hodnotu pre kľúč.
     */
    V* get(const K& key) {
        int index = hash(key);

        // Prehľadaj zoznam na danom indexe
        for (auto& [k, v] : table[index]) {
            if (k == key) {
                cout << "   [*] Najdene: '" << key << "' = "
                     << v << " na indexe " << index << endl;
                return &v;
            }
        }

        cout << "   [-] Kluc '" << key << "' neexistuje" << endl;
        return nullptr;
    }

    /**
     * Zmaž pár s daným kľúčom.
     */
    bool remove(const K& key) {
        int index = hash(key);

        auto& bucket = table[index];
        for (auto it = bucket.begin(); it != bucket.end(); ++it) {
            if (it->first == key) {
                bucket.erase(it);
                count--;
                cout << "   [x] Zmazane: '" << key << "' z indexu " << index << endl;
                return true;
            }
        }

        cout << "   [-] Kluc '" << key << "' neexistuje" << endl;
        return false;
    }

    /**
     * Zobraz celú hash tabuľku.
     */
    void display() {
        cout << "\nStav hash tabulky:" << endl;
        for (int i = 0; i < size; i++) {
            if (!table[i].empty()) {
                cout << "   Index " << i << ": [";
                bool first = true;
                for (const auto& [k, v] : table[i]) {
                    if (!first) cout << ", ";
                    cout << "'" << k << "': " << v;
                    first = false;
                }
                cout << "]" << endl;
            } else {
                cout << "   Index " << i << ": []" << endl;
            }
        }
        cout << "Celkovy pocet prvkov: " << count << endl << endl;
    }

    int getCount() const { return count; }
};
```

---

#### Krok 3: Príklad použitia

```cpp
int main() {
    cout << "============================================================" << endl;
    cout << "HASH MAPA - Separate Chaining" << endl;
    cout << "============================================================" << endl;
    cout << endl;

    // Vytvor hash mapu
    HashMapChaining<string, int> hm(5);
    cout << endl;

    // Vkladanie
    cout << "Vkladanie prvkov:" << endl;
    hm.put("apple", 5);
    hm.put("banana", 8);
    hm.put("cherry", 12);
    hm.put("date", 3);
    hm.put("elderberry", 15);

    hm.display();

    // Vyhľadávanie
    cout << "Vyhladavanie:" << endl;
    hm.get("apple");
    hm.get("cherry");
    hm.get("orange");
    cout << endl;

    // Aktualizácia
    cout << "Aktualizacia:" << endl;
    hm.put("apple", 10);  // Aktualizuj existujúci kľúč
    hm.display();

    // Mazanie
    cout << "Mazanie:" << endl;
    hm.remove("banana");
    hm.display();

    cout << "============================================================" << endl;

    return 0;
}
```

---

#### Krok 4: Riešenie kolízií - Linear Probing

```cpp
/**
 * Hash mapa s riešením kolízií pomocou linear probing.
 * Pri kolízii hľadá najbližší voľný slot.
 */
template<typename K, typename V>
class HashMapLinearProbing {
private:
    struct Entry {
        K key;
        V value;
        bool occupied;
        bool deleted;

        Entry() : occupied(false), deleted(false) {}
        Entry(K k, V v) : key(k), value(v), occupied(true), deleted(false) {}
    };

    int size;
    int count;
    vector<Entry> table;

    int hash(const K& key) {
        if constexpr (is_same_v<K, string>) {
            int hashValue = 0;
            for (char c : key) {
                hashValue += static_cast<int>(c);
            }
            return hashValue % size;
        } else {
            return key % size;
        }
    }

    int probe(int index) {
        return (index + 1) % size;
    }

public:
    HashMapLinearProbing(int tableSize = 10) : size(tableSize), count(0) {
        table.resize(size);
        cout << "Vytvorena hash mapa (Linear Probing) s velkostou "
             << size << endl;
    }

    bool put(const K& key, const V& value) {
        if (count >= size) {
            cout << "   [-] Hash mapa je plna!" << endl;
            return false;
        }

        int index = hash(key);
        int originalIndex = index;
        int probes = 0;

        while (table[index].occupied && !table[index].deleted) {
            // Ak existuje, aktualizuj
            if (table[index].key == key) {
                V oldValue = table[index].value;
                table[index].value = value;
                cout << "   [~] Aktualizovane: '" << key << "' na indexe "
                     << index << " (" << oldValue << " -> " << value << ")" << endl;
                return true;
            }

            // Linear probing
            index = probe(index);
            probes++;

            // Kontrola zacyklenia
            if (index == originalIndex) {
                cout << "   [-] Hash mapa je plna!" << endl;
                return false;
            }
        }

        // Vlož na nájdený voľný slot
        table[index] = Entry(key, value);
        count++;

        if (probes > 0) {
            cout << "   [+] Pridane: '" << key << "': " << value
                 << " na index " << index << " (po " << probes << " probes)" << endl;
        } else {
            cout << "   [+] Pridane: '" << key << "': " << value
                 << " na index " << index << endl;
        }
        return true;
    }

    V* get(const K& key) {
        int index = hash(key);
        int originalIndex = index;
        int probes = 0;

        while (table[index].occupied || table[index].deleted) {
            if (table[index].occupied && !table[index].deleted
                && table[index].key == key) {
                cout << "   [*] Najdene: '" << key << "' = "
                     << table[index].value << " na indexe " << index
                     << " (po " << probes << " probes)" << endl;
                return &table[index].value;
            }

            index = probe(index);
            probes++;

            if (index == originalIndex) break;
        }

        cout << "   [-] Kluc '" << key << "' neexistuje" << endl;
        return nullptr;
    }

    void display() {
        cout << "\nStav hash tabulky:" << endl;
        for (int i = 0; i < size; i++) {
            if (table[i].occupied && !table[i].deleted) {
                cout << "   Index " << i << ": '" << table[i].key
                     << "': " << table[i].value << endl;
            } else {
                cout << "   Index " << i << ": [prazdny]" << endl;
            }
        }
        cout << "Celkovy pocet prvkov: " << count << endl << endl;
    }
};
```

---

### Časová zložitosť

| Operácia     | Priemer | Najhorší prípad |
| ------------ | ------- | --------------- |
| Vyhľadávanie | O(1)    | O(n)            |
| Vkladanie    | O(1)    | O(n)            |
| Mazanie      | O(1)    | O(n)            |

**Load Factor** = n / size (pomer zaplnenosti)

- Ak > 0.7, treba tabuľku zväčšiť (rehashing)

---

### C++ STL - `std::unordered_map`

C++ už obsahuje hotovú implementáciu hash mapy:

```cpp
#include <unordered_map>

int main() {
    // Vytvorenie hash mapy
    unordered_map<string, int> mp;

    // Vkladanie
    mp["apple"] = 5;
    mp["banana"] = 8;
    mp.insert({"cherry", 12});

    // Vyhľadávanie
    if (mp.find("apple") != mp.end()) {
        cout << "apple = " << mp["apple"] << endl;
    }

    // Iterácia
    for (const auto& [key, value] : mp) {
        cout << key << ": " << value << endl;
    }

    // Mazanie
    mp.erase("banana");

    // Veľkosť
    cout << "Pocet prvkov: " << mp.size() << endl;

    return 0;
}
```

---

### Kompilácia a spustenie

```bash
# Kompilácia
g++ -std=c++17 -o hashmap hashmap.cpp

# Spustenie
./hashmap
```

---

### Čo si sa naučil?

- **Hash mapa** umožňuje O(1) vyhľadávanie
- **Hash funkcia** premení kľúč na index
- **Separate chaining** = zoznamy v slotoch
- **Linear probing** = hľadanie voľného slotu
- **Load factor** určuje, kedy zväčšiť tabuľku
- C++ má hotovú implementáciu: `std::unordered_map`

---

### Časté chyby a ako sa im vyhnúť

| Chyba | Prečo nastáva | Riešenie |
|-------|---------------|----------|
| Zlá hash funkcia | Veľa kolízií, degradácia na O(n) | Použiť overenú hash funkciu |
| Neošetrený load factor | Tabuľka sa zaplní, výkon klesá | Rehashing keď load factor > 0.7 |
| Linear probing clustering | Dlhé reťazce obsadených slotov | Použiť quadratic probing alebo double hashing |
| Mazanie v linear probing | Narušenie vyhľadávania | Použiť "tombstone" (deleted flag) |
| Záporný index | Modulo záporného čísla | `((hash % size) + size) % size` |

**Typické bugs v kóde:**

```cpp
// CHYBA: Záporný výsledok modulo
int hash(const string& key) {
    int hashValue = 0;
    for (char c : key) {
        hashValue += c;  // môže pretiecť do záporných čísel!
    }
    return hashValue % size;  // môže byť záporné!
}

// SPRÁVNE: Zabezpečiť kladný výsledok
int hash(const string& key) {
    int hashValue = 0;
    for (char c : key) {
        hashValue += static_cast<unsigned char>(c);
    }
    return ((hashValue % size) + size) % size;  // vždy kladné
}
```

```cpp
// CHYBA: Mazanie v linear probing bez tombstone
bool remove(const K& key) {
    int index = hash(key);
    while (table[index].occupied) {
        if (table[index].key == key) {
            table[index].occupied = false;  // PROBLÉM!
            return true;
        }
        index = (index + 1) % size;
    }
    return false;
}
// Po zmazaní sa "zlomí" reťazec a niektoré kľúče sa nenájdu!

// SPRÁVNE: Použiť deleted flag
bool remove(const K& key) {
    int index = hash(key);
    while (table[index].occupied || table[index].deleted) {
        if (table[index].occupied && table[index].key == key) {
            table[index].occupied = false;
            table[index].deleted = true;  // tombstone
            return true;
        }
        index = (index + 1) % size;
    }
    return false;
}
```

---

### Tipy na testovanie

**1. Test kolízií:**
```cpp
// Vytvor kľúče s rovnakým hashom
HashMapChaining<int, string> hm(10);
hm.put(5, "five");    // hash = 5
hm.put(15, "fifteen"); // hash = 5 (kolízia)
hm.put(25, "twentyfive"); // hash = 5 (kolízia)

assert(*hm.get(5) == "five");
assert(*hm.get(15) == "fifteen");
assert(*hm.get(25) == "twentyfive");
```

**2. Test aktualizácie existujúceho kľúča:**
```cpp
hm.put("key", 100);
hm.put("key", 200);  // aktualizácia, nie nový záznam
assert(*hm.get("key") == 200);
assert(hm.getCount() == 1);  // stále len 1 záznam
```

**3. Test mazania a následného vyhľadávania (linear probing):**
```cpp
HashMapLinearProbing<int, string> hm(10);
hm.put(5, "A");
hm.put(15, "B");  // kolízia, uložené na index 6
hm.put(25, "C");  // kolízia, uložené na index 7

hm.remove(15);    // zmaž prostredný

// "C" musí byť stále nájditeľné!
assert(hm.get(25) != nullptr);
```

**4. Kontrolný checklist:**
- [ ] Je hash funkcia deterministická (rovnaký vstup = rovnaký výstup)?
- [ ] Ošetrujem prípad plnej tabuľky?
- [ ] Funguje mazanie správne (tombstones)?
- [ ] Je load factor pod kontrolou?

---

### Skús sám - Doplň chýbajúci kód

```cpp
template<typename K, typename V>
class SimpleHashMap {
private:
    vector<list<pair<K, V>>> table;
    int size;

    int hash(const K& key) {
        // TODO 1: Implementuj jednoduchú hash funkciu pre int
        // Hint: modulo veľkosťou tabuľky
        return _________________________________;
    }

public:
    SimpleHashMap(int s) : size(s) {
        table.resize(size);
    }

    void put(const K& key, const V& value) {
        int index = hash(key);

        // TODO 2: Skontroluj, či kľúč už existuje a aktualizuj
        for (auto& [k, v] : table[index]) {
            if (_________________________________) {
                v = value;
                return;
            }
        }

        // TODO 3: Pridaj nový pár na správny index
        _________________________________;
    }

    V* get(const K& key) {
        int index = hash(key);

        // TODO 4: Nájdi hodnotu pre daný kľúč
        for (auto& [k, v] : table[index]) {
            if (k == key) {
                return _________________________________;
            }
        }
        return nullptr;
    }
};
```

<details>
<summary>Riešenie (klikni pre zobrazenie)</summary>

```cpp
// TODO 1: Hash funkcia
return key % size;

// TODO 2: Kontrola existujúceho kľúča
if (k == key)

// TODO 3: Pridanie nového páru
table[index].push_back({key, value});

// TODO 4: Vrátenie pointera na hodnotu
return &v;
```
</details>

---

### Praktické úlohy

#### Úloha 4.1: Quadratic Probing

Implementuj hash mapu s quadratic probing namiesto linear:

- Probe sekvencia: i, i+1², i+2², i+3², ...

#### Úloha 4.2: Rehashing

Implementuj automatické zväčšenie tabuľky, keď load factor > 0.7:

- Vytvor novú väčšiu tabuľku (2× veľkosť)
- Presuň všetky prvky (rehashovanie)

#### Úloha 4.3: Vlastná hash funkcia

Implementuj lepšiu hash funkciu pre stringy:

- Použite polynomial rolling hash
- Napríklad: hash = s[0] _ 31^(n-1) + s[1] _ 31^(n-2) + ... + s[n-1]

---

# ČASŤ 2: STROMOVÉ ŠTRUKTÚRY

## Úvod: Od Linked Listu k Stromu

**Prečo táto sekcia?** Ak ste robili linked listy, máte perfektný základ pre pochopenie stromov. Strom je vlastne **rozšírenie linked listu** - namiesto jedného "next" ukazovateľa má uzol viac ukazovateľov na potomkov.

---

### Čo už vieš z Linked Listu

Linked list používa uzol s jedným ukazovateľom:

```cpp
// Linked List uzol - poznáš toto
struct ListNode {
    int data;           // Hodnota
    ListNode* next;     // Ukazovateľ na ďalší uzol
};
```

**Vizualizácia Linked Listu:**
```
HEAD
  ↓
[10] → [20] → [30] → [40] → nullptr

Každý uzol "vie" len o jednom nasledovníkovi.
```

**Kľúčové vlastnosti:**
- Jeden smer (next)
- Lineárna štruktúra
- Prístup k n-tému prvku: O(n)
- Vkladanie na začiatok: O(1)

---

### Strom = Linked List s viacerými "next"

**Kľúčový insight:** Strom vznikne, keď namiesto jedného `next` má uzol **viac ukazovateľov** na potomkov.

```cpp
// Linked List uzol
struct ListNode {
    int data;
    ListNode* next;      // 1 ukazovateľ
};

// Binárny strom uzol - má 2 ukazovatele namiesto 1
struct TreeNode {
    int data;
    TreeNode* left;      // Ukazovateľ na ľavého potomka
    TreeNode* right;     // Ukazovateľ na pravého potomka
};

// Všeobecný strom - môže mať ľubovoľný počet potomkov
struct GeneralTreeNode {
    int data;
    vector<GeneralTreeNode*> children;  // Zoznam potomkov
};
```

**Vizuálne porovnanie:**

```
LINKED LIST (1 next):              BINÁRNY STROM (2 next):

[10] → [20] → [30] → [40]                  [10]
                                          /    \
                                       [20]    [30]
                                       /  \       \
                                    [40]  [50]   [60]

Linked list je vlastne          Strom sa "rozvetvuje"
"strom" kde každý uzol          do viacerých smerov
má max 1 dieťa!
```

---

### Prečo potrebujeme stromy? (Linked List nestačí)

| Operácia | Linked List | Binárny vyhľadávací strom |
|----------|-------------|---------------------------|
| Vyhľadávanie | O(n) - musíš prejsť všetko | O(log n) - polovica v každom kroku |
| Vkladanie (zoradené) | O(n) - nájsť miesto | O(log n) |
| Min/Max | O(n) | O(log n) alebo O(1) |

**Príklad - Hľadanie čísla 75:**

```
Linked List (musíš prejsť všetko):
[10] → [25] → [30] → [50] → [60] → [75] → [80]
  ↓      ↓      ↓      ↓      ↓      ↓
  1      2      3      4      5      6 krokov

Binárny vyhľadávací strom:
          [50]           50 < 75? Áno → idem VPRAVO
         /    \
      [25]    [75]       75 = 75? NÁJDENÉ!
      /  \    /  \
   [10][30][60][80]

   Len 2 kroky!
```

**Analógia z reálneho života:**

- **Linked List** = hľadanie v nezoradenom zozname mien
- **Strom** = telefónny zoznam / slovník - otvoríš uprostred a vieš či ísť dopredu alebo dozadu

---

### Základné pojmy stromov (Slovník)

```
                    [A]  ← KOREŇ (root) - jediný uzol bez rodiča
                   / | \
                  /  |  \
               [B]  [C]  [D]  ← DETI (children) uzla A
               /\        |       A je ich RODIČ (parent)
              /  \       |       B, C, D sú SÚRODENCI (siblings)
           [E]  [F]     [G]
           /
         [H]  ← LIST (leaf) - uzol bez detí

POJMY:
• Koreň (root): Vrchný uzol, nemá rodiča. Tu: A
• List (leaf): Uzol bez detí. Tu: F, C, G, H
• Vnútorný uzol: Má aspoň jedno dieťa. Tu: A, B, D, E
• Rodič (parent): Uzol priamo nad. Rodič E je B.
• Dieťa (child): Uzol priamo pod. Deti A sú B, C, D.
• Súrodenci (siblings): Uzly s rovnakým rodičom. B, C, D sú súrodenci.
• Predok (ancestor): Uzol na ceste ku koreňu. Predkovia H sú E, B, A.
• Potomok (descendant): Uzol v podstrome. Potomkovia B sú E, F, H.
```

---

### Hĺbka vs Výška (DÔLEŽITÉ!)

```
                    [A]  ← Hĺbka 0
                   / | \
               [B]  [C]  [D]  ← Hĺbka 1
               /\        |
           [E]  [F]     [G]  ← Hĺbka 2
           /
         [H]  ← Hĺbka 3

HĹBKA (depth) uzla = vzdialenosť od KOREŇA (zhora dole)
• Hĺbka A = 0
• Hĺbka B = 1
• Hĺbka H = 3

VÝŠKA (height) uzla = vzdialenosť k NAJHLBŠIEMU listu (zdola hore)
• Výška H = 0 (je list)
• Výška E = 1
• Výška B = 2
• Výška A = 3 (výška celého stromu)

VÝŠKA STROMU = výška koreňa = najdlhšia cesta od koreňa k listu
Tu: Výška stromu = 3
```

**Pamätačka:**
- **Hĺbka** = "ako hlboko som PONORENÝ od hladiny (koreňa)"
- **Výška** = "ako VYSOKO siaha môj podstrom"

---

### Typy stromov - Prehľad

```
1. VŠEOBECNÝ STROM          2. BINÁRNY STROM           3. BINÁRNY VYHĽADÁVACÍ
   (ľubovoľný počet detí)      (max 2 deti)               STROM (BST)

        [A]                        [A]                        [50]
       /|\ \                      /   \                      /    \
     [B][C][D][E]               [B]   [C]                 [30]    [70]
     /\                         / \     \                 /  \    /  \
   [F][G]                     [D] [E]   [F]            [20][40][60][80]

   Súborový systém           Výrazy, rozhodnutia       Hodnoty zoradené!
   Organizačná štruktúra                                left < root < right


4. VYVÁŽENÝ STROM           5. ÚPLNÝ BINÁRNY           6. B-STROM
   (AVL, Red-Black)            STROM                      (pre databázy)

       [50]                       [A]                    [10|20|30]
      /    \                    /     \                  /  |  |  \
   [30]    [70]               [B]     [C]              [5][15][25][35]
   /  \    /  \              / \     / \
 [20][40][60][80]          [D][E]  [F][G]            Viac kľúčov v uzle

 Garantuje O(log n)        Všetky úrovne plné        Menej úrovní = rýchlejšie
```

---

### Od Linked Listu k Stromu - Kód

**Linked List (ktorý poznáš):**

```cpp
#include <iostream>
using namespace std;

// Linked List - jeden ukazovateľ
struct ListNode {
    int data;
    ListNode* next;

    ListNode(int val) : data(val), next(nullptr) {}
};

// Pridanie na koniec linked listu
void append(ListNode*& head, int val) {
    ListNode* newNode = new ListNode(val);

    if (head == nullptr) {
        head = newNode;
        return;
    }

    ListNode* current = head;
    while (current->next != nullptr) {
        current = current->next;
    }
    current->next = newNode;
}

// Výpis linked listu
void printList(ListNode* head) {
    ListNode* current = head;
    while (current != nullptr) {
        cout << current->data;
        if (current->next) cout << " -> ";
        current = current->next;
    }
    cout << " -> nullptr" << endl;
}
```

**Binárny strom (nový koncept):**

```cpp
// Binárny strom - DVA ukazovatele
struct TreeNode {
    int data;
    TreeNode* left;    // Namiesto "next" máme "left" a "right"
    TreeNode* right;

    TreeNode(int val) : data(val), left(nullptr), right(nullptr) {}
};

// Výpis stromu (in-order - zoradené)
void printTree(TreeNode* root) {
    if (root == nullptr) return;

    printTree(root->left);        // Najprv ľavý podstrom
    cout << root->data << " ";    // Potom aktuálny uzol
    printTree(root->right);       // Nakoniec pravý podstrom
}

// Hlavný rozdiel: REKURZIA je prirodzená pre stromy!
```

**Porovnanie:**

```cpp
int main() {
    // === LINKED LIST ===
    ListNode* list = nullptr;
    append(list, 10);
    append(list, 20);
    append(list, 30);

    cout << "Linked List: ";
    printList(list);
    // Výstup: 10 -> 20 -> 30 -> nullptr

    // === BINÁRNY STROM ===
    //        10
    //       /  \
    //      5    15
    //     / \
    //    3   7

    TreeNode* tree = new TreeNode(10);
    tree->left = new TreeNode(5);
    tree->right = new TreeNode(15);
    tree->left->left = new TreeNode(3);
    tree->left->right = new TreeNode(7);

    cout << "Strom (in-order): ";
    printTree(tree);
    cout << endl;
    // Výstup: 3 5 7 10 15 (zoradené!)

    return 0;
}
```

---

### Prečo rekurzia a stromy idú spolu

**Linked List - zvyčajne iterácia (while cyklus):**
```cpp
void printList(ListNode* head) {
    ListNode* current = head;
    while (current != nullptr) {    // Iterácia
        cout << current->data << " ";
        current = current->next;
    }
}
```

**Strom - prirodzene rekurzia:**
```cpp
void printTree(TreeNode* root) {
    if (root == nullptr) return;    // Základný prípad

    printTree(root->left);          // Rekurzívne volanie (ľavý podstrom)
    cout << root->data << " ";      // Spracovanie uzla
    printTree(root->right);         // Rekurzívne volanie (pravý podstrom)
}
```

**Prečo rekurzia?**
- Strom má **vetvy** - potrebuješ sa vrátiť a ísť inou cestou
- Každý **podstrom** je tiež strom - perfektné pre rekurziu
- Iterácia by vyžadovala **explicitný stack** (simulovať rekurziu)

```
Rekurzia na strome:

        [10]
       /    \
     [5]    [15]     Volanie: printTree(10)
                     → printTree(5)  → printTree(3) → return
                                     → print 5
                                     → printTree(7) → return
                     → print 10
                     → printTree(15) → return
```

---

### Zhrnutie: Linked List vs Strom

| Vlastnosť | Linked List | Binárny strom |
|-----------|-------------|---------------|
| Počet ukazovateľov | 1 (next) | 2 (left, right) |
| Štruktúra | Lineárna | Hierarchická |
| Prístup k prvku | O(n) | O(log n) pri BST |
| Prirodzený prístup | Iterácia (while) | Rekurzia |
| Použitie | Zoznamy, fronty, stacky | Vyhľadávanie, hierarchie |

**Kľúčové pochopenie:**
1. **Strom = linked list s viacerými next ukazovateľmi**
2. **Rekurzia je prirodzená** pre stromy (každý podstrom je strom)
3. **BST umožňuje O(log n)** vyhľadávanie (vľavo menšie, vpravo väčšie)

---

### Cvičenie: Over si pochopenie

**Otázka 1:** Koľko ukazovateľov má uzol binárneho stromu?
<details><summary>Odpoveď</summary>
Dva: left a right (oproti jednému "next" v linked liste)
</details>

**Otázka 2:** Prečo je vyhľadávanie v BST O(log n)?
<details><summary>Odpoveď</summary>
Lebo v každom kroku eliminujeme polovicu možností (ideme len vľavo ALEBO vpravo).
</details>

**Otázka 3:** Čo je výška stromu?
<details><summary>Odpoveď</summary>
Najdlhšia cesta od koreňa k listu (počet hrán).
</details>

**Otázka 4:** Nakresli binárny strom pre čísla: 50, 30, 70, 20, 40
<details><summary>Odpoveď</summary>

```
       [50]
      /    \
   [30]    [70]
   /  \
[20]  [40]
```
</details>

---

**Teraz si pripravený na Úlohu 5: Binárny strom!**

---

## Úloha 5: Binárny strom - Základná stromová štruktúra

**Čo sa naučíš:** Ako reprezentovať a pracovať s binárnym stromom v C++

> **Prerekvizity:** [Úvod: Od Linked Listu k Stromu](#úvod-od-linked-listu-k-stromu) **Prečítaj si úvod ak si nerobil stromy!**
>
> **Kam ďalej:** [DFS/BFS (prehľadávanie)](#úloha-9-dfs---prehľadávanie-do-hĺbky) → [BST (vyhľadávanie)](#úloha-6-binárny-vyhľadávací-strom-bst---efektívne-vyhľadávanie) → [AVL (vyvažovanie)](#úloha-7-avl-stromy---samovyvažujúce-binárne-stromy)

### Teória - Čo je to binárny strom?

**Binárny strom** = hierarchická dátová štruktúra, kde každý uzol má najviac **dvoch potomkov** (ľavý a pravý).

**Základné pojmy:**
- **Koreň (root)** = vrchný uzol stromu
- **List (leaf)** = uzol bez potomkov
- **Vnútorný uzol** = uzol s aspoň jedným potomkom
- **Hĺbka uzla** = vzdialenosť od koreňa
- **Výška stromu** = maximálna hĺbka

**Analógia:** Rodokmeň - každý človek má najviac dvoch rodičov, ktorých môžeme sledovať späť ku koreňu.

### Vizualizácia - Anatómia binárneho stromu

```
                    [10]  ← Koreň (root), hĺbka 0
                   /    \
                 /        \
              [5]          [15]  ← Vnútorné uzly, hĺbka 1
             /   \        /    \
           [3]   [7]    [12]   [20]  ← hĺbka 2
           /       \             \
         [1]       [6]           [25]  ← Listy (leaves), hĺbka 3

Výška stromu: 3
Počet uzlov: 10
Počet listov: 4 (uzly 1, 6, 12, 25... vlastne 12 má rodiča, tak listy sú 1, 6, 25)
```

**Typy binárnych stromov:**

```
Plný (Full):           Kompletný:            Degenerovaný:
      [A]                   [A]                   [A]
     /   \                 /   \                    \
   [B]   [C]             [B]   [C]                  [B]
   / \   / \            /  \    /                     \
 [D] [E][F][G]        [D] [E] [F]                     [C]
                                                        \
Každý uzol má         Všetky úrovne plné              [D]
0 alebo 2 deti        okrem poslednej           (vlastne linked list)
```

---

### Krok za krokom

#### Krok 1: Štruktúra uzla

```cpp
#include <iostream>
#include <queue>
#include <stack>
using namespace std;

/**
 * Uzol binárneho stromu.
 * Každý uzol obsahuje hodnotu a ukazovatele na ľavého a pravého potomka.
 */
template<typename T>
struct TreeNode {
    T data;              // Hodnota uzla
    TreeNode* left;      // Ukazovateľ na ľavého potomka
    TreeNode* right;     // Ukazovateľ na pravého potomka

    // Konštruktor
    TreeNode(T value) : data(value), left(nullptr), right(nullptr) {
        cout << "   Vytvoreny uzol s hodnotou: " << value << endl;
    }

    // Destruktor
    ~TreeNode() {
        // Rekurzívne zmazanie potomkov sa robí v triede BinaryTree
    }

    // Kontrola, či je uzol list
    bool isLeaf() const {
        return left == nullptr && right == nullptr;
    }
};
```

---

#### Krok 2: Trieda Binárny strom

```cpp
/**
 * Binárny strom s základnými operáciami.
 */
template<typename T>
class BinaryTree {
private:
    TreeNode<T>* root;

    /**
     * Rekurzívne zmazanie stromu (post-order).
     */
    void destroyTree(TreeNode<T>* node) {
        if (node == nullptr) return;

        destroyTree(node->left);
        destroyTree(node->right);
        delete node;
    }

    /**
     * Rekurzívny výpočet výšky stromu.
     */
    int heightHelper(TreeNode<T>* node) const {
        if (node == nullptr) return -1;  // Prázdny strom má výšku -1

        int leftHeight = heightHelper(node->left);
        int rightHeight = heightHelper(node->right);

        return 1 + max(leftHeight, rightHeight);
    }

    /**
     * Rekurzívny výpočet počtu uzlov.
     */
    int sizeHelper(TreeNode<T>* node) const {
        if (node == nullptr) return 0;

        return 1 + sizeHelper(node->left) + sizeHelper(node->right);
    }

    /**
     * Rekurzívny výpočet počtu listov.
     */
    int countLeavesHelper(TreeNode<T>* node) const {
        if (node == nullptr) return 0;
        if (node->isLeaf()) return 1;

        return countLeavesHelper(node->left) + countLeavesHelper(node->right);
    }

    /**
     * Pomocná funkcia na vizualizáciu stromu.
     */
    void printTreeHelper(TreeNode<T>* node, string prefix, bool isLeft) const {
        if (node == nullptr) return;

        cout << prefix;
        cout << (isLeft ? "├── " : "└── ");
        cout << node->data << endl;

        printTreeHelper(node->left, prefix + (isLeft ? "│   " : "    "), true);
        printTreeHelper(node->right, prefix + (isLeft ? "│   " : "    "), false);
    }

public:
    BinaryTree() : root(nullptr) {
        cout << "Vytvoreny prazdny binarny strom" << endl;
    }

    ~BinaryTree() {
        cout << "Mazem binarny strom..." << endl;
        destroyTree(root);
    }

    // Getter pre koreň (potrebný pre traversal algoritmy)
    TreeNode<T>* getRoot() const { return root; }

    /**
     * Manuálne vytvorenie stromu pre demonštráciu.
     */
    void buildSampleTree() {
        cout << "\nVytvaram ukazkovy strom:" << endl;

        root = new TreeNode<T>(10);
        root->left = new TreeNode<T>(5);
        root->right = new TreeNode<T>(15);
        root->left->left = new TreeNode<T>(3);
        root->left->right = new TreeNode<T>(7);
        root->right->left = new TreeNode<T>(12);
        root->right->right = new TreeNode<T>(20);
        root->left->left->left = new TreeNode<T>(1);
        root->left->right->right = new TreeNode<T>(6);
        root->right->right->right = new TreeNode<T>(25);

        cout << "Strom vytvoreny." << endl;
    }

    /**
     * Vráti výšku stromu.
     */
    int height() const {
        return heightHelper(root);
    }

    /**
     * Vráti počet uzlov v strome.
     */
    int size() const {
        return sizeHelper(root);
    }

    /**
     * Vráti počet listov v strome.
     */
    int countLeaves() const {
        return countLeavesHelper(root);
    }

    /**
     * Kontrola, či je strom prázdny.
     */
    bool isEmpty() const {
        return root == nullptr;
    }

    /**
     * Vizualizácia stromu v konzole.
     */
    void printTree() const {
        cout << "\nVizualizacia stromu:" << endl;
        if (root == nullptr) {
            cout << "(prazdny strom)" << endl;
            return;
        }
        printTreeHelper(root, "", false);
    }

    /**
     * Výpis štatistík stromu.
     */
    void printStats() const {
        cout << "\nStatistiky stromu:" << endl;
        cout << "   Vyska: " << height() << endl;
        cout << "   Pocet uzlov: " << size() << endl;
        cout << "   Pocet listov: " << countLeaves() << endl;
        cout << "   Je prazdny: " << (isEmpty() ? "ano" : "nie") << endl;
    }
};
```

---

#### Krok 3: Hlavný program - príklad použitia

```cpp
int main() {
    cout << "============================================================" << endl;
    cout << "BINARNY STROM - Zakladna struktura" << endl;
    cout << "============================================================" << endl;

    BinaryTree<int> tree;
    tree.buildSampleTree();

    tree.printTree();
    tree.printStats();

    cout << "============================================================" << endl;

    return 0;
}
```

**Očakávaný výstup:**

```
============================================================
BINARNY STROM - Zakladna struktura
============================================================
Vytvoreny prazdny binarny strom

Vytvaram ukazkovy strom:
   Vytvoreny uzol s hodnotou: 10
   Vytvoreny uzol s hodnotou: 5
   Vytvoreny uzol s hodnotou: 15
   Vytvoreny uzol s hodnotou: 3
   Vytvoreny uzol s hodnotou: 7
   Vytvoreny uzol s hodnotou: 12
   Vytvoreny uzol s hodnotou: 20
   Vytvoreny uzol s hodnotou: 1
   Vytvoreny uzol s hodnotou: 6
   Vytvoreny uzol s hodnotou: 25
Strom vytvoreny.

Vizualizacia stromu:
└── 10
    ├── 5
    │   ├── 3
    │   │   ├── 1
    │   │   └── (null)
    │   └── 7
    │       ├── (null)
    │       └── 6
    └── 15
        ├── 12
        └── 20
            └── 25

Statistiky stromu:
   Vyska: 3
   Pocet uzlov: 10
   Pocet listov: 4
   Je prazdny: nie
============================================================
```

---

### Časová zložitosť

| Operácia | Zložitosť |
|----------|-----------|
| Výška stromu | O(n) |
| Počet uzlov | O(n) |
| Počet listov | O(n) |
| Prístup ku koreňu | O(1) |

**Priestorová zložitosť:** O(n) pre uloženie n uzlov + O(h) pre rekurzívny stack (h = výška)

---

### Čo si sa naučil?

- **Binárny strom** je hierarchická štruktúra s max. 2 potomkami na uzol
- Uzol obsahuje **dáta** a **ukazovatele** na potomkov
- **Výška** = najdlhšia cesta od koreňa k listu
- **List** = uzol bez potomkov
- Rekurzia je prirodzený spôsob práce so stromami

---

### Časté chyby a ako sa im vyhnúť

| Chyba | Prečo nastáva | Riešenie |
|-------|---------------|----------|
| Memory leak | Zabudnuté uvoľnenie uzlov | Implementovať destruktor s rekurzívnym mazaním |
| Segmentation fault | Prístup k nullptr | Vždy kontrolovať `if (node == nullptr)` |
| Nesprávna výška | Prázdny strom má výšku -1 alebo 0? | Dohodnúť sa na konvencii (my používame -1) |
| Stack overflow | Príliš hlboká rekurzia | Pre veľmi hlboké stromy použiť iteratívne riešenie |

---

### Skús sám - Doplň chýbajúci kód

```cpp
template<typename T>
class BinaryTree {
private:
    TreeNode<T>* root;

    // TODO 1: Spočítaj počet uzlov rekurzívne
    int sizeHelper(TreeNode<T>* node) const {
        if (node == nullptr) return _________________________________;

        return _________________________________;
    }

    // TODO 2: Zisti, či strom obsahuje hodnotu
    bool containsHelper(TreeNode<T>* node, T value) const {
        if (node == nullptr) return _________________________________;

        if (node->data == value) return true;

        return _________________________________;
    }

public:
    int size() const { return sizeHelper(root); }
    bool contains(T value) const { return containsHelper(root, value); }
};
```

<details>
<summary>Riešenie (klikni pre zobrazenie)</summary>

```cpp
// TODO 1: Počet uzlov
if (node == nullptr) return 0;
return 1 + sizeHelper(node->left) + sizeHelper(node->right);

// TODO 2: Obsahuje hodnotu
if (node == nullptr) return false;
return containsHelper(node->left, value) || containsHelper(node->right, value);
```
</details>

---

### Praktické úlohy

#### Úloha 5.1: Zrkadlový strom
Implementuj funkciu `mirror()`, ktorá vytvorí zrkadlový obraz stromu (prehodí ľavé a pravé podstromy).

#### Úloha 5.2: Rovnaké stromy
Implementuj funkciu `isEqual(BinaryTree& other)`, ktorá zistí, či sú dva stromy identické.

#### Úloha 5.3: Maximálna hodnota
Implementuj funkciu `findMax()`, ktorá nájde maximálnu hodnotu v strome (nie BST, takže musíš prejsť všetky uzly).

---

## Úloha 6: Binárny vyhľadávací strom (BST) - Efektívne vyhľadávanie

**Čo sa naučíš:** Ako využiť usporiadanie pre rýchle vyhľadávanie v C++

> **Prerekvizity:** [Úloha 5: Binárny strom](#úloha-5-binárny-strom---základná-stromová-štruktúra)
>
> **Súvisiace témy:** [DFS (in-order dáva zoradené hodnoty)](#úloha-9-dfs---prehľadávanie-do-hĺbky) • [AVL (vyvážený BST)](#úloha-7-avl-stromy---samovyvažujúce-binárne-stromy) • [Binárne vyhľadávanie](#úloha-11-binárne-vyhľadávanie---rýchle-hľadanie-v-zoradenom-poli)

### Teória - Čo je BST?

**Binárny vyhľadávací strom (BST)** = binárny strom s pravidlom:
- Všetky hodnoty v **ľavom podstrome** sú **menšie** ako koreň
- Všetky hodnoty v **pravom podstrome** sú **väčšie** ako koreň
- Toto platí **rekurzívne** pre každý uzol

**Analógia:** Telefónny zoznam - mená sú zoradené abecedne, takže vieš, či hľadať vľavo alebo vpravo.

### Vizualizácia - BST vlastnosť

```
Správny BST:                    Nesprávny BST:
       [8]                            [8]
      /   \                          /   \
    [3]   [10]                     [3]   [10]
   /   \     \                    /   \     \
 [1]   [6]   [14]               [1]   [9]   [14]  ← 9 > 8, ale je vľavo!
      /   \   /                      /   \
    [4]   [7][13]                  [4]   [7]

Vlastnosť BST:                  Porušená vlastnosť!
1 < 3 < 4 < 6 < 7 < 8 < 10 < 13 < 14
```

**Vyhľadávanie v BST:**
```
Hľadám hodnotu 6:

       [8]  ← 6 < 8, idem VĽAVO
      /
    [3]  ← 6 > 3, idem VPRAVO
       \
       [6]  ← NÁJDENÉ!

Počet krokov: 3 (log₂8 ≈ 3)
```

---

### Krok za krokom

#### Krok 1: Štruktúra BST

```cpp
#include <iostream>
#include <queue>
using namespace std;

/**
 * Uzol BST.
 */
template<typename T>
struct BSTNode {
    T data;
    BSTNode* left;
    BSTNode* right;

    BSTNode(T value) : data(value), left(nullptr), right(nullptr) {}
};

/**
 * Binárny vyhľadávací strom.
 */
template<typename T>
class BST {
private:
    BSTNode<T>* root;

    /**
     * Rekurzívne vloženie hodnoty.
     */
    BSTNode<T>* insertHelper(BSTNode<T>* node, T value) {
        // Prázdne miesto - vytvor nový uzol
        if (node == nullptr) {
            cout << "   [+] Vkladam: " << value << endl;
            return new BSTNode<T>(value);
        }

        // Rozhodnutie kam ísť
        if (value < node->data) {
            cout << "   " << value << " < " << node->data << ", idem VLAVO" << endl;
            node->left = insertHelper(node->left, value);
        } else if (value > node->data) {
            cout << "   " << value << " > " << node->data << ", idem VPRAVO" << endl;
            node->right = insertHelper(node->right, value);
        } else {
            cout << "   [!] Hodnota " << value << " uz existuje, preskakujem" << endl;
        }

        return node;
    }

    /**
     * Rekurzívne vyhľadávanie hodnoty.
     */
    BSTNode<T>* searchHelper(BSTNode<T>* node, T value, int& steps) const {
        steps++;

        if (node == nullptr) {
            return nullptr;
        }

        cout << "   Krok " << steps << ": Kontrolujem " << node->data;

        if (value == node->data) {
            cout << " -> NAJDENE!" << endl;
            return node;
        } else if (value < node->data) {
            cout << " -> " << value << " < " << node->data << ", idem VLAVO" << endl;
            return searchHelper(node->left, value, steps);
        } else {
            cout << " -> " << value << " > " << node->data << ", idem VPRAVO" << endl;
            return searchHelper(node->right, value, steps);
        }
    }

    /**
     * Nájdi minimálny uzol v podstrome.
     */
    BSTNode<T>* findMin(BSTNode<T>* node) const {
        while (node->left != nullptr) {
            node = node->left;
        }
        return node;
    }

    /**
     * Rekurzívne zmazanie hodnoty.
     */
    BSTNode<T>* deleteHelper(BSTNode<T>* node, T value) {
        if (node == nullptr) {
            cout << "   [-] Hodnota " << value << " neexistuje" << endl;
            return nullptr;
        }

        // Hľadanie uzla na zmazanie
        if (value < node->data) {
            node->left = deleteHelper(node->left, value);
        } else if (value > node->data) {
            node->right = deleteHelper(node->right, value);
        } else {
            // Našli sme uzol na zmazanie
            cout << "   [x] Mazem uzol: " << value << endl;

            // Prípad 1: List (žiadni potomkovia)
            if (node->left == nullptr && node->right == nullptr) {
                cout << "       (list - jednoduche zmazanie)" << endl;
                delete node;
                return nullptr;
            }

            // Prípad 2: Jeden potomok
            if (node->left == nullptr) {
                cout << "       (jeden potomok - prava vetva)" << endl;
                BSTNode<T>* temp = node->right;
                delete node;
                return temp;
            }
            if (node->right == nullptr) {
                cout << "       (jeden potomok - lava vetva)" << endl;
                BSTNode<T>* temp = node->left;
                delete node;
                return temp;
            }

            // Prípad 3: Dva potomkovia
            // Nájdi in-order nasledovníka (minimum v pravom podstrome)
            BSTNode<T>* successor = findMin(node->right);
            cout << "       (dva potomkovia - nahradim s " << successor->data << ")" << endl;
            node->data = successor->data;
            node->right = deleteHelper(node->right, successor->data);
        }

        return node;
    }

    /**
     * In-order traversal (zoradené hodnoty).
     */
    void inorderHelper(BSTNode<T>* node) const {
        if (node == nullptr) return;

        inorderHelper(node->left);
        cout << node->data << " ";
        inorderHelper(node->right);
    }

    /**
     * Rekurzívne mazanie stromu.
     */
    void destroyTree(BSTNode<T>* node) {
        if (node == nullptr) return;
        destroyTree(node->left);
        destroyTree(node->right);
        delete node;
    }

    /**
     * Vizualizácia stromu.
     */
    void printHelper(BSTNode<T>* node, string prefix, bool isLeft) const {
        if (node == nullptr) return;

        cout << prefix << (isLeft ? "├── " : "└── ") << node->data << endl;

        printHelper(node->left, prefix + (isLeft ? "│   " : "    "), true);
        printHelper(node->right, prefix + (isLeft ? "│   " : "    "), false);
    }

public:
    BST() : root(nullptr) {}

    ~BST() {
        destroyTree(root);
    }

    BSTNode<T>* getRoot() const { return root; }

    /**
     * Vlož hodnotu do BST.
     */
    void insert(T value) {
        cout << "\nVkladanie " << value << ":" << endl;
        root = insertHelper(root, value);
    }

    /**
     * Vyhľadaj hodnotu v BST.
     */
    bool search(T value) const {
        cout << "\nHladanie " << value << ":" << endl;
        int steps = 0;
        BSTNode<T>* result = searchHelper(root, value, steps);
        cout << "   Celkovy pocet krokov: " << steps << endl;
        return result != nullptr;
    }

    /**
     * Zmaž hodnotu z BST.
     */
    void remove(T value) {
        cout << "\nMazanie " << value << ":" << endl;
        root = deleteHelper(root, value);
    }

    /**
     * Vypíš zoradené hodnoty (in-order).
     */
    void printSorted() const {
        cout << "\nZoradene hodnoty (in-order): ";
        inorderHelper(root);
        cout << endl;
    }

    /**
     * Vizualizácia stromu.
     */
    void printTree() const {
        cout << "\nVizualizacia BST:" << endl;
        if (root == nullptr) {
            cout << "(prazdny strom)" << endl;
            return;
        }
        printHelper(root, "", false);
    }
};
```

---

#### Krok 2: Hlavný program - príklad použitia

```cpp
int main() {
    cout << "============================================================" << endl;
    cout << "BINARNY VYHLADAVACI STROM (BST)" << endl;
    cout << "============================================================" << endl;

    BST<int> bst;

    // Vkladanie
    cout << "\n--- VKLADANIE ---" << endl;
    int values[] = {8, 3, 10, 1, 6, 14, 4, 7, 13};
    for (int val : values) {
        bst.insert(val);
    }

    bst.printTree();
    bst.printSorted();

    // Vyhľadávanie
    cout << "\n--- VYHLADAVANIE ---" << endl;
    bst.search(6);
    bst.search(15);

    // Mazanie
    cout << "\n--- MAZANIE ---" << endl;
    bst.remove(1);   // List
    bst.printTree();

    bst.remove(14);  // Jeden potomok
    bst.printTree();

    bst.remove(3);   // Dva potomkovia
    bst.printTree();

    bst.printSorted();

    cout << "============================================================" << endl;

    return 0;
}
```

---

### Časová zložitosť

| Operácia | Priemerný prípad | Najhorší prípad |
|----------|------------------|-----------------|
| Vyhľadávanie | O(log n) | O(n) |
| Vkladanie | O(log n) | O(n) |
| Mazanie | O(log n) | O(n) |

**Najhorší prípad** nastáva pri degenerovanom strome (všetky uzly v línii).

**Riešenie:** Použiť samovyvažovacie stromy (AVL, Red-Black).

---

### Časté chyby a ako sa im vyhnúť

| Chyba | Prečo nastáva | Riešenie |
|-------|---------------|----------|
| Duplicity | Vloženie rovnakej hodnoty | Rozhodnúť: ignorovať alebo povoliť |
| Nesprávne mazanie | Zabudnutie na prípad s dvoma potomkami | Použiť in-order nasledovníka |
| Strata podstromov | Pri mazaní uzla s potomkami | Správne prepojiť potomkov |
| Degenerovaný strom | Vkladanie zoradených hodnôt | Použiť AVL alebo vkladať náhodne |

**Typický bug pri mazaní:**

```cpp
// CHYBA: Zabudnutie na pravý podstrom
if (node->left == nullptr) {
    delete node;
    return nullptr;  // Stratili sme pravý podstrom!
}

// SPRÁVNE:
if (node->left == nullptr) {
    BSTNode<T>* temp = node->right;
    delete node;
    return temp;  // Vrátime pravý podstrom
}
```

---

### Skús sám - Doplň chýbajúci kód

```cpp
BSTNode<T>* searchHelper(BSTNode<T>* node, T value) const {
    // TODO 1: Základný prípad - uzol neexistuje
    if (_________________________________) {
        return nullptr;
    }

    // TODO 2: Našli sme hodnotu
    if (value == node->data) {
        return _________________________________;
    }

    // TODO 3: Rekurzívne hľadanie
    if (value < node->data) {
        return _________________________________;
    } else {
        return _________________________________;
    }
}
```

<details>
<summary>Riešenie (klikni pre zobrazenie)</summary>

```cpp
// TODO 1:
if (node == nullptr)

// TODO 2:
return node;

// TODO 3:
return searchHelper(node->left, value);
return searchHelper(node->right, value);
```
</details>

---

### Praktické úlohy

#### Úloha 6.1: Validácia BST
Implementuj funkciu `isValidBST()`, ktorá overí, či strom spĺňa BST vlastnosť.

**Hint:** Použi in-order traversal a over, či sú hodnoty zoradené.

#### Úloha 6.2: k-tý najmenší prvok
Implementuj funkciu `kthSmallest(int k)`, ktorá vráti k-tý najmenší prvok v BST.

#### Úloha 6.3: Spoločný predok
Implementuj funkciu `lowestCommonAncestor(T a, T b)`, ktorá nájde najnižšieho spoločného predka dvoch hodnôt.

---

## Úloha 7: AVL stromy - Samovyvažujúce binárne stromy

**Čo sa naučíš:** Ako udržať BST vyvážený pomocou rotácií v C++

> **Prerekvizity:** [Úloha 6: BST](#úloha-6-binárny-vyhľadávací-strom-bst---efektívne-vyhľadávanie) **DOLEZITE - musíš rozumieť BST!**
>
> **Súvisiace témy:** [B-stromy (iný prístup k vyvažovaniu)](#úloha-8-b-stromy---stromy-pre-databázy)

### Teória - Prečo potrebujeme AVL?

**Problém s BST:** Pri vkladaní zoradených hodnôt sa strom degeneruje na linked list → O(n) operácie.

```
Vloženie 1, 2, 3, 4, 5 do BST:

    [1]
      \
      [2]
        \
        [3]
          \
          [4]
            \
            [5]

Výška: 4 (malo by byť ~2)
Vyhľadávanie 5: 5 krokov (malo by byť ~3)
```

**AVL strom** (Adelson-Velsky a Landis, 1962):
- Samovyvažujúci BST
- **Balance factor** = výška(ľavý) - výška(pravý)
- Pre každý uzol: balance factor ∈ {-1, 0, 1}
- Pri porušení → **rotácia**

### Vizualizácia - Rotácie

```
PRAVÁ ROTÁCIA (Right Rotation) - keď ľavý podstrom je príliš vysoký:

        [y]                    [x]
       /   \                  /   \
     [x]   [C]    ─────>    [A]   [y]
    /   \                        /   \
  [A]   [B]                    [B]   [C]

Balance factor y: 2 → 0


ĽAVÁ ROTÁCIA (Left Rotation) - keď pravý podstrom je príliš vysoký:

    [x]                        [y]
   /   \                      /   \
 [A]   [y]      ─────>      [x]   [C]
      /   \                /   \
    [B]   [C]            [A]   [B]

Balance factor x: -2 → 0


ĽAVO-PRAVÁ ROTÁCIA (Left-Right) - zig-zag vľavo:

      [z]              [z]              [y]
     /                /                /   \
   [x]      ─L─>    [y]      ─R─>    [x]   [z]
     \              /
     [y]          [x]


PRAVO-ĽAVÁ ROTÁCIA (Right-Left) - zig-zag vpravo:

   [x]               [x]                [y]
     \                 \               /   \
     [z]    ─R─>       [y]    ─L─>   [x]   [z]
     /                   \
   [y]                   [z]
```

---

### Krok za krokom

#### Krok 1: AVL Uzol s výškou

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

/**
 * Uzol AVL stromu.
 * Obsahuje navyše výšku pre výpočet balance factoru.
 */
template<typename T>
struct AVLNode {
    T data;
    AVLNode* left;
    AVLNode* right;
    int height;  // Výška podstromu s koreňom v tomto uzle

    AVLNode(T value) : data(value), left(nullptr), right(nullptr), height(1) {}
};
```

---

#### Krok 2: AVL Strom s rotáciami

```cpp
/**
 * AVL strom - samovyvažujúci BST.
 */
template<typename T>
class AVLTree {
private:
    AVLNode<T>* root;

    /**
     * Získaj výšku uzla (nullptr má výšku 0).
     */
    int getHeight(AVLNode<T>* node) const {
        return node == nullptr ? 0 : node->height;
    }

    /**
     * Vypočítaj balance factor uzla.
     */
    int getBalance(AVLNode<T>* node) const {
        return node == nullptr ? 0 : getHeight(node->left) - getHeight(node->right);
    }

    /**
     * Aktualizuj výšku uzla.
     */
    void updateHeight(AVLNode<T>* node) {
        node->height = 1 + max(getHeight(node->left), getHeight(node->right));
    }

    /**
     * Pravá rotácia.
     *
     *       y                x
     *      / \              / \
     *     x   C    --->    A   y
     *    / \                  / \
     *   A   B                B   C
     */
    AVLNode<T>* rightRotate(AVLNode<T>* y) {
        cout << "   Prava rotacia okolo " << y->data << endl;

        AVLNode<T>* x = y->left;
        AVLNode<T>* B = x->right;

        // Rotácia
        x->right = y;
        y->left = B;

        // Aktualizuj výšky (y prvé, lebo je teraz nižšie)
        updateHeight(y);
        updateHeight(x);

        return x;  // Nový koreň podstromu
    }

    /**
     * Ľavá rotácia.
     *
     *     x                  y
     *    / \                / \
     *   A   y     --->     x   C
     *      / \            / \
     *     B   C          A   B
     */
    AVLNode<T>* leftRotate(AVLNode<T>* x) {
        cout << "   Lava rotacia okolo " << x->data << endl;

        AVLNode<T>* y = x->right;
        AVLNode<T>* B = y->left;

        // Rotácia
        y->left = x;
        x->right = B;

        // Aktualizuj výšky
        updateHeight(x);
        updateHeight(y);

        return y;  // Nový koreň podstromu
    }

    /**
     * Vyváženie uzla po vložení/zmazaní.
     */
    AVLNode<T>* balance(AVLNode<T>* node) {
        updateHeight(node);
        int bf = getBalance(node);

        cout << "   Balance(" << node->data << ") = " << bf;

        // Ľavý-Ľavý prípad (bf > 1 a nová hodnota je v ľavom podstrome ľavého potomka)
        if (bf > 1 && getBalance(node->left) >= 0) {
            cout << " -> Lavy-Lavy pripad" << endl;
            return rightRotate(node);
        }

        // Pravý-Pravý prípad
        if (bf < -1 && getBalance(node->right) <= 0) {
            cout << " -> Pravy-Pravy pripad" << endl;
            return leftRotate(node);
        }

        // Ľavý-Pravý prípad (zig-zag)
        if (bf > 1 && getBalance(node->left) < 0) {
            cout << " -> Lavy-Pravy pripad" << endl;
            node->left = leftRotate(node->left);
            return rightRotate(node);
        }

        // Pravý-Ľavý prípad (zig-zag)
        if (bf < -1 && getBalance(node->right) > 0) {
            cout << " -> Pravy-Lavy pripad" << endl;
            node->right = rightRotate(node->right);
            return leftRotate(node);
        }

        cout << " -> OK" << endl;
        return node;  // Už je vyvážený
    }

    /**
     * Rekurzívne vloženie s vyvažovaním.
     */
    AVLNode<T>* insertHelper(AVLNode<T>* node, T value) {
        // Štandardné BST vloženie
        if (node == nullptr) {
            cout << "   [+] Vkladam: " << value << endl;
            return new AVLNode<T>(value);
        }

        if (value < node->data) {
            node->left = insertHelper(node->left, value);
        } else if (value > node->data) {
            node->right = insertHelper(node->right, value);
        } else {
            return node;  // Duplicity ignorujeme
        }

        // Vyváženie
        return balance(node);
    }

    /**
     * Nájdi minimum v podstrome.
     */
    AVLNode<T>* findMin(AVLNode<T>* node) const {
        while (node->left != nullptr) {
            node = node->left;
        }
        return node;
    }

    /**
     * Rekurzívne zmazanie s vyvažovaním.
     */
    AVLNode<T>* deleteHelper(AVLNode<T>* node, T value) {
        if (node == nullptr) return nullptr;

        // Štandardné BST mazanie
        if (value < node->data) {
            node->left = deleteHelper(node->left, value);
        } else if (value > node->data) {
            node->right = deleteHelper(node->right, value);
        } else {
            // Našli sme uzol na zmazanie
            cout << "   [x] Mazem: " << value << endl;

            if (node->left == nullptr || node->right == nullptr) {
                AVLNode<T>* temp = node->left ? node->left : node->right;

                if (temp == nullptr) {
                    // Žiadny potomok
                    delete node;
                    return nullptr;
                } else {
                    // Jeden potomok
                    delete node;
                    return temp;
                }
            } else {
                // Dva potomkovia
                AVLNode<T>* successor = findMin(node->right);
                node->data = successor->data;
                node->right = deleteHelper(node->right, successor->data);
            }
        }

        // Vyváženie
        return balance(node);
    }

    /**
     * In-order traversal.
     */
    void inorderHelper(AVLNode<T>* node) const {
        if (node == nullptr) return;
        inorderHelper(node->left);
        cout << node->data << "(h:" << node->height << ") ";
        inorderHelper(node->right);
    }

    /**
     * Vizualizácia.
     */
    void printHelper(AVLNode<T>* node, string prefix, bool isLeft) const {
        if (node == nullptr) return;

        cout << prefix << (isLeft ? "├── " : "└── ");
        cout << node->data << " [bf:" << getBalance(node) << "]" << endl;

        printHelper(node->left, prefix + (isLeft ? "│   " : "    "), true);
        printHelper(node->right, prefix + (isLeft ? "│   " : "    "), false);
    }

    void destroyTree(AVLNode<T>* node) {
        if (node == nullptr) return;
        destroyTree(node->left);
        destroyTree(node->right);
        delete node;
    }

public:
    AVLTree() : root(nullptr) {}
    ~AVLTree() { destroyTree(root); }

    void insert(T value) {
        cout << "\nVkladanie " << value << ":" << endl;
        root = insertHelper(root, value);
    }

    void remove(T value) {
        cout << "\nMazanie " << value << ":" << endl;
        root = deleteHelper(root, value);
    }

    void printTree() const {
        cout << "\nAVL Strom:" << endl;
        if (root == nullptr) {
            cout << "(prazdny)" << endl;
            return;
        }
        printHelper(root, "", false);
    }

    void printInorder() const {
        cout << "In-order: ";
        inorderHelper(root);
        cout << endl;
    }

    int height() const {
        return getHeight(root);
    }
};
```

---

#### Krok 3: Hlavný program

```cpp
int main() {
    cout << "============================================================" << endl;
    cout << "AVL STROM - Samovyvazujuci BST" << endl;
    cout << "============================================================" << endl;

    AVLTree<int> avl;

    // Vkladanie zoradených hodnôt (v BST by vytvorilo degenerovaný strom)
    cout << "\n--- VKLADANIE 1, 2, 3, 4, 5, 6, 7 ---" << endl;
    for (int i = 1; i <= 7; i++) {
        avl.insert(i);
        avl.printTree();
    }

    cout << "\nVyska stromu: " << avl.height() << " (log2(7) ≈ 2.8)" << endl;
    avl.printInorder();

    // Mazanie
    cout << "\n--- MAZANIE ---" << endl;
    avl.remove(4);
    avl.printTree();

    cout << "============================================================" << endl;

    return 0;
}
```

---

### Časová zložitosť

| Operácia | Zložitosť |
|----------|-----------|
| Vyhľadávanie | O(log n) |
| Vkladanie | O(log n) |
| Mazanie | O(log n) |
| Rotácia | O(1) |

**Výhoda oproti BST:** Garantovaná O(log n) aj v najhoršom prípade!

**Nevýhoda:** Overhead na udržiavanie výšok a rotácie.

---

### Časté chyby a ako sa im vyhnúť

| Chyba | Prečo nastáva | Riešenie |
|-------|---------------|----------|
| Nesprávne poradie aktualizácie výšok | Po rotácii treba aktualizovať spodný uzol prvý | Vždy: najprv potomok, potom rodič |
| Zábudnutá rotácia | Nekontroluje sa balance factor | Po každom insert/delete volať balance() |
| Nesprávny smer rotácie | Zamieňanie LL/RR/LR/RL prípadov | Nakresliť si obrázok, skontrolovať balance factory |
| Chybný balance factor výpočet | left - right vs right - left | Konzistentne používať jednu konvenciu |

---

### Skús sám - Doplň chýbajúci kód

```cpp
AVLNode<T>* rightRotate(AVLNode<T>* y) {
    // TODO 1: Ktorý uzol sa stane novým koreňom?
    AVLNode<T>* x = _________________________________;
    AVLNode<T>* B = x->right;

    // TODO 2: Vykonaj rotáciu
    x->right = _________________________________;
    y->left = _________________________________;

    // TODO 3: V akom poradí aktualizujeme výšky?
    updateHeight(_________________________________);
    updateHeight(_________________________________);

    return x;
}
```

<details>
<summary>Riešenie (klikni pre zobrazenie)</summary>

```cpp
// TODO 1:
AVLNode<T>* x = y->left;

// TODO 2:
x->right = y;
y->left = B;

// TODO 3: Najprv y (je teraz nižšie), potom x
updateHeight(y);
updateHeight(x);
```
</details>

---

### Praktické úlohy

#### Úloha 7.1: Počítanie rotácií
Uprav implementáciu tak, aby počítala celkový počet rotácií pri vkladaní n prvkov.

#### Úloha 7.2: Vizuálne porovnanie s BST
Vlož rovnakú postupnosť čísel do BST aj AVL a porovnaj výšky stromov.

#### Úloha 7.3: Overenie AVL vlastnosti
Implementuj funkciu `isAVL()`, ktorá overí, či strom spĺňa AVL vlastnosť.

---

## Úloha 8: B-stromy - Stromy pre databázy

**Čo sa naučíš:** Ako fungujú B-stromy používané v databázach a súborových systémoch

### Teória - Prečo B-stromy?

**Problém:** Pri práci s diskom je čítanie/zápis pomalé. Chceme minimalizovať počet prístupov na disk.

**B-strom:**
- Vyvážený strom s **viac ako 2 potomkami** na uzol
- Všetky listy sú na **rovnakej úrovni**
- Uzly obsahujú **viacero kľúčov**
- Ideálny pre **databázy** a **súborové systémy**

**Parametre B-stromu rádu t (minimálny stupeň):**
- Každý uzol (okrem koreňa) má aspoň t-1 kľúčov
- Každý uzol má najviac 2t-1 kľúčov
- Koreň má aspoň 1 kľúč
- Vnútorný uzol s k kľúčmi má k+1 potomkov

### Vizualizácia - B-strom rádu 2 (2-3-4 strom)

```
B-strom rádu t=2 (min 1 kľúč, max 3 kľúče v uzle):

                    [10 | 20]
                   /    |    \
                  /     |     \
         [3 | 6]    [12 | 15]   [25 | 30 | 35]
         /  |  \     /  |  \     /  |   |   \
       [1] [4] [7] [11][13][18] [22][27][32][40]

Vlastnosti:
- Všetky listy sú na úrovni 2
- Koreň má 2 kľúče → 3 potomkov
- Uzol [25|30|35] má 3 kľúče → 4 potomkov
```

**Vyhľadávanie hodnoty 13:**
```
[10 | 20] → 10 < 13 < 20, idem do stredného potomka
[12 | 15] → 12 < 13 < 15, idem do stredného potomka
[13] → NÁJDENÉ!

Počet prístupov na disk: 3 (namiesto log₂(n) ≈ 4-5)
```

---

### Krok za krokom

#### Krok 1: Štruktúra B-strom uzla

```cpp
#include <iostream>
#include <vector>
using namespace std;

/**
 * B-strom uzol.
 * t = minimálny stupeň (min t-1 kľúčov, max 2t-1 kľúčov)
 */
template<typename T>
class BTreeNode {
public:
    vector<T> keys;           // Kľúče v uzle
    vector<BTreeNode*> children;  // Ukazovatele na potomkov
    int t;                    // Minimálny stupeň
    bool isLeaf;              // Je to list?

    BTreeNode(int _t, bool _isLeaf) : t(_t), isLeaf(_isLeaf) {
        // Rezervuj miesto pre max kľúče a potomkov
        keys.reserve(2 * t - 1);
        children.reserve(2 * t);
    }

    /**
     * Nájdi index prvého kľúča >= k.
     */
    int findKey(T k) {
        int idx = 0;
        while (idx < keys.size() && keys[idx] < k) {
            idx++;
        }
        return idx;
    }

    /**
     * Vyhľadaj kľúč v podstrome.
     */
    BTreeNode* search(T k, int& comparisons) {
        int idx = findKey(k);
        comparisons++;

        // Našli sme kľúč
        if (idx < keys.size() && keys[idx] == k) {
            return this;
        }

        // Je to list a nenašli sme
        if (isLeaf) {
            return nullptr;
        }

        // Rekurzívne hľadaj v potomkovi
        return children[idx]->search(k, comparisons);
    }

    /**
     * Vlož kľúč do neprázdneho uzla.
     */
    void insertNonFull(T k) {
        int i = keys.size() - 1;

        if (isLeaf) {
            // List: vlož na správne miesto
            keys.push_back(T());  // Rozšír vektor
            while (i >= 0 && keys[i] > k) {
                keys[i + 1] = keys[i];
                i--;
            }
            keys[i + 1] = k;
            cout << "   [+] Vlozene " << k << " do listu" << endl;
        } else {
            // Vnútorný uzol: nájdi správneho potomka
            while (i >= 0 && keys[i] > k) {
                i--;
            }
            i++;

            // Ak je potomok plný, rozdeľ ho
            if (children[i]->keys.size() == 2 * t - 1) {
                splitChild(i, children[i]);
                if (keys[i] < k) {
                    i++;
                }
            }
            children[i]->insertNonFull(k);
        }
    }

    /**
     * Rozdeľ plné dieťa.
     */
    void splitChild(int i, BTreeNode* y) {
        cout << "   [/] Rozdelujem uzol s klucmi: ";
        for (T key : y->keys) cout << key << " ";
        cout << endl;

        // Vytvor nový uzol z
        BTreeNode* z = new BTreeNode(y->t, y->isLeaf);

        // Presuň druhú polovicu kľúčov do z
        for (int j = 0; j < t - 1; j++) {
            z->keys.push_back(y->keys[j + t]);
        }

        // Presuň druhú polovicu potomkov do z (ak nie je list)
        if (!y->isLeaf) {
            for (int j = 0; j < t; j++) {
                z->children.push_back(y->children[j + t]);
            }
            y->children.resize(t);
        }

        // Stredný kľúč pôjde do rodiča
        T middleKey = y->keys[t - 1];

        // Zmenši y
        y->keys.resize(t - 1);

        // Vlož z ako potomka tohto uzla
        children.insert(children.begin() + i + 1, z);

        // Vlož stredný kľúč do tohto uzla
        keys.insert(keys.begin() + i, middleKey);

        cout << "   [/] Stredny kluc " << middleKey << " posunuty do rodica" << endl;
    }

    /**
     * Výpis uzla.
     */
    void print(int level = 0) {
        string indent(level * 4, ' ');

        cout << indent << "[";
        for (int i = 0; i < keys.size(); i++) {
            if (i > 0) cout << " | ";
            cout << keys[i];
        }
        cout << "]" << (isLeaf ? " (list)" : "") << endl;

        if (!isLeaf) {
            for (auto child : children) {
                child->print(level + 1);
            }
        }
    }
};
```

---

#### Krok 2: B-strom trieda

```cpp
/**
 * B-strom.
 */
template<typename T>
class BTree {
private:
    BTreeNode<T>* root;
    int t;  // Minimálny stupeň

public:
    BTree(int _t) : t(_t), root(nullptr) {
        cout << "Vytvoreny B-strom radu " << t << endl;
        cout << "   Min klucov v uzle: " << (t - 1) << endl;
        cout << "   Max klucov v uzle: " << (2 * t - 1) << endl;
    }

    /**
     * Vyhľadaj kľúč.
     */
    bool search(T k) {
        if (root == nullptr) {
            cout << "Strom je prazdny" << endl;
            return false;
        }

        cout << "\nHladanie " << k << ":" << endl;
        int comparisons = 0;
        BTreeNode<T>* result = root->search(k, comparisons);

        if (result != nullptr) {
            cout << "   NAJDENE po " << comparisons << " porovnaniach" << endl;
            return true;
        } else {
            cout << "   NENAJDENE po " << comparisons << " porovnaniach" << endl;
            return false;
        }
    }

    /**
     * Vlož kľúč.
     */
    void insert(T k) {
        cout << "\nVkladanie " << k << ":" << endl;

        if (root == nullptr) {
            root = new BTreeNode<T>(t, true);
            root->keys.push_back(k);
            cout << "   [+] Vytvoreny koren s hodnotou " << k << endl;
            return;
        }

        // Ak je koreň plný, strom vyrastie
        if (root->keys.size() == 2 * t - 1) {
            cout << "   [^] Koren je plny, strom rastie" << endl;
            BTreeNode<T>* newRoot = new BTreeNode<T>(t, false);
            newRoot->children.push_back(root);
            newRoot->splitChild(0, root);

            // Rozhodnutie do ktorého potomka ísť
            int i = (newRoot->keys[0] < k) ? 1 : 0;
            newRoot->children[i]->insertNonFull(k);

            root = newRoot;
        } else {
            root->insertNonFull(k);
        }
    }

    /**
     * Výpis stromu.
     */
    void print() {
        cout << "\nB-strom:" << endl;
        if (root == nullptr) {
            cout << "(prazdny)" << endl;
            return;
        }
        root->print();
    }

    /**
     * Výška stromu.
     */
    int height() {
        if (root == nullptr) return 0;

        int h = 1;
        BTreeNode<T>* node = root;
        while (!node->isLeaf) {
            node = node->children[0];
            h++;
        }
        return h;
    }
};
```

---

#### Krok 3: Hlavný program

```cpp
int main() {
    cout << "============================================================" << endl;
    cout << "B-STROM - Stromy pre databazy" << endl;
    cout << "============================================================" << endl;

    // B-strom rádu 2 (2-3-4 strom)
    BTree<int> btree(2);

    // Vkladanie
    int values[] = {10, 20, 5, 6, 12, 30, 7, 17, 3, 8};
    for (int val : values) {
        btree.insert(val);
        btree.print();
    }

    cout << "\nVyska B-stromu: " << btree.height() << endl;

    // Vyhľadávanie
    cout << "\n--- VYHLADAVANIE ---" << endl;
    btree.search(6);
    btree.search(15);
    btree.search(30);

    cout << "============================================================" << endl;

    return 0;
}
```

---

### Časová zložitosť

| Operácia | Zložitosť |
|----------|-----------|
| Vyhľadávanie | O(log_t n) |
| Vkladanie | O(log_t n) |
| Mazanie | O(log_t n) |

**Pre t = 100 a n = 1 milión:**
- B-strom výška: log₁₀₀(1M) ≈ 3
- BST výška: log₂(1M) ≈ 20

→ **7× menej prístupov na disk!**

---

### Použitie v praxi

- **Databázy:** MySQL, PostgreSQL, Oracle používajú B+ stromy
- **Súborové systémy:** NTFS, ext4, HFS+
- **Indexy:** Rýchle vyhľadávanie v databázových tabuľkách

---

### Praktické úlohy

#### Úloha 8.1: B+ strom
Implementuj B+ strom, kde všetky dáta sú len v listoch a listy sú prepojené linked listom.

#### Úloha 8.2: Mazanie z B-stromu
Implementuj operáciu delete pre B-strom (zložitejšia ako insert).

#### Úloha 8.3: Porovnanie s AVL
Porovnaj počet porovnaní pri vyhľadávaní v B-strome a AVL strome pre 10000 prvkov.

---

## Úloha 9: DFS - Prehľadávanie do hĺbky

**Čo sa naučíš:** Ako systematicky prehľadať strom/graf pomocou DFS v C++

> **Prerekvizity:** [Úloha 5: Binárny strom](#úloha-5-binárny-strom---základná-stromová-štruktúra) • Rekurzia • Stack
>
> **Súvisiace témy:** [BFS (alternatívny prístup)](#úloha-10-bfs---prehľadávanie-do-šírky) • [BST (in-order = zoradené)](#úloha-6-binárny-vyhľadávací-strom-bst---efektívne-vyhľadávanie) • [Grafové algoritmy](#úloha-1-kruskalov-algoritmus---minimálna-kostra-grafu)

### Teória - Čo je DFS?

**DFS (Depth-First Search)** = prehľadávanie do hĺbky
- Choď čo najhlbšie, potom sa vráť a skús inú vetvu
- Používa **stack** (zásobník) - explicitne alebo cez rekurziu

**Analógia:** Bludisko - ideš stále rovne, až kým nenarazíš na stenu. Potom sa vrátiš a skúsiš inú cestu.

### Vizualizácia - DFS na strome

```
Strom:
           [1]
          / | \
        [2][3][4]
        /\     \
      [5][6]   [7]
         |
        [8]

DFS poradie (pre-order): 1 → 2 → 5 → 6 → 8 → 3 → 4 → 7

Stack simulácia:
Krok 1: navštív 1, pridaj deti [4,3,2] na stack
Krok 2: pop 2, navštív, pridaj [6,5]
Krok 3: pop 5, navštív (list)
Krok 4: pop 6, navštív, pridaj [8]
Krok 5: pop 8, navštív (list)
Krok 6: pop 3, navštív (list)
Krok 7: pop 4, navštív, pridaj [7]
Krok 8: pop 7, navštív (list)
```

### Tri typy DFS pre binárne stromy

```
        [A]
       /   \
     [B]   [C]
    /   \
  [D]   [E]

Pre-order (NLR):  A → B → D → E → C     (koreň, ľavý, pravý)
In-order (LNR):   D → B → E → A → C     (ľavý, koreň, pravý)
Post-order (LRN): D → E → B → C → A     (ľavý, pravý, koreň)
```

**Použitie:**
- **Pre-order:** Kopírovanie stromu, výrazy s prefixovou notáciou
- **In-order:** Zoradené hodnoty v BST
- **Post-order:** Mazanie stromu, výpočet veľkosti podstromov

---

### Krok za krokom

#### Krok 1: Rekurzívna implementácia

```cpp
#include <iostream>
#include <vector>
#include <stack>
using namespace std;

// Použijeme štruktúru TreeNode z predchádzajúcich úloh
template<typename T>
struct TreeNode {
    T data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(T val) : data(val), left(nullptr), right(nullptr) {}
};

/**
 * DFS Traversals - rekurzívne implementácie.
 */
template<typename T>
class DFS {
public:
    /**
     * Pre-order: Najprv spracuj uzol, potom potomkov.
     * Použitie: kopírovanie stromu, serializácia
     */
    static void preorder(TreeNode<T>* node, vector<T>& result) {
        if (node == nullptr) return;

        result.push_back(node->data);     // Spracuj uzol
        preorder(node->left, result);     // Ľavý podstrom
        preorder(node->right, result);    // Pravý podstrom
    }

    /**
     * In-order: Najprv ľavý, potom uzol, potom pravý.
     * Použitie: zoradené hodnoty v BST
     */
    static void inorder(TreeNode<T>* node, vector<T>& result) {
        if (node == nullptr) return;

        inorder(node->left, result);      // Ľavý podstrom
        result.push_back(node->data);     // Spracuj uzol
        inorder(node->right, result);     // Pravý podstrom
    }

    /**
     * Post-order: Najprv potomkovia, potom uzol.
     * Použitie: mazanie stromu, výpočet veľkosti
     */
    static void postorder(TreeNode<T>* node, vector<T>& result) {
        if (node == nullptr) return;

        postorder(node->left, result);    // Ľavý podstrom
        postorder(node->right, result);   // Pravý podstrom
        result.push_back(node->data);     // Spracuj uzol
    }
};
```

---

#### Krok 2: Iteratívna implementácia (pomocou stack)

```cpp
/**
 * DFS - iteratívne implementácie pomocou stacku.
 */
template<typename T>
class DFSIterative {
public:
    /**
     * Pre-order iteratívne.
     */
    static vector<T> preorder(TreeNode<T>* root) {
        vector<T> result;
        if (root == nullptr) return result;

        stack<TreeNode<T>*> s;
        s.push(root);

        cout << "Pre-order (iterativne):" << endl;

        while (!s.empty()) {
            TreeNode<T>* node = s.top();
            s.pop();

            result.push_back(node->data);
            cout << "   Navstiveny: " << node->data
                 << " (stack size: " << s.size() << ")" << endl;

            // Pravý prvý (bude spracovaný ako posledný)
            if (node->right) s.push(node->right);
            if (node->left) s.push(node->left);
        }

        return result;
    }

    /**
     * In-order iteratívne.
     */
    static vector<T> inorder(TreeNode<T>* root) {
        vector<T> result;
        stack<TreeNode<T>*> s;
        TreeNode<T>* current = root;

        cout << "In-order (iterativne):" << endl;

        while (current != nullptr || !s.empty()) {
            // Choď čo najďalej vľavo
            while (current != nullptr) {
                s.push(current);
                current = current->left;
            }

            // Spracuj uzol
            current = s.top();
            s.pop();
            result.push_back(current->data);
            cout << "   Navstiveny: " << current->data << endl;

            // Prejdi na pravý podstrom
            current = current->right;
        }

        return result;
    }

    /**
     * Post-order iteratívne (zložitejšie - dva stacky).
     */
    static vector<T> postorder(TreeNode<T>* root) {
        vector<T> result;
        if (root == nullptr) return result;

        stack<TreeNode<T>*> s1, s2;
        s1.push(root);

        cout << "Post-order (iterativne):" << endl;

        // Prvý prechod: vytvor obrátené pre-order
        while (!s1.empty()) {
            TreeNode<T>* node = s1.top();
            s1.pop();
            s2.push(node);

            if (node->left) s1.push(node->left);
            if (node->right) s1.push(node->right);
        }

        // Druhý prechod: vyprázdni s2
        while (!s2.empty()) {
            result.push_back(s2.top()->data);
            cout << "   Navstiveny: " << s2.top()->data << endl;
            s2.pop();
        }

        return result;
    }
};
```

---

#### Krok 3: DFS na grafe (detekcia cyklov)

```cpp
/**
 * DFS na grafe reprezentovanom ako zoznam susedov.
 */
class GraphDFS {
private:
    int V;  // Počet vrcholov
    vector<vector<int>> adj;

public:
    GraphDFS(int vertices) : V(vertices) {
        adj.resize(V);
    }

    void addEdge(int u, int v) {
        adj[u].push_back(v);
        // Pre neorientovaný graf: adj[v].push_back(u);
    }

    /**
     * DFS prehľadávanie grafu.
     */
    void dfs(int start) {
        vector<bool> visited(V, false);
        cout << "\nDFS z vrcholu " << start << ": ";
        dfsHelper(start, visited);
        cout << endl;
    }

private:
    void dfsHelper(int v, vector<bool>& visited) {
        visited[v] = true;
        cout << v << " ";

        for (int neighbor : adj[v]) {
            if (!visited[neighbor]) {
                dfsHelper(neighbor, visited);
            }
        }
    }

public:
    /**
     * Detekcia cyklu v orientovanom grafe.
     */
    bool hasCycle() {
        vector<int> color(V, 0);  // 0=biely, 1=šedý, 2=čierny

        for (int i = 0; i < V; i++) {
            if (color[i] == 0) {
                if (hasCycleHelper(i, color)) {
                    return true;
                }
            }
        }
        return false;
    }

private:
    bool hasCycleHelper(int v, vector<int>& color) {
        color[v] = 1;  // Označíme ako šedý (v spracovaní)

        for (int neighbor : adj[v]) {
            if (color[neighbor] == 1) {
                // Našli sme šedý uzol - cyklus!
                cout << "Cyklus detekovaný: hrana " << v << " -> " << neighbor << endl;
                return true;
            }
            if (color[neighbor] == 0) {
                if (hasCycleHelper(neighbor, color)) {
                    return true;
                }
            }
        }

        color[v] = 2;  // Označíme ako čierny (hotový)
        return false;
    }
};
```

---

#### Krok 4: Hlavný program

```cpp
// Pomocná funkcia na vytvorenie ukážkového stromu
TreeNode<int>* buildSampleTree() {
    TreeNode<int>* root = new TreeNode<int>(1);
    root->left = new TreeNode<int>(2);
    root->right = new TreeNode<int>(3);
    root->left->left = new TreeNode<int>(4);
    root->left->right = new TreeNode<int>(5);
    root->right->right = new TreeNode<int>(6);
    return root;
}

int main() {
    cout << "============================================================" << endl;
    cout << "DFS - Prehladavanie do hlbky" << endl;
    cout << "============================================================" << endl;

    // DFS na strome
    cout << "\n--- DFS NA STROME ---" << endl;
    cout << "Strom:" << endl;
    cout << "       [1]" << endl;
    cout << "      /   \\" << endl;
    cout << "    [2]   [3]" << endl;
    cout << "   /   \\     \\" << endl;
    cout << " [4]   [5]   [6]" << endl;

    TreeNode<int>* root = buildSampleTree();

    // Rekurzívne
    vector<int> pre, in, post;
    DFS<int>::preorder(root, pre);
    DFS<int>::inorder(root, in);
    DFS<int>::postorder(root, post);

    cout << "\nRekurzivne:" << endl;
    cout << "   Pre-order:  "; for (int x : pre) cout << x << " "; cout << endl;
    cout << "   In-order:   "; for (int x : in) cout << x << " "; cout << endl;
    cout << "   Post-order: "; for (int x : post) cout << x << " "; cout << endl;

    // Iteratívne
    cout << "\nIterativne:" << endl;
    DFSIterative<int>::preorder(root);

    // DFS na grafe
    cout << "\n--- DFS NA GRAFE ---" << endl;
    GraphDFS g(6);
    g.addEdge(0, 1);
    g.addEdge(0, 2);
    g.addEdge(1, 3);
    g.addEdge(2, 4);
    g.addEdge(4, 5);

    g.dfs(0);

    // Detekcia cyklu
    cout << "\n--- DETEKCIA CYKLU ---" << endl;
    GraphDFS gCycle(4);
    gCycle.addEdge(0, 1);
    gCycle.addEdge(1, 2);
    gCycle.addEdge(2, 0);  // Cyklus!
    gCycle.addEdge(2, 3);

    cout << "Graf obsahuje cyklus: " << (gCycle.hasCycle() ? "ANO" : "NIE") << endl;

    cout << "============================================================" << endl;

    return 0;
}
```

---

### Časová zložitosť

| Štruktúra | Zložitosť |
|-----------|-----------|
| Strom (n uzlov) | O(n) |
| Graf (V vrcholov, E hrán) | O(V + E) |

**Priestorová zložitosť:**
- Rekurzívne: O(h) kde h = výška stromu (stack frames)
- Iteratívne: O(n) v najhoršom prípade

---

### Časté chyby a ako sa im vyhnúť

| Chyba | Prečo nastáva | Riešenie |
|-------|---------------|----------|
| Stack overflow | Príliš hlboký strom | Použiť iteratívnu verziu |
| Nekonečná slučka v grafe | Chýba visited pole | Vždy označiť navštívené uzly |
| Nesprávne poradie traversal | Zámena left/right | Nakresliť si diagram |
| Chýbajúci nullptr check | Prístup k neexistujúcemu uzlu | `if (node == nullptr) return;` |

---

### Skús sám - Doplň chýbajúci kód

```cpp
// In-order traversal iteratívne
vector<T> inorder(TreeNode<T>* root) {
    vector<T> result;
    stack<TreeNode<T>*> s;
    TreeNode<T>* current = root;

    while (_________________________________ || _________________________________) {
        // Choď čo najďalej vľavo
        while (current != nullptr) {
            _________________________________;
            current = _________________________________;
        }

        // Spracuj uzol
        current = s.top();
        s.pop();
        result.push_back(_________________________________);

        // Prejdi na pravý podstrom
        current = _________________________________;
    }

    return result;
}
```

<details>
<summary>Riešenie (klikni pre zobrazenie)</summary>

```cpp
while (current != nullptr || !s.empty())

s.push(current);
current = current->left;

result.push_back(current->data);

current = current->right;
```
</details>

---

### Praktické úlohy

#### Úloha 9.1: Hĺbka stromu pomocou DFS
Implementuj funkciu `maxDepth()` pomocou DFS.

#### Úloha 9.2: Cesta v strome
Nájdi cestu od koreňa k danému uzlu pomocou DFS.

#### Úloha 9.3: Topologické triedenie
Implementuj topologické triedenie DAGu pomocou DFS.

---

## Úloha 10: BFS - Prehľadávanie do šírky

**Čo sa naučíš:** Ako prehľadávať strom/graf po úrovniach pomocou BFS v C++

> **Prerekvizity:** [Úloha 5: Binárny strom](#úloha-5-binárny-strom---základná-stromová-štruktúra) • Queue (fronta)
>
> **Súvisiace témy:** [DFS (alternatívny prístup)](#úloha-9-dfs---prehľadávanie-do-hĺbky) • [Dijkstra (podobný princíp)](#úloha-3-dijkstrov-algoritmus---najkratšie-cesty)

### Teória - Čo je BFS?

**BFS (Breadth-First Search)** = prehľadávanie do šírky
- Najprv spracuj všetky uzly na aktuálnej úrovni, potom prejdi na ďalšiu
- Používa **queue** (front) namiesto stacku

**Analógia:** Vlny na vode - šíria sa rovnomerne do všetkých strán.

### Vizualizácia - BFS vs DFS

```
Strom:
           [1]
          / | \
        [2][3][4]
        /\     \
      [5][6]   [7]

DFS: 1 → 2 → 5 → 6 → 3 → 4 → 7  (do hĺbky)
BFS: 1 → 2 → 3 → 4 → 5 → 6 → 7  (po úrovniach)

BFS Queue simulácia:
Krok 1: dequeue 1, enqueue [2,3,4]     Queue: [2,3,4]
Krok 2: dequeue 2, enqueue [5,6]       Queue: [3,4,5,6]
Krok 3: dequeue 3                       Queue: [4,5,6]
Krok 4: dequeue 4, enqueue [7]         Queue: [5,6,7]
Krok 5: dequeue 5                       Queue: [6,7]
Krok 6: dequeue 6                       Queue: [7]
Krok 7: dequeue 7                       Queue: []
```

**Použitie BFS:**
- **Najkratšia cesta** v neohodnotenom grafe
- **Level-order** traversal stromu
- **Najbližší sused** problémy
- **Šírenie** (vírus, informácia)

---

### Krok za krokom

#### Krok 1: BFS na strome (Level-order traversal)

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

template<typename T>
struct TreeNode {
    T data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(T val) : data(val), left(nullptr), right(nullptr) {}
};

/**
 * BFS na binárnom strome.
 */
template<typename T>
class BFS {
public:
    /**
     * Level-order traversal - jednoduché BFS.
     */
    static vector<T> levelOrder(TreeNode<T>* root) {
        vector<T> result;
        if (root == nullptr) return result;

        queue<TreeNode<T>*> q;
        q.push(root);

        cout << "Level-order traversal:" << endl;

        while (!q.empty()) {
            TreeNode<T>* node = q.front();
            q.pop();

            result.push_back(node->data);
            cout << "   Navstiveny: " << node->data
                 << " (queue size: " << q.size() << ")" << endl;

            if (node->left) q.push(node->left);
            if (node->right) q.push(node->right);
        }

        return result;
    }

    /**
     * Level-order s oddelením úrovní.
     */
    static vector<vector<T>> levelOrderByLevel(TreeNode<T>* root) {
        vector<vector<T>> result;
        if (root == nullptr) return result;

        queue<TreeNode<T>*> q;
        q.push(root);

        cout << "Level-order po urovniach:" << endl;
        int level = 0;

        while (!q.empty()) {
            int levelSize = q.size();  // Počet uzlov na tejto úrovni
            vector<T> currentLevel;

            cout << "   Uroven " << level << ": ";

            for (int i = 0; i < levelSize; i++) {
                TreeNode<T>* node = q.front();
                q.pop();

                currentLevel.push_back(node->data);
                cout << node->data << " ";

                if (node->left) q.push(node->left);
                if (node->right) q.push(node->right);
            }

            cout << endl;
            result.push_back(currentLevel);
            level++;
        }

        return result;
    }

    /**
     * Minimálna hĺbka stromu (pomocou BFS - efektívnejšie).
     */
    static int minDepth(TreeNode<T>* root) {
        if (root == nullptr) return 0;

        queue<pair<TreeNode<T>*, int>> q;
        q.push({root, 1});

        while (!q.empty()) {
            auto [node, depth] = q.front();
            q.pop();

            // Ak nájdeme list, vrátime hĺbku
            if (node->left == nullptr && node->right == nullptr) {
                return depth;
            }

            if (node->left) q.push({node->left, depth + 1});
            if (node->right) q.push({node->right, depth + 1});
        }

        return 0;
    }
};
```

---

#### Krok 2: BFS na grafe (Najkratšia cesta)

```cpp
/**
 * BFS na grafe - najkratšia cesta v neohodnotenom grafe.
 */
class GraphBFS {
private:
    int V;
    vector<vector<int>> adj;

public:
    GraphBFS(int vertices) : V(vertices) {
        adj.resize(V);
    }

    void addEdge(int u, int v) {
        adj[u].push_back(v);
        adj[v].push_back(u);  // Neorientovaný graf
    }

    /**
     * BFS prehľadávanie.
     */
    void bfs(int start) {
        vector<bool> visited(V, false);
        queue<int> q;

        visited[start] = true;
        q.push(start);

        cout << "\nBFS z vrcholu " << start << ": ";

        while (!q.empty()) {
            int v = q.front();
            q.pop();
            cout << v << " ";

            for (int neighbor : adj[v]) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    q.push(neighbor);
                }
            }
        }
        cout << endl;
    }

    /**
     * Najkratšia cesta medzi dvoma vrcholmi.
     */
    vector<int> shortestPath(int start, int end) {
        vector<bool> visited(V, false);
        vector<int> parent(V, -1);
        queue<int> q;

        visited[start] = true;
        q.push(start);

        cout << "\nHladanie najkratsej cesty " << start << " -> " << end << ":" << endl;

        while (!q.empty()) {
            int v = q.front();
            q.pop();

            if (v == end) {
                // Rekonštruuj cestu
                vector<int> path;
                for (int at = end; at != -1; at = parent[at]) {
                    path.push_back(at);
                }
                reverse(path.begin(), path.end());
                return path;
            }

            for (int neighbor : adj[v]) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    parent[neighbor] = v;
                    q.push(neighbor);
                    cout << "   Navstiveny " << neighbor << " (rodic: " << v << ")" << endl;
                }
            }
        }

        return {};  // Cesta neexistuje
    }

    /**
     * Vzdialenosti od štartu ku všetkým vrcholom.
     */
    vector<int> distances(int start) {
        vector<int> dist(V, -1);
        queue<int> q;

        dist[start] = 0;
        q.push(start);

        while (!q.empty()) {
            int v = q.front();
            q.pop();

            for (int neighbor : adj[v]) {
                if (dist[neighbor] == -1) {
                    dist[neighbor] = dist[v] + 1;
                    q.push(neighbor);
                }
            }
        }

        return dist;
    }
};
```

---

#### Krok 3: Hlavný program

```cpp
TreeNode<int>* buildSampleTree() {
    TreeNode<int>* root = new TreeNode<int>(1);
    root->left = new TreeNode<int>(2);
    root->right = new TreeNode<int>(3);
    root->left->left = new TreeNode<int>(4);
    root->left->right = new TreeNode<int>(5);
    root->right->right = new TreeNode<int>(6);
    root->right->right->left = new TreeNode<int>(7);
    return root;
}

int main() {
    cout << "============================================================" << endl;
    cout << "BFS - Prehladavanie do sirky" << endl;
    cout << "============================================================" << endl;

    // BFS na strome
    cout << "\n--- BFS NA STROME ---" << endl;
    TreeNode<int>* root = buildSampleTree();

    vector<int> levelOrder = BFS<int>::levelOrder(root);
    cout << "Vysledok: ";
    for (int x : levelOrder) cout << x << " ";
    cout << endl;

    cout << "\n";
    BFS<int>::levelOrderByLevel(root);

    cout << "\nMinimalna hlbka: " << BFS<int>::minDepth(root) << endl;

    // BFS na grafe
    cout << "\n--- BFS NA GRAFE ---" << endl;
    GraphBFS g(7);
    g.addEdge(0, 1);
    g.addEdge(0, 2);
    g.addEdge(1, 3);
    g.addEdge(1, 4);
    g.addEdge(2, 5);
    g.addEdge(2, 6);

    g.bfs(0);

    // Najkratšia cesta
    vector<int> path = g.shortestPath(0, 6);
    cout << "Najkratsia cesta 0 -> 6: ";
    for (int v : path) cout << v << " ";
    cout << "(dlzka: " << path.size() - 1 << ")" << endl;

    // Vzdialenosti
    vector<int> dist = g.distances(0);
    cout << "\nVzdialenosti od vrcholu 0:" << endl;
    for (int i = 0; i < dist.size(); i++) {
        cout << "   0 -> " << i << ": " << dist[i] << endl;
    }

    cout << "============================================================" << endl;

    return 0;
}
```

---

### Časová zložitosť

| Štruktúra | Zložitosť |
|-----------|-----------|
| Strom (n uzlov) | O(n) |
| Graf (V vrcholov, E hrán) | O(V + E) |

**Priestorová zložitosť:** O(w) kde w = maximálna šírka stromu/grafu

---

### BFS vs DFS - Kedy čo použiť?

| Kritérium | BFS | DFS |
|-----------|-----|-----|
| Najkratšia cesta | Áno (neohodnotený graf) | Nie |
| Pamäť | Viac (celá úroveň) | Menej (len cesta) |
| Úplnosť | Vždy nájde riešenie | Môže sa zaseknúť |
| Implementácia | Queue | Stack/rekurzia |

**Použite BFS keď:**
- Hľadáte najkratšiu cestu
- Graf je plytký a široký
- Potrebujete najbližšie riešenie

**Použite DFS keď:**
- Hľadáte akékoľvek riešenie
- Graf je hlboký
- Potrebujete ušetriť pamäť

---

### Praktické úlohy

#### Úloha 10.1: Zigzag Level Order
Implementuj zigzag level order traversal - párne úrovne zľava doprava, nepárne sprava doľava.

#### Úloha 10.2: Bipartitný graf
Zisti pomocou BFS, či je graf bipartitný (dá sa ofarbiť dvoma farbami).

#### Úloha 10.3: Word Ladder
Nájdi najkratšiu postupnosť transformácií slov (napr. "hit" → "hot" → "dot" → "dog" → "cog").

---

## Úloha 11: Binárne vyhľadávanie - Rýchle hľadanie v zoradenom poli

**Čo sa naučíš:** Ako efektívne hľadať v zoradených dátach pomocou binary search v C++

### Teória - Prečo binárne vyhľadávanie?

**Lineárne vyhľadávanie:** Prejdi všetky prvky → O(n)

**Binárne vyhľadávanie:** Rozdeľuj a panuj → O(log n)

**Podmienka:** Dáta musia byť **zoradené**!

**Analógia:** Hľadanie slova v slovníku - nelistuješ od začiatku, otvoríš niekde uprostred.

### Vizualizácia

```
Hľadanie čísla 23 v zoradenom poli:

[2, 5, 8, 12, 16, 23, 38, 56, 72, 91]
 0  1  2   3   4   5   6   7   8   9

Krok 1: left=0, right=9, mid=4
        arr[4]=16 < 23, hľadaj VPRAVO
        [2, 5, 8, 12, 16, 23, 38, 56, 72, 91]
                       ^   ←───────────────→

Krok 2: left=5, right=9, mid=7
        arr[7]=56 > 23, hľadaj VĽAVO
        [2, 5, 8, 12, 16, 23, 38, 56, 72, 91]
                          ←───→  ^

Krok 3: left=5, right=6, mid=5
        arr[5]=23 == 23, NÁJDENÉ!
        [2, 5, 8, 12, 16, 23, 38, 56, 72, 91]
                          ^

Počet krokov: 3 (namiesto 6 pri lineárnom)
```

---

### Krok za krokom

#### Krok 1: Základná implementácia

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

/**
 * Binary Search - rôzne implementácie.
 */
class BinarySearch {
public:
    /**
     * Iteratívne binárne vyhľadávanie.
     * Vráti index prvku alebo -1 ak neexistuje.
     */
    static int searchIterative(const vector<int>& arr, int target) {
        int left = 0;
        int right = arr.size() - 1;
        int steps = 0;

        cout << "Hladanie " << target << " (iterativne):" << endl;

        while (left <= right) {
            steps++;
            int mid = left + (right - left) / 2;  // Bezpečné pred overflow

            cout << "   Krok " << steps << ": left=" << left
                 << ", right=" << right << ", mid=" << mid
                 << ", arr[mid]=" << arr[mid] << endl;

            if (arr[mid] == target) {
                cout << "   NAJDENE na indexe " << mid << endl;
                return mid;
            } else if (arr[mid] < target) {
                cout << "   " << arr[mid] << " < " << target << ", idem VPRAVO" << endl;
                left = mid + 1;
            } else {
                cout << "   " << arr[mid] << " > " << target << ", idem VLAVO" << endl;
                right = mid - 1;
            }
        }

        cout << "   NENAJDENE po " << steps << " krokoch" << endl;
        return -1;
    }

    /**
     * Rekurzívne binárne vyhľadávanie.
     */
    static int searchRecursive(const vector<int>& arr, int target,
                               int left, int right) {
        if (left > right) return -1;

        int mid = left + (right - left) / 2;

        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            return searchRecursive(arr, target, mid + 1, right);
        } else {
            return searchRecursive(arr, target, left, mid - 1);
        }
    }
};
```

---

#### Krok 2: Lower Bound a Upper Bound

```cpp
/**
 * Lower/Upper Bound - dôležité pre rozsahy.
 */
class BoundSearch {
public:
    /**
     * Lower Bound: Nájdi prvý index kde arr[i] >= target.
     * Užitočné pre: "koľko prvkov je menších ako X?"
     */
    static int lowerBound(const vector<int>& arr, int target) {
        int left = 0;
        int right = arr.size();

        cout << "Lower bound pre " << target << ":" << endl;

        while (left < right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] < target) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        cout << "   Vysledok: index " << left << endl;
        return left;
    }

    /**
     * Upper Bound: Nájdi prvý index kde arr[i] > target.
     * Užitočné pre: "koľko prvkov je <= X?"
     */
    static int upperBound(const vector<int>& arr, int target) {
        int left = 0;
        int right = arr.size();

        cout << "Upper bound pre " << target << ":" << endl;

        while (left < right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] <= target) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }

        cout << "   Vysledok: index " << left << endl;
        return left;
    }

    /**
     * Počet výskytov hodnoty v zoradenom poli.
     */
    static int countOccurrences(const vector<int>& arr, int target) {
        int lb = lowerBound(arr, target);
        int ub = upperBound(arr, target);
        return ub - lb;
    }
};
```

---

#### Krok 3: Pokročilé aplikácie

```cpp
/**
 * Pokročilé aplikácie binary search.
 */
class AdvancedBinarySearch {
public:
    /**
     * Nájdi peak element (vrchol) - prvok väčší ako susedia.
     */
    static int findPeak(const vector<int>& arr) {
        int left = 0;
        int right = arr.size() - 1;

        cout << "Hladanie peak elementu:" << endl;

        while (left < right) {
            int mid = left + (right - left) / 2;

            cout << "   mid=" << mid << ", arr[mid]=" << arr[mid]
                 << ", arr[mid+1]=" << arr[mid + 1] << endl;

            if (arr[mid] < arr[mid + 1]) {
                // Stúpame, peak je vpravo
                left = mid + 1;
            } else {
                // Klesáme alebo plateau, peak je tu alebo vľavo
                right = mid;
            }
        }

        cout << "   Peak na indexe " << left << " = " << arr[left] << endl;
        return left;
    }

    /**
     * Binary search na odpoveď - nájdi minimálnu kapacitu lode.
     * Problém: Preprav tovar za D dní, minimalizuj kapacitu lode.
     */
    static int shipWithinDays(const vector<int>& weights, int days) {
        // Minimálna kapacita = najťažší balík
        int left = *max_element(weights.begin(), weights.end());
        // Maximálna kapacita = súčet všetkých
        int right = accumulate(weights.begin(), weights.end(), 0);

        cout << "Hladanie minimalnej kapacity lode:" << endl;
        cout << "   Rozsah: [" << left << ", " << right << "]" << endl;

        while (left < right) {
            int mid = left + (right - left) / 2;
            int daysNeeded = countDays(weights, mid);

            cout << "   Kapacita " << mid << " -> " << daysNeeded << " dni" << endl;

            if (daysNeeded <= days) {
                right = mid;  // Skúsime menšiu kapacitu
            } else {
                left = mid + 1;  // Potrebujeme väčšiu
            }
        }

        cout << "   Minimalna kapacita: " << left << endl;
        return left;
    }

private:
    static int countDays(const vector<int>& weights, int capacity) {
        int days = 1;
        int currentLoad = 0;

        for (int w : weights) {
            if (currentLoad + w > capacity) {
                days++;
                currentLoad = w;
            } else {
                currentLoad += w;
            }
        }

        return days;
    }

public:
    /**
     * Nájdi v rotovanom zoradenom poli.
     * Napríklad: [4, 5, 6, 7, 0, 1, 2]
     */
    static int searchRotated(const vector<int>& arr, int target) {
        int left = 0;
        int right = arr.size() - 1;

        cout << "Hladanie " << target << " v rotovanom poli:" << endl;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            cout << "   left=" << left << ", right=" << right
                 << ", mid=" << mid << ", arr[mid]=" << arr[mid] << endl;

            if (arr[mid] == target) {
                return mid;
            }

            // Ktorá polovica je zoradená?
            if (arr[left] <= arr[mid]) {
                // Ľavá polovica je zoradená
                if (target >= arr[left] && target < arr[mid]) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            } else {
                // Pravá polovica je zoradená
                if (target > arr[mid] && target <= arr[right]) {
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }

        return -1;
    }
};
```

---

#### Krok 4: Hlavný program

```cpp
int main() {
    cout << "============================================================" << endl;
    cout << "BINARNE VYHLADAVANIE" << endl;
    cout << "============================================================" << endl;

    // Základné vyhľadávanie
    cout << "\n--- ZAKLADNE VYHLADAVANIE ---" << endl;
    vector<int> arr = {2, 5, 8, 12, 16, 23, 38, 56, 72, 91};
    cout << "Pole: ";
    for (int x : arr) cout << x << " ";
    cout << endl << endl;

    BinarySearch::searchIterative(arr, 23);
    cout << endl;
    BinarySearch::searchIterative(arr, 25);

    // Lower/Upper bound
    cout << "\n--- LOWER/UPPER BOUND ---" << endl;
    vector<int> arr2 = {1, 2, 2, 2, 3, 4, 4, 5};
    cout << "Pole: ";
    for (int x : arr2) cout << x << " ";
    cout << endl << endl;

    BoundSearch::lowerBound(arr2, 2);
    BoundSearch::upperBound(arr2, 2);
    cout << "Pocet 2-jok: " << BoundSearch::countOccurrences(arr2, 2) << endl;

    // Peak element
    cout << "\n--- PEAK ELEMENT ---" << endl;
    vector<int> arr3 = {1, 3, 8, 12, 4, 2};
    cout << "Pole: ";
    for (int x : arr3) cout << x << " ";
    cout << endl;
    AdvancedBinarySearch::findPeak(arr3);

    // Rotované pole
    cout << "\n--- ROTOVANE POLE ---" << endl;
    vector<int> arr4 = {4, 5, 6, 7, 0, 1, 2};
    cout << "Pole: ";
    for (int x : arr4) cout << x << " ";
    cout << endl;
    int idx = AdvancedBinarySearch::searchRotated(arr4, 0);
    cout << "Index 0: " << idx << endl;

    cout << "============================================================" << endl;

    return 0;
}
```

---

### Časová zložitosť

| Operácia | Zložitosť |
|----------|-----------|
| Binary search | O(log n) |
| Lower/Upper bound | O(log n) |
| STL binary_search | O(log n) |

**Porovnanie s lineárnym:**
- n = 1 000 000: Linear = 1M porovnaní, Binary = 20 porovnaní

---

### C++ STL funkcie

```cpp
#include <algorithm>

vector<int> arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

// binary_search - vráti true/false
bool found = binary_search(arr.begin(), arr.end(), 5);

// lower_bound - iterator na prvý >= target
auto lb = lower_bound(arr.begin(), arr.end(), 5);
int index = lb - arr.begin();

// upper_bound - iterator na prvý > target
auto ub = upper_bound(arr.begin(), arr.end(), 5);

// equal_range - vráti pair(lower_bound, upper_bound)
auto [lo, hi] = equal_range(arr.begin(), arr.end(), 5);
int count = hi - lo;  // Počet výskytov
```

---

### Časté chyby a ako sa im vyhnúť

| Chyba | Prečo nastáva | Riešenie |
|-------|---------------|----------|
| Integer overflow | `(left + right) / 2` pretečie | `left + (right - left) / 2` |
| Nekonečná slučka | Nesprávne `left = mid` | Vždy `mid + 1` alebo `mid - 1` |
| Off-by-one | Nesprávne hranice | Premysli: inclusive vs exclusive |
| Nezoradené pole | Binary search nefunguje | Vždy over, že pole je zoradené |

---

### Skús sám - Doplň chýbajúci kód

```cpp
int binarySearch(const vector<int>& arr, int target) {
    int left = 0;
    int right = _________________________________;

    while (_________________________________) {
        // Bezpečný výpočet mid
        int mid = _________________________________;

        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            left = _________________________________;
        } else {
            right = _________________________________;
        }
    }

    return -1;
}
```

<details>
<summary>Riešenie (klikni pre zobrazenie)</summary>

```cpp
int right = arr.size() - 1;

while (left <= right)

int mid = left + (right - left) / 2;

left = mid + 1;
right = mid - 1;
```
</details>

---

### Praktické úlohy

#### Úloha 11.1: Prvý a posledný výskyt
Nájdi prvý a posledný výskyt hodnoty v zoradenom poli.

#### Úloha 11.2: Druhá odmocnina
Implementuj `sqrt(x)` pomocou binary search (celočíselná verzia).

#### Úloha 11.3: Minimálne maximum
Rozdeľ pole na k častí tak, aby maximálny súčet časti bol minimálny.

---

## Úloha 12: Huffmanovo kódovanie - Kompresia dát

**Čo sa naučíš:** Ako komprimovať dáta pomocou Huffmanovho algoritmu v C++

### Teória - Čo je Huffmanovo kódovanie?

**Problém:** Štandardné kódovanie (ASCII) používa 8 bitov pre každý znak, aj keď niektoré znaky sú častejšie.

**Huffmanovo kódovanie:**
- **Frekventné znaky** = **krátke kódy**
- **Zriedkavé znaky** = **dlhšie kódy**
- **Prefix-free:** Žiadny kód nie je prefixom iného

**Analógia:** Morseova abeceda - 'E' je len ".", zatiaľ čo 'Q' je "-- · -".

### Vizualizácia - Huffmanov strom

```
Text: "ABRACADABRA"
Frekvencie: A=5, B=2, R=2, C=1, D=1

Budovanie stromu (min-heap):
Krok 1: Spoj najmenšie: C(1) + D(1) = CD(2)
Krok 2: Spoj: B(2) + R(2) = BR(4)
Krok 3: Spoj: CD(2) + BR(4) = CDBR(6)  [alebo CD + A]
Krok 4: Spoj: A(5) + CDBR(6) = root(11)

Huffmanov strom:
            [11]
           /    \
         [A]    [6]
         (5)   /    \
             [2]    [BR]
            /   \   /   \
          [C]  [D][B]  [R]
          (1)  (1)(2)  (2)

Kódy:
A = 0       (1 bit)
C = 100     (3 bity)
D = 101     (3 bity)
B = 110     (3 bity)
R = 111     (3 bity)

Originál:   11 znakov × 8 bitov = 88 bitov
Komprimované: 5×1 + 2×3 + 2×3 + 1×3 + 1×3 = 23 bitov
Úspora: 74%!
```

---

### Krok za krokom

#### Krok 1: Štruktúra Huffmanovho uzla

```cpp
#include <iostream>
#include <queue>
#include <unordered_map>
#include <string>
using namespace std;

/**
 * Uzol Huffmanovho stromu.
 */
struct HuffmanNode {
    char ch;           // Znak (pre listy)
    int freq;          // Frekvencia
    HuffmanNode* left;
    HuffmanNode* right;

    HuffmanNode(char c, int f) : ch(c), freq(f), left(nullptr), right(nullptr) {}

    // Pre vnútorné uzly
    HuffmanNode(int f, HuffmanNode* l, HuffmanNode* r)
        : ch('\0'), freq(f), left(l), right(r) {}

    bool isLeaf() const {
        return left == nullptr && right == nullptr;
    }
};

/**
 * Komparátor pre min-heap.
 */
struct Compare {
    bool operator()(HuffmanNode* a, HuffmanNode* b) {
        return a->freq > b->freq;  // Min-heap podľa frekvencie
    }
};
```

---

#### Krok 2: Huffman Encoder/Decoder

```cpp
/**
 * Huffmanovo kódovanie.
 */
class HuffmanCoding {
private:
    HuffmanNode* root;
    unordered_map<char, string> codes;      // Znak -> kód
    unordered_map<string, char> reverseCodes; // Kód -> znak

    /**
     * Rekurzívne generovanie kódov.
     */
    void generateCodes(HuffmanNode* node, string code) {
        if (node == nullptr) return;

        if (node->isLeaf()) {
            codes[node->ch] = code.empty() ? "0" : code;
            reverseCodes[code.empty() ? "0" : code] = node->ch;
            cout << "   '" << node->ch << "' -> " << (code.empty() ? "0" : code)
                 << " (frekvencia: " << node->freq << ")" << endl;
            return;
        }

        generateCodes(node->left, code + "0");
        generateCodes(node->right, code + "1");
    }

    /**
     * Rekurzívne zmazanie stromu.
     */
    void destroyTree(HuffmanNode* node) {
        if (node == nullptr) return;
        destroyTree(node->left);
        destroyTree(node->right);
        delete node;
    }

    /**
     * Vizualizácia stromu.
     */
    void printTree(HuffmanNode* node, string prefix, bool isLeft) const {
        if (node == nullptr) return;

        cout << prefix << (isLeft ? "├── " : "└── ");
        if (node->isLeaf()) {
            cout << "'" << node->ch << "' (" << node->freq << ")" << endl;
        } else {
            cout << "[" << node->freq << "]" << endl;
        }

        printTree(node->left, prefix + (isLeft ? "│   " : "    "), true);
        printTree(node->right, prefix + (isLeft ? "│   " : "    "), false);
    }

public:
    HuffmanCoding() : root(nullptr) {}

    ~HuffmanCoding() {
        destroyTree(root);
    }

    /**
     * Postav Huffmanov strom z textu.
     */
    void buildTree(const string& text) {
        cout << "=== BUDOVANIE HUFFMANOVHO STROMU ===" << endl;
        cout << "Text: \"" << text << "\"" << endl;
        cout << "Dlzka: " << text.length() << " znakov" << endl << endl;

        // Krok 1: Spočítaj frekvencie
        unordered_map<char, int> freq;
        for (char c : text) {
            freq[c]++;
        }

        cout << "Frekvencie:" << endl;
        for (auto& [ch, f] : freq) {
            cout << "   '" << ch << "': " << f << endl;
        }
        cout << endl;

        // Krok 2: Vytvor min-heap
        priority_queue<HuffmanNode*, vector<HuffmanNode*>, Compare> pq;

        for (auto& [ch, f] : freq) {
            pq.push(new HuffmanNode(ch, f));
        }

        // Krok 3: Buduj strom
        cout << "Budovanie stromu:" << endl;
        int step = 0;

        while (pq.size() > 1) {
            step++;
            HuffmanNode* left = pq.top(); pq.pop();
            HuffmanNode* right = pq.top(); pq.pop();

            int sum = left->freq + right->freq;
            HuffmanNode* parent = new HuffmanNode(sum, left, right);
            pq.push(parent);

            cout << "   Krok " << step << ": Spojene ";
            if (left->isLeaf()) cout << "'" << left->ch << "'";
            else cout << "[" << left->freq << "]";
            cout << " + ";
            if (right->isLeaf()) cout << "'" << right->ch << "'";
            else cout << "[" << right->freq << "]";
            cout << " = [" << sum << "]" << endl;
        }

        root = pq.top();
        cout << endl;

        // Krok 4: Generuj kódy
        cout << "Huffmanove kody:" << endl;
        generateCodes(root, "");
        cout << endl;
    }

    /**
     * Zakóduj text.
     */
    string encode(const string& text) {
        string encoded = "";
        for (char c : text) {
            encoded += codes[c];
        }
        return encoded;
    }

    /**
     * Dekóduj bitový reťazec.
     */
    string decode(const string& encoded) {
        string decoded = "";
        HuffmanNode* current = root;

        for (char bit : encoded) {
            if (bit == '0') {
                current = current->left;
            } else {
                current = current->right;
            }

            if (current->isLeaf()) {
                decoded += current->ch;
                current = root;
            }
        }

        return decoded;
    }

    /**
     * Štatistiky kompresie.
     */
    void printStats(const string& original, const string& encoded) {
        int originalBits = original.length() * 8;
        int encodedBits = encoded.length();
        double ratio = (1.0 - (double)encodedBits / originalBits) * 100;

        cout << "=== STATISTIKY KOMPRESIE ===" << endl;
        cout << "Original: " << original.length() << " znakov = "
             << originalBits << " bitov" << endl;
        cout << "Komprimovane: " << encodedBits << " bitov" << endl;
        cout << "Kompresny pomer: " << ratio << "%" << endl;
    }

    /**
     * Zobraz strom.
     */
    void printTree() const {
        cout << "Huffmanov strom:" << endl;
        printTree(root, "", false);
    }
};
```

---

#### Krok 3: Hlavný program

```cpp
int main() {
    cout << "============================================================" << endl;
    cout << "HUFFMANOVO KODOVANIE - Kompresia dat" << endl;
    cout << "============================================================" << endl;
    cout << endl;

    HuffmanCoding hc;

    // Test 1: Jednoduchý text
    string text = "ABRACADABRA";
    hc.buildTree(text);
    hc.printTree();

    string encoded = hc.encode(text);
    cout << "\nZakodovany text: " << encoded << endl;

    string decoded = hc.decode(encoded);
    cout << "Dekodovany text: " << decoded << endl;

    hc.printStats(text, encoded);

    // Test 2: Dlhší text
    cout << "\n============================================================" << endl;
    cout << "\nTest 2 - dlhsi text:" << endl;

    HuffmanCoding hc2;
    string text2 = "the quick brown fox jumps over the lazy dog";
    hc2.buildTree(text2);

    string encoded2 = hc2.encode(text2);
    string decoded2 = hc2.decode(encoded2);

    cout << "Original: " << text2 << endl;
    cout << "Dekodovane: " << decoded2 << endl;
    cout << "Zhoda: " << (text2 == decoded2 ? "ANO" : "NIE") << endl;

    hc2.printStats(text2, encoded2);

    cout << "\n============================================================" << endl;

    return 0;
}
```

---

### Časová zložitosť

| Operácia | Zložitosť |
|----------|-----------|
| Budovanie stromu | O(n log n) |
| Kódovanie | O(n) |
| Dekódovanie | O(m) kde m = dĺžka zakódovaného textu |

**Priestorová zložitosť:** O(k) kde k = počet unikátnych znakov

---

### Použitie v praxi

- **ZIP, GZIP** - používajú varianty Huffmanovho kódovania
- **JPEG, MP3** - súčasť kompresného pipeline
- **Fax** - Run-Length + Huffman

---

### Praktické úlohy

#### Úloha 12.1: Súbor
Implementuj kompresor súborov pomocou Huffmanovho kódovania.

#### Úloha 12.2: Adaptive Huffman
Implementuj adaptívne Huffmanovo kódovanie, ktoré mení strom počas kódovania.

#### Úloha 12.3: Porovnanie
Porovnaj kompresný pomer pre rôzne typy textov (anglický, zdrojový kód, náhodné dáta).

---

## Zhrnutie - Čo si sa naučil?

### Grafové algoritmy

- **Kruskalov algoritmus**: Minimálna kostra, Union-Find v C++
- **Primov algoritmus**: Minimálna kostra, prioritná fronta v C++
- **Dijkstrov algoritmus**: Najkratšie cesty, greedy prístup v C++

### Dátové štruktúry

- **Hash Mapy**: O(1) vyhľadávanie v C++, kolízie, `std::unordered_map`

### Stromové štruktúry

- **Binárny strom**: Základná hierarchická štruktúra, rekurzia
- **BST (Binary Search Tree)**: Usporiadané vyhľadávanie O(log n)
- **AVL strom**: Samovyvažovanie pomocou rotácií
- **B-strom**: Multi-way stromy pre databázy a súborové systémy

### Algoritmy na prehľadávanie

- **DFS (Depth-First Search)**: Stack/rekurzia, pre-order/in-order/post-order
- **BFS (Breadth-First Search)**: Queue, level-order, najkratšia cesta
- **Binárne vyhľadávanie**: O(log n) v zoradených dátach, lower/upper bound

### Kompresia

- **Huffmanovo kódovanie**: Prefix-free kódy, prioritná fronta, kompresný pomer

### Kľúčové koncepty C++

- **STL kontajnery**: `vector`, `list`, `queue`, `stack`, `priority_queue`, `unordered_map`
- **Templates**: Generické programovanie
- **Pair a Tuple**: Viacnásobné návratové hodnoty
- **Range-based for**: Moderná iterácia cez kontajnery
- **Auto keyword**: Automatická dedukcia typu
- **Structured bindings** (C++17): `auto [a, b] = pair`

---

## Kontrolné otázky - Over si, či rozumieš

### Kruskalov algoritmus

1. **Prečo triedime hrany na začiatku?**
   <details><summary>Odpoveď</summary>
   Aby sme vždy vybrali hranu s najmenšou váhou, ktorá nevytvori cyklus. Greedy prístup.
   </details>

2. **Čo sa stane, ak zabudneme na Union-Find a použijeme len pole `visited`?**
   <details><summary>Odpoveď</summary>
   Nebudeme správne detekovať cykly. Pole visited funguje len pre súvislý strom, nie pre les (viacero stromov).
   </details>

3. **Koľko hrán má minimálna kostra grafu s n vrcholmi?**
   <details><summary>Odpoveď</summary>
   Presne n-1 hrán. Menej = nesúvislý, viac = obsahuje cyklus.
   </details>

### Primov algoritmus

4. **Prečo je dôležité kontrolovať `visited[u]` hneď po vytiahnutí z fronty?**
   <details><summary>Odpoveď</summary>
   Pretože vo fronte môžu byť duplicitné záznamy pre ten istý vrchol s rôznymi váhami. Spracujeme len prvý (najmenší).
   </details>

5. **Zmení sa celková váha MST, ak začneme z iného vrcholu?**
   <details><summary>Odpoveď</summary>
   Nie, celková váha MST je vždy rovnaká (ak je MST unikátna). Môže sa zmeniť len poradie hrán.
   </details>

### Dijkstrov algoritmus

6. **Prečo Dijkstra nefunguje pre záporné váhy? Uveď príklad.**
   <details><summary>Odpoveď</summary>
   Graf: 0->1(1), 0->2(4), 1->2(-5). Dijkstra nájde 0->2 s váhou 4 a označí vrchol 2 ako hotový. Ale kratšia cesta je 0->1->2 s váhou 1+(-5)=-4.
   </details>

7. **Aký je rozdiel medzi `dist[u]` a `currentDist` vo fronte?**
   <details><summary>Odpoveď</summary>
   `dist[u]` je aktuálne najlepšia známa vzdialenosť. `currentDist` je vzdialenosť v momente vloženia do fronty - môže byť zastaraná.
   </details>

### Hash Mapy

8. **Čo je to load factor a prečo je dôležitý?**
   <details><summary>Odpoveď</summary>
   Load factor = počet_prvkov / veľkosť_tabuľky. Ak je príliš vysoký (>0.7), narastá počet kolízií a výkon degraduje z O(1) na O(n).
   </details>

9. **Prečo potrebujeme "tombstone" pri mazaní v linear probing?**
   <details><summary>Odpoveď</summary>
   Ak zmažeme prvok v strede reťazca kolízií, preruší sa vyhľadávanie. Tombstone hovorí "tu niečo bolo, pokračuj v hľadaní".
   </details>

10. **Aký je rozdiel medzi separate chaining a linear probing?**
    <details><summary>Odpoveď</summary>
    Separate chaining: každý slot má zoznam prvkov. Linear probing: pri kolízii hľadáme najbližší voľný slot v tabuľke.
    </details>

### Stromové štruktúry

11. **Aká je BST vlastnosť a prečo je dôležitá?**
    <details><summary>Odpoveď</summary>
    Všetky hodnoty v ľavom podstrome sú menšie ako koreň, všetky v pravom sú väčšie. Umožňuje O(log n) vyhľadávanie.
    </details>

12. **Prečo potrebujeme AVL stromy? Čo riešia?**
    <details><summary>Odpoveď</summary>
    BST môže degenerovať na linked list (O(n) operácie). AVL garantuje vyváženie pomocou rotácií → vždy O(log n).
    </details>

13. **Kedy použijeme pravú rotáciu v AVL?**
    <details><summary>Odpoveď</summary>
    Keď je balance factor > 1 (ľavý podstrom je príliš vysoký) a nová hodnota bola vložená do ľavého podstromu ľavého potomka (Left-Left case).
    </details>

14. **Prečo sú B-stromy vhodné pre databázy?**
    <details><summary>Odpoveď</summary>
    Majú veľa kľúčov v jednom uzle → menej prístupov na disk. Pre t=100 a 1M prvkov: výška ~3 namiesto ~20 v BST.
    </details>

### Algoritmy na prehľadávanie

15. **Aký je rozdiel medzi DFS a BFS?**
    <details><summary>Odpoveď</summary>
    DFS ide do hĺbky (stack), BFS ide do šírky po úrovniach (queue). BFS nájde najkratšiu cestu v neohodnotenom grafe.
    </details>

16. **Kedy použijeme in-order traversal?**
    <details><summary>Odpoveď</summary>
    Pre výpis zoradených hodnôt v BST. In-order: ľavý → koreň → pravý.
    </details>

17. **Prečo je binárne vyhľadávanie O(log n)?**
    <details><summary>Odpoveď</summary>
    V každom kroku eliminujeme polovicu zostávajúcich prvkov. Po k krokoch zostáva n/2^k prvkov → k = log₂(n).
    </details>

18. **Aký je rozdiel medzi lower_bound a upper_bound?**
    <details><summary>Odpoveď</summary>
    lower_bound: prvý index kde arr[i] >= target. upper_bound: prvý index kde arr[i] > target. Rozdiel = počet výskytov.
    </details>

### Huffmanovo kódovanie

19. **Prečo sú Huffmanove kódy prefix-free?**
    <details><summary>Odpoveď</summary>
    Lebo každý znak je v liste stromu. Žiadny kód nie je prefixom iného → jednoznačné dekódovanie bez separátorov.
    </details>

20. **Ako funguje Huffmanov algoritmus?**
    <details><summary>Odpoveď</summary>
    1) Spočítaj frekvencie, 2) Vytvor min-heap, 3) Opakuj: spoj dva najmenšie, 4) Čítaj kódy od koreňa k listom (0=ľavo, 1=pravo).
    </details>

---

## Cheat Sheet 

### Časové zložitosti - Prehľad

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║  DÁTOVÁ ŠTRUKTÚRA        │ VYHĽADÁVANIE │ VKLADANIE │ MAZANIE │ PRIESTOR     ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║  Pole (Array)            │ O(n)         │ O(n)      │ O(n)    │ O(n)         ║
║  Zoradené pole           │ O(log n)     │ O(n)      │ O(n)    │ O(n)         ║
║  Linked List             │ O(n)         │ O(1)*     │ O(1)*   │ O(n)         ║
║  Hash Mapa               │ O(1) avg     │ O(1) avg  │ O(1) avg│ O(n)         ║
║  BST (nevyvážený)        │ O(n) worst   │ O(n) worst│ O(n)    │ O(n)         ║
║  BST (vyvážený/AVL)      │ O(log n)     │ O(log n)  │ O(log n)│ O(n)         ║
║  B-strom                 │ O(log n)     │ O(log n)  │ O(log n)│ O(n)         ║
╚═══════════════════════════════════════════════════════════════════════════════╝
* ak máme ukazovateľ na miesto
```

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║  ALGORITMUS              │ ČASOVÁ ZLOŽITOSŤ           │ PRIESTOROVÁ          ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║  DFS (strom/graf)        │ O(V + E) alebo O(n)        │ O(h) rekurzia        ║
║  BFS (strom/graf)        │ O(V + E) alebo O(n)        │ O(w) šírka           ║
║  Binárne vyhľadávanie    │ O(log n)                   │ O(1) iter, O(log n)  ║
║  Kruskal                 │ O(E log E)                 │ O(V)                 ║
║  Prim                    │ O(E log V)                 │ O(V)                 ║
║  Dijkstra                │ O(E log V)                 │ O(V)                 ║
║  Huffman (build)         │ O(n log n)                 │ O(n)                 ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

---

### Stromové štruktúry - Rýchly prehľad

```
BINÁRNY STROM              BST (Binary Search Tree)      AVL STROM
      [A]                        [50]                       [50]
     /   \                      /    \                     /    \
   [B]   [C]                 [30]    [70]               [30]    [70]
   / \     \                 /  \    /  \               /  \    /  \
 [D] [E]   [F]            [20][40][60][80]           [20][40][60][80]

Max 2 deti               left < root < right         |balance| ≤ 1
na uzol                  O(log n) ak vyvážený        Garantovaný O(log n)
```

**BST vlastnosť:** `všetko_vľavo < koreň < všetko_vpravo`

**AVL balance factor:** `výška(ľavý) - výška(pravý)` musí byť -1, 0, alebo 1

---

### Rotácie AVL - Vizuálne

```
PRAVÁ ROTÁCIA (LL case):        ĽAVÁ ROTÁCIA (RR case):
     [y]          [x]                [x]          [y]
     /           /   \                 \         /   \
   [x]    →    [A]   [y]              [y]  →   [x]   [C]
   /                 /                  \       \
 [A]               [B]                 [C]      [B]

ĽAVO-PRAVÁ (LR):               PRAVO-ĽAVÁ (RL):
   [z]       [z]      [y]         [x]      [x]       [y]
   /         /       /   \          \        \      /   \
 [x]   →   [y]  →  [x]   [z]       [z] →    [y] → [x]   [z]
   \       /                       /          \
   [y]   [x]                     [y]          [z]
```

---

### DFS vs BFS

```
DFS (Depth-First Search)              BFS (Breadth-First Search)
─────────────────────────             ─────────────────────────
Dátová štruktúra: STACK               Dátová štruktúra: QUEUE
Implementácia: Rekurzia/Stack         Implementácia: Queue (fronta)

Poradie:    1→2→4→5→3→6               Poradie:    1→2→3→4→5→6
        [1]                                   [1]
       /   \                                 /   \
     [2]   [3]                             [2]   [3]
     / \     \                             / \     \
   [4] [5]   [6]                         [4] [5]   [6]

Použitie:                             Použitie:
• Topologické triedenie               • Najkratšia cesta
• Detekcia cyklov                     • Level-order traversal
• Backtracking                        • Najbližší sused
```

**Traversal typy (DFS):**
```
Pre-order:  ROOT → Left → Right    (kopírovanie stromu)
In-order:   Left → ROOT → Right    (zoradené hodnoty v BST)
Post-order: Left → Right → ROOT    (mazanie stromu)
```

---

### Binárne vyhľadávanie - Vzorec

```cpp
int binarySearch(vector<int>& arr, int target) {
    int left = 0;
    int right = arr.size() - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;  // Bezpečné pred overflow!

        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;  // Nenájdené
}
```

**Lower/Upper bound:**
- `lower_bound`: prvý index kde `arr[i] >= target`
- `upper_bound`: prvý index kde `arr[i] > target`
- Počet výskytov: `upper_bound - lower_bound`

---

### Grafové algoritmy - Kedy čo použiť

| Problém | Algoritmus | Poznámka |
|---------|------------|----------|
| Minimálna kostra (riedky graf) | **Kruskal** | Triedi hrany, Union-Find |
| Minimálna kostra (hustý graf) | **Prim** | Podobný Dijkstrovi |
| Najkratšia cesta (1 zdroj) | **Dijkstra** | Len nezáporné váhy! |
| Najkratšia cesta (záporné váhy) | **Bellman-Ford** | Pomalší, O(VE) |
| Najkratšia cesta (všetky páry) | **Floyd-Warshall** | O(V³) |

**Kruskal:**
```
1. Zoraď hrany podľa váhy
2. Pre každú hranu: ak nespojí cyklus → pridaj do MST
3. Použij Union-Find na detekciu cyklov
```

**Dijkstra:**
```
1. dist[start] = 0, ostatné = ∞
2. Vyber uzol s najmenšou vzdialenosťou
3. Relaxuj susedov: ak dist[u] + w < dist[v] → aktualizuj
4. Opakuj kým nie je prázdna prioritná fronta
```

---

### Hash Mapy - Riešenie kolízií

```
SEPARATE CHAINING:              LINEAR PROBING:
┌───┐                           ┌───┐
│ 0 │→ [A:5]                    │ 0 │ A:5
├───┤                           ├───┤
│ 1 │→ [B:3]→[C:7]              │ 1 │ B:3
├───┤                           ├───┤
│ 2 │→ null                     │ 2 │ C:7  ← posunuté z indexu 1
└───┘                           └───┘

Každý slot má linked list       Hľadaj najbližší voľný slot
```

**Load factor = n / capacity** → ak > 0.7, zväčši tabuľku

---

### Huffmanovo kódovanie

```
Text: "AABBC"
Frekvencie: A=2, B=2, C=1

Postup:
1. Min-heap: [C:1, A:2, B:2]
2. Spoj C+A → [3]: heap = [[3], B:2]
3. Spoj [3]+B → [5]: heap = [[5]]

Strom:        Kódy:
   [5]        A = 01
  /   \       B = 1
[3]   [B]     C = 00
/  \
[C] [A]

Prefix-free: Žiadny kód nie je prefix iného
```

---

### Vzorce na pamätanie

```
Výška vyváženého stromu:     h = O(log n)
Počet uzlov plného stromu:   n = 2^(h+1) - 1
Počet listov:                l = ⌈n/2⌉
Počet hrán v strome:         e = n - 1

BST:
  In-order traversal = zoradené hodnoty

AVL:
  Balance factor = height(left) - height(right)
  |BF| > 1 → potrebná rotácia

MST (Minimum Spanning Tree):
  Počet hrán = V - 1

Hash mapa:
  Load factor = n / capacity
  Rehash keď LF > 0.7
```

---

### Kedy použiť ktorú štruktúru

| Potrebujem... | Použi... |
|---------------|----------|
| Rýchle vyhľadávanie O(1) | Hash mapa |
| Zoradené dáta + rýchle vyhľadávanie | BST/AVL |
| Najkratšia cesta | BFS (nevážený) / Dijkstra (vážený) |
| Minimálna kostra | Kruskal / Prim |
| Hierarchická štruktúra | Strom |
| FIFO (First In First Out) | Queue |
| LIFO (Last In First Out) | Stack |
| Kompresia | Huffman |

---

### Najčastejšie chyby

```cpp
// 1. Integer overflow pri mid
int mid = (left + right) / 2;           // CHYBA
int mid = left + (right - left) / 2;    // SPRAVNE

// 2. Zabudnutý nullptr check
if (root->left->data == x)              // CHYBA (čo ak left je null?)
if (root->left && root->left->data == x) // SPRAVNE

// 3. Nesprávna priority_queue (default je max-heap)
priority_queue<int> pq;                          // max-heap
priority_queue<int, vector<int>, greater<int>> pq; // min-heap

// 4. BST mazanie - zabudnutie na prípad s 2 potomkami
// Treba nájsť in-order nasledovníka/predchodcu

// 5. AVL - nesprávne poradie aktualizácie výšok
// Vždy: najprv potomok, potom rodič
```

---

Ohodnoť sa na škále 1-5 (1=nerozumiem, 5=viem vysvetliť a implementovať):

| Téma | Hodnotenie |
|------|------------|
| **Grafové algoritmy** | |
| Kruskalov algoritmus - princíp | [ ] |
| Union-Find implementácia | [ ] |
| Primov algoritmus - princíp | [ ] |
| Dijkstrov algoritmus - princíp | [ ] |
| Relaxácia hrán | [ ] |
| **Dátové štruktúry** | |
| Hash funkcia a kolízie | [ ] |
| Separate chaining vs Linear probing | [ ] |
| **Stromové štruktúry** | |
| Binárny strom - rekurzia | [ ] |
| BST - insert, search, delete | [ ] |
| AVL - balance factor a rotácie | [ ] |
| B-strom - princíp a využitie | [ ] |
| **Prehľadávanie** | |
| DFS - rekurzívne aj iteratívne | [ ] |
| BFS - queue a level-order | [ ] |
| In-order, Pre-order, Post-order | [ ] |
| Binárne vyhľadávanie | [ ] |
| Lower/Upper bound | [ ] |
| **Kompresia** | |
| Huffmanovo kódovanie | [ ] |
| **C++ koncepty** | |
| Priority queue v C++ | [ ] |
| STL kontajnery (vector, queue, stack) | [ ] |
| Templates a auto | [ ] |

**Ak máš niekde menej ako 3, vráť sa k tej sekcii!**

---

## Ďalšie štúdium

### Pokročilé témy

1. **Graf ové algoritmy**:
   - Bellman-Ford (záporné váhy)
   - Floyd-Warshall (všetky páry ciest)
   - Topologické triedenie
2. **Pokročilé stromy**:

   - B-stromy (nasleduje v Úlohe 6)
   - AVL stromy (nasleduje v Úlohe 7)
   - Red-Black stromy
   - Segment stromy

3. **STL algoritmy**:
   - `std::sort`, `std::find`, `std::binary_search`
   - `std::accumulate`, `std::transform`
   - Vlastné komparátory a lambda funkcie

---
**Licencia:** Developed by Tomáš Mucha - Tento materiál je voľne použiteľný pre vzdelávacie účely.
