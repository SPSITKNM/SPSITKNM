# Programovanie a algoritmizácia – Osnova komisionálnej skúšky

## 🧠 Študijný teoretický základ

Nasledujúci text predstavuje odborný prehľad kľúčových tém, ktoré sú predmetom komisionálnej skúšky z programovania so zameraním na algoritmizáciu pre študentov 4. ročníka strednej školy. Text je štruktúrovaný do tematických kapitol, ktoré korešpondujú s vyššie uvedenými skúšobnými otázkami.

### 1. Analýza algoritmov a výpočtová zložitosť

Výpočtová zložitosť predstavuje fundamentálny aspekt posudzovania efektívnosti algoritmov. Rozlišujeme:

- **Časovú zložitosť** – počet operácií v závislosti od vstupu.
- **Priestorovú zložitosť** – množstvo pamäte potrebnej na výpočet.

Používané notácie:
- `O(f(n))`: horné ohraničenie,
- `Ω(f(n))`: dolné ohraničenie,
- `Θ(f(n))`: presné ohraničenie.

Dôležité prístupy:
- **Najlepší, priemerný, najhorší prípad**
- **Amortizovaná analýza**
- **Pravdepodobnostná analýza** pre randomizované algoritmy

---

### 2. Pokročilé stromové štruktúry

- **AVL stromy**: garantovaná výšková rovnováha, rotácie
- **Red-Black stromy**: menej rotácií, červené/čierne uzly
- **B-stromy (B+, B\*)**: optimalizované pre diskový prístup

---

### 3. Najkratšie cesty v grafoch

- **Dijkstrov algoritmus** – nezáporné hrany, `O(E + V log V)`
- **A\* algoritmus** – heuristika, efektívne pri známej cieľovej pozícii
- **Bellman-Ford** – záporné hrany, detekcia záporných cyklov
- **Floyd-Warshall** – všetky dvojice vrcholov, `O(V³)`

---

### 4. Minimálna kostra grafu (MST)

- **Kruskalov algoritmus** – Union-Find, `O(E log V)`
- **Primov algoritmus** – prioritný front, `O(E + V log V)`
- **Bóruvkov algoritmus** – paralelný prístup

---

### 5. Výpočtová zložitosť a NP-úplnosť

- **Triedy P, NP**
- **NP-úplné problémy**: SAT, obchodný cestujúci
- **Redukcia problémov**
- **Techniky riešenia**: aproximačné, heuristické, parametrizované

---

### 6. Vyvažovanie stromov

- **DSW algoritmus**: rotácie, `O(n)` čas, `O(1)` pamäť
- **Inorder rekonštrukcia**: `O(n)` čas, `O(n)` pamäť

---

### 7. Dynamické programovanie

- **Knapsack problem** (0-1, unbounded): `O(nW)`
- **Optimalizácie pamäte**: rolling array
- **Vlastnosti**: optimálna podštruktúra, prekrývajúce sa podproblémy

---

### 8. Agilné metodiky vývoja softvéru

- **SCRUM**: role, artefakty, udalosti, sprints
- **Kanban**: vizualizácia práce, WIP limity
- **Hybridné prístupy**: Scrumban
- **Porovnanie s waterfall modelom**

---

### 9. Vyhľadávanie v texte

- **KMP algoritmus**: prefix tabuľka, `O(n + m)`
- **Rabin-Karp**: hashovanie, možnosť kolízií
- **Boyer-Moore**: heuristiky, výkonný v praxi

---

### 10. Topologické usporiadanie

- **DAG** – topologické triedenie je možné len ak nie sú cykly
- **DFS implementácia** – reverzné poradie skončenia prechodu
- **Kahnov algoritmus** – počítadlá vstupných hrán
- **Aplikácie**: plánovanie, kompilácia, detekcia cyklov

---

## ✅ Skúšobné otázky – Komisionálna časť

1. **QuickSort**:  
   Analyzujte zložitosť v rôznych prípadoch, popíšte optimalizácie pre výber pivotu a implementujte efektívnu verziu.

2. **AVL vs Red-Black stromy**:  
   Porovnajte ich vlastnosti a vhodnosť použitia. Implementujte rotáciu v AVL strome.

3. **Najkratšia cesta – Dijkstra a A\***:  
   Vysvetlite princíp a porovnajte ich výkon. Implementujte A\* na mriežkový graf.

4. **MST – Kruskal vs Prim**:  
   Analyzujte ich efektívnosť s ohľadom na dátové štruktúry. Implementujte Kruskal s Union-Find.

5. **P vs NP**:  
   Definujte pojmy, uveďte príklady a predveďte polynomiálnu redukciu Hamiltonovskej cesty na TSP.

6. **Vyvažovanie BST**:  
   Implementujte algoritmus s `O(n)` časom a `O(log n)` pamäťou. Ukážte ho na príklade.

7. **Dynamické programovanie – Knapsack**:  
   Riešte 0-1 aj unbounded verziu, porovnajte ich zložitosť a navrhnite pamäťovú optimalizáciu.

8. **Agilné metodiky**:  
   Porovnajte SCRUM a Kanban, uveďte plán implementácie SCRUM pre tím mobilnej aplikácie.

9. **KMP algoritmus**:  
   Vysvetlite prefix tabuľku a implementujte KMP. Porovnajte s naivným a Rabin-Karp algoritmom.

10. **Topologické triedenie**:  
    Implementujte DFS a Kahnov algoritmus. Uveďte aplikácie a diskutujte o detekcii cyklov.

---

**Poznámka:**  
Tento dokument je určený ako komplexná príprava na ústnu časť komisionálnej skúšky. Dôraz sa kladie nielen na znalosť algoritmov, ale aj na schopnosť ich analyzovať, porovnávať a prakticky implementovať.

