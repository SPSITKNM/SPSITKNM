# Úloha: Implementácia a manipulácia s jednoduchým linkovaným zoznamom

## Zadanie

Vytvorte triedu `LinkedList`, ktorá bude implementovať **jednoduchý linkovaný zoznam**. Tento zoznam bude obsahovať nasledujúce funkcie:

### 1. Vloženie na začiatok zoznamu
- Pridajte nový uzol na začiatok zoznamu.

### 2. Vloženie na koniec zoznamu
- Pridajte nový uzol na koniec zoznamu.

### 3. Zmazanie prvého uzla
- Zmažte prvý uzol v zozname.

### 4. Vyhľadanie hodnoty
- Skontrolujte, či zoznam obsahuje určitú hodnotu.

### 5. Výpis zoznamu
- Vytlačte všetky hodnoty v zozname.

## Struktúra triedy

### 1. Trieda `Node`
Trieda `Node` bude obsahovať:
- `value`: hodnota uzla (celé číslo).
- `next`: ukazovateľ na ďalší uzol v zozname.

```cpp
class Node {
public:
    int value;     // Hodnota uzla
    Node* next;    // Ukazovateľ na ďalší uzol

    Node(int val) : value(val), next(nullptr) {}
};
```

## 2. Trieda `LinkedList`

### Trieda LinkedList bude mať:

- Ukazovateľ na prvý uzol (head), ktorý bude inicializovaný na nullptr.

- Implementujte metódy pre pridávanie uzlov na začiatok aj na koniec, mazanie prvého uzla a vyhľadanie hodnoty.


```cpp
class LinkedList {
public:
    Node* head;  // Ukazovateľ na prvý uzol v zozname

    LinkedList() : head(nullptr) {}

    // Vloženie na začiatok zoznamu
    void insertAtBeginning(int value) {
        Node* newNode = new Node(value);
        newNode->next = head;
        head = newNode;
    }

    // Vloženie na koniec zoznamu
    void insertAtEnd(int value) {
        Node* newNode = new Node(value);
        if (!head) {
            head = newNode;
            return;
        }
        Node* temp = head;
        while (temp->next) {
            temp = temp->next;
        }
        temp->next = newNode;
    }

    // Zmazanie prvého uzla
    void deleteFirstNode() {
        if (head) {
            Node* temp = head;
            head = head->next;
            delete temp;
        }
    }

    // Vyhľadanie hodnoty v zozname
    bool search(int value) {
        Node* temp = head;
        while (temp) {
            if (temp->value == value) {
                return true;
            }
            temp = temp->next;
        }
        return false;
    }

    // Výpis zoznamu
    void printList() {
        Node* temp = head;
        while (temp) {
            cout << temp->value << " ";
            temp = temp->next;
        }
        cout << endl;
    }
};
```

## Testovanie

Vytvorte objekt `LinkedList` a použite implementované metódy na testovanie funkcií:

```cpp
int main() {
    LinkedList list;

    list.insertAtBeginning(10);
    list.insertAtBeginning(20);
    list.insertAtEnd(30);
    list.printList();  // Výstup: 20 10 30

    list.deleteFirstNode();
    list.printList();  // Výstup: 10 30

    cout << "Hodnota 10 v zozname: " << (list.search(10) ? "Nájdená" : "Nenájdená") << endl;
    cout << "Hodnota 50 v zozname: " << (list.search(50) ? "Nájdená" : "Nenájdená") << endl;

    return 0;
}
```

## Očakávaný výstup:

```yaml
Zoznam po vkladani: 5 10 20 
Vyhladanie 10: Nájdené
Zoznam po zmazani prveho uzla: 10 20
```

---

# Úloha 2: Zmena poradia uzlov v linkovanom zozname

## Zadanie:

Implementujte funkciu, ktorá otočí poradie uzlov v jednoduchom linkovanom zozname. Funkcia by mala upravit poradie uzlov tak, aby posledný uzol zoznamu sa stal prvým a prvý uzol posledným, pričom všetky ostatné uzly zmenia svoje pozície.

## Funkcie:

- `reverse()` : Funkcia, ktorá otočí poradie uzlov v zozname.
- Po otočení zoznamu vypíšte obsah zoznamu, aby ste skontrolovali správnosť.

## Ukážka : 

### Pred otočením zoznam:

```rust
1 -> 2 -> 3 -> 4 -> 5
```

```rust
5 -> 4 -> 3 -> 2 -> 1
```

---


# Úloha 3: Detekcia cyklu v linkovanom zozname

##Zadanie:

