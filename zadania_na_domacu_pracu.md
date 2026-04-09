# Opakovacie úlohy: Dátové štruktúry

Každá úloha obsahuje popis, vizualizáciu a hinty. Implementuj metódy podľa zadania.

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

Pracuješ s touto základnou štruktúrou. Neupravuj ju – len dopĺňaj metódy.

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

Pridaj nový uzol na **koniec** zoznamu.

```
PRED:
head --> [3] --> [7] --> nullptr
                  ^
                 tail

VOLANIE: append(12)

PO:
head --> [3] --> [7] --> [12] --> nullptr
                           ^
                          tail
length: 2 --> 3
```

**Hinty:**
1. Vytvor nový uzol pomocou `new Node(value)`.
2. Ak je zoznam prázdny (`head == nullptr`), nový uzol sa stane zároveň `head` aj `tail`.
3. Inak: `tail->next` ukazuje na nový uzol a `tail` sa aktualizuje na nový uzol.
4. Nezabudni zvýšiť `length`.

```cpp
void append(int value) {
    // sem napíš kód
}
```

**Otestuj:**
```cpp
LinkedList ll(3);
ll.append(7);
ll.append(12);
ll.printList();
// Výstup: 3  7  12
```

---

## LL-2: Prepend

Pridaj nový uzol na **začiatok** zoznamu.

```
PRED:
head --> [7] --> [12] --> nullptr

VOLANIE: prepend(3)

PO:
head --> [3] --> [7] --> [12] --> nullptr
```

**Hinty:**
1. Vytvor nový uzol.
2. Nastav `newNode->next = head`.
3. `head` presmeruj na nový uzol.
4. Ak bol zoznam prázdny, nový uzol je aj `tail`.
5. Zvýš `length`.

```cpp
void prepend(int value) {
    // sem napíš kód
}
```

**Otestuj:**
```cpp
LinkedList ll(7);
ll.append(12);
ll.prepend(3);
ll.printList();
// Výstup: 3  7  12
```

---

## LL-3: Delete First

Vymaž **prvý** uzol. Vráť ukazovateľ na vymazaný uzol (alebo `nullptr` ak je zoznam prázdny).

```
PRED:
head --> [3] --> [7] --> [12] --> nullptr

VOLANIE: deleteFirst()

PO:
head --> [7] --> [12] --> nullptr
vrátená hodnota: ukazovateľ na [3]
```

**Hinty:**
1. Ak je `head == nullptr`, vráť `nullptr`.
2. Ulož `head` do dočasnej premennej `temp`.
3. Posuň `head` na `head->next`.
4. Nastav `temp->next = nullptr` (odpoj vymazaný uzol).
5. Ak je zoznam po vymazaní prázdny, nastav `tail = nullptr`.
6. Zmenši `length` a vráť `temp`.

```cpp
Node* deleteFirst() {
    // sem napíš kód
}
```

**Otestuj:**
```cpp
LinkedList ll(3);
ll.append(7);
ll.append(12);
Node* deleted = ll.deleteFirst();
cout << deleted->value << "\n";  // 3
ll.printList();                  // 7  12
```

---

## LL-4: Delete Last

Vymaž **posledný** uzol. Vráť ukazovateľ na vymazaný uzol.

```
PRED:
head --> [3] --> [7] --> [12] --> nullptr
                           ^
                          tail

VOLANIE: deleteLast()

PO:
head --> [3] --> [7] --> nullptr
                  ^
                 tail
vrátená hodnota: ukazovateľ na [12]
```

**Hinty:**
1. Ak je zoznam prázdny, vráť `nullptr`.
2. Ak má zoznam **jeden** uzol: nastav `head = tail = nullptr`, zmenši `length`, vráť uzol.
3. Pre bežný prípad: prechádzaj zoznamom, kým nenájdeš **predposledný** uzol (ten, ktorého `next == tail`).
4. Ulož `tail` do `temp`, nastav predposledný uzol ako nový `tail`, odpoj ho (`tail->next = nullptr`).
5. Zmenši `length` a vráť `temp`.

