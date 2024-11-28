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












