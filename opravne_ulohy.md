# Séria opravných úloh z algoritmizácie a dátových štruktúr by Tomáš Mucha

# Úloha 1: Maximálny súčet podpoľa (Kadane's Algorithm)

**Náročnosť:** ★★★★☆☆

---

## Zadanie

Napíšte algoritmus, ktorý v poli celých čísel nájde súvislé podpole s **maximálnym súčtom**.

Implementujte aj variantu, ktorá vráti **indexy začiatku a konca** tohto podpoľa.

---

### Príklad

**Vstup:**
```text
[-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

**Výstup:**
```text
6 (podpole [4, -1, 2, 1])
Indexy: začiatok = 3, koniec = 6
```

---

## Požadované implementácie

1. ✅ **Základná verzia Kadane's algoritmu** – časová zložitosť `O(n)`
2. ✅ **Rozšírenie pre vrátenie indexov** (začiatok, koniec podpoľa)
3. ✅ **Riešenie pre kruhové pole (circular array)**
4. ✅ **Riešenie pre 2D maticu** – nájsť maximálny súvislý obdĺžnik

---

## Hodnotenie

| Časť úlohy                  | Váha     |
|----------------------------|----------|
| Základný Kadane            | 30%      |
| Vrátenie indexov           | 20%      |
| Kruhové pole               | 25%      |
| 2D verzia                  | 25%      |

---

## Materiály na štúdium

- 🎥 **Video z SPŠIT KNM:** Dynamické programovanie
- 💻 **SPŠIT KNM GitHub:** Príklady algoritmov
- 📘 **GeeksforGeeks:** [Kadane's Algorithm](https://www.geeksforgeeks.org/kadanes-algorithm/)
- 📗 **Competitive Programming 3:** Kapitola o dynamickom programovaní

---

# Úloha 2: Union-Find s optimalizáciami

**Náročnosť:** ★★★★☆☆

---

## Zadanie

Implementujte dátovú štruktúru **Union-Find (Disjoint Set Union)** s pokročilými optimalizáciami.  
Použite ju na riešenie dvoch problémov:
- **Detekcia cyklov v neorientovanom grafe**
- **Hľadanie minimálnej kostry (Kruskal's algorithm)**

---

## Požiadavky

1. ✅ Základná implementácia Union-Find
2. ✅ **Path compression** optimalizácia
3. ✅ **Union by rank/size** optimalizácia
4. ✅ Aplikácia: **Detekcia cyklov** v grafe
5. ✅ Aplikácia: **Kruskalov algoritmus** pre minimálny kostrový strom (MST)

---

## Špecifikácia triedy

```cpp
class UnionFind {
    void makeSet(int x);
    int find(int x);
    void unionSets(int x, int y);
    bool isSameSet(int x, int y);
    int getSetSize(int x);
    int getNumberOfSets();
};
```

---

## Hodnotenie

| Časť úlohy           | Váha     |
|----------------------|----------|
| Základná implementácia | 25%    |
| Path compression       | 20%    |
| Union by rank/size     | 20%    |
| Detekcia cyklov        | 15%    |
| Kruskalov algoritmus   | 20%    |

---

## Materiály na štúdium

- 🎥 **SPŠIT KNM:** Video – Grafové algoritmy
- 📘 **Cormen:** Introduction to Algorithms – Kapitola o Union-Find
- 💻 **CP-Algorithms:** [DSU – Disjoint Set Union](https://cp-algorithms.com/data_structures/disjoint_set_union.html)
- 💡 **SPŠIT GitHub:** Príklady DSU implementácií

---

# Úloha 3: LRU Cache s pokročilými funkciami

**Náročnosť:** ★★★★★☆

---

## Zadanie

Implementujte **LRU Cache (Least Recently Used)** s časovou zložitosťou `O(1)` pre operácie `get` a `put`.  
Rozšírte základnú implementáciu o **pokročilé funkcie**, ktoré sa vyskytujú v reálnych systémoch cache.

---

## Základné požiadavky

- ✅ `get(key)` – návrat hodnoty pre daný kľúč, ak existuje, inak `-1` – `O(1)`
- ✅ `put(key, value)` – vloženie alebo aktualizácia hodnoty – `O(1)`
- ✅ Použitie **hash mapy** a **obojsmerne zreťazeného zoznamu** (doubly linked list)

---

## Rozšírené funkcie

1. 🔒 **Multi-threading support** – **thread-safe** implementácia
2. ⏳ **TTL (Time To Live)** – expirácia záznamov po určitom čase
3. 📊 **Štatistiky** – počítanie `hit rate` a `miss rate`
4. 💾 **Perzistencia na disk** – možnosť uloženia a načítania cache obsahu

---

## Príklad použitia (C++ štýl)

```cpp
LRUCache cache(3); // kapacita 3
cache.put(1, 10);
cache.put(2, 20);
cache.put(3, 30);
cache.get(1);     // vráti 10
cache.put(4, 40); // vyhodí kľúč 2 (najmenej používaný)
cache.get(2);     // vráti -1 (nenájdené)
```

---

## Hodnotenie

| Časť úlohy              | Váha     |
|-------------------------|----------|
| Základná implementácia  | 35%      |
| Thread-safety           | 25%      |
| TTL funkcionalita       | 20%      |
| Štatistiky + Perzistencia | 20%    |

---

## Materiály na štúdium

- 📚 **SPŠIT KNM:** Dátové štruktúry
- 📘 **Operating System Concepts (Silberschatz):** Kapitola o cache
- 💡 **LeetCode diskusia:** [Problem 146 – LRU Cache](https://leetcode.com/problems/lru-cache/)
- 📗 **Java Concurrency in Practice:** Thread-safety, synchronizácia

---

# Úloha 4: Suffix Array a LCP Array

**Náročnosť:** ★★★★★☆

---

## Zadanie

Implementujte efektívnu konštrukciu **Suffix Array** a **Longest Common Prefix (LCP) Array**.  
Použite tieto štruktúry na riešenie pokročilých problémov so stringami.

---

## Požiadavky

- ✅ **Suffix Array** konštrukcia: `O(n log n)` alebo lepšie
- ✅ **LCP Array** konštrukcia: `O(n)`

---

## Aplikácie

1. 🔍 **Najdlhší spoločný podreťazec** dvoch stringov
2. 🔢 **Počet rôznych podreťazcov**
3. 🔁 **Najdlhší opakujúci sa podreťazec**

---

## Príklad

**String:** `"banana"`  
**Suffix Array:** `[5, 3, 1, 0, 4, 2]`  
**LCP Array:** `[0, 1, 3, 0, 0, 2]`

---

## Hodnotenie

| Časť úlohy              | Váha     |
|-------------------------|----------|
| Suffix Array            | 35%      |
| LCP Array               | 25%      |
| Aplikácie (3x)          | 40%      |

---

## Materiály na štúdium

- 📘 **Competitive Programming 3:** Kapitola o stringových algoritmoch
- 🎥 **SPŠIT KNM:** Video – Stringové algoritmy
- 💡 **CP-Algorithms:** [Suffix Array](https://cp-algorithms.com/string/suffix-array.html)
- 📚 **Stanford CS97SI:** Introduction to Programming Contests

---

# Úloha 5: Segment Tree s lazy propagation

**Náročnosť:** ★★★★★★

---

## Zadanie

Implementujte pokročilý **Segment Tree s lazy propagation** pre efektívne:
- **range queries**
- **range updates**

Rozšírte základnú implementáciu o **viaceré typy operácií**.

---

## Požadované operácie

- ✅ `Range sum query`
- ✅ `Range minimum/maximum query`
- ✅ `Range update` (pridať hodnotu k intervalu)
- ✅ `Range set` (nastaviť všetky hodnoty v intervale)
- ⭐ **Bonus:** Perzistentný Segment Tree

---

## Príklad použitia (C++ štýl)

```cpp
SegmentTree st(array);
st.rangeUpdate(1, 5, 10);  // pridaj 10 k prvkom 1-5
st.rangeQuery(2, 7);       // získaj súčet prvkov 2-7
st.rangeSet(3, 4, 0);      // nastav prvky 3-4 na 0
```

---

## Časová zložitosť

- Konštrukcia: `O(n)`
- Query: `O(log n)`
- Update: `O(log n)`

---

## Hodnotenie

| Časť úlohy                | Váha     |
|---------------------------|----------|
| Základný Segment Tree     | 25%      |
| Lazy propagation          | 30%      |
| Viaceré typy operácií     | 25%      |
| Perzistentná verzia       | 20%      |

---

## Materiály na štúdium

- 📘 **SPŠIT KNM:** Pokročilé dátové štruktúry
- 🎥 **Video SPŠIT KNM:** Segment Trees
- 💻 **Codeforces EDU:** Segment Tree
- 💡 **CP-Algorithms:** [Segment Tree](https://cp-algorithms.com/data_structures/segment_tree.html)

---

# Úloha 5: Segment Tree s lazy propagation

**Náročnosť:** ★★★★★★

---

## Zadanie

Implementujte pokročilý **Segment Tree** s **lazy propagation** pre efektívne `range queries` a `range updates`.  
Rozšírte základnú implementáciu o podporu **viacerých typov operácií**.

---

## Požadované operácie

- ✅ **Range sum query**
- ✅ **Range minimum / maximum query**
- ✅ **Range update** – pridať hodnotu k prvkom v intervale
- ✅ **Range set** – nastaviť všetky prvky v intervale na určitú hodnotu
- 🏅 **Bonus:** Perzistentný Segment Tree

---

## Príklad použitia (C++ štýl)

```cpp
SegmentTree st(array);
st.rangeUpdate(1, 5, 10);  // pridaj 10 k prvkom 1-5
st.rangeQuery(2, 7);       // získaj súčet prvkov 2-7
st.rangeSet(3, 4, 0);      // nastav prvky 3-4 na 0
```

---

## Časová zložitosť

- 🔧 **Konštrukcia:** `O(n)`
- 🔍 **Query:** `O(log n)`
- 🔁 **Update:** `O(log n)`

---

## Hodnotenie

| Časť úlohy                    | Váha     |
|------------------------------|----------|
| Základný Segment Tree        | 25%      |
| Lazy propagation             | 30%      |
| Viaceré typy operácií        | 25%      |
| Perzistentná verzia (bonus)  | 20%      |

---

## Materiály na štúdium

- 🎥 **SPŠIT KNM:** Pokročilé dátové štruktúry
- 🎞️ **Video tutoriály SPŠIT KNM:** Segment Trees
- 🧠 **Codeforces EDU:** Kurz [Segment Tree](https://codeforces.com/edu/course/2/lesson/4)
- 📘 **CP-Algorithms:** [Segment Tree](https://cp-algorithms.com/data_structures/segment_tree.html)

---

# Úloha 6: Maximálny tok v sieti (Network Flow)

**Náročnosť:** ★★★★★★

---

## Zadanie

Implementujte pokročilé algoritmy pre hľadanie **maximálneho toku v sieti**.  
Porovnajte výkonnosť rôznych prístupov a aplikujte ich na **praktické problémy**.

---

## Požadované algoritmy

1. 🔁 **Ford-Fulkerson** s použitím DFS
2. 🔄 **Edmonds-Karp** – implementácia pomocou BFS
3. ⚡ **Dinic's Algorithm**
4. 💧 **Push-Relabel Algorithm**

---

## Aplikácie

- 🤝 **Maximálne párovanie v bipartitnom grafe**
- ✂️ **Minimálny rez v grafe**
- 🔄 **Cirkulácia s dolnými hranicami**
- 🛠️ **Multi-commodity flow** *(bonus)*

---

## Testovanie

- 🔧 Generujte rôzne typy sietí: husté, riedke, bipartitné
- ⏱️ Porovnajte výkonnosť algoritmov
- 📈 Vizualizujte tok v sieti

---

## Hodnotenie

| Časť úlohy                    | Váha     |
|-------------------------------|----------|
| Implementácia 4 algoritmov    | 40%      |
| Testovanie a porovnanie       | 30%      |
| Dokumentácia                  | 30%      |

---

## Požiadavky na odovzdanie

- 💻 Zdrojový kód s komentármi
- 📄 Dokumentácia algoritmu
- 📊 Analýza časovej a pamäťovej zložitosti
- 🧪 Testovacie prípady (min. 2 pre každú úlohu)

---

## Odporúčané programovacie jazyky

- ⚙️ C++ (odporúčané pre výkon)
- 🐍 Python *(len pre úlohy s ★★★★)*

---

## Materiály na štúdium

### Knihy

- 📘 *Introduction to Algorithms* – Cormen, Leiserson, Rivest, Stein
- 📗 *Competitive Programming 3* – Steven & Felix Halim
- 📙 *Algorithm Design* – Kleinberg & Tardos

### Online kurzy

- 📺 **SPŠIT KNM YouTube** – Grafové algoritmy, Network Flow
- 🎓 **MIT 6.006:** Introduction to Algorithms
- 🧠 **Stanford CS161:** Design and Analysis of Algorithms

### Praktické zdroje

- 💻 **SPŠIT KNM GitHub**
- 🔍 **Codeforces EDU** – sekcia Network Flow
- 💡 **AtCoder** – Educational DP Contest
- 🐮 **USACO Training Pages**

---

## Bonusové body za

- 🖼️ Vizualizáciu algoritmov
- ⚙️ Optimalizácie nad rámec zadania
- 🧪 Vlastné testovacie prípady

---

## Konzultácie

- 🗣️ Záverečná obhajoba projektu

---