```
Prechádzanie na predposledný uzol:

pre --> [3] --> [7] --> [12] --> nullptr
                ^
          tu zastavíme (pre->next == tail)
```

```cpp
Node* deleteLast() {
    // sem napíš kód
}
```

**Otestuj:**
```cpp
LinkedList ll(3);
ll.append(7);
ll.append(12);
Node* deleted = ll.deleteLast();
cout << deleted->value << "\n";  // 12
ll.printList();                  // 3  7
```

---

## LL-5: Get

Vráť **ukazovateľ na uzol** na danom indexe (indexovanie od 0). Ak index neexistuje, vráť `nullptr`.

```
head --> [3] --> [7] --> [12] --> nullptr
index:    0       1        2

get(1)  -->  vráti ukazovateľ na uzol s hodnotou 7
get(5)  -->  vráti nullptr
```

**Hinty:**
1. Ak je `index < 0` alebo `index >= length`, vráť `nullptr`.
2. Začni s `temp = head` a prechádzaj cyklom `index`-krát.
3. Po skončení cyklu `temp` ukazuje na hľadaný uzol.

```cpp
Node* get(int index) {
    // sem napíš kód
}
```

**Otestuj:**
```cpp
LinkedList ll(3);
ll.append(7);
ll.append(12);
cout << ll.get(1)->value << "\n";  // 7
cout << (ll.get(5) == nullptr) << "\n";  // 1 (true)
```

---

## LL-6: Set

**Zmeň hodnotu** uzla na danom indexe. Vráť `true` ak sa zmena podarila, inak `false`.

```
PRED:
head --> [3] --> [7] --> [12] --> nullptr

VOLANIE: set(1, 99)

PO:
head --> [3] --> [99] --> [12] --> nullptr
```

**Hinty:**
1. Použi metódu `get(index)` na získanie uzla.
2. Ak `get` vráti `nullptr`, vráť `false`.
3. Inak zmeň `node->value` a vráť `true`.

```cpp
bool set(int index, int value) {
    // sem napíš kód
}
```

**Otestuj:**
```cpp
LinkedList ll(3);
ll.append(7);
ll.append(12);
cout << ll.set(1, 99) << "\n";  // 1 (true)
ll.printList();                 // 3  99  12
cout << ll.set(5, 99) << "\n"; // 0 (false)
```

---

## LL-7: Insert

Vlož nový uzol na **daný index**. Vráť `true` ak sa operácia podarila.

```
PRED:
head --> [3] --> [7] --> [12] --> nullptr
index:    0       1        2

VOLANIE: insert(1, 50)

PO:
head --> [3] --> [50] --> [7] --> [12] --> nullptr
index:    0        1       2        3
```

**Hinty:**
1. Ak je `index < 0` alebo `index > length`, vráť `false`.
2. Ak `index == 0`, použi `prepend(value)` a vráť `true`.
3. Ak `index == length`, použi `append(value)` a vráť `true`.
4. Pre bežný prípad: získaj uzol na indexe `index - 1` pomocou `get`.
5. Nastav `newNode->next = prev->next` a `prev->next = newNode`.
6. Zvýš `length` a vráť `true`.

```
prev = get(index - 1)

... --> [prev] --> [7] --> ...
             \
              [50] --> [7] --> ...

Krok A: newNode->next = prev->next   (50 ukazuje na 7)
Krok B: prev->next    = newNode      (3 ukazuje na 50)
```

```cpp
bool insert(int index, int value) {
    // sem napíš kód
}
```

**Otestuj:**
```cpp
LinkedList ll(3);
ll.append(7);
ll.append(12);
ll.insert(1, 50);
ll.printList();  // 3  50  7  12
```

---

## LL-8: Delete Node

Vymaž uzol na **danom indexe**. Vráť ukazovateľ na vymazaný uzol.

```
PRED:
head --> [3] --> [50] --> [7] --> [12] --> nullptr

VOLANIE: deleteNode(1)

PO:
head --> [3] --> [7] --> [12] --> nullptr
vrátená hodnota: ukazovateľ na [50]
```

