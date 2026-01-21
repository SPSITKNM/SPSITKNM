# Zadanie na komisionálnu skúšku - Algoritmy a dátové štruktúry

---

## ČASŤ A: Časová a priestorová zložitosť 

### A1: Analýza jednoduchého cyklu
**Zadanie:** 
Analyzujte časovú zložitosť nasledujúceho kódu:

```cpp
void printElements(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << endl;
    }
}
```

**Čo je tvoja úloha :**
- Určiť časovú zložitosť
- Vysvetliť prečo
- Nepovinné : Určiť priestorovú zložitosť

---

### A2: Analýza vnorených cyklov
**Zadanie:** 
Analyzujte časovú zložitosť nasledujúceho kódu:

```cpp
int mysteryFunction(int arr[], int n) {
    int count = 0;
    
    for (int i = 0; i < n; i++) {
        for (int j = i; j < n; j++) {
            count += arr[i] + arr[j];
        }
    }
    
    return count;
}
```

**Čo je tvoja úloha :**
- Určiť časovú zložitosť
- Vysvetliť, prečo má práve túto zložitosť
- Nepovinné : Porovnať s O(n) a O(n³)

---

### A3: Priestorová zložitosť
**Zadanie:**
Porovnajte priestorovú zložitosť týchto dvoch funkcií:

```cpp
// Funkcia 1
int sumIterative(int n) {
    int total = 0;
    for (int i = 1; i <= n; i++) {
        total += i;
    }
    return total;
}

// Funkcia 2
int sumRecursive(int n) {
    if (n == 0) {
        return 0;
    }
    return n + sumRecursive(n - 1);
}
```

**Čo je tvoja úloha :**
- Určiť priestorovú zložitosť oboch funkcií
- Vysvetliť rozdiel
- Uviesť, ktorá je lepšia a prečo

---

## ČASŤ B: Sortovacie algoritmy 

### B1: Bubble Sort implementácia
**Zadanie:**
Implementujte Bubble Sort algoritmus:

```cpp
void bubbleSort(int arr[], int n) {
    // Váš kód tu
}

// Test
int main() {
    int numbers[] = {64, 34, 25, 12, 22, 11, 90};
    int n = 7;
    
    bubbleSort(numbers, n);
    
    // Vypíše: 11 12 22 25 34 64 90
    for (int i = 0; i < n; i++) {
        cout << numbers[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Napísať funkčný Bubble Sort
- Vysvetliť princíp fungovania
- Uviesť časovú zložitosť 

---

### B2: Selection Sort implementácia
**Zadanie:**
Implementujte Selection Sort algoritmus:

```cpp
void selectionSort(int arr[], int n) {
    // Váš kód tu
    // Hint: Hľadáme minimum v nezoradené časti a dávame ho na začiatok
}