Implementujte funkciu, ktorá deteguje, či linkovaný zoznam obsahuje cyklus. Ak sa niektorý uzol odkazuje späť na nejaký predchádzajúci uzol (cyklus), funkcia by mala vrátiť true, inak false.

Tip: Použite metódu "pomalý a rýchly ukazovateľ" (Floydov cyklický algoritmus). Tento algoritmus používa dvoch ukazovateľov: jeden prechádza zoznam pomalšie (po jednom uzle), druhý rýchlejšie (po dvoch uzloch). Ak sa ukazovatele stretnú, znamená to, že zoznam obsahuje cyklus.

## Funkcie:

- `hasCycle()` : Funkcia, ktorá deteguje cyklus v zozname.
- Funkcia by mala vrátiť `true`, ak zoznam obsahuje cyklus, inak `false`.

## Ukážka:

### Príklad so zoznamom bez cyklu:

## Výstup: `false`

```rust
1 -> 2 -> 3 -> 4 -> 5 (konec)
```

## Výstup: `true`

Príklad so zoznamom s cyklom:

```rust

1 -> 2 -> 3 -> 4 -> 5 -> 2 (cyklus začína opäť na 2)

```

```cpp
### Dobrovoľný kod na test Vášho cyklu: 


#include <iostream>

using namespace std;

// Struktúra uzla v linkovanom zozname
struct Node {
    int data;
    Node* next;
    Node(int val) : data(val), next(nullptr) {}
};

class LinkedList {
public:
    Node* head;

    LinkedList() : head(nullptr) {}

    // Funkcia na pripojenie nového uzla na koniec zoznamu
    void append(int val) {
        Node* newNode = new Node(val);
        if (!head) {
            head = newNode;
        } else {
            Node* temp = head;
            while (temp->next) {
                temp = temp->next;
            }
            temp->next = newNode;
        }
    }

    // Funkcia na detekciu cyklu pomocou Floydovho algoritmu (pomalý a rýchly ukazovateľ)
    bool hasCycle() {
        if (!head) return false;  // Prázdny zoznam nemôže mať cyklus

        Node* slow = head;    // Pomalý ukazovateľ
        Node* fast = head;    // Rýchly ukazovateľ

        while (fast && fast->next) {
            slow = slow->next;            // Pomalý ukazovateľ posúva o 1 uzol
            fast = fast->next->next;      // Rýchly ukazovateľ posúva o 2 uzly

            if (slow == fast) {           // Ak sa stretnú, je tam cyklus
                return true;
            }
        }

        return false; // Ak rýchly ukazovateľ dosiahne koniec zoznamu, cyklus nie je
    }

    // Funkcia na vytvorenie cyklu v zozname (pre testovanie)
    void createCycle(int pos) {
        Node* temp = head;
        Node* cycleStartNode = nullptr;
        int count = 1;

        while (temp->next) {
            if (count == pos) {
                cycleStartNode = temp;
            }
            temp = temp->next;
            count++;
        }
        if (cycleStartNode) {
            temp->next = cycleStartNode; // Vytvorenie cyklu
        }
    }

    // Funkcia na vypísanie zoznamu (pomocná pre vizualizáciu)
    void printList() {
        Node* temp = head;
        while (temp) {
            cout << temp->data << " -> ";
            temp = temp->next;
        }
        cout << "nullptr" << endl;
    }
};

// Hlavná funkcia pre testovanie
int main() {
    LinkedList list;

    // Pridanie uzlov do zoznamu
    list.append(1);
    list.append(2);
    list.append(3);
    list.append(4);
    list.append(5);

    // Vytvorenie cyklu v zozname
    // Pre testovanie, cyklus sa vytvorí na pozícii 2 (t.j. uzol s hodnotou 2)
    list.createCycle(2);

    // Testujeme, či zoznam obsahuje cyklus
    if (list.hasCycle()) {
        cout << "Zoznam obsahuje cyklus!" << endl;
    } else {
        cout << "Zoznam neobsahuje cyklus." << endl;
    }

    return 0;
}

```

--- 

# Úloha 4: Spájanie dvoch zoradených linkovaných zoznamov

##Zadanie:

Máte dva zoradené linkované zoznamy, `list1` a `list2`, každý obsahuje celé čísla. Vašou úlohou je spojiť oba zoznamy do jedného zoradeného zoznamu.

- Vstup: Dva linkované zoznamy, každý zoradený v nerastúcom poradí.

- Výstup: Jeden nový linkovaný zoznam, ktorý bude obsahovať všetky prvky zo vstupných zoznamov v zoradenom poradí.

##Požiadavky:

- Použite iteratívnu metódu na spojenie zoznamov (vyhnite sa rekurzii).

