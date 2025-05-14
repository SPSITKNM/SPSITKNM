# Programovanie a algoritmizácia – Osnova komisionálnej skúšky

## 🧠 Študijný teoretický základ

Tento text predstavuje komplexný teoretický základ pre prípravu na komisionálnu skúšku z programovania a algoritmizácie. Každá kapitola korešponduje s jednou zo skúšobných otázok a poskytuje fundamentálne koncepty a techniky potrebné pre úspešné absolvovanie skúšky.

### 1. Analýza algoritmov a výpočtová zložitosť

Výpočtová zložitosť predstavuje fundamentálny aspekt posudzovania efektívnosti algoritmov. Rozlišujeme časovú zložitosť, ktorá kvantifikuje počet elementárnych operácií v závislosti od veľkosti vstupu, a priestorovú zložitosť, hodnotiacu množstvo pamäte potrebnej na vykonanie algoritmu.

Pre formálnu reprezentáciu zložitosti sa používa asymptotická notácia, najčastejšie O-notácia (horné ohraničenie), Ω-notácia (dolné ohraničenie) a Θ-notácia (tesné ohraničenie). Pri analýze algoritmu musíme uvažovať najlepší prípad (best case), priemerný prípad (average case) a najhorší prípad (worst case).

Pokročilejšie techniky analýzy zahŕňajú amortizovanú analýzu, ktorá poskytuje priemerný čas operácie v sekvencii operácií, a pravdepodobnostnú analýzu pre randomizované algoritmy.

### Zhrnutie

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

Vyvážené vyhľadávacie stromy predstavujú sofistikované dátové štruktúry optimalizované pre efektívne vyhľadávanie, vkladanie a mazanie prvkov. AVL stromy garantujú výškovú vyváženosť prostredníctvom parametra vyváženosti, ktorý zabezpečuje, že rozdiel výšok ľavého a pravého podstromu každého uzla nepresahuje jednotku. Pre udržanie tejto vlastnosti sa používajú rotácie (jednoduché a dvojité).

Red-Black stromy predstavujú alternatívny prístup k vyváženým stromom, ktorý relaxuje podmienku vyváženosti výmenou za menší počet rebalančných operácií. Každý uzol má priradenú farbu (červenú alebo čiernu) a musia byť splnené špecifické vlastnosti týkajúce sa distribúcie farieb a čiernej výšky.

B-stromy a ich varianty (B+ stromy, B* stromy) sú optimalizované pre externé pamäťové systémy, poskytujú efektívne operácie pri minimalizácii diskových operácií a maximalizácii zaplnenia uzlov.

### Zhrnutie

- **AVL stromy**: garantovaná výšková rovnováha, rotácie
- **Red-Black stromy**: menej rotácií, červené/čierne uzly
- **B-stromy (B+, B\*)**: optimalizované pre diskový prístup

---

### 3. Najkratšie cesty v grafoch

Grafové algoritmy predstavujú esenciálnu súčasť teoretickej informatiky s rozsiahlymi praktickými aplikáciami. Dijkstrov algoritmus efektívne rieši problém najkratšej cesty z jedného zdroja v grafoch s nezápornými hranami. Jeho implementácia s prioritným frontom (binárna halda, Fibonacci halda) dosahuje časovú zložitosť O(E + V log V), kde E je počet hrán a V počet vrcholov.

A* algoritmus rozširuje Dijkstrov algoritmus o heuristickú funkciu, ktorá odhaduje vzdialenosť od aktuálneho vrcholu k cieľu. Pri použití prípustnej (nepreceňujúcej) a konzistentnej heuristiky garantuje nájdenie optimálnej cesty a spravidla expanduje menej vrcholov než Dijkstrov algoritmus.

Bellman-Fordov algoritmus rieši problém najkratšej cesty aj v prítomnosti záporných hrán s časovou zložitosťou O(V*E) a dokáže detegovať záporné cykly. Floyd-Warshallov algoritmus efektívne počíta najkratšie cesty medzi všetkými pármi vrcholov s časovou zložitosťou O(V³).

