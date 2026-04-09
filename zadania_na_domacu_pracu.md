# Test: Dátové štruktúry

---

## Obsah

- [Sekcia 1 – Linked List](#sekcia-1--linked-list)
- [Sekcia 2 – Stack a Queue](#sekcia-2--stack-a-queue)
- [Sekcia 3 – Binárny vyhľadávací strom (BST)](#sekcia-3--binárny-vyhľadávací-strom-bst)
- [Sekcia 4 – Hash Table](#sekcia-4--hash-table)
- [Sekcia 5 – Graf](#sekcia-5--graf)

---

---

# Sekcia 1 – Linked List

Pracuješ so streamovacou službou, ktorá uchováva prehrávaný playlist ako spájaný zoznam skladieb. Každý uzol predstavuje jednu skladbu.

```cpp
class Node {
public:
    int value;
    Node* next;
    Node(int value) : value(value), next(nullptr) {}
};

class LinkedList {
public:
    Node* head;
    Node* tail;
    int length;

    LinkedList(int value) {
        Node* newNode = new Node(value);
        head = newNode;
        tail = newNode;
        length = 1;
    }

    void printList() {
        Node* temp = head;
        while (temp) {
            cout << temp->value << "\n";
            temp = temp->next;
        }
    }
};
```

---

## LL-1: Append

Používateľ klikol na „Pridať na koniec playlistu". Implementuj metódu `append`, ktorá pridá novú skladbu na koniec zoznamu.

```
PRED:
head --> [101] --> [237] --> nullptr
                     ^
                    tail

append(348)

PO:
head --> [101] --> [237] --> [348] --> nullptr
                               ^
                              tail
```

**Hint:** Mysli na to, čo sa stane keď je playlist úplne prázdny – vtedy nová skladba zastáva dve roly naraz.

```cpp
void append(int value) {

}
```

**Otestuj:**
```cpp
LinkedList ll(101);
ll.append(237);
ll.append(348);
ll.printList();
// 101  237  348
```

---

## LL-2: Prepend

Počas prehrávania si používateľ vybral skladbu, ktorá má hrať ako nasledujúca – teda hneď na začiatku. Implementuj metódu `prepend`.

```
PRED:
head --> [237] --> [348] --> nullptr

prepend(101)

PO:
head --> [101] --> [237] --> [348] --> nullptr
```

**Hint:** Nová skladba musí vedieť, kto bol pred ňou prvý.

```cpp
void prepend(int value) {

}
```

**Otestuj:**
```cpp
LinkedList ll(237);
ll.append(348);
ll.prepend(101);
ll.printList();
// 101  237  348
```

---

## LL-3: Delete First

Skladba dohrala – systém ju vyradí zo začiatku playlistu a vráti jej ID (napríklad pre štatistiky prehrávania). Implementuj metódu `deleteFirst`.

```
PRED:
head --> [101] --> [237] --> [348] --> nullptr

deleteFirst()

PO:
head --> [237] --> [348] --> nullptr
vrátená hodnota: ukazovateľ na [101]
```

**Hint:** Čo sa stane s `tail` ak v playliste ostane len jedna skladba a tú vyradíš?

```cpp
Node* deleteFirst() {

}
```

**Otestuj:**
```cpp
LinkedList ll(101);
ll.append(237);
ll.append(348);
Node* removed = ll.deleteFirst();
cout << removed->value << "\n";  // 101
ll.printList();                  // 237  348
```

---

## LL-4: Delete Last

Používateľ sa rozhodol odstrániť poslednú skladbu z playlistu. Implementuj metódu `deleteLast`, ktorá vráti ukazovateľ na vymazaný uzol.

```
PRED:
head --> [101] --> [237] --> [348] --> nullptr
                               ^
                              tail

deleteLast()

PO:
head --> [101] --> [237] --> nullptr
                     ^
                    tail
```

**Hint:** Na rozdiel od `deleteFirst` tu musíš nájsť predposledný uzol – `tail` sám o sebe nevie, kto je pred ním.

```
... --> [101] --> [237] --> [348] --> nullptr
                   ^
             tu zastavíš (tento->next == tail)
```

```cpp
Node* deleteLast() {

}
```

**Otestuj:**
```cpp
LinkedList ll(101);
ll.append(237);
ll.append(348);
Node* removed = ll.deleteLast();
cout << removed->value << "\n";  // 348
ll.printList();                  // 101  237
```

---

## LL-5: Get

Moderátor chce zobraziť skladbu na konkrétnej pozícii v playliste. Implementuj metódu `get(index)`, ktorá vráti ukazovateľ na uzol na danom indexe (od 0). Ak pozícia neexistuje, vráť `nullptr`.

```
head --> [101] --> [237] --> [348] --> nullptr
index:     0         1         2

get(1)  -->  ukazovateľ na uzol [237]
get(9)  -->  nullptr
```

**Hint:** Prechádzaš od začiatku – koľkokrát musíš skočiť na `next`, aby si sa dostal na index `i`?

```cpp
Node* get(int index) {

}
```

---

## LL-6: Set

Moderátor opravil chybné ID skladby na danej pozícii. Implementuj metódu `set(index, value)`, ktorá zmení hodnotu uzla. Vráť `true` ak sa zmena podarila.

```
PRED:
head --> [101] --> [237] --> [348] --> nullptr

set(1, 999)

PO:
head --> [101] --> [999] --> [348] --> nullptr
```

**Hint:** Nemusíš prechádzať zoznam znova – máš metódu, ktorá ti uzol nájde.

```cpp
bool set(int index, int value) {

}
```

---

## LL-7: Insert

Redaktor chce vsunúť bonusovú skladbu na konkrétnu pozíciu v playliste, nie na začiatok ani koniec. Implementuj metódu `insert(index, value)`.

```
PRED:
head --> [101] --> [348] --> nullptr
index:     0         1

insert(1, 237)

PO:
head --> [101] --> [237] --> [348] --> nullptr
index:     0         1         2
```

**Hint:** Nová skladba sa musí „zapojiť" do reťaze – najprv prevezmie nasledovníka svojho predchodcu, až potom predchodca ukazuje na ňu. Na opačné poradie si daj pozor.

```
prev->next = ?        (krok A)
newNode->next = ?     (krok B)

Záleží na poradí krokov A a B – ktorý ide ako prvý?
```

```cpp
bool insert(int index, int value) {

}
```

**Otestuj:**
```cpp
LinkedList ll(101);
ll.append(348);
ll.insert(1, 237);
ll.printList();  // 101  237  348
```

---

## LL-8: Delete Node

Skladba bola stiahnutá kvôli autorským právam – musí byť vymazaná z ľubovoľnej pozície v playliste. Implementuj metódu `deleteNode(index)`.

```
PRED:
head --> [101] --> [237] --> [348] --> nullptr

deleteNode(1)

PO:
head --> [101] --> [348] --> nullptr
vrátená hodnota: ukazovateľ na [237]
```

**Hint:** Uzol pred vymazávaným musí „preskočiť" vymazávaný a ukazovať priamo na jeho nasledovníka. Pre krajné pozície (prvá, posledná) máš už hotové metódy.

```cpp
Node* deleteNode(int index) {

}
```

---

## LL-9: Reverse

Používateľ zapol režim „Prehrať playlist pozadu". Implementuj metódu `reverse`, ktorá obráti poradie skladieb priamo v existujúcom zozname bez vytvorenia nového.

```
PRED:
head --> [1] --> [2] --> [3] --> [4] --> nullptr
                                  ^
                                 tail

PO:
head --> [4] --> [3] --> [2] --> [1] --> nullptr
                                  ^
                                 tail
```

**Hint:** Predstav si, že otáčaš šípky medzi uzlami jednu po druhej. Potrebuješ si vždy pamätať, kde si bol predtým, a kde ideš potom – inak stratíš zvyšok zoznamu.

```
Stav po každom kroku (tri ukazovatele: prev, temp, after):

Krok 1:  null <-- [1]    [2] --> [3] --> [4]
Krok 2:  null <-- [1] <-- [2]    [3] --> [4]
Krok 3:  null <-- [1] <-- [2] <-- [3]    [4]
Krok 4:  null <-- [1] <-- [2] <-- [3] <-- [4]
```

```cpp
void reverse() {

}
```

**Otestuj:**
```cpp
LinkedList ll(1);
ll.append(2);
ll.append(3);
ll.append(4);
ll.reverse();
ll.printList();  // 4  3  2  1
```

---

---

# Sekcia 2 – Stack a Queue

```cpp
class Node {
public:
    int value;
    Node* next;
    Node(int value) : value(value), next(nullptr) {}
};
```

---

## SQ-1: Stack – Push

Textový editor si pamätá históriu zmien ako zásobník – každá nová zmena sa uloží na vrchol. Implementuj metódu `push`.

```
PRED:
top --> [zmena2] --> [zmena1] --> nullptr
height = 2

push(zmena3)

PO:
top --> [zmena3] --> [zmena2] --> [zmena1] --> nullptr
height = 3
```

```cpp
class Stack {
public:
    Node* top;
    int height;

    Stack(int value) {
        Node* newNode = new Node(value);
        top = newNode;
        height = 1;
    }

    void push(int value) {

    }
};
```

**Hint:** Zásobník rastie smerom nahor – nový prvok sa stáva vrcholom a ukazuje na pôvodný vrchol.

---

## SQ-2: Stack – Pop

Používateľ stlačil Ctrl+Z. Editor odoberie poslednú zmenu z vrcholu zásobníka a vráti ju. Implementuj metódu `pop`.

```
PRED:
top --> [zmena3] --> [zmena2] --> [zmena1] --> nullptr

pop()

PO:
top --> [zmena2] --> [zmena1] --> nullptr
vrátená hodnota: hodnota zmena3
```

**Hint:** Uzol, ktorý odoberáš, musí byť pred vymazaním odpojený od zvyšku zásobníka.

```cpp
int pop() {

}
```

**Otestuj:**
```cpp
Stack s(1);
s.push(2);
s.push(3);
cout << s.pop() << "\n";  // 3
cout << s.pop() << "\n";  // 2
```

---

## SQ-3: Queue – Enqueue

Na pokladni v kine sa tvoria rady. Každý nový zákazník sa zaradí na **koniec** fronty. Implementuj metódu `enqueue`.

```
PRED:
first --> [A] --> [B] --> nullptr
                    ^
                   last

enqueue(C)

PO:
first --> [A] --> [B] --> [C] --> nullptr
                            ^
                           last
```

```cpp
class Queue {
public:
    Node* first;
    Node* last;
    int length;

    Queue(int value) {
        Node* newNode = new Node(value);
        first = newNode;
        last = newNode;
        length = 1;
    }

    void enqueue(int value) {

    }
};
```

**Hint:** Na rozdiel od stacku tu pridávaš na opačný koniec, ako odoberáš.

---

## SQ-4: Queue – Dequeue

Pokladník odbavil zákazníka z **čela** fronty. Implementuj metódu `dequeue`, ktorá ho odstráni a vráti jeho hodnotu.

```
PRED:
first --> [A] --> [B] --> [C] --> nullptr

dequeue()

PO:
first --> [B] --> [C] --> nullptr
vrátená hodnota: hodnota A
```

**Hint:** Ak po odobratí fronta ostane prázdna, nezabudni aktualizovať aj `last`.

```cpp
int dequeue() {

}
```

**Otestuj:**
```cpp
Queue q(10);
q.enqueue(20);
q.enqueue(30);
cout << q.dequeue() << "\n";  // 10
cout << q.dequeue() << "\n";  // 20
```

---

## SQ-5: Overenie závoriek

Kompilátor kontroluje zdrojový kód – každá otvárajúca závorka musí mať svoju zatváraci dvojicu v správnom poradí. Napíš funkciu `isBalanced(string s)`, ktorá to overí pomocou zásobníka.

```
"({[]})"  -->  true
"({[})"   -->  false
"((())"   -->  false
```

**Hint:** Zásobník tu funguje ako „pamäť" – otvárací znak si odložíš a keď narazíš na zatvárajúci, overíš, či sedí s tým, čo je na vrchole.

```
Príklad "({[]})":

Znak  |  Zásobník
------|-----------
(     |  (
{     |  { (
[     |  [ { (
]     |  { (
}     |  (
)     |  prazdny
--> true
```

```cpp
bool isBalanced(string s) {

}
```

---

---

# Sekcia 3 – Binárny vyhľadávací strom (BST)

Knižnica buduje digitálny katalóg kníh. Každá kniha má unikátne katalógové číslo. Katalóg je uložený ako BST – vďaka tomu sa dá v ňom rýchlo vyhľadávať.

```cpp
class Node {
public:
    int value;
    Node* left;
    Node* right;
    Node(int value) : value(value), left(nullptr), right(nullptr) {}
};

class BinarySearchTree {
public:
    Node* root;
    BinarySearchTree() : root(nullptr) {}
};
```

---

## BST-1: Insert

Nová kniha dorazila do knižnice. Zaraď jej katalógové číslo do BST. Ak číslo už existuje, nič nerob (vráť `false`).

```
Zaraďujeme postupne: 47, 21, 76, 18, 52

        47
       /  \
     21    76
    /      /
  18      52
```

**Hint:** V každom uzle sa rozhoduješ – doľava alebo doprava. Prechádzaš stromom, kým nenarazíš na voľné miesto.

```
Kde skončí číslo 52?

47 --> 52 > 47, idem doprava
76 --> 52 < 76, idem doľava
nullptr --> tu vlož nový uzol
```

```cpp
bool insert(int value) {

}
```

**Otestuj:**
```cpp
BinarySearchTree bst;
bst.insert(47);
bst.insert(21);
bst.insert(76);
bst.insert(18);
bst.insert(52);
cout << bst.root->value << "\n";         // 47
cout << bst.root->left->value << "\n";   // 21
cout << bst.root->right->value << "\n";  // 76
```

---

## BST-2: Contains

Čitateľ hľadá knihu podľa katalógového čísla. Implementuj metódu `contains`, ktorá vráti `true` ak kniha v katalógu existuje.

```
        47
       /  \
     21    76
    /      /
  18      52

contains(52)  -->  true
contains(99)  -->  false
```

**Hint:** Cesta stromom je rovnaká logika ako pri vkladaní – len namiesto vkladania hľadáš zhodu.

```
Hľadanie 52:
47 --> doprava
76 --> doľava
52 --> nashli sme
```

```cpp
bool contains(int value) {

}
```

---

## BST-3: Inorder traversal

Knižnica potrebuje vypísať všetky katalógové čísla v zoradenom poradí pre tlač zoznamu. Implementuj rekurzívny Inorder prechod stromom (doľava – koreň – doprava).

```
        47
       /  \
     21    76
    /  \   /
  18   27 52

Inorder výpis: 18  21  27  47  52  76
```

**Hint:** Rekurzia tu funguje prirodzene – každý uzol hovorí: „nechaj ľavú stranu vypísať sa, potom ja, potom pravá."

```
inorder(47)
  inorder(21)
    inorder(18) --> vypíše 18
    vypíše 21
    inorder(27) --> vypíše 27
  vypíše 47
  inorder(76)
    inorder(52) --> vypíše 52
    vypíše 76
```

```cpp
void inorderHelper(Node* node) {

}

void inorder() {
    inorderHelper(root);
}
```

---

---

# Sekcia 4 – Hash Table

Sklad stavebnín eviduje zásoby tovaru. Každá položka má textový názov a počet kusov na sklade. Pre rýchly prístup podľa názvu používa sklad hašovaciu tabuľku.

```cpp
class HashTable {
private:
    static const int SIZE = 7;
    vector<vector<pair<string, int>>> dataMap;

    int hash(string key) {
        int index = 0;
        for (char c : key) {
            index = (index + (int)c * 23) % SIZE;
        }
        return index;
    }

public:
    HashTable() : dataMap(SIZE) {}
};
```

---

## HT-1: Set

Skladník zapíše novú položku do evidencie. Implementuj metódu `set(key, value)`.

```
set("nails",  1000)  -->  index 4
set("tile",    400)  -->  index 1
set("lumber", 3000)  -->  index 4  (kolízia!)

Index 0: []
Index 1: [("tile", 400)]
Index 2: []
Index 3: []
Index 4: [("nails", 1000), ("lumber", 3000)]
Index 5: []
Index 6: []
```

**Hint:** Kolízia nie je chyba – reťazec na danom indexe môže obsahovať viacero položiek.

```cpp
void set(string key, int value) {

}
```

---

## HT-2: Get

Skladník hľadá, koľko kusov má na sklade od daného tovaru. Implementuj metódu `get(key)`. Ak tovar neexistuje, vráť `0`.

```
get("tile")    -->  400
get("lumber")  -->  3000
get("cement")  -->  0
```

**Hint:** Na jednom indexe môže byť viac položiek – musíš prehľadať celý reťazec a porovnávať kľúče.

```cpp
int get(string key) {

}
```

**Otestuj:**
```cpp
HashTable ht;
ht.set("nails", 1000);
ht.set("tile", 400);
ht.set("lumber", 3000);
cout << ht.get("tile") << "\n";    // 400
cout << ht.get("cement") << "\n";  // 0
```

---

## HT-3: Keys

Riaditeľ chce vidieť zoznam všetkého tovaru, ktorý je v evidencii. Implementuj metódu `keys()`, ktorá vráti vektor všetkých kľúčov.

```
ht.keys()  -->  ["tile", "nails", "lumber"]
               (poradie môže byť rôzne)
```

**Hint:** Musíš prejsť každý index tabuľky a z každého reťazca zozbierať kľúče.

```cpp
vector<string> keys() {

}
```

---

## HT-4: Item in Common

Dva sklady majú každý svoj zoznam ID produktov. Centrála chce vedieť, či existuje aspoň jeden produkt, ktorý majú oba sklady spoločný. Napíš funkciu `itemInCommon`. Riešenie musí mať časovú zložitosť **O(n)**.

```
{1, 3, 5, 7}  a  {2, 4, 5, 8}  -->  true   (spoločné: 5)
{1, 3, 5, 7}  a  {2, 4, 6, 8}  -->  false
```

**Hint:** Namiesto porovnávania každého prvku s každým, ulož prvky prvého zoznamu do štruktúry, v ktorej je vyhľadávanie rýchle – potom stačí jeden prechod druhým zoznamom.

```cpp
bool itemInCommon(vector<int> a, vector<int> b) {

}
```

---

---

# Sekcia 5 – Graf

Mesto modeluje svoju cestnú sieť ako neorientovaný graf – každé mesto je vrchol, každá cesta medzi nimi je hrana.

```cpp
class Graph {
private:
    unordered_map<string, vector<string>> adjList;

public:
    void printGraph() {
        for (auto& [vertex, edges] : adjList) {
            cout << vertex << ": [";
            for (int i = 0; i < (int)edges.size(); i++) {
                cout << edges[i];
                if (i < (int)edges.size() - 1) cout << ", ";
            }
            cout << "]\n";
        }
    }
};
```

---

## G-1: Add Vertex

Postavilo sa nové mesto. Pridaj ho do mapy siete. Ak mesto s týmto názvom už existuje, vráť `false`.

```
addVertex("Bratislava")
addVertex("Trnava")
addVertex("Nitra")

adjList:
Bratislava: []
Trnava:     []
Nitra:      []
```

**Hint:** Nové mesto zatiaľ nemá žiadne cesty – jeho zoznam susedov je prázdny.

```cpp
bool addVertex(string vertex) {

}
```

---

## G-2: Add Edge

Medzi dvoma mestami vybudovali diaľnicu. Pridaj obojsmernú cestu medzi ne. Ak niektoré mesto neexistuje, vráť `false`.

```
addEdge("Bratislava", "Trnava")
addEdge("Trnava", "Nitra")

adjList:
Bratislava: [Trnava]
Trnava:     [Bratislava, Nitra]
Nitra:      [Trnava]
```

**Hint:** Cesta je obojsmerná – musíš ju zaznamenať v zozname susedov oboch miest.

```cpp
bool addEdge(string vertex1, string vertex2) {

}
```

**Otestuj:**
```cpp
Graph g;
g.addVertex("Bratislava");
g.addVertex("Trnava");
g.addVertex("Nitra");
g.addEdge("Bratislava", "Trnava");
g.addEdge("Trnava", "Nitra");
g.printGraph();
```

---

## G-3: Remove Edge

Cesta medzi dvoma mestami bola uzavretá. Odstráň ju z mapy. Ak niektoré mesto neexistuje, vráť `false`.

```
PRED:
Bratislava: [Trnava, Nitra]
Trnava:     [Bratislava, Nitra]
Nitra:      [Bratislava, Trnava]

removeEdge("Bratislava", "Nitra")

PO:
Bratislava: [Trnava]
Trnava:     [Bratislava, Nitra]
Nitra:      [Trnava]
```

**Hint:** Keďže je cesta obojsmerná, musíš ju odstrániť z oboch zoznamov. Na vymazanie prvku z vektora môžeš použiť:
```cpp
auto& vec = adjList[vertex1];
vec.erase(remove(vec.begin(), vec.end(), vertex2), vec.end());
```

```cpp
bool removeEdge(string vertex1, string vertex2) {

}
```

---

## G-4: Remove Vertex

Mesto bolo zrušené a vymazané z mapy – spolu s ním zaniknú aj všetky cesty, ktoré k nemu viedli. Implementuj metódu `removeVertex`.

```
PRED:
Bratislava: [Trnava, Nitra]
Trnava:     [Bratislava, Nitra]
Nitra:      [Bratislava, Trnava]

removeVertex("Trnava")

PO:
Bratislava: [Nitra]
Nitra:      [Bratislava]
```

**Hint:** Nestačí len vymazať mesto zo zoznamu – každé mesto, ku ktorému viedla cesta, si stále pamätá spojenie. Najprv uprac susedov, potom vymaz mesto.

```
Susedia Trnava: [Bratislava, Nitra]

Krok 1: z Bratislava odstráň Trnava
Krok 2: z Nitra odstráň Trnava
Krok 3: vymaz Trnava z adjList
```

```cpp
bool removeVertex(string vertex) {

}
```

---

## G-5: BFS – najkratšia cesta po počte zastávok

Cestujúci stojí v meste `start` a chce sa dostať do čo najviac miest v čo najmenšom počte prestupov. Implementuj BFS, ktorý vypíše mestá v poradí, v akom by ich cestujúci navštívil.

```
Sieť:
Bratislava -- Trnava -- Nitra
     |              |
  Senec          Topolcany

BFS od "Bratislava":
Výstup: Bratislava  Trnava  Senec  Nitra  Topolcany
```

**Hint:** BFS prirodzene prechádza najprv všetky mestá vzdialené 1 prestup, potom 2 prestupy atď. Potrebuješ sledovať, ktoré mestá si už navštívil – inak sa môžeš zacykliť.

```
Fronta:   [Bratislava]
Ober Bratislava -> susedia: Trnava, Senec
Fronta:   [Trnava, Senec]
Ober Trnava -> susedia: Nitra, Topcany (Bratislava uz navstivena)
Fronta:   [Senec, Nitra, Topolcany]
...
```

```cpp
void bfs(string start) {

}
```

---

*Test | Dátové štruktúry | SPSIT*