- Po skončení operácie by mal byť výsledný zoznam správne zoradený bez potreby znovu zoradovať.

## Príklad:

## Vstupy:

- `list1: 1 -> 3 -> 5 -> 7`
- `list2: 2 -> 4 -> 6 -> 8`

## Výstup:

- `1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8`

## Tip: 

Môžete začať iterovať cez oba zoznamy, porovnávať hodnoty a pripojiť menšiu hodnotu k výslednému zoznamu. Keď jeden zo zoznamov skončí, pridajte zostávajúce uzly z druhého zoznamu.

--- 

# Úloha 5: Detekcia a odstránenie cyklu v linkovanom zozname

## Zadanie:

Implementujte funkciu, ktorá najprv deteguje cyklus v linkovanom zozname a následne odstráni cyklus, ak existuje.

Detekcia cyklu: Ak je v zozname cyklus (t. j. nejaký uzol odkazuje späť na predchádzajúci uzol), detegujte ho. Použite Floydov algoritmus s dvoma ukazovateľmi: pomalý (ktorý prejde jeden uzol) a rýchly (ktorý prejde dva uzly).

Odstránenie cyklu: Ak cyklus existuje, funkcia musí odstrániť cyklus. To znamená, že nájdete uzol, ktorý tvorí cyklus, a nastavíte jeho `next` ukazovateľ na `nullptr`.


##Požiadavky:

- Detekcia cyklu pomocou dvoch ukazovateľov.

- Po zistení cyklu odstráňte spojenie, ktoré cyklus vytvára.
  
- Funkcia by mala mať časovú zložitosť O(n), kde n je počet uzlov v zozname.
  

## Príklad:

### Vstup: Zoznam obsahuje cyklus:

```rust
1 -> 2 -> 3 -> 4 -> 5 -> 6
                ^---------|

```

### Výstup: Po odstránení cyklu:

```rust
1 -> 2 -> 3 -> 4 -> 5 -> 6

```

## Tipy:

- Použite Floydov algoritmus pre detekciu cyklu.

- Po detekcii cyklu, nájdite uzol, ktorý odkazuje späť na predchádzajúci uzol, a nastavte jeho `next` na `nullptr` pre odstránenie cyklu.

--- 

# Úloha 6: Zistenie dĺžky linkovaného zoznamu

## Zadanie:

Vytvorte funkciu, ktorá vypočíta dĺžku jednoduchého linkovaného zoznamu. Funkcia by mala prejsť celý zoznam a spočítať počet uzlov v zozname.

##Požiadavky:

- Implementujte funkciu `getLength()`, ktorá vráti počet uzlov v zozname.

## Čiastkový kód:


```cpp
class LinkedList {
public:
    Node* head;

    LinkedList() : head(nullptr) {}

    // Funkcia pre zistenie dĺžky zoznamu
    int getLength() {
        int length = 0;
        Node* temp = head;
        while (temp) {
            length++;
            temp = temp->next;
        }
        return length;
    }
};

```

Tip:

- Prechádzajte zoznam a počítajte uzly jeden po druhom až do konca zoznamu, kým sa temp nestane `nullptr`.

--- 

# Úloha 7: Zlúčenie dvoch zoradených zoznamov

## Zadanie:

Vytvorte funkciu, ktorá odstráni prvý uzol v linkovanom zozname, ktorý obsahuje konkrétnu hodnotu.

##Požiadavky:

- Implementujte funkciu `deleteNode(int value)`, ktorá vyhľadá hodnotu v zozname a odstráni prvý uzol, ktorý obsahuje túto hodnotu.

## Čiastkový kód 
  
```cpp
class LinkedList {
public:
    Node* head;

    LinkedList() : head(nullptr) {}

    // Funkcia na odstránenie uzla podľa hodnoty
    void deleteNode(int value) {
        Node* temp = head;
        if (temp && temp->value == value) {
            head = temp->next;
            delete temp;
            return;
        }
        while (temp && temp->next) {
            if (temp->next->value == value) {
                Node* toDelete = temp->next;
                temp->next = temp->next->next;
                delete toDelete;
                return;
            }
            temp = temp->next;
        }
    }
};

```

Tip:

- Ak je prvý uzol ten, ktorý chceme odstrániť, je potrebné zmeniť `head` zoznamu.
- Ak ho nájdeme na inej pozícii, upravíme ukazovateľ na `next` predchádzajúceho uzla.

---

# Úloha 8: Detekcia cyklu v linkovanom zozname

## Zadanie:


Máte dva zoradené linkované zoznamy. Vytvorte funkciu, ktorá spojí oba zoznamy do jedného zoradeného zoznamu.


