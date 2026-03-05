# Dátové štruktúry a Algoritmy v C++

Tento materiál pokrýva päť kľúčových oblastí: **Dvojito prepojený zoznam (DLL)**, **Zásobníky a Fronty**, **Stromy (BST)**, **Hash Tables**, a **Grafy**. Každá kapitola obsahuje teóriu, vizualizácie, čiastočné implementácie na dopracovanie a **samostatné úlohy na odovzdanie**.

> **Kľúčová rada:** "Kresli, kresli, kresli!" - Pred písaním kódu vždy nakresli štruktúru na papier.

---

# Prehľad úloh na odovzdanie

| #   | Úloha                                                               | Sekcia     | Obtiažnosť |
| --- | ------------------------------------------------------------------- | ---------- | ---------- |
| 1   | [DLL: Implementácia základných metód](#uloha-1-dll-zakladne-metody) | DLL        | Stredná    |
| 2   | [DLL: Reverse](#uloha-2-dll-reverse)                                | DLL        | Stredná    |
| 3   | [Stack: Balanced Parentheses](#uloha-3-stack-balanced-parentheses)  | Stack      | Stredná    |
| 4   | [Queue: Implementácia a Simulácia](#uloha-4-queue-implementacia)    | Queue      | Stredná    |
| 5   | [BST: Kompletná implementácia](#uloha-5-bst-implementacia)          | BST        | Vyššia     |
| 6   | [BST: Traversal metódy](#uloha-6-bst-traversal)                     | BST        | Vyššia     |
| 7   | [Hash Table: Implementácia](#uloha-7-hash-table-implementacia)      | Hash Table | Stredná    |
| 8   | [Hash Table: Two Sum](#uloha-8-hash-table-two-sum)                  | Hash Table | Vyššia     |
| 9   | [Graph: Implementácia](#uloha-9-graph-implementacia)                | Graph      | Stredná    |
| 10  | [Graph: BFS a DFS](#uloha-10-graph-bfs-dfs)                         | Graph      | Vyššia     |

---

# Časť 1: Dvojito prepojený zoznam (Doubly Linked List)

## 1.1 Úvod do DLL

**Doubly Linked List** je lineárna dátová štruktúra, kde každý uzol obsahuje:

- **Hodnotu (value)**
- **Ukazovateľ na predchádzajúci uzol (prev)**
- **Ukazovateľ na nasledujúci uzol (next)**

### Porovnanie s jednoduchým prepojeným zoznamom:

| Vlastnosť     | Singly Linked List                  | Doubly Linked List         |
| ------------- | ----------------------------------- | -------------------------- |
| Smer prechodu | Len dopredu                         | Dopredu aj dozadu          |
| Pamäť na uzol | Menej (1 pointer)                   | Viac (2 pointers)          |
| Mazanie uzla  | O(n) - potrebujeme nájsť predchodcu | O(1) - máme priamy prístup |
| Implementácia | Jednoduchšia                        | Zložitejšia                |

### Vizualizácia DLL:

```
    ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
    │     HEAD     │     │              │     │     TAIL     │
    ├──────────────┤     ├──────────────┤     ├──────────────┤
    │ prev = NULL  │◄────│    prev      │◄────│    prev      │
    │ value = 10   │     │ value = 20   │     │ value = 30   │
    │    next      │────►│    next      │────►│ next = NULL  │
    └──────────────┘     └──────────────┘     └──────────────┘
```

---

## 1.2 DLL: Constructor (Konštruktor)

### Teória

Konštruktor inicializuje DLL s jedným uzlom, ktorý je súčasne **head** aj **tail**.

### Implementácia

```cpp
#include <iostream>
using namespace std;

class Node {
public:
    int value;
    Node* next;
    Node* prev;

    Node(int value) {
        this->value = value;
        this->next = nullptr;
        this->prev = nullptr;
    }
};

class DoublyLinkedList {
public:
    Node* head;
    Node* tail;
    int length;

    // CONSTRUCTOR - vytvorí DLL s jedným uzlom
    DoublyLinkedList(int value) {
        Node* newNode = new Node(value);
        head = newNode;
        tail = newNode;
        length = 1;
    }

    void printList() {
        Node* temp = head;
        cout << "NULL <-> ";
        while (temp != nullptr) {
            cout << temp->value << " <-> ";
            temp = temp->next;
        }
        cout << "NULL" << endl;
    }
};
```

**Časová zložitosť:** O(1)

---

## 1.3 DLL: Append (Pridanie na koniec)

### Teória

**Append** pridáva nový uzol na **koniec** zoznamu. Musíme:

1. Vytvoriť nový uzol
2. Ak je zoznam prázdny → head a tail ukazujú na nový uzol
3. Inak → prepojiť tail s novým uzlom

### Implementácia

```cpp
void append(int value) {
    Node* newNode = new Node(value);

    // Prípad 1: Prázdny zoznam
    if (length == 0) {
        head = newNode;
        tail = newNode;
    }
    // Prípad 2: Zoznam má prvky
    else {
        tail->next = newNode;      // Starý tail ukazuje na nový uzol
        newNode->prev = tail;       // Nový uzol ukazuje späť na starý tail
        tail = newNode;             // Tail sa posunie na nový uzol
    }
    length++;
}
```

### Vizualizácia - Append(3) do [1, 2]:

```
PRED:
    head           tail
      │              │
      ▼              ▼
    ┌────┐         ┌────┐
    │ 1  │◄───────►│ 2  │
    └────┘         └────┘

PO:
    head                     tail
      │                        │
      ▼                        ▼
    ┌────┐         ┌────┐    ┌────┐
    │ 1  │◄───────►│ 2  │◄──►│ 3  │
    └────┘         └────┘    └────┘
```

**Časová zložitosť:** O(1)

---

## 1.4 DLL: Delete Last (Mazanie z konca)

### Teória

**Delete Last** odstráni posledný uzol. Výhodou DLL je, že nepotrebujeme prechádzať celý zoznam - máme priamy prístup cez `tail->prev`.

### Implementácia

```cpp
Node* deleteLast() {
    // Prípad 1: Prázdny zoznam
    if (length == 0) return nullptr;

    Node* temp = tail;

    // Prípad 2: Jeden prvok
    if (length == 1) {
        head = nullptr;
        tail = nullptr;
    }
    // Prípad 3: Viac prvkov
    else {
        tail = tail->prev;          // Tail sa posunie na predchádzajúci uzol
        tail->next = nullptr;       // Nový tail už neukazuje na nič
        temp->prev = nullptr;       // Odpojíme mazaný uzol
    }
    length--;
    return temp;
}
```

**Časová zložitosť:** O(1) - výhoda oproti SLL kde je O(n)!

---

## 1.5 DLL: Prepend (Pridanie na začiatok)

### Teória

**Prepend** pridáva nový uzol na **začiatok** zoznamu.

### Implementácia

```cpp
void prepend(int value) {
    Node* newNode = new Node(value);

    // Prípad 1: Prázdny zoznam
    if (length == 0) {
        head = newNode;
        tail = newNode;
    }
    // Prípad 2: Zoznam má prvky
    else {
        newNode->next = head;       // Nový uzol ukazuje na starý head
        head->prev = newNode;       // Starý head ukazuje späť na nový uzol
        head = newNode;             // Head sa posunie na nový uzol
    }
    length++;
}
```

**Časová zložitosť:** O(1)

---

## 1.6 DLL: Delete First (Mazanie zo začiatku)

### Teória

**Delete First** odstráni prvý uzol zo zoznamu.

### Implementácia

```cpp
Node* deleteFirst() {
    // Prípad 1: Prázdny zoznam
    if (length == 0) return nullptr;

    Node* temp = head;

    // Prípad 2: Jeden prvok
    if (length == 1) {
        head = nullptr;
        tail = nullptr;
    }
    // Prípad 3: Viac prvkov
    else {
        head = head->next;          // Head sa posunie na ďalší uzol
        head->prev = nullptr;       // Nový head už neukazuje späť
        temp->next = nullptr;       // Odpojíme mazaný uzol
    }
    length--;
    return temp;
}
```

**Časová zložitosť:** O(1)

---

## 1.7 DLL: Get (Získanie uzla na indexe)

### Teória

**Get** vráti uzol na danom indexe. Výhoda DLL: môžeme začať od **head** alebo **tail** podľa toho, čo je bližšie!

### Implementácia

```cpp
Node* get(int index) {
    // Kontrola platnosti indexu
    if (index < 0 || index >= length) return nullptr;

    Node* temp;

    // Optimalizácia: začni od bližšieho konca
    if (index < length / 2) {
        // Index je v prvej polovici → začni od head
        temp = head;
        for (int i = 0; i < index; i++) {
            temp = temp->next;
        }
    } else {
        // Index je v druhej polovici → začni od tail
        temp = tail;
        for (int i = length - 1; i > index; i--) {
            temp = temp->prev;
        }
    }
    return temp;
}
```

### Vizualizácia optimalizácie:

```
Index:    0     1     2     3     4     5
        ┌───┬───┬───┬───┬───┬───┐
        │ A │ B │ C │ D │ E │ F │
        └───┴───┴───┴───┴───┴───┘
          ↑                   ↑
        head                tail

get(1): Začni od HEAD  → 1 krok
get(4): Začni od TAIL  → 1 krok
```

**Časová zložitosť:** O(n) - ale v priemere len O(n/2) vďaka optimalizácii!

---

## 1.8 - 1.10: Metódy na samostatné dopracovanie

Na základe predchádzajúcich príkladov **dopracujte sami** tieto metódy:

### Set (Nastavenie hodnoty)

**Teória:** Zmení hodnotu uzla na danom indexe. Využíva metódu get().

```cpp
bool set(int index, int value) {
    // TODO: Dopracujte sami
    // 1. Použite get() na získanie uzla
    // 2. Ak uzol existuje, zmeňte jeho hodnotu
    // 3. Vráťte true/false podľa úspechu
}
```

### Insert (Vloženie na index)

**Teória:** Vloží nový uzol na určený index. Musíte správne prepojiť 4 ukazovatele!

```cpp
bool insert(int index, int value) {
    // TODO: Dopracujte sami
    // 1. Skontrolujte platnosť indexu
    // 2. Špeciálne prípady: index 0 (prepend) a index length (append)
    // 3. Všeobecný prípad: nájdite uzol pred pozíciou a prepojte 4 ukazovatele
}
```

### Delete Node (Mazanie na indexe)

**Teória:** Odstráni uzol na určenom indexe.

```cpp
Node* deleteNode(int index) {
    // TODO: Dopracujte sami
    // 1. Skontrolujte platnosť indexu
    // 2. Špeciálne prípady: index 0 (deleteFirst) a index length-1 (deleteLast)
    // 3. Všeobecný prípad: prepojte susedné uzly a odpojte mazaný
}
```

---

## DLL: Kód na dopracovanie {#uloha-1-dll-zakladne-metody}

### ÚLOHA 1: DLL - Základné metódy

**Zadanie:** Dopracujte chýbajúce časti označené `// TODO`:

```cpp
#include <iostream>
using namespace std;

class Node {
public:
    int value;
    Node* next;
    Node* prev;

    Node(int value) {
        this->value = value;
        this->next = nullptr;
        this->prev = nullptr;
    }
};

class DoublyLinkedList {
public:
    Node* head;
    Node* tail;
    int length;

    DoublyLinkedList(int value) {
        Node* newNode = new Node(value);
        head = newNode;
        tail = newNode;
        length = 1;
    }

    void printList() {
        Node* temp = head;
        cout << "NULL <-> ";
        while (temp != nullptr) {
            cout << temp->value << " <-> ";
            temp = temp->next;
        }
        cout << "NULL" << endl;
    }

    void append(int value) {
        Node* newNode = new Node(value);
        if (length == 0) {
            head = newNode;
            tail = newNode;
        } else {
            tail->next = newNode;
            newNode->prev = tail;
            tail = newNode;
        }
        length++;
    }

    Node* deleteLast() {
        if (length == 0) return nullptr;
        Node* temp = tail;
        if (length == 1) {
            head = nullptr;
            tail = nullptr;
        } else {
            tail = tail->prev;
            tail->next = nullptr;
            temp->prev = nullptr;
        }
        length--;
        return temp;
    }

    void prepend(int value) {
        // TODO: Implementujte prepend
        // Hint: Podobné ako append, ale pracujete s head
    }

    Node* deleteFirst() {
        // TODO: Implementujte deleteFirst
        // Hint: Podobné ako deleteLast, ale pracujete s head
    }

    Node* get(int index) {
        if (index < 0 || index >= length) return nullptr;
        Node* temp;
        if (index < length / 2) {
            temp = head;
            for (int i = 0; i < index; i++) {
                temp = temp->next;
            }
        } else {
            temp = tail;
            for (int i = length - 1; i > index; i--) {
                temp = temp->prev;
            }
        }
        return temp;
    }

    bool set(int index, int value) {
        // TODO: Implementujte set
        // Hint: Použite get() a zmeňte hodnotu
    }

    bool insert(int index, int value) {
        // TODO: Implementujte insert
        // Hint: Ošetrite edge cases (0, length), potom prepojte 4 pointery
    }

    Node* deleteNode(int index) {
        // TODO: Implementujte deleteNode
        // Hint: Ošetrite edge cases, potom prepojte susedov
    }
};

// Testovanie:
int main() {
    DoublyLinkedList* dll = new DoublyLinkedList(1);
    dll->append(2);
    dll->append(3);
    dll->prepend(0);
    dll->printList();  // Očakávaný výstup: NULL <-> 0 <-> 1 <-> 2 <-> 3 <-> NULL

    dll->insert(2, 100);
    dll->printList();  // Očakávaný výstup: NULL <-> 0 <-> 1 <-> 100 <-> 2 <-> 3 <-> NULL

    dll->deleteNode(2);
    dll->printList();  // Očakávaný výstup: NULL <-> 0 <-> 1 <-> 2 <-> 3 <-> NULL

    return 0;
}
```

---

## ÚLOHA 2: DLL - Reverse {#uloha-2-dll-reverse}

**Zadanie:** Implementujte metódu `reverse()` ktorá obráti poradie prvkov v DLL.

```cpp
void reverse() {
    // TODO: Implementujte reverse
    // Hint: Pre každý uzol vymeňte prev a next
    // Hint: Na konci vymeňte head a tail
}

// Test:
// Vstup:  NULL <-> 1 <-> 2 <-> 3 <-> 4 <-> NULL
// Výstup: NULL <-> 4 <-> 3 <-> 2 <-> 1 <-> NULL
```

---

## DLL: Tabuľka časovej zložitosti

| Operácia     | DLL      | SLL (pre porovnanie) |
| ------------ | -------- | -------------------- |
| Append       | O(1)     | O(1)                 |
| Delete Last  | **O(1)** | O(n)                 |
| Prepend      | O(1)     | O(1)                 |
| Delete First | O(1)     | O(1)                 |
| Get          | O(n)     | O(n)                 |
| Set          | O(n)     | O(n)                 |
| Insert       | O(n)     | O(n)                 |
| Delete Node  | O(n)     | O(n)                 |

> **Hlavná výhoda DLL:** Delete Last je O(1) namiesto O(n)!

---

# Časť 2: Zásobníky a Fronty (Stacks & Queues)

## 2.1 Stack: Úvod (Zásobník)

### Teória

**Stack (zásobník)** je dátová štruktúra typu **LIFO** - Last In, First Out (posledný dnu, prvý von).

### Analógia z reálneho sveta:

- Stoh tanierov - pridávame a berieme z vrchu
- Tlačidlo "Späť" v prehliadači - posledná navštívená stránka
- Undo/Redo v textovom editore
- Volanie funkcií v programe (call stack)

### Základné operácie:

- **Push** - pridaj na vrch
- **Pop** - odstráň z vrchu
- **Top/Peek** - pozri na vrch bez odstránenia

### Vizualizácia:

```
        │       │
        │   4   │ ← TOP (sem pridávame, odtiaľ berieme)
        │   3   │
        │   2   │
        │   1   │ ← BOTTOM
        └───────┘

Push(5):            Pop():
        │       │           │       │
        │   5   │ ← NEW     │   4   │ ← TOP
        │   4   │           │   3   │
        │   3   │           │   2   │
        │   2   │           │   1   │
        │   1   │           └───────┘
        └───────┘
```

---

## 2.2 Stack: Constructor a Push

### Implementácia

```cpp
#include <iostream>
using namespace std;

class Node {
public:
    int value;
    Node* next;

    Node(int value) {
        this->value = value;
        this->next = nullptr;
    }
};

class Stack {
public:
    Node* top;
    int height;

    // CONSTRUCTOR
    Stack(int value) {
        Node* newNode = new Node(value);
        top = newNode;
        height = 1;
    }

    void printStack() {
        Node* temp = top;
        cout << "TOP" << endl;
        while (temp != nullptr) {
            cout << " │ " << temp->value << " │" << endl;
            temp = temp->next;
        }
        cout << "BOTTOM" << endl;
    }

    void push(int value) {
        Node* newNode = new Node(value);
        if (height == 0) {
            top = newNode;
        } else {
            newNode->next = top;    // Nový uzol ukazuje na starý top
            top = newNode;          // Top sa posunie na nový uzol
        }
        height++;
    }
};
```

---

## 2.3 Stack: Pop - na dopracovanie

```cpp
Node* pop() {
    // TODO: Dopracujte sami
    // 1. Ak je stack prázdny, vráťte nullptr
    // 2. Uložte top do temp
    // 3. Posuňte top na ďalší prvok
    // 4. Odpojte temp a vráťte ho
}
```

---

## ÚLOHA 3: Stack - Balanced Parentheses {#uloha-3-stack-balanced-parentheses}

**Zadanie:** Použi stack na kontrolu, či sú zátvorky v reťazci správne uzavreté.

```cpp
#include <iostream>
#include <string>
using namespace std;

// Použite Stack z predchádzajúcej implementácie

bool isBalanced(string str) {
    // TODO: Implementujte
    // 1. Pre každý znak v reťazci:
    //    - Ak je to '(', '[', '{' → push na stack
    //    - Ak je to ')', ']', '}' → pop a skontroluj či sa zhoduje
    // 2. Na konci musí byť stack prázdny

    // Hint: Môžete pushovať ASCII hodnoty alebo samotné znaky
}

int main() {
    cout << isBalanced("({[]})") << endl;   // 1 (true)
    cout << isBalanced("({[}])") << endl;   // 0 (false)
    cout << isBalanced("((()))") << endl;   // 1 (true)
    cout << isBalanced("(()") << endl;      // 0 (false)
    return 0;
}
```

---

## 2.4 Queue: Úvod (Fronta)

### Teória

**Queue (fronta)** je dátová štruktúra typu **FIFO** - First In, First Out (prvý dnu, prvý von).

### Analógia z reálneho sveta:

- Fronta v obchode - kto príde prvý, je obslúžený prvý
- Tlačiareň - dokumenty sa tlačia v poradí
- Playlist pesničiek

### Základné operácie:

- **Enqueue** - pridaj na koniec
- **Dequeue** - odstráň zo začiatku

### Vizualizácia:

```
Enqueue →   ┌───┬───┬───┬───┐   → Dequeue
            │ A │ B │ C │ D │
            └───┴───┴───┴───┘
              ↑             ↑
            first         last
```

---

## ÚLOHA 4: Queue - Implementácia {#uloha-4-queue-implementacia}

**Zadanie:** Dokončite implementáciu Queue a simulujte frontu v obchode.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Node {
public:
    string value;  // Meno zákazníka
    Node* next;

    Node(string value) {
        this->value = value;
        this->next = nullptr;
    }
};

class Queue {
public:
    Node* first;
    Node* last;
    int length;

    Queue() {
        first = nullptr;
        last = nullptr;
        length = 0;
    }

    void printQueue() {
        Node* temp = first;
        cout << "FRONTA: ";
        while (temp != nullptr) {
            cout << temp->value;
            if (temp->next != nullptr) cout << " → ";
            temp = temp->next;
        }
        cout << endl;
    }

    void enqueue(string value) {
        // TODO: Implementujte enqueue
        // Pridá zákazníka na koniec fronty
    }

    string dequeue() {
        // TODO: Implementujte dequeue
        // Obslúži prvého zákazníka (vráti jeho meno)
        // Ak je fronta prázdna, vráti "Nikto nečaká"
    }

    string peek() {
        // TODO: Implementujte peek
        // Vráti meno prvého zákazníka bez jeho odstránenia
    }
};

int main() {
    Queue* obchod = new Queue();

    obchod->enqueue("Peter");
    obchod->enqueue("Jana");
    obchod->enqueue("Miro");
    obchod->printQueue();  // FRONTA: Peter → Jana → Miro

    cout << "Obsluhujem: " << obchod->dequeue() << endl;  // Peter
    obchod->printQueue();  // FRONTA: Jana → Miro

    obchod->enqueue("Eva");
    cout << "Ďalší na rade: " << obchod->peek() << endl;  // Jana

    return 0;
}
```

---

## Stacks & Queues: Tabuľka časovej zložitosti

| Operácia     | Stack | Queue |
| ------------ | ----- | ----- |
| Push/Enqueue | O(1)  | O(1)  |
| Pop/Dequeue  | O(1)  | O(1)  |
| Peek         | O(1)  | O(1)  |
| isEmpty      | O(1)  | O(1)  |
| Search       | O(n)  | O(n)  |

---

# Časť 3: Stromy (Trees)

## 3.1 Trees: Úvod a Terminológia

### Teória

**Strom** je hierarchická dátová štruktúra. Kľúčová myšlienka:

> "Strom je linked list, kde každý uzol môže mať viacero `next` ukazovateľov."

### Terminológia:

- **Root (koreň)** - vrchný uzol, nemá rodiča
- **Node (uzol)** - základný prvok stromu
- **Edge (hrana)** - spojenie medzi uzlami
- **Parent (rodič)** - uzol s potomkami
- **Child (dieťa)** - uzol s rodičom
- **Leaf (list)** - uzol bez potomkov
- **Height (výška)** - najdlhšia cesta od koreňa k listu
- **Depth (hĺbka)** - vzdialenosť uzla od koreňa

### Vizualizácia:

```
                    ┌───┐
         Root ────► │ A │ ◄──── Depth 0
                    └─┬─┘
              ┌───────┼───────┐
              ▼       ▼       ▼
            ┌───┐   ┌───┐   ┌───┐
Depth 1 ──► │ B │   │ C │   │ D │
            └─┬─┘   └───┘   └─┬─┘
              │               │
        ┌─────┴─────┐   ┌─────┴─────┐
        ▼           ▼   ▼           ▼
      ┌───┐       ┌───┐┌───┐      ┌───┐
      │ E │       │ F ││ G │      │ H │ ◄── Leaves (listy)
      └───┘       └───┘└───┘      └───┘
```

---

## 3.2 Binary Search Tree (BST): Pravidlá

### Teória

**Binary Search Tree** je binárny strom s pravidlom:

- **Ľavý podstrom** obsahuje hodnoty **menšie** ako rodič
- **Pravý podstrom** obsahuje hodnoty **väčšie** ako rodič

### Príklad BST:

```
                    ┌────┐
                    │ 47 │
                    └────┘
                   /      \
             ┌────┐        ┌────┐
             │ 21 │        │ 76 │
             └────┘        └────┘
            /      \      /      \
       ┌────┐  ┌────┐ ┌────┐  ┌────┐
       │ 18 │  │ 27 │ │ 52 │  │ 82 │
       └────┘  └────┘ └────┘  └────┘
```

---

## 3.3 BST: Big O (Časová zložitosť)

| Operácia | Priemerný prípad | Najhorší prípad |
| -------- | ---------------- | --------------- |
| Insert   | O(log n)         | O(n)            |
| Contains | O(log n)         | O(n)            |
| Remove   | O(log n)         | O(n)            |

### Prečo O(log n)?

Pri každom kroku eliminujeme **polovicu** zostávajúcich uzlov.

### Kedy nastáva O(n)?

Keď je strom **degenerovaný** (vyzerá ako linked list).

---

## 3.4 BST: Constructor a Insert

### Implementácia

```cpp
#include <iostream>
using namespace std;

class Node {
public:
    int value;
    Node* left;
    Node* right;

    Node(int value) {
        this->value = value;
        this->left = nullptr;
        this->right = nullptr;
    }
};

class BinarySearchTree {
public:
    Node* root;

    BinarySearchTree() {
        root = nullptr;
    }

    bool insert(int value) {
        Node* newNode = new Node(value);

        // Prípad: Prázdny strom
        if (root == nullptr) {
            root = newNode;
            return true;
        }

        // Hľadanie správnej pozície
        Node* temp = root;
        while (true) {
            // Duplicitná hodnota - nevkladáme
            if (newNode->value == temp->value) {
                delete newNode;
                return false;
            }

            // Hodnota je menšia → choď doľava
            if (newNode->value < temp->value) {
                if (temp->left == nullptr) {
                    temp->left = newNode;
                    return true;
                }
                temp = temp->left;
            }
            // Hodnota je väčšia → choď doprava
            else {
                if (temp->right == nullptr) {
                    temp->right = newNode;
                    return true;
                }
                temp = temp->right;
            }
        }
    }
};
```

---

## ÚLOHA 5: BST - Kompletná implementácia {#uloha-5-bst-implementacia}

**Zadanie:** Dokončite BST implementáciu - dopracujte metódy `contains` a `minValue`.

```cpp
class BinarySearchTree {
public:
    Node* root;

    BinarySearchTree() {
        root = nullptr;
    }

    bool insert(int value) {
        // ... (implementácia vyššie)
    }

    bool contains(int value) {
        // TODO: Implementujte contains
        // 1. Začnite v koreni
        // 2. Ak hodnota < aktuálny uzol → choď doľava
        // 3. Ak hodnota > aktuálny uzol → choď doprava
        // 4. Ak hodnota == aktuálny uzol → vráť true
        // 5. Ak narazíš na nullptr → vráť false
    }

    int minValue(Node* currentNode) {
        // TODO: Implementujte minValue
        // Hint: Najmenšia hodnota je vždy úplne vľavo
    }

    int maxValue(Node* currentNode) {
        // TODO: Implementujte maxValue
        // Hint: Najväčšia hodnota je vždy úplne vpravo
    }
};

// Test:
int main() {
    BinarySearchTree* bst = new BinarySearchTree();
    bst->insert(47);
    bst->insert(21);
    bst->insert(76);
    bst->insert(18);
    bst->insert(27);
    bst->insert(52);
    bst->insert(82);

    cout << "Contains 27: " << bst->contains(27) << endl;  // 1 (true)
    cout << "Contains 17: " << bst->contains(17) << endl;  // 0 (false)
    cout << "Min: " << bst->minValue(bst->root) << endl;   // 18
    cout << "Max: " << bst->maxValue(bst->root) << endl;   // 82

    return 0;
}
```

---

## ÚLOHA 6: BST - Traversal metódy {#uloha-6-bst-traversal}

**Zadanie:** Implementujte tri základné prechody stromom.

```cpp
#include <iostream>
#include <vector>
using namespace std;

class BinarySearchTree {
    // ... predchádzajúca implementácia ...

    // In-Order: ľavý → root → pravý (výstup je zoradený!)
    void inOrder(Node* node, vector<int>& result) {
        // TODO: Implementujte rekurzívne
        // 1. Ak node nie je nullptr:
        //    a) Zavolaj inOrder pre ľavé dieťa
        //    b) Pridaj node->value do result
        //    c) Zavolaj inOrder pre pravé dieťa
    }

    // Pre-Order: root → ľavý → pravý
    void preOrder(Node* node, vector<int>& result) {
        // TODO: Implementujte rekurzívne
    }

    // Post-Order: ľavý → pravý → root
    void postOrder(Node* node, vector<int>& result) {
        // TODO: Implementujte rekurzívne
    }
};

// Test pre strom:
//        47
//       /  \
//      21   76
//     / \   / \
//    18 27 52 82

// Očakávané výstupy:
// In-Order:   18, 21, 27, 47, 52, 76, 82  (zoradené!)
// Pre-Order:  47, 21, 18, 27, 76, 52, 82
// Post-Order: 18, 27, 21, 52, 82, 76, 47
```

---

## BST: Tabuľka časovej zložitosti

| Operácia | Vyvážený BST | Nevyvážený BST |
| -------- | ------------ | -------------- |
| Insert   | O(log n)     | O(n)           |
| Contains | O(log n)     | O(n)           |
| Delete   | O(log n)     | O(n)           |
| Min/Max  | O(log n)     | O(n)           |

---

# Časť 4: Hash Tables (Hašovacie tabuľky)

## 4.1 Hash Table: Úvod

### Teória

**Hash Table** je dátová štruktúra, ktorá umožňuje **veľmi rýchly prístup** k dátam pomocou **kľúča**.

> "Hash table je ako super-rýchly slovník - zadáš kľúč, okamžite dostaneš hodnotu."

### Ako to funguje?

1. Máme **pole** (array) s fixnou veľkosťou
2. **Hash funkcia** transformuje kľúč na **index** v poli
3. Hodnota sa uloží na tento index

### Vizualizácia:

```
Kľúč: "meno"                    Index: 2
        │                          │
        ▼                          ▼
   ┌─────────┐                ┌─────────┐
   │ "meno"  │ ──► HASH() ──► │    2    │
   └─────────┘                └─────────┘

Array (Hash Table):
Index:  0       1       2       3       4       5       6
      ┌─────┬─────┬─────────┬─────┬─────┬─────┬─────┐
      │     │     │ "Peter" │     │     │     │     │
      └─────┴─────┴─────────┴─────┴─────┴─────┴─────┘
```

### Prečo Hash Table?

| Operácia            | Array | Linked List | Hash Table |
| ------------------- | ----- | ----------- | ---------- |
| Prístup podľa kľúča | O(n)  | O(n)        | **O(1)**   |
| Vloženie            | O(n)  | O(1)        | **O(1)**   |
| Vymazanie           | O(n)  | O(n)        | **O(1)**   |

---

## 4.2 HT: Collisions (Kolízie)

### Teória

**Kolízia** nastáva, keď dva rôzne kľúče majú rovnaký hash (index).

### Riešenia kolízií:

#### 1. Separate Chaining (Reťazenie)

Každý index obsahuje **linked list** všetkých prvkov s rovnakým hashom.

#### 2. Linear Probing (Lineárne sondovanie)

Ak je pozícia obsadená, hľadaj **nasledujúcu voľnú**.

---

## 4.3 - 4.6: Hash Table implementácia

### Základná štruktúra

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Node {
public:
    string key;
    int value;
    Node* next;

    Node(string key, int value) {
        this->key = key;
        this->value = value;
        this->next = nullptr;
    }
};

class HashTable {
private:
    static const int SIZE = 7;
    Node* dataMap[SIZE];

public:
    HashTable() {
        for (int i = 0; i < SIZE; i++) {
            dataMap[i] = nullptr;
        }
    }

    int hash(string key) {
        int hash = 0;
        for (int i = 0; i < key.length(); i++) {
            int asciiValue = (int)key[i];
            hash = (hash + asciiValue * 23) % SIZE;
        }
        return hash;
    }

    void printTable() {
        for (int i = 0; i < SIZE; i++) {
            cout << i << ":" << endl;
            Node* temp = dataMap[i];
            while (temp != nullptr) {
                cout << "   {" << temp->key << ", " << temp->value << "}" << endl;
                temp = temp->next;
            }
        }
    }
};
```

---

## ÚLOHA 7: Hash Table - Implementácia {#uloha-7-hash-table-implementacia}

**Zadanie:** Dokončite implementáciu Hash Table - dopracujte metódy `set`, `get` a `keys`.

```cpp
class HashTable {
    // ... predchádzajúca implementácia ...

    void set(string key, int value) {
        // TODO: Implementujte set
        // 1. Vypočítajte index pomocou hash()
        // 2. Vytvorte nový Node
        // 3. Ak je pozícia prázdna → vložte Node
        // 4. Ak nie je prázdna (kolízia) → pridajte na začiatok linked listu
    }

    int get(string key) {
        // TODO: Implementujte get
        // 1. Vypočítajte index pomocou hash()
        // 2. Prejdite linked list na danom indexe
        // 3. Nájdite uzol s hľadaným kľúčom
        // 4. Vráťte hodnotu (alebo 0 ak nenájdené)
    }

    vector<string> keys() {
        // TODO: Implementujte keys
        // 1. Vytvorte prázdny vector
        // 2. Prejdite všetky indexy
        // 3. Pre každý linked list pridajte všetky kľúče do vectora
        // 4. Vráťte vector
    }
};

// Test:
int main() {
    HashTable* ht = new HashTable();
    ht->set("nails", 100);
    ht->set("tile", 50);
    ht->set("lumber", 80);
    ht->set("bolts", 200);

    ht->printTable();

    cout << "lumber: " << ht->get("lumber") << endl;  // 80
    cout << "hammer: " << ht->get("hammer") << endl;  // 0

    vector<string> allKeys = ht->keys();
    cout << "Všetky kľúče:" << endl;
    for (string k : allKeys) {
        cout << "  " << k << endl;
    }

    return 0;
}
```

---

## ÚLOHA 8: Hash Table - Two Sum {#uloha-8-hash-table-two-sum}

**Zadanie:** Máš pole čísel a cieľový súčet. Nájdi dva indexy, ktorých hodnoty dávajú cieľový súčet.

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;

vector<int> twoSum(vector<int>& nums, int target) {
    // TODO: Implementujte pomocou hash mapy
    //
    // Brute force by bol O(n²) - skúsiť každú dvojicu
    // S hash mapou môžeme dosiahnuť O(n):
    //
    // 1. Pre každé číslo num na indexe i:
    //    a) Vypočítaj complement = target - num
    //    b) Ak complement existuje v mape → našli sme riešenie
    //    c) Inak pridaj num do mapy s indexom i
    //
    // Hint: unordered_map<int, int> mapa;  // hodnota → index
    // Hint: mapa.find(complement) != mapa.end()  // kontrola existencie

    return {};  // Vráťte {index1, index2}
}

int main() {
    vector<int> nums1 = {2, 7, 11, 15};
    vector<int> result1 = twoSum(nums1, 9);
    cout << "[" << result1[0] << ", " << result1[1] << "]" << endl;  // [0, 1]

    vector<int> nums2 = {3, 2, 4};
    vector<int> result2 = twoSum(nums2, 6);
    cout << "[" << result2[0] << ", " << result2[1] << "]" << endl;  // [1, 2]

    vector<int> nums3 = {3, 3};
    vector<int> result3 = twoSum(nums3, 6);
    cout << "[" << result3[0] << ", " << result3[1] << "]" << endl;  // [0, 1]

    return 0;
}
```

---

## HT: Tabuľka časovej zložitosti

| Operácia | Priemer | Najhorší prípad |
| -------- | ------- | --------------- |
| Hash     | O(k)\*  | O(k)            |
| Set      | O(1)    | O(n)            |
| Get      | O(1)    | O(n)            |
| Delete   | O(1)    | O(n)            |
| Keys     | O(n)    | O(n)            |

\*k = dĺžka kľúča

---

# Časť 5: Grafy (Graphs)

## 5.1 Graph: Úvod

### Teória

**Graf** je dátová štruktúra pozostávajúca z **vrcholov (vertices)** a **hrán (edges)**, ktoré ich spájajú.

> "Graf je ako mapa miest a ciest medzi nimi."

### Základná terminológia:

- **Vertex (vrchol)** - uzol v grafe
- **Edge (hrana)** - spojenie medzi dvoma vrcholmi
- **Weighted (vážený)** - hrany majú priradenú hodnotu (napr. vzdialenosť)
- **Directed (orientovaný)** - hrany majú smer (A → B neznamená B → A)
- **Undirected (neorientovaný)** - hrany sú obojsmerné

### Príklady použitia grafov:

- Sociálne siete (priatelia)
- Mapy a navigácia (Google Maps)
- Odporúčacie systémy (Netflix, Spotify)
- Počítačové siete

### Vizualizácia:

```
NEORIENTOVANÝ GRAF:              ORIENTOVANÝ GRAF:

    A ─────── B                      A ──────► B
    │ \       │                      │         │
    │   \     │                      ▼         ▼
    │     \   │                      C ◄────── D
    D ─────── C

VÁŽENÝ GRAF:

    A ───5─── B
    │ \       │
    2   3     4
    │     \   │
    D ───1─── C
```

---

## 5.2 Graph: Reprezentácie

### Adjacency Matrix (Matica susednosti)

2D pole kde `matrix[i][j] = 1` ak existuje hrana medzi vrcholom i a j.

```
Graf:                   Matica susednosti:
    A ─── B                   A  B  C  D
    │     │              A [  0  1  0  1 ]
    │     │              B [  1  0  1  0 ]
    D ─── C              C [  0  1  0  1 ]
                         D [  1  0  1  0 ]
```

**Výhody:**

- Rýchla kontrola existencie hrany: O(1)
- Jednoduchá implementácia

**Nevýhody:**

- Pamäťová náročnosť: O(V²) kde V = počet vrcholov
- Nevhodná pre riedke grafy (málo hrán)

### Adjacency List (Zoznam susednosti)

Každý vrchol má zoznam svojich susedov.

```
Graf:                   Zoznam susednosti:
    A ─── B             A: [B, D]
    │     │             B: [A, C]
    │     │             C: [B, D]
    D ─── C             D: [A, C]
```

**Výhody:**

- Pamäťovo efektívna: O(V + E) kde E = počet hrán
- Rýchle prechádzanie susedov

**Nevýhody:**

- Kontrola existencie hrany: O(V) v najhoršom prípade

---

## 5.3 Graph: Big O (Časová zložitosť)

| Operácia          | Adjacency Matrix | Adjacency List |
| ----------------- | ---------------- | -------------- |
| Pamäť             | O(V²)            | O(V + E)       |
| Pridanie vrcholu  | O(V²)            | O(1)           |
| Pridanie hrany    | O(1)             | O(1)           |
| Odstránenie hrany | O(1)             | O(E)           |
| Kontrola hrany    | O(1)             | O(V)           |
| Prechod susedov   | O(V)             | O(E/V)         |

> **Kedy použiť čo?**
>
> - **Adjacency Matrix** - husté grafy (veľa hrán), časté kontroly existencie hrán
> - **Adjacency List** - riedke grafy (málo hrán), prechádzanie grafom (BFS, DFS)

---

## 5.4 Graph: Implementácia s Adjacency List

### Základná štruktúra

```cpp
#include <iostream>
#include <unordered_map>
#include <unordered_set>
using namespace std;

class Graph {
public:
    // Každý vrchol má množinu susedov
    unordered_map<string, unordered_set<string>> adjList;

    void printGraph() {
        for (auto& [vertex, edges] : adjList) {
            cout << vertex << ": [ ";
            for (auto& edge : edges) {
                cout << edge << " ";
            }
            cout << "]" << endl;
        }
    }
};
```

### Vizualizácia štruktúry:

```
adjList = {
    "A": {"B", "C"},
    "B": {"A", "D"},
    "C": {"A", "D"},
    "D": {"B", "C"}
}
```

---

## 5.5 Graph: Add Vertex (Pridanie vrcholu)

### Teória

Pridanie nového vrcholu s prázdnym zoznamom susedov.

### Implementácia

```cpp
bool addVertex(string vertex) {
    // Ak vrchol už existuje, nevkladáme
    if (adjList.count(vertex) == 0) {
        adjList[vertex] = unordered_set<string>();
        return true;
    }
    return false;
}

// Použitie:
int main() {
    Graph* g = new Graph();
    g->addVertex("A");
    g->addVertex("B");
    g->addVertex("C");
    g->printGraph();
    // A: [ ]
    // B: [ ]
    // C: [ ]
    return 0;
}
```

**Časová zložitosť:** O(1)

---

## 5.6 Graph: Add Edge (Pridanie hrany)

### Teória

Pri neorientovanom grafe pridáme hranu obojsmerne - A→B aj B→A.

### Implementácia

```cpp
bool addEdge(string vertex1, string vertex2) {
    // Oba vrcholy musia existovať
    if (adjList.count(vertex1) != 0 && adjList.count(vertex2) != 0) {
        adjList[vertex1].insert(vertex2);  // A → B
        adjList[vertex2].insert(vertex1);  // B → A
        return true;
    }
    return false;
}

// Použitie:
int main() {
    Graph* g = new Graph();
    g->addVertex("A");
    g->addVertex("B");
    g->addVertex("C");
    g->addVertex("D");

    g->addEdge("A", "B");
    g->addEdge("A", "C");
    g->addEdge("B", "D");
    g->addEdge("C", "D");

    g->printGraph();
    // A: [ B C ]
    // B: [ A D ]
    // C: [ A D ]
    // D: [ B C ]
    return 0;
}
```

### Vizualizácia:

```
Po addEdge("A", "B"):

    A ─── B

    adjList:
    A: [B]
    B: [A]
```

**Časová zložitosť:** O(1)

---

## 5.7 Graph: Remove Edge (Odstránenie hrany)

### Teória

Odstránenie hrany z oboch zoznamov susednosti.

### Implementácia

```cpp
bool removeEdge(string vertex1, string vertex2) {
    if (adjList.count(vertex1) != 0 && adjList.count(vertex2) != 0) {
        adjList[vertex1].erase(vertex2);  // Odstráň B z A
        adjList[vertex2].erase(vertex1);  // Odstráň A z B
        return true;
    }
    return false;
}
```

**Časová zložitosť:** O(1) s unordered_set

---

## ÚLOHA 9: Graph - Implementácia {#uloha-9-graph-implementacia}

**Zadanie:** Dokončite implementáciu grafu - dopracujte metódu `removeVertex`.

```cpp
#include <iostream>
#include <unordered_map>
#include <unordered_set>
using namespace std;

class Graph {
public:
    unordered_map<string, unordered_set<string>> adjList;

    void printGraph() {
        for (auto& [vertex, edges] : adjList) {
            cout << vertex << ": [ ";
            for (auto& edge : edges) {
                cout << edge << " ";
            }
            cout << "]" << endl;
        }
    }

    bool addVertex(string vertex) {
        if (adjList.count(vertex) == 0) {
            adjList[vertex] = unordered_set<string>();
            return true;
        }
        return false;
    }

    bool addEdge(string vertex1, string vertex2) {
        if (adjList.count(vertex1) != 0 && adjList.count(vertex2) != 0) {
            adjList[vertex1].insert(vertex2);
            adjList[vertex2].insert(vertex1);
            return true;
        }
        return false;
    }

    bool removeEdge(string vertex1, string vertex2) {
        if (adjList.count(vertex1) != 0 && adjList.count(vertex2) != 0) {
            adjList[vertex1].erase(vertex2);
            adjList[vertex2].erase(vertex1);
            return true;
        }
        return false;
    }

    bool removeVertex(string vertex) {
        // TODO: Implementujte removeVertex
        // 1. Skontrolujte či vrchol existuje
        // 2. Pre každého suseda tohto vrcholu:
        //    - Odstráňte hranu (vertex, sused)
        // 3. Odstráňte vrchol z adjList
        //
        // Hint: Musíte odstrániť všetky hrany vedúce DO aj Z vrcholu
        // Hint: for (auto& edge : adjList[vertex]) { ... }
    }
};

// Test:
int main() {
    Graph* g = new Graph();
    g->addVertex("A");
    g->addVertex("B");
    g->addVertex("C");
    g->addVertex("D");

    g->addEdge("A", "B");
    g->addEdge("A", "C");
    g->addEdge("A", "D");
    g->addEdge("B", "D");
    g->addEdge("C", "D");

    cout << "Pred odstránením A:" << endl;
    g->printGraph();
    // A: [ B C D ]
    // B: [ A D ]
    // C: [ A D ]
    // D: [ A B C ]

    g->removeVertex("A");

    cout << "\nPo odstránení A:" << endl;
    g->printGraph();
    // B: [ D ]
    // C: [ D ]
    // D: [ B C ]

    return 0;
}
```

---

## ÚLOHA 10: Graph - BFS a DFS {#uloha-10-graph-bfs-dfs}

**Zadanie:** Implementujte prehľadávanie grafu do šírky (BFS) a do hĺbky (DFS).

```cpp
#include <iostream>
#include <unordered_map>
#include <unordered_set>
#include <queue>
#include <stack>
#include <vector>
using namespace std;

class Graph {
    // ... predchádzajúca implementácia ...

    // BFS - Breadth First Search (prehľadávanie do šírky)
    vector<string> BFS(string startVertex) {
        // TODO: Implementujte BFS
        // 1. Vytvorte frontu (queue) a množinu navštívených
        // 2. Pridajte štartovací vrchol do fronty a označte ako navštívený
        // 3. Kým fronta nie je prázdna:
        //    a) Vyberte prvok z fronty
        //    b) Pridajte ho do výsledku
        //    c) Pre každého nenavštíveného suseda:
        //       - Označte ako navštíveného
        //       - Pridajte do fronty
        //
        // Hint: queue<string> q;
        // Hint: unordered_set<string> visited;
    }

    // DFS - Depth First Search (prehľadávanie do hĺbky)
    vector<string> DFS(string startVertex) {
        // TODO: Implementujte DFS
        // Podobné ako BFS, ale použite STACK namiesto QUEUE
        //
        // Hint: stack<string> s;
    }
};

// Test pre graf:
//     A ─── B
//     │     │
//     │     │
//     C ─── D ─── E

// Očakávané výstupy (môžu sa líšiť podľa poradia susedov):
// BFS z A: A, B, C, D, E (po vrstvách)
// DFS z A: A, C, D, E, B (do hĺbky)
```

### Vizualizácia BFS vs DFS:

```
Graf:               BFS z A:              DFS z A:
    A ─── B         Vrstva 0: A           1. A
    │     │         Vrstva 1: B, C        2. B (alebo C)
    │     │         Vrstva 2: D           3. D
    C ─── D         Vrstva 3: E           4. E (alebo C)
          │                               5. C (alebo E)
          E
```

---

## Graph: Tabuľka časovej zložitosti

| Operácia      | Adjacency List |
| ------------- | -------------- |
| Add Vertex    | O(1)           |
| Add Edge      | O(1)           |
| Remove Edge   | O(1)\*         |
| Remove Vertex | O(V + E)       |
| BFS/DFS       | O(V + E)       |

\*S unordered_set

---

# Súhrnná tabuľka: Všetky dátové štruktúry

| Štruktúra             | Pridanie | Odstránenie  | Prístup  | Vyhľadávanie |
| --------------------- | -------- | ------------ | -------- | ------------ |
| **DLL**               | O(1)\*   | O(1)\*       | O(n)     | O(n)         |
| **Stack**             | O(1)     | O(1)         | O(n)     | O(n)         |
| **Queue**             | O(1)     | O(1)         | O(n)     | O(n)         |
| **BST (balanced)**    | O(log n) | O(log n)     | O(log n) | O(log n)     |
| **Hash Table**        | O(1)\*\* | O(1)\*\*     | O(1)\*\* | O(1)\*\*     |
| **Graph (Adj. List)** | O(1)     | O(V+E)\*\*\* | -        | O(V+E)       |

\*Na začiatok/koniec
**Priemerný prípad, najhorší je O(n) \***Odstránenie vrcholu

---

# Úlohy na odovzdanie - Súhrn

| #   | Názov úlohy                 | Popis                                                    | Odkaz                                                  |
| --- | --------------------------- | -------------------------------------------------------- | ------------------------------------------------------ |
| 1   | DLL: Základné metódy        | Dopracujte prepend, deleteFirst, set, insert, deleteNode | [Prejsť na úlohu](#uloha-1-dll-zakladne-metody)        |
| 2   | DLL: Reverse                | Implementujte metódu na obrátenie DLL                    | [Prejsť na úlohu](#uloha-2-dll-reverse)                |
| 3   | Stack: Balanced Parentheses | Kontrola správneho uzatvárania zátvoriek                 | [Prejsť na úlohu](#uloha-3-stack-balanced-parentheses) |
| 4   | Queue: Implementácia        | Dokončite Queue a simulujte frontu v obchode             | [Prejsť na úlohu](#uloha-4-queue-implementacia)        |
| 5   | BST: Implementácia          | Dopracujte contains, minValue, maxValue                  | [Prejsť na úlohu](#uloha-5-bst-implementacia)          |
| 6   | BST: Traversal              | Implementujte inOrder, preOrder, postOrder               | [Prejsť na úlohu](#uloha-6-bst-traversal)              |
| 7   | Hash Table: Implementácia   | Dopracujte set, get, keys                                | [Prejsť na úlohu](#uloha-7-hash-table-implementacia)   |
| 8   | Hash Table: Two Sum         | Optimalizovaný algoritmus s hash mapou                   | [Prejsť na úlohu](#uloha-8-hash-table-two-sum)         |
| 9   | Graph: Implementácia        | Dopracujte removeVertex                                  | [Prejsť na úlohu](#uloha-9-graph-implementacia)        |
| 10  | Graph: BFS a DFS            | Implementujte prehľadávanie grafu                        | [Prejsť na úlohu](#uloha-10-graph-bfs-dfs)             |

---

# Kontrolné otázky na sebahodnotenie

## DLL

- [ ] Viem vysvetliť rozdiel medzi SLL a DLL
- [ ] Viem implementovať všetky základné operácie
- [ ] Rozumiem prečo je delete z konca O(1) pri DLL a O(n) pri SLL

## Stack & Queue

- [ ] Viem vysvetliť LIFO a FIFO princíp
- [ ] Viem implementovať Stack a Queue pomocou linked list

## BST

- [ ] Viem vysvetliť BST pravidlo (ľavý < rodič < pravý)
- [ ] Viem implementovať insert a contains
- [ ] Rozumiem kedy je časová zložitosť O(log n) vs O(n)

## Hash Table

- [ ] Viem vysvetliť ako funguje hash funkcia
- [ ] Rozumiem čo je kolízia a ako ju riešiť
- [ ] Viem použiť hash table na optimalizáciu algoritmov

## Graph

- [ ] Viem vysvetliť rozdiel medzi Adjacency Matrix a Adjacency List
- [ ] Viem implementovať graf pomocou Adjacency List
- [ ] Rozumiem algoritmom BFS a DFS
- [ ] Viem kedy použiť BFS (najkratšia cesta) vs DFS (prehľadávanie všetkých ciest)

---

**Autor:** Tom. Muc.