### Zhrnutie

- **Dijkstrov algoritmus** – nezáporné hrany, `O(E + V log V)`
- **A\* algoritmus** – heuristika, efektívne pri známej cieľovej pozícii
- **Bellman-Ford** – záporné hrany, detekcia záporných cyklov
- **Floyd-Warshall** – všetky dvojice vrcholov, `O(V³)`

---

### 4. Minimálna kostra grafu (MST)

Minimálna kostra grafu (MST - Minimum Spanning Tree) reprezentuje podgraf, ktorý spája všetky vrcholy pôvodného grafu s minimálnou celkovou váhou hrán. Kruskalov algoritmus konštruuje MST "zdola nahor" postupným pridávaním hrán s najmenšou váhou, ktoré nevytvárajú cyklus. Jeho implementácia s efektívnou dátovou štruktúrou Union-Find s kompresiou ciest a rankovanou úniou dosahuje časovú zložitosť O(E log V).

Primov algoritmus buduje MST "od stredu" postupným pridávaním vrcholov s najmenšou hranou pripájajúcou vrchol k budovanému stromu. Pri implementácii s prioritným frontom dosahuje časovú zložitosť O(E + V log V). Bóruvkov algoritmus predstavuje paralelnú alternatívu k vyššie uvedeným algoritmom.

Teoretická analýza ukazuje, že dolná hranica časovej zložitosti problému MST je Ω(E), čo indikuje priestor pre potenciálne optimalizácie súčasných algoritmov.

### Zhrnutie

- **Kruskalov algoritmus** – Union-Find, `O(E log V)`
- **Primov algoritmus** – prioritný front, `O(E + V log V)`
- **Bóruvkov algoritmus** – paralelný prístup

---

### 5. Výpočtová zložitosť a NP-úplnosť

Teória výpočtovej zložitosti klasifikuje problémy do tried podľa zdrojov potrebných na ich riešenie. Trieda P zahŕňa problémy riešiteľné v polynomiálnom čase deterministickým Turingovým strojom. Trieda NP obsahuje problémy, ktorých riešenie možno verifikovať v polynomiálnom čase.

NP-úplné problémy reprezentujú "najťažšie" problémy v triede NP - problém je NP-úplný, ak patrí do NP a každý problém z NP sa naň dá polynomiálne redukovať. Prvým dokázaným NP-úplným problémom bol problém splniteľnosti booleovskej formuly (SAT).

Problém P vs NP, teda otázka, či P = NP, zostáva jedným z najvýznamnejších otvorených problémov teoretickej informatiky. Jeho vyriešenie by malo fundamentálne dôsledky pre kryptografiu, optimalizáciu a ďalšie oblasti.

Štandardné techniky práce s NP-ťažkými problémami zahŕňajú aproximačné algoritmy (poskytujúce riešenie s garantovanou kvalitou), heuristické algoritmy (prakticky efektívne bez teoretických garancií) a parametrizované algoritmy (efektívne pre určité hodnoty parametrov).

### Zhrnutie

- **Triedy P, NP**
- **NP-úplné problémy**: SAT, obchodný cestujúci
- **Redukcia problémov**
- **Techniky riešenia**: aproximačné, heuristické, parametrizované

---

### 6. Vyvažovanie stromov

Vyvažovanie binárnych vyhľadávacích stromov predstavuje kľúčovú operáciu pre zachovanie ich efektívnosti. DSW algoritmus (Day-Stout-Warren) transformuje ľubovoľný binárny vyhľadávací strom na dokonale vyvážený strom v lineárnom čase O(n) s konstantnou dodatočnou pamäťou.

Tento proces prebieha v dvoch fázach: najprv sa strom "rozbalí" do pravej cesty (backbone) pomocou série rotácií vľavo, následne sa aplikujú rotácie vpravo na vytvorenie vyváženej štruktúry. Počet rotácií je priamo úmerný veľkosti stromu, čo garantuje linearitu algoritmu.