##Požiadavky:


- Použite iteratívnu metódu.
- Nezotriedte zoznam po spojení, ale priamo ho vytvorte v zoradenom poradí.
  

## Čiastkový kód  

```cpp
class LinkedList {
public:
    Node* head;

    LinkedList() : head(nullptr) {}

    // Funkcia na zlúčenie dvoch zoradených zoznamov
    Node* mergeSortedLists(Node* list1, Node* list2) {
        Node* dummy = new Node(0);
        Node* tail = dummy;

        while (list1 && list2) {
            if (list1->value < list2->value) {
                tail->next = list1;
                list1 = list1->next;
            } else {
                tail->next = list2;
                list2 = list2->next;
            }
            tail = tail->next;
        }

        if (list1) {
            tail->next = list1;
        } else {
            tail->next = list2;
        }

        return dummy->next;
    }
};

```

Tip:

- Použite pomocný uzol `dummy`, aby ste uľahčili prácu s začiatkom zoznamu.
- Po skončení jedného zo zoznamov pripojte zvyšok druhého zoznamu k výsledku.

---

# Úloha 9: Zlúčenie a zoradenie k-násobného zoznamu


## Zadanie:


Máte k zoradených linkovaných zoznamov. Vytvorte funkciu, ktorá všetky tieto zoznamy zlúči do jedného zoradeného zoznamu.


- Implementujte funkciu `mergeKSortedLists()`, ktorá zlúči k zoradených zoznamov do jedného.
- Použite min-heap (prioritný front) na optimalizáciu výkonu.


### Tip: 


- Pre každú hodnotu z každého zoznamu môžete použiť priority queue (min-heap), aby ste udržali najmenší prvok na vrchole a efektívne ho pridali do výsledného zoznamu.
- Použitie priority queue (min-heap) umožňuje efektívne získať najmenší uzol zo všetkých zoznamov.
- Po spracovaní uzla, ak existuje ďalší uzol v zozname, pridajte ho do fronty.
- 

## Čiastkový kód  


```cpp
#include <queue>
#include <vector>

class LinkedList {
public:
    Node* head;

    LinkedList() : head(nullptr) {}

    // Funkcia na zlúčenie k zoradených zoznamov
    Node* mergeKSortedLists(std::vector<Node*>& lists) {
        auto cmp = [](Node* a, Node* b) { return a->value > b->value; };
        std::priority_queue<Node*, std::vector<Node*>, decltype(cmp)> pq(cmp);

        for (Node* list : lists) {
            if (list) {
                pq.push(list);
            }
        }

        Node* dummy = new Node(0);
        Node* tail = dummy;

        while (!pq.empty()) {
            Node* minNode = pq.top();
            pq.pop();
            tail->next = minNode;
            tail = tail->next;

            if (minNode->next) {
                pq.push(minNode->next);
            }
        }

        return dummy->next;
    }
};


```


# Úloha pre 6.12.2024 : Nájdi všetky podmnožiny, ktoré dávajú požadovaný súčet

## Popis úlohy

Tvojou úlohou je napísať program, ktorý pre danú množinu kladných celých čísel a cieľový súčet nájde všetky podmnožiny, ktorých prvky dávajú práve tento súčet. Podrobnejšie informácie nájdeš v knihe od Levittina, alebo v iných príbuzných materiáloch.

Program bude postupovať nasledovne:

1. **Načíta množinu čísel zo súboru.**
2. **Nájde všetky podmnožiny, ktoré dávajú požadovaný súčet.**
3. **Vypíše počet podmnožín, ktoré dávajú požadovaný súčet, na štandardný výstup.**

Úloha je navrhnutá na vyskúšanie rekurzívneho hľadania podmnožín. Použijete algoritmus založený na prechádzaní stromu možností (backtracking):
- Pre každý prvok rozhodnite, či bude zahrnutý do podmnožiny, alebo nie.
- Sledujte aktuálny súčet podmnožiny, aby ste zastavili zbytočné vetvy (ak súčet presiahne cieľový súčet).
- Ak nájdete nejaký iný pekný algoritmus na riešenie tejto úlohy, môžete ho pridať tiež.

## Formát vstupu

- Súbor obsahuje sekvenciu kladných celých čísel, v jednom riadku, oddelených medzerami.
- Na príkazovej riadke bude program spustený v formáte: `./main nazov_souboru.txt suma`

## Testy

Pre vstupné dáta:

```cpp
2 3 5 7
```

a cieľovú sumu **10** by nemalo byť ťažké si rozmyslieť, že výstup bude **2**.

Pre cieľ **50** program s týmito dátami vráti **0**.






