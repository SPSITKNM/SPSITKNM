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

# Úloha 7: Zistenie dĺžky linkovaného zoznamu

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

# Úloha 8: Zistenie dĺžky linkovaného zoznamu

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