Alternatívny prístup využíva inorder prechod stromom a rekonštrukciu vyváženého stromu pomocou rekurzívneho delenia poľa prvkov. Tento prístup vyžaduje dodatočný priestor O(n), ale zachováva linearitu časovej zložitosti.

### Zhrnutie

- **DSW algoritmus**: rotácie, `O(n)` čas, `O(1)` pamäť
- **Inorder rekonštrukcia**: `O(n)` čas, `O(n)` pamäť

---

### 7. Dynamické programovanie

Dynamické programovanie predstavuje výkonnú algoritmickú paradigmu riešiacu komplexné problémy ich dekompozíciou na podproblémy, ktorých riešenia sú ukladané do pamäťových štruktúr (memoizácia) pre zabránenie redundantným výpočtom.

Problém batohu (Knapsack Problem) ilustruje efektívnosť dynamického programovania. Pri klasickej variante (0-1 Knapsack) riešenie dosahuje časovú zložitosť O(nW) a priestorovú zložitosť O(nW), kde n je počet predmetov a W je kapacita batohu. Pre unbounded Knapsack (neobmedzený počet položiek každého typu) časová zložitosť zostáva O(n*W), ale priestorovú zložitosť možno redukovať na O(W).

Optimalizácia priestorovej zložitosti často využíva techniku "rolling array", kde si namiesto celej tabuľky uchováme len niekoľko (často dva) posledných riadkov alebo stĺpcov, čo redukuje priestorovú zložitosť na O(W) aj pre klasický problém batohu.

Subproblémy v dynamickom programovaní musia spĺňať princíp optimálnej podštruktúry (optimálne riešenie problému obsahuje optimálne riešenia podproblémov) a vykazovať prekrývajúce sa podproblémy (opakované riešenie rovnakých podproblémov).

### Zhrnutie

- **Knapsack problem** (0-1, unbounded): `O(nW)`
- **Optimalizácie pamäte**: rolling array
- **Vlastnosti**: optimálna podštruktúra, prekrývajúce sa podproblémy

---

### 8. Agilné metodiky vývoja softvéru

Agilné metodiky vývoja softvéru predstavujú modernú alternatívu k tradičným sekvenčným metodikám (waterfall). Agilný manifest zdôrazňuje adaptáciu na zmeny, spoluprácu s klientom, funkčný softvér a interakcie medzi ľuďmi.

SCRUM definuje iteratívny a inkrementálny rámec s presne definovanými rolami (Product Owner, Scrum Master, Development Team), artefaktmi (Product Backlog, Sprint Backlog, Increment) a udalosťami (Sprint Planning, Daily Scrum, Sprint Review, Sprint Retrospective). Sprints predstavujú časovo ohraničené (zvyčajne 2-týždňové) iterácie vývoja.

Kanban sa sústreďuje na vizualizáciu pracovného procesu, limitovanie rozpracovanej práce (WIP - Work In Progress) a kontinuálne zlepšovanie. Na rozdiel od SCRUMu nevyužíva fixné časové iterácie, ale kontinuálny tok práce.

Implementácia agilných metodík vyžaduje kultúrnu zmenu v organizácii, dôraz na transparentnú komunikáciu a kontinuálne zlepšovanie. Hybridné prístupy (napr. Scrumban) kombinujú prvky rôznych metodík podľa potrieb projektu.

### Zhrnutie

- **SCRUM**: role, artefakty, udalosti, sprints
- **Kanban**: vizualizácia práce, WIP limity
- **Hybridné prístupy**: Scrumban
- **Porovnanie s waterfall modelom**

---

### 9. Vyhľadávanie v texte

Algoritmy na vyhľadávanie vzorov v texte optimalizujú proces lokalizácie výskytov hľadaného reťazca (pattern) v dlhšom texte. Knuth-Morris-Prattov (KMP) algoritmus eliminuje redundantné porovnania využitím prefixtabuľky, ktorá pre každú pozíciu vo vzore určuje dĺžku najdlhšieho vlastného prefixu, ktorý je súčasne suffixom.