// Test
int main() {
    int numbers[] = {29, 10, 14, 37, 13};
    int n = 5;
    
    selectionSort(numbers, n);
    
    // Vypíše: 10 13 14 29 37
    for (int i = 0; i < n; i++) {
        cout << numbers[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať Selection Sort
- Vysvetliť rozdiel oproti Bubble Sort
- Uviesť časovú zložitosť

---

### B3: Je pole zoradené?
**Zadanie:**
Napíšte funkciu, ktorá zistí, či je pole zoradené vzostupne:

```cpp
bool isSorted(int arr[], int n) {
    // Váš kód tu
}

// Test
int main() {
    int arr1[] = {1, 2, 3, 4, 5};
    int arr2[] = {1, 3, 2, 4, 5};
    int arr3[] = {5, 4, 3, 2, 1};
    
    cout << isSorted(arr1, 5) << endl;  // 1 (true)
    cout << isSorted(arr2, 5) << endl;  // 0 (false)
    cout << isSorted(arr3, 5) << endl;  // 0 (false)
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať funkciu
- Určiť časovú zložitosť
- Vysvetliť logiku

---

### B4: Porovnanie algoritmov (teoretická)
**Zadanie:**
Máte k dispozícii tieto sortovacie algoritmy:
- Bubble Sort: O(n²)
- Selection Sort: O(n²)
- Merge Sort: O(n log n)
- Quick Sort: O(n log n) priemerne, O(n²) najhoršie

**Čo je tvoja úloha :**
- Vysvetliť, prečo sú niektoré rýchlejšie ako iné
- Kedy by ste použili jednoduchší O(n²) algoritmus?
- Poznáš ešte nejaký sortovací algoritmus?

---

## ČASŤ C: Linked List 

### C1: Vytvorenie linked listu
**Zadanie:**
Vytvorte jednoduchý linked list s tromi prvkami a vypíšte ho:

```cpp
struct Node {
    int data;
    Node* next;
    
    Node(int val) : data(val), next(nullptr) {}
};

class LinkedList {
private:
    Node* head;
    
public:
    LinkedList() : head(nullptr) {}
    
    void printList() {
        // Váš kód tu
    }
};

// Test - vytvorte list: 1 -> 2 -> 3 -> nullptr
int main() {
    LinkedList ll;
    // Váš kód tu - vytvorte 3 uzly a pospájajte ich
    
    ll.printList();  // Má vypísať: 1 -> 2 -> 3 -> nullptr
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Vytvoriť 3 uzly a pospájovať ich
- Implementovať printList metódu
- Vysvetliť štruktúru linked listu

---

### C2: Pridanie na koniec
**Zadanie:**
Implementujte metódu na pridanie prvku na koniec linked listu:

```cpp
class LinkedList {
private:
    Node* head;
    
public:
    LinkedList() : head(nullptr) {}
    
    void append(int data) {
        // Váš kód tu
    }
    
    void printList() {
        Node* current = head;
        while (current != nullptr) {
            cout << current->data << " -> ";
            current = current->next;
        }
        cout << "nullptr" << endl;
    }
};

// Test
int main() {
    LinkedList ll;
    ll.append(1);
    ll.append(2);
    ll.append(3);
    ll.printList();  // 1 -> 2 -> 3 -> nullptr
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať append metódu
- Vysvetliť časovú zložitosť
- Ako by sa dala zlepšiť? (hint: tail pointer)

---

### C3: Vloženie na pozíciu
**Zadanie:**
Implementujte metódu na vloženie prvku na konkrétnu pozíciu:

```cpp
class LinkedList {
    // ... predchádzajúce metódy ...
    
    void insertAtPosition(int data, int position) {
        // Váš kód tu
        // position 0 = na začiatok, position 1 = za prvý prvok, atď.
    }
};

// Test
int main() {
    LinkedList ll;
    ll.append(1);
    ll.append(2);
    ll.append(4);
    
    ll.insertAtPosition(3, 2);
    ll.printList();  // 1 -> 2 -> 3 -> 4 -> nullptr
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať metódu
- Vysvetliť kroky algoritmu
- Časová zložitosť?

---

### C4: Linked List vs Array
**Zadanie (teoretická otázka):**
Porovnajte linked list a pole (array):

**Čo je tvoja úloha :**
- Výhody linked listu
- Nevýhody linked listu
- Kedy použiť linked list vs. array?
- Časová zložitosť prístupu k n-tému prvku v oboch štruktúrach

---

## ČASŤ D: Základy OOP 

### D1: Jednoduchá trieda
**Zadanie:**
Vytvorte triedu `Book` s atribútmi a metódami:

```cpp
class Book {
private:
    string title;
    string author;
    int pages;
    
public:
    // Váš kód tu - konstruktor
    
    string getInfo() {
        // Vráti string: "Title by Author, Pages pages"
    }
    
    bool isLong() {
        // Vráti true ak má viac ako 300 strán
    }
};

// Test
int main() {
    Book book1("1984", "George Orwell", 328);
    cout << book1.getInfo() << endl;  // "1984 by George Orwell, 328 pages"
    cout << book1.isLong() << endl;   // 1 (true)
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať triedu
- Vysvetliť čo sú atribúty a metódy
- Vysvetliť konštruktor a modifikátory prístupu (private/public)

---

### D2: Trieda so zoznamom
**Zadanie:**
Vytvorte triedu `Library`, ktorá spravuje knihy:

```cpp
#include <vector>

class Library {
private:
    string name;
    vector<Book> books;
    
public:
    Library(string libraryName) : name(libraryName) {}
    
    void addBook(Book book) {
        // Pridá knihu do knižnice
    }
    
    int countBooks() {
        // Vráti počet kníh
    }
    
    Book findLongestBook() {
        // Nájde knihu s najväčším počtom strán
    }
};

// Test
int main() {
    Library lib("Mestská knižnica");
    lib.addBook(Book("1984", "George Orwell", 328));
    lib.addBook(Book("Hobbit", "J.R.R. Tolkien", 310));
    lib.addBook(Book("Harry Potter", "J.K. Rowling", 450));
    
    cout << lib.countBooks() << endl;  // 3
    Book longest = lib.findLongestBook();
    cout << longest.getInfo() << endl;  // "Harry Potter by J.K. Rowling, 450 pages"
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať triedu Library
- Vysvetliť vzťah medzi triedami Book a Library
- Nepovinné : Časová zložitosť findLongestBook?

---

### D3: Dedičnosť
**Zadanie:**
Vytvorte triedu `EBook`, ktorá dedí z `Book`:

```cpp
class EBook : public Book {
private:
    double fileSize;  // v MB
    
public:
    // Váš kód tu - konstruktor
    
    string getInfo() {
        // Rozšírte pôvodnú metódu o veľkosť súboru
        // "Title by Author, Pages pages, FileSize MB"
    }
};

// Test
int main() {
    EBook ebook("Digital Book", "Jane Doe", 250, 5.2);
    cout << ebook.getInfo() << endl;  
    // "Digital Book by Jane Doe, 250 pages, 5.2 MB"
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať EBook triedu
- Vysvetliť dedičnosť
- Nepovinné : Vysvetliť rozdiel medzi override a preťažením metódy

---

### D4: Študentská databáza
**Zadanie:**
Vytvorte systém na správu študentov:

```cpp
#include <vector>

class Student {
private:
    string name;
    string studentId;
    vector<int> grades;  // známky napr. {1, 2, 1, 1}
    
public:
    // Váš kód tu - konstruktor
    
    double getAverage() {
        // Vypočíta priemer známok
    }
    
    string toString() {
        // Vráti: "Name (ID): average"
    }
    
    string getName() { return name; }
};

class StudentDatabase {
private:
    vector<Student> students;
    
public:
    void addStudent(Student student) {
        // Pridá študenta
    }
    
    Student findBestStudent() {
        // Nájde študenta s najlepším priemerom
    }
    
    double getAverageOfAll() {
        // Vypočíta celkový priemer všetkých študentov
    }
};

// Test
int main() {
    StudentDatabase db;
    db.addStudent(Student("Ján", "001", {1, 2, 1, 1}));
    db.addStudent(Student("Mária", "002", {1, 1, 2, 1}));
    db.addStudent(Student("Peter", "003", {2, 3, 2, 2}));
    
    Student best = db.findBestStudent();
    cout << "Najlepší študent: " << best.toString() << endl;
    cout << "Celkový priemer: " << db.getAverageOfAll() << endl;
    
    return 0;
}
```

**Čo má študent urobiť:**
- Implementovať obe triedy
- Vysvetliť účel metódy toString()
- Nepovinné : Časová zložitosť findBestStudent?
- Nepovinné :  zložitosť getAverageOfAll?

---

## ČASŤ E: Vyhľadávacie algoritmy (2 úlohy)

### E1: Lineárne vyhľadávanie
**Zadanie:**
Implementujte lineárne vyhľadávanie v poli:

```cpp
int linearSearch(int arr[], int n, int target) {
    // Vráti index prvku alebo -1 ak sa nenašiel
}

// Test
int main() {
    int numbers[] = {5, 3, 7, 1, 9, 2};
    int n = 6;
    
    cout << linearSearch(numbers, n, 7) << endl;   // 2
    cout << linearSearch(numbers, n, 10) << endl;  // -1
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať funkciu
- Vysvetliť princíp
- Časová zložitosť (best, worst, average)

---

### E2: Binárne vyhľadávanie (bonus)
**Zadanie:**
Implementujte binárne vyhľadávanie v **zoradenom** poli:

```cpp
int binarySearch(int arr[], int n, int target) {
    // Pole MUSÍ byť zoradené!
    // Vráti index prvku alebo -1
}

// Test
int main() {
    int numbers[] = {1, 3, 5, 7, 9, 11, 13, 15};
    int n = 8;
    
    cout << binarySearch(numbers, n, 7) << endl;   // 3
    cout << binarySearch(numbers, n, 10) << endl;  // -1
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať funkciu (iteratívne alebo rekurzívne)
- Vysvetliť princíp "rozpolenia"
- Časová zložitosť
- Prečo musí byť pole zoradené?

---

## ČASŤ F: Doplňujúce úlohy (3 úlohy)

### F1: Reverz poľa
**Zadanie:**
Napíšte funkciu, ktorá otočí pole (reverse):

```cpp
void reverseArray(int arr[], int n) {
    // Váš kód tu
    // Môžete použiť pomocné pole alebo otočiť in-place
}

// Test
int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int n = 5;
    
    reverseArray(arr, n);
    
    // Vypíše: 5 4 3 2 1
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať funkciu
- Časová zložitosť?
- Priestorová zložitosť? (líši sa pre in-place vs. pomocné pole)

---

### F2: Reverz linked listu
**Zadanie:**
Napíšte funkciu, ktorá otočí linked list:

```cpp
Node* reverseLinkedList(Node* head) {
    // Váš kód tu
    // Vráti nový head
}

// Test - vytvorte list 1->2->3->nullptr a otočte ho na 3->2->1->nullptr
int main() {
    Node* head = new Node(1);
    head->next = new Node(2);
    head->next->next = new Node(3);
    
    head = reverseLinkedList(head);
    
    // Vypíše: 3 2 1
    Node* current = head;
    while (current != nullptr) {
        cout << current->data << " ";
        current = current->next;
    }
    cout << endl;
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať funkciu
- Vysvetliť kroky (preukazovanie pointerov)
- Časová a priestorová zložitosť

---

### F3: Duplicitné prvky
**Zadanie:**
Napíšte funkciu, ktorá odstráni duplicity z poľa:

```cpp
#include <vector>
#include <set>

vector<int> removeDuplicates(int arr[], int n) {
    // Vráti nový vector bez duplicít
    // Poradie prvkov nemusí byť zachované
}

// Test
int main() {
    int arr[] = {1, 2, 2, 3, 4, 4, 5};
    int n = 7;
    
    vector<int> result = removeDuplicates(arr, n);
    
    // Vypíše: 1 2 3 4 5 (poradie môže byť iné)
    for (int num : result) {
        cout << num << " ";
    }
    cout << endl;
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať funkciu
- Časová zložitosť?
- Nepovinné Diskusia: Aký je rozdiel medzi použitím set a manuálnym prechádzaním?

---

## BONUSOVÉ | pokiaľ si buduete chcieť precvičiť.

### Bonus 1: Detekcia cyklu v linked liste
**Zadanie:**
Napíšte funkciu, ktorá zistí, či linked list obsahuje cyklus:

```cpp
bool hasCycle(Node* head) {
    // Floyd's algorithm: slow a fast pointer
}

// Test
int main() {
    // Vytvorenie listu s cyklom: 1->2->3->4->2 (cyklus)
    Node* head = new Node(1);
    Node* second = new Node(2);
    Node* third = new Node(3);
    Node* fourth = new Node(4);
    
    head->next = second;
    second->next = third;
    third->next = fourth;
    fourth->next = second;  // vytvorí cyklus
    
    cout << hasCycle(head) << endl;  // 1 (true)
    
    return 0;
}
```

**Hint:** Použite dva pointery - jeden pomalý (1 krok) a jeden rýchly (2 kroky)

---

### Bonus 2: Fibonacci
**Zadanie:**
Implementujte Fibonacci čísla iteratívne a rekurzívne. Porovnajte časovú zložitosť:

```cpp
int fibonacciIterative(int n) {
    // Váš kód tu
}

int fibonacciRecursive(int n) {
    // Váš kód tu
}

// Test
int main() {
    int n = 10;
    
    cout << "Iterative: " << fibonacciIterative(n) << endl;  // 55
    cout << "Recursive: " << fibonacciRecursive(n) << endl;  // 55
    
    return 0;
}
```

**Čo je tvoja úloha :**
- Implementovať obe verzie
- Porovnať časovú zložitosť
- Ktorá je efektívnejšia a prečo?

---

## Rozdelenie bodov a hodnotenie

**ČASŤ A - Zložitosť (3 úlohy):** 15 bodov  
- A1: 3 body  
- A2: 7 bodov  
- A3: 5 bodov  

**ČASŤ B - Sortovacie algoritmy (4 úlohy):** 20 bodov  
- B1: 7 bodov  
- B2: 7 bodov  
- B3: 3 body  
- B4: 3 body  

**ČASŤ C - Linked List (4 úlohy):** 20 bodov  
- C1: 4 body  
- C2: 5 bodov  
- C3: 7 bodov  
- C4: 4 body  

**ČASŤ D - OOP (4 úlohy):** 25 bodov  
- D1: 5 bodov  
- D2: 7 bodov  
- D3: 5 bodov  
- D4: 8 bodov  

**ČASŤ E - Vyhľadávanie (2 úlohy):** 10 bodov  
- E1: 4 body  
- E2: 6 bodov (bonus)  

**ČASŤ F - Doplňujúce (3 úlohy):** 10 bodov  
- F1: 3 body  
- F2: 4 body  
- F3: 3 body  

**BONUSY:** +10 bodov max  

**Celkom:** 100 bodov + max 10 bonusových

---

Designed by : Tom. Muc. 
