# Algoritmy a Dátové štruktúry - Cvičebné úlohy (C++)

## Obsah

1. [Kruskalov algoritmus](#úloha-1-kruskalov-algoritmus---minimálna-kostra-grafu)
2. [Primov algoritmus](#úloha-2-primov-algoritmus---iný-prístup-ku-koste)
3. [Dijkstrov algoritmus](#úloha-3-dijkstrov-algoritmus---najkratšie-cesty)
4. [Hash Mapy](#úloha-4-hash-mapy---rýchle-vyhľadávanie)
5. [Huffmanovo kódovanie](#úloha-5-huffmanovo-kódovanie---kompresia-dát)
6. [B-stromy](#úloha-6-b-stromy---vyvážené-stromy-pre-databázy)
7. [AVL stromy](#úloha-7-avl-stromy---samovyvažujúce-binárne-stromy)

---

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