Konštrukcia prefix tabuľky má lineárnu časovú zložitosť O(m), kde m je dĺžka vzoru. Samotný vyhľadávací proces má časovú zložitosť O(n), kde n je dĺžka textu, čo vedie k celkovej časovej zložitosti O(n+m) - významné zlepšenie oproti naivnému algoritmu s časovou zložitosťou O(n*m).

Rabin-Karpov algoritmus využíva hashovacie funkcie na efektívne porovnávanie reťazcov. Namiesto porovnávania znakov porovnáva hashe podreťazcov textu s hashom vzoru. Pri správnej implementácii tiež dosahuje očakávanú lineárnu časovú zložitosť, je však náchylnejší na kolízie hashov.

Boyer-Mooreov algoritmus predstavuje ďalšiu efektívnu alternatívu, ktorá skenuje vzor sprava doľava a využíva dve heuristiky (bad character a good suffix) na preskočenie zbytočných porovnaní. V praxi často prekonáva KMP a Rabin-Karp, najmä pre dlhšie vzory a veľké abecedy.

### Zhrnutie

- **KMP algoritmus**: prefix tabuľka, `O(n + m)`
- **Rabin-Karp**: hashovanie, možnosť kolízií
- **Boyer-Moore**: heuristiky, výkonný v praxi

---

### 10. Topologické usporiadanie

Topologické usporiadanie orientovaného acyklického grafu (DAG) predstavuje lineárne usporiadanie vrcholov také, že pre každú hranu (u, v) vrchol u predchádza vrcholu v. Topologické usporiadanie existuje práve vtedy, keď graf neobsahuje orientovaný cyklus.

Implementácia využívajúca prehľadávanie do hĺbky (DFS) konštruuje topologické usporiadanie v reverznom poradí dokončenia DFS prehľadávania vrcholov. Algoritmus má časovú zložitosť O(V + E) a priestorovú zložitosť O(V) na uloženie rekurzívneho zásobníka a výsledného usporiadania.