**Hinty:**
1. Ak `index == 0`, použi `deleteFirst()`.
2. Ak `index == length - 1`, použi `deleteLast()`.
3. Pre bežný prípad: získaj uzol na indexe `index - 1` (`prev`).
4. Ulož `prev->next` (uzol na vymazanie) do `temp`.
5. Nastav `prev->next = temp->next` (preskočí vymazávaný uzol).
6. Odpoj: `temp->next = nullptr`.
7. Zmenši `length` a vráť `temp`.

```
prev = get(index - 1)

... --> [3] --> [50] --> [7] --> ...
                  ^
                temp

prev->next = temp->next  -->  [3] --> [7] --> ...
temp->next = nullptr         [50] --> nullptr  (odpojený)
```

```cpp
Node* deleteNode(int index) {
    // sem napíš kód
}
```

**Otestuj:**
```cpp
LinkedList ll(3);
ll.append(50);
ll.append(7);
ll.append(12);
Node* del = ll.deleteNode(1);
cout << del->value << "\n";  // 50
ll.printList();              // 3  7  12
```

---

## LL-9: Reverse (stredne náročná)

**Obráť** poradie uzlov v zozname in-place (bez vytvorenia nového zoznamu).

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

**Hinty:**
1. Prehoď `head` a `tail`.
2. Použi tri ukazovatele: `prev = nullptr`, `temp = head` (pôvodný head, teraz tail), `after`.
3. V každej iterácii:
   - Ulož `after = temp->next`
   - Otočí šípku: `temp->next = prev`
   - Posuň: `prev = temp`, `temp = after`
4. Opakuj, kým `temp != nullptr`.

```
Vizualizácia otáčania šípok krok za krokom:

Štart:
prev=null  temp=[1]  after=[2]

Krok 1:  null <-- [1]   [2] --> [3] --> [4]
         prev=[1]  temp=[2]  after=[3]

Krok 2:  null <-- [1] <-- [2]   [3] --> [4]
         prev=[2]  temp=[3]  after=[4]

Krok 3:  null <-- [1] <-- [2] <-- [3]   [4]
         prev=[3]  temp=[4]  after=null

Krok 4:  null <-- [1] <-- [2] <-- [3] <-- [4]
         prev=[4]  temp=null  --> koniec
```

```cpp
void reverse() {
    // sem napíš kód
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

## Základná štruktúra (použi pre Stack aj Queue)

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

Stack funguje na princípe **LIFO** (Last In, First Out). Implementuj metódu `push`, ktorá pridá prvok na **vrchol**.

```
PRED:
top --> [2] --> [1] --> nullptr
height = 2

VOLANIE: push(3)

PO:
top --> [3] --> [2] --> [1] --> nullptr
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
        // sem napíš kód
    }
};
```

**Hinty:**
1. Vytvor nový uzol.
2. Nastav `newNode->next = top`.
3. `top` presmeruj na nový uzol.
4. Zvýš `height`.

**Otestuj:**
```cpp
Stack s(1);
s.push(2);
s.push(3);
// top ukazuje na uzol s hodnotou 3
```

---

## SQ-2: Stack – Pop

Implementuj metódu `pop`, ktorá **odoberie a vráti** hodnotu z vrcholu zásobníka.

```
PRED:
top --> [3] --> [2] --> [1] --> nullptr
height = 3

VOLANIE: pop()