Alternatívna implementácia využíva algoritmus založený na počítadlách vstupných hrán (Kahn's algorithm). Algoritmus iteratívne odstraňuje vrcholy s nulovým počtom vstupných hrán a aktualizuje počítadlá pre ich susedov. Táto implementácia tiež dosahuje lineárnu časovú zložitosť O(V + E).

Aplikácie topologického usporiadania zahŕňajú plánovanie projektov (identifikácia kritickej cesty), kompiláciu (určenie poradia kompilácie modulov), a dátové spracovanie (určenie poradia vyhodnocovania výrazov). Algoritmus možno adaptovať aj na detekciu cyklov v orientovanom grafe.

- **DAG** – topologické triedenie je možné len ak nie sú cykly
- **DFS implementácia** – reverzné poradie skončenia prechodu
- **Kahnov algoritmus** – počítadlá vstupných hrán
- **Aplikácie**: plánovanie, kompilácia, detekcia cyklov

---

## ✅ Skúšobné otázky – Komisionálna časť

1. **QuickSort**:  
   Analyzujte časovú a priestorovú zložitosť algoritmu QuickSort v najhoršom, priemernom a najlepšom prípade. Vysvetlite, za akých podmienok nastáva najhorší prípad a navrhnite optimalizáciu na jeho zmiernenie. Implementujte funkciu, ktorá bude využívať vhodný pivotný prvok na minimalizáciu pravdepodobnosti výskytu najhoršieho prípadu.

2. **AVL vs Red-Black stromy**:  
   Porovnajte implementáciu vyvážených vyhľadávacích stromov (AVL a Red-Black) z hľadiska časovej zložitosti operácií vkladania, mazania a vyhľadávania. Analyzujte, kedy je vhodné použiť jednotlivé typy stromov vzhľadom na konkrétne aplikácie. Implementujte funkciu rotácie v AVL strome a demonštrujte jej použitie pri vkladaní prvku, ktorý naruší vyváženosť stromu.

3. **Najkratšia cesta – Dijkstra a A\***:  
   Vysvetlite princíp Dijkstrovho algoritmu a A algoritmu pre hľadanie najkratšej cesty v grafe. Analyzujte ich časovú a priestorovú zložitosť a porovnajte ich efektívnosť v rôznych typoch grafov. Implementujte A algoritmus vrátane heuristickej funkcie pre nájdenie najkratšej cesty v mriežkovom grafe s prekážkami.**

4. **MST – Kruskal vs Prim**:  
   Analyzujte Kruskalov a Primov algoritmus pre hľadanie minimálnej kostry grafu. Diskutujte o ich časovej a priestorovej zložitosti vzhľadom na rôzne implementácie dátových štruktúr (najmä Union-Find pri Kruskalovom algoritme a prioritné fronty pri Primovom algoritme). Implementujte Kruskalov algoritmus s použitím efektívnej implementácie Union-Find s kompresiou ciest a rankovanou úniou.

5. **P vs NP**:  
   Vysvetlite rozdiely medzi triedami problémov P a NP a diskutujte o P vs NP probléme. Uveďte príklady problémov patriacich do triedy P, NP-úplných problémov a problémov, ktoré patria do NP, ale nie sú NP-úplné (ak také existujú). Navrhnite polynomiálnu redukciu problému hamiltonovskej cesty na problém obchodného cestujúceho.

6. **Vyvažovanie BST**:  
   Implementujte efektívny algoritmus na vyváženie binárneho vyhľadávacieho stromu s časovou zložitosťou O(n) a priestorovou zložitosťou O(log n), kde n je počet uzlov v strome. Vysvetlite princíp algoritmu a analyzujte jeho časovú a priestorovú zložitosť. Demonštrujte funkčnosť algoritmu na konkrétnom nevyváženom strome.

7. **Dynamické programovanie – Knapsack**:  
  Navrhnite a implementujte riešenie problému dynamického programovania na príklade problému batohu (Knapsack problem) a analyzujte jeho časovú a priestorovú zložitosť. Vysvetlite, ako by sa zmenila implementácia a zložitosť pri obmedzení, že počet položiek každého typu môže byť neobmedzený (unbounded knapsack). Optimalizujte riešenie z hľadiska priestorovej zložitosti.

8. **Agilné metodiky**:  
  Vysvetlite princípy agilných metodík vývoja softvéru, najmä SCRUM a Kanban. Porovnajte ich s tradičnými waterfall prístupmi a diskutujte o ich výhodách a nevýhodách v rôznych typoch projektov. Navrhnite konkrétny plán implementácie SCRUM metodiky v tíme vyvíjajúcom mobilnú aplikáciu a identifikujte potenciálne problémy a riešenia.

9. **KMP algoritmus**:  
  Analyzujte a implementujte algoritmus na vyhľadávanie v texte pomocou Knuth-Morris-Prattovho (KMP) algoritmu. Vysvetlite princíp vytvorenia tabuľky najdlhších prefixov, ktoré sú súčasne suffixami, a demonštrujte, ako algoritmus využíva túto tabuľku na efektívne vyhľadávanie. Porovnajte KMP algoritmus s naivným prístupom a Rabin-Karpovým algoritmom z hľadiska časovej a priestorovej zložitosti.

10. **Topologické triedenie**:  
    Implementujte algoritmus topologického triedenia orientovaného acyklického grafu (DAG) a vysvetlite jeho princíp. Analyzujte časovú a priestorovú zložitosť implementácie využívajúcej DFS (depth-first search) aj implementácie využívajúcej frontu s počítadlami vstupných hrán. Diskutujte o aplikáciách topologického triedenia v plánovaní projektov a detekcii cyklov v grafe.
---

**Vytvorené Tomášom Muchom vyučujúci predmetu PRO**

**Poznámka:**  
Tento dokument je určený ako komplexná príprava na ústnu časť komisionálnej skúšky. Dôraz sa kladie nielen na znalosť algoritmov, ale aj na schopnosť ich analyzovať, porovnávať a prakticky implementovať.