PO:
top --> [2] --> [1] --> nullptr
height = 2
vrátená hodnota: 3
```

**Hinty:**
1. Ak je zásobník prázdny (`height == 0`), vráť `INT_MIN` alebo hoď výnimku.
2. Ulož `top` do `temp`.
3. Posuň `top` na `top->next`.
4. Odpoj vymazaný uzol: `temp->next = nullptr`.
5. Zmenši `height`, ulož hodnotu, vymaž `temp` (`delete temp`), vráť hodnotu.

```cpp
int pop() {
    // sem napíš kód
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

Queue funguje na princípe **FIFO** (First In, First Out). Implementuj metódu `enqueue`, ktorá pridá prvok na **koniec** fronty.

```
PRED:
first --> [10] --> [20] --> nullptr
                    ^
                   last
length = 2

VOLANIE: enqueue(30)

PO:
first --> [10] --> [20] --> [30] --> nullptr
                              ^
                             last
length = 3
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
        // sem napíš kód
    }
};
```

**Hinty:**
1. Vytvor nový uzol.
2. Ak je fronta prázdna, nový uzol je zároveň `first` aj `last`.
3. Inak: `last->next = newNode` a `last = newNode`.
4. Zvýš `length`.

---

## SQ-4: Queue – Dequeue

Implementuj metódu `dequeue`, ktorá **odoberie a vráti** hodnotu z **začiatku** fronty.

```
PRED:
first --> [10] --> [20] --> [30] --> nullptr
length = 3

VOLANIE: dequeue()

PO:
first --> [20] --> [30] --> nullptr
length = 2
vrátená hodnota: 10
```

**Hinty:**
1. Ak je fronta prázdna, vráť `INT_MIN`.
2. Ulož `first` do `temp`.
3. Posuň `first` na `first->next`.
4. Ak je fronta po odobratí prázdna, nastav `last = nullptr`.
5. Odpoj `temp`, zmenši `length`, vráť hodnotu.

```cpp
int dequeue() {
    // sem napíš kód
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

## SQ-5: Overenie závoriek (stredne náročná)

Napíš funkciu `isBalanced(string s)`, ktorá pomocou zásobníka skontroluje, či sú závorky v reťazci správne spárované.

```
"({[]})"  -->  true
"({[})"   -->  false   (} zatvára [, nie {)
"((())"   -->  false   (jeden ( zostal otvorený)
```

**Hinty:**
1. Prechádzaj reťazec znak po znaku.
2. Ak je znak otvárajúca závorka `(`, `[`, `{` – vlož ho na zásobník (`push`).
3. Ak je znak zatvárajúca závorka `)`, `]`, `}`:
   - Ak je zásobník prázdny, vráť `false`.
   - Ober vrchol zásobníka (`pop`) a skontroluj, či zodpovedá aktuálnej zatvárajúcej závorke.
   - Ak nie, vráť `false`.
4. Na konci: ak je zásobník prázdny, vráť `true`, inak `false`.

```
Príklad pre "({[]})":

Znak  |  Zásobník (top vľavo)
------|----------------------
(     |  (
{     |  { (
[     |  [ { (
]     |  { (        (] páruje s [, pop)
}     |  (          (} páruje s {, pop)
)     |  prazdny    () páruje s (, pop)
koniec -> zasobnik je prázdny -> true
```

```cpp
bool isBalanced(string s) {
    // sem napíš kód
}
```

---

---

# Sekcia 3 – Binárny vyhľadávací strom (BST)

## Základná štruktúra

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

Vlož hodnotu do BST. Ak hodnota už existuje, nič nerob (vráť `false`).

**Pravidlo BST:** hodnoty menšie ako aktuálny uzol idú **doľava**, väčšie **doprava**.

```
Vkladáme postupne: 47, 21, 76, 18, 52

insert(47):         47

insert(21):         47
                   /
                 21

insert(76):         47
                   /  \
                 21    76

insert(18):         47
                   /  \
                 21    76
                /
              18

insert(52):         47
                   /  \
                 21    76
                /      /
              18      52
```

**Hinty:**
1. Vytvor nový uzol.
2. Ak je strom prázdny (`root == nullptr`), nový uzol sa stane `root`.
3. Inak: začni v `root` a prechádzaj stromom:
   - Ak `value < current->value` choď doľava.
   - Ak `value > current->value` choď doprava.
   - Ak `value == current->value` vráť `false`.
   - Ak je miesto voľné (`nullptr`), vlož tam nový uzol a vráť `true`.

```
Prechádzanie pre insert(52):

current = 47  -->  52 > 47, choď doprava
current = 76  -->  52 < 76, choď doľava
current = nullptr  -->  vlož tu nový uzol [52]
```

```cpp
bool insert(int value) {
    // sem napíš kód
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
cout << bst.root->value << "\n";          // 47
cout << bst.root->left->value << "\n";    // 21
cout << bst.root->right->value << "\n";   // 76
```

---

## BST-2: Contains

Vráť `true` ak hodnota v strome existuje, inak `false`.

```
Strom:
        47
       /  \
     21    76
    /      /
  18      52

contains(52)  -->  true
contains(99)  -->  false
```

**Hinty:**
1. Začni v `root`.
2. Ak je `current == nullptr`, vráť `false` (hodnota neexistuje).
3. Ak `value == current->value`, vráť `true`.
4. Ak `value < current->value`, choď doľava (`current = current->left`).
5. Ak `value > current->value`, choď doprava (`current = current->right`).
6. Opakuj, kým nenájdeš hodnotu alebo nenarazíš na `nullptr`.

```
Hľadanie 52:

current = 47  -->  52 > 47, choď doprava
current = 76  -->  52 < 76, choď doľava
current = 52  -->  52 == 52, nashli sme! return true
```

```cpp
bool contains(int value) {
    // sem napíš kód
}
```

**Otestuj:**
```cpp
cout << bst.contains(52) << "\n";   // 1 (true)
cout << bst.contains(99) << "\n";   // 0 (false)
cout << bst.contains(21) << "\n";   // 1 (true)
```

---

## BST-3: Inorder traversal (stredne náročná)

Implementuj rekurzívny prechod stromom **Inorder** (doľava – koreň – doprava).
Inorder BST vypíše hodnoty v **zoradenom poradí**.

```
Strom:
        47
       /  \
     21    76
    /  \   /
  18   27 52

Inorder: 18  21  27  47  52  76
```

**Hinty:**
1. Napíš pomocnú rekurzívnu funkciu `inorderHelper(Node* node)`.
2. Základný prípad: ak `node == nullptr`, vráť sa.
3. Inak:
   - Volaj `inorderHelper(node->left)`
   - Vypíš `node->value`
   - Volaj `inorderHelper(node->right)`

```
Poradie volaní pre koreň 47:

inorder(47)
  inorder(21)
    inorder(18)
      inorder(nullptr) --> return
      print 18
      inorder(nullptr) --> return
    print 21
    inorder(27)
      ...
  print 47
  inorder(76)
    ...
```

```cpp
void inorderHelper(Node* node) {
    // sem napíš kód
}

void inorder() {
    inorderHelper(root);
}
```

---

---

# Sekcia 4 – Hash Table

## Základná štruktúra

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

Vlož dvojicu `(key, value)` do hašovacej tabuľky.

```
Tabuľka (SIZE = 7):

set("nails", 1000)  -->  hash("nails") = 4
set("tile",  400)   -->  hash("tile")  = 1
set("lumber",3000)  -->  hash("lumber")= 4  (kolízia s "nails"!)

Index 0: []
Index 1: [("tile", 400)]
Index 2: []
Index 3: []
Index 4: [("nails", 1000), ("lumber", 3000)]  <-- reťazec (chaining)
Index 5: []
Index 6: []
```

**Hinty:**
1. Vypočítaj index pomocou `hash(key)`.
2. Vlož `make_pair(key, value)` do `dataMap[index]` pomocou `push_back`.

```cpp
void set(string key, int value) {
    // sem napíš kód
}
```

---

## HT-2: Get

Vráť hodnotu pre daný kľúč. Ak kľúč neexistuje, vráť `0`.

```
get("tile")    -->  400
get("lumber")  -->  3000
get("cement")  -->  0   (neexistuje)
```

**Hinty:**
1. Vypočítaj index pomocou `hash(key)`.
2. Prechádzaj cyklom cez `dataMap[index]` (môže tam byť viac párov – chaining).
3. Pre každý pár skontroluj, či `pair.first == key`.
4. Ak áno, vráť `pair.second`.
5. Ak nenájdeš, vráť `0`.

```cpp
int get(string key) {
    // sem napíš kód
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

Vráť vektor všetkých kľúčov v tabuľke. Každý kľúč sa má objaviť len raz.

```
ht.keys()  -->  ["tile", "nails", "lumber"]
               (poradie môže byť rôzne)
```

**Hinty:**
1. Vytvor prázdny `vector<string> allKeys`.
2. Prechádzaj cyklom cez všetky indexy `dataMap` (od 0 po SIZE).
3. Pre každý index prechádzaj cyklom cez páry v reťazci.
4. Vlož `pair.first` do `allKeys`.
5. Vráť `allKeys`.

```cpp
vector<string> keys() {
    // sem napíš kód
}
```

---

## HT-4: Item in Common (stredne náročná)

Napíš funkciu `itemInCommon`, ktorá zistí, či majú dva vektory celých čísel aspoň jeden spoločný prvok.
Riešenie musí mať časovú zložitosť **O(n)** – použi hašovaciu tabuľku (napr. `unordered_map` alebo `unordered_set`).

```
{1, 3, 5, 7}  a  {2, 4, 5, 8}  -->  true   (spoločné: 5)
{1, 3, 5, 7}  a  {2, 4, 6, 8}  -->  false
```

**Hinty:**
1. Prechádzaj prvý vektor a vlož každý prvok do `unordered_set<int>`.
2. Prechádzaj druhý vektor a pre každý prvok skontroluj, či je v sete (`set.count(x) > 0`).
3. Ak áno, vráť `true`. Ak po prechode všetkých prvkov nič nenájdeš, vráť `false`.

```
Prečo O(n) a nie O(n^2)?

O(n^2) – dva vnorené cykly:          O(n) – set lookup je O(1):
for každý x v A:                     vlož A do setu: O(n)
  for každý y v B:                   for každý y v B:
    if x == y: return true             if y v sete: return true
```

```cpp
bool itemInCommon(vector<int> a, vector<int> b) {
    // sem napíš kód
}
```

---

---

# Sekcia 5 – Graf

## Základná štruktúra

```cpp
class Graph {
private:
    unordered_map<string, vector<string>> adjList;

public:
    void printGraph() {
        for (auto& [vertex, edges] : adjList) {
            cout << vertex << ": [";
            for (int i = 0; i < edges.size(); i++) {
                cout << edges[i];
                if (i < edges.size() - 1) cout << ", ";
            }
            cout << "]\n";
        }
    }
};
```

---

## G-1: Add Vertex

Pridaj nový vrchol do grafu. Ak vrchol už existuje, vráť `false`.

```
addVertex("A")
addVertex("B")
addVertex("C")

adjList:
A: []
B: []
C: []
```

**Hinty:**
1. Skontroluj, či `adjList.count(vertex) > 0`. Ak áno, vráť `false`.
2. Inak vlož `adjList[vertex] = {}` (prázdny vektor hrán).
3. Vráť `true`.

```cpp
bool addVertex(string vertex) {
    // sem napíš kód
}
```

---

## G-2: Add Edge

Pridaj **neorientovanú** hranu medzi dva vrcholy. Ak niektorý vrchol neexistuje, vráť `false`.

```
PRED:
A: []
B: []
C: []

addEdge("A", "B")
addEdge("B", "C")

PO:
A: [B]
B: [A, C]
C: [B]
```

**Hinty:**
1. Skontroluj, či obidva vrcholy existujú v `adjList`. Ak nie, vráť `false`.
2. Pridaj `vertex2` do `adjList[vertex1]` (pomocou `push_back`).
3. Pridaj `vertex1` do `adjList[vertex2]` (neorientovaný graf – pridáš z oboch strán).
4. Vráť `true`.

```cpp
bool addEdge(string vertex1, string vertex2) {
    // sem napíš kód
}
```

**Otestuj:**
```cpp
Graph g;
g.addVertex("A");
g.addVertex("B");
g.addVertex("C");
g.addEdge("A", "B");
g.addEdge("B", "C");
g.printGraph();
// A: [B]
// B: [A, C]
// C: [B]
```

---

## G-3: Remove Edge

Odstráň hranu medzi dvoma vrcholmi. Ak niektorý vrchol neexistuje, vráť `false`.

```
PRED:
A: [B, C]
B: [A, C]
C: [A, B]

removeEdge("A", "C")

PO:
A: [B]
B: [A, C]
C: [B]
```

**Hinty:**
1. Skontroluj, či obidva vrcholy existujú.
2. Z `adjList[vertex1]` odstráň `vertex2`.
3. Z `adjList[vertex2]` odstráň `vertex1`.
4. Na odstránenie prvku z vektora použi:
   ```cpp
   auto& vec = adjList[vertex1];
   vec.erase(remove(vec.begin(), vec.end(), vertex2), vec.end());
   ```

```cpp
bool removeEdge(string vertex1, string vertex2) {
    // sem napíš kód
}
```

---

## G-4: Remove Vertex

Odstráň vrchol **a všetky hrany** vedúce k nemu.

```
PRED:
A: [B, C]
B: [A, C]
C: [A, B]

removeVertex("B")

PO:
A: [C]
C: [A]
```

**Hinty:**
1. Skontroluj, či vrchol existuje. Ak nie, vráť `false`.
2. Pre každého suseda odstraňovaného vrcholu: odstráň odstraňovaný vrchol zo susedovho zoznamu.
   ```cpp
   for (auto otherVertex : adjList[vertex]) {
       // odstráň vertex z adjList[otherVertex]
   }
   ```
3. Vymaz samotný vrchol z `adjList` pomocou `adjList.erase(vertex)`.
4. Vráť `true`.

```
Pre removeVertex("B"):

Susedia B: [A, C]

  Krok 1: z A odstráň B  -->  A: [C]
  Krok 2: z C odstráň B  -->  C: [A]
  Krok 3: vymaz B z adjList
```

```cpp
bool removeVertex(string vertex) {
    // sem napíš kód
}
```

**Otestuj:**
```cpp
Graph g;
g.addVertex("A");
g.addVertex("B");
g.addVertex("C");
g.addEdge("A", "B");
g.addEdge("B", "C");
g.addEdge("A", "C");
g.removeVertex("B");
g.printGraph();
// A: [C]
// C: [A]
```

---

## G-5: BFS – prehľadávanie do šírky (stredne náročná)

Implementuj prehľadávanie grafu do šírky (Breadth-First Search) od daného vrcholu.
Vypíš vrcholy v poradí, v akom sú navštívené.

```
Graf:
A -- B -- D
|    |
C -- E

BFS od "A":
Navštívime: A, potom susedov A (B, C), potom susedov B (D, E)...

Výstup: A  B  C  D  E
(poradie susedov závisí od adj. listu)
```

**Hinty:**
1. Vytvor `queue<string>` a `unordered_set<string> visited`.
2. Vlož štartovací vrchol do fronty aj do `visited`.
3. Kým fronta nie je prázdna:
   - Ober prvý vrchol z fronty (`currentVertex = queue.front(); queue.pop()`).
   - Vypíš ho.
   - Pre každého suseda:
     - Ak ešte nebol navštívený, vlož ho do `visited` a do fronty.

```
Vizualizácia BFS pre graf vyššie od "A":

Fronta:   [A]          Visited: {A}
Ober A -> vypíš A
  Susedia A: B, C -> vlož do fronty
Fronta:   [B, C]       Visited: {A, B, C}

Ober B -> vypíš B
  Susedia B: A (uz visited), D, E -> vlož D, E
Fronta:   [C, D, E]    Visited: {A, B, C, D, E}

Ober C -> vypíš C
  Susedia C: uz vsetci visited
Fronta:   [D, E]

Ober D -> vypíš D  ...
Ober E -> vypíš E  ...
```

```cpp
void bfs(string start) {
    // sem napíš kód
}
```

---

*Opakovacie úlohy | Dátové štruktúry | SPSIT*
