# C++ OOP - Opravné úlohy
Dátové štruktúry (Linked Lists) + Triediace algoritmy

Pre študentov: Tieto úlohy sú navrhnuté tak, aby ste si precvičili OOP princípy, linked listy a sorting. Každá úloha má povinné minimum (75% bodov) a kreatívne rozšírenia (25% bodov + bonusy).

---

## Prehľad úloh

| Číslo | Názov | Téma | Body |
|-------|-------|------|------|
| 1 | Student Database | Doubly Linked List + Bubble Sort | 25 (+5) |
| 2 | Warehouse Manager | Singly Linked List + 3 Sorting Algorithms | 25 (+7) |
| 3 | Music Playlist | Circular Linked List + QuickSort | 25 (+8) |
| 4 | Task Manager | Linked List + Merge Sort | 25 (+7) |
| 5 | Mini Library | Linked List + Vlastný algoritmus | 25 (+10) |

---

# ÚLOHA 1: Student Database
Doubly Linked List + Bubble Sort

## Čo vytvoríš?

Systém na správu študentov ako malú databázu. Študenti budú v obojsmerne viazanom zozname (môžeš ísť dopredu aj dozadu).

### Ako to bude vyzerať?

```
╔-------------------------------------------------------╗
|           STUDENT DATABASE SYSTEM                     |
╠-------------------------------------------------------╣
|  Celkom študentov: 7                                  |
|  Priemerný GPA: 2.14                                  |
╚-------------------------------------------------------╝

ID    | Meno              | GPA   | Status
------|-------------------|-------|--------
1001  | Ján Novák         | 1.50  |  Excellent
1002  | Anna Kováčová     | 2.30  |  Good
1003  | Peter Horváth     | 3.20  | Average

[A]dd student | [D]elete | [S]ort | [F]ind | [Q]uit
```

### ČO presne máš SPRAVIŤ? (Krok za krokom)

```cpp
class Student {
private:
    int id;
    string firstName;
    string lastName;
    double gpa;  // priemerná známka (1.0 - 4.0)
    
public:
    // Konštruktor
    Student(int id, string first, string last, double gpa);
    
    // Gettery
    int getId() const;
    string getFullName() const;  // vráti "Ján Novák"
    double getGpa() const;
    
    // Užitočná metóda
    string getGrade() const {
        if (gpa <= 1.5) return " Excellent";
        if (gpa <= 2.5) return " Good";
        if (gpa <= 3.5) return "Average";
        return "Needs Improvement";
    }
    
    // Pre výpis
    friend ostream& operator<<(ostream& os, const Student& s);
};
```

#### KROK 2: Pochop Doubly Linked List (VIZUALIZÁCIA)
```
Normálny array:
+---+---+---+---+
| 1 | 2 | 3 | 4 |  Fixná veľkosť, ťažko sa vkladá/maže
+---+---+---+---+

Doubly Linked List:
     +---------+      +---------+      +---------+
NULL | Data: 1 |--| Data: 2 |--| Data: 3 | NULL
     | prev|next|      | prev|next|      | prev|next|
     +---------+      +---------+      +---------+
      ^head                                  ^tail

Výhody:
 Ľahko pridávať/mazať
 Môžeš ísť vpred AJ dozadu
 Dynamická veľkosť
```

```cpp
class Node {
public:
    Student data;      // Samotný študent
    Node prev;        // Ukazovateľ na predošlý uzol
    Node next;        // Ukazovateľ na ďalší uzol
    
    Node(Student s) : data(s), prev(nullptr), next(nullptr) {}
};
```


```cpp
class StudentList {
private:
    Node head;  // Prvý uzol
    Node tail;  // Posledný uzol
    int size;    // Počet študentov
    
public:
    StudentList() : head(nullptr), tail(nullptr), size(0) {}
    
    // === POVINNÉ METÓDY === (musíš implementovať)
    
    void insertAtEnd(Student s) {
        // TODO: Pridaj študenta na koniec
        // Hint: Vytvor nový Node, napoj ho na tail, aktualizuj tail
    }
    
    void insertAtBeginning(Student s) {
        // TODO: Pridaj študenta na začiatok
    }
    
    bool removeStudent(int id) {
        // TODO: Nájdi študenta podľa ID a vymaž ho
        // Hint: Musíš prepojit prev a next susedov
        // POZOR: Nezabudni delete!
    }
    
    Student findStudent(int id) {
        // TODO: Nájdi študenta podľa ID
        // Vráť pointer na Student alebo nullptr ak nenájdeš
    }
    
    void display() {
        // TODO: Vypíš všetkých študentov pekne naformátovaných
    }
    
    void sortByGpa() {
        // TODO: Zoraď študentov od najlepšieho (1.0) po najhoršieho
        // POUŽI BUBBLE SORT!
    }
    
    // Destruktor - DÔLEŽITÉ!
    ~StudentList() {
        // TODO: Prejdi celý zoznam a delete každý Node
    }
};
```


Princíp Bubble Sort:
```
Nezoradené: [3, 1, 4, 2]

Prechod 1:    [3, 1, 4, 2]  porovnaj 3 a 1
              [1, 3, 4, 2]  swap!
              [1, 3, 4, 2]  3 < 4, OK
              [1, 3, 2, 4]  swap! (4 > 2)

Prechod 2:    [1, 3, 2, 4]
              [1, 2, 3, 4]  swap!
              
Hotovo!       [1, 2, 3, 4]
```

Pre Linked List:
```cpp
void sortByGpa() {
    if (!head) return;  // Prázdny zoznam
    
    bool swapped;
    do {
        swapped = false;
        Node current = head;
        
        while (current->next != nullptr) {
            // Porovnaj GPA
            if (current->data.getGpa() > current->next->data.getGpa()) {
                // Swap DATA (nie ukazovateľov!)
                Student temp = current->data;
                current->data = current->next->data;
                current->next->data = temp;
                swapped = true;
            }
            current = current->next;
        }
    } while (swapped);
}
```

```cpp
int main() {
    StudentList database;
    
    // Pridaj študentov
    database.insertAtEnd(Student(1001, "Ján", "Novák", 1.5));
    database.insertAtEnd(Student(1002, "Anna", "Kováčová", 2.3));
    database.insertAtEnd(Student(1003, "Peter", "Horváth", 3.2));
    database.insertAtEnd(Student(1004, "Mária", "Tóthová", 1.8));
    database.insertAtEnd(Student(1005, "Lukáš", "Varga", 2.7));
    database.insertAtEnd(Student(1006, "Eva", "Molnárová", 1.2));
    database.insertAtEnd(Student(1007, "Tomáš", "Balog", 3.5));
    
    cout << "=== PRED ZORADENÍM ===" << endl;
    database.display();
    
    database.sortByGpa();
    
    cout << "\n=== PO ZORADENÍ ===" << endl;
    database.display();
    
    // Test mazania
    database.removeStudent(1003);
    cout << "\n=== PO VYMAZANÍ ID 1003 ===" << endl;
    database.display();
    
    return 0;
}
```

---

## HODNOTENIE (25 bodov)

Základná časť: 19 bodov (75%)
Kvalita kódu: 6 bodov (25%)


## KREATÍVNE ROZŠÍRENIA (+5 bodov navyše)

Vyber si čo chceš spraviť:

### Rozšírenia (+1-2 body každé)
- +1b Farebný výstup (použi ANSI kódy)
- +1b Počítanie štatistík (priemerné GPA, najlepší študent)
- +2b Uloženie/načítanie zo súboru (napr. `students.txt`)
- +1b Validácia vstupov (GPA musí byť 1.0-4.0)

### Rozšírenia (+2-3 body)
- +2b Interaktívne menu (ako v ukážke vyššie)
- +2b Vyhľadávanie podľa mena (nie len ID)
- +3b Export do CSV formátu

### Rozšírenia (+3-4 body)
- +3b Porovnanie Bubble Sort vs. iný algoritmus (napr. Selection Sort)
- +4b BONUS za kreativitu: Pridaj vlastnú užitočnú funkciu!
  - Napr.: filtrovanie študentov s GPA < 2.0
  - Napr.: histogram známok v ASCII arte
  - Napr.: export do HTML tabuľky
  - Čokoľvek čo ťa napadne a je užitočné!

---

## TIPY A ČASTÉ CHYBY

### Správny prístup
```cpp
// Pri mazaní uzla
Node toDelete = current;
current->prev->next = current->next;  // Prepoj susedov
current->next->prev = current->prev;
delete toDelete;  // Uvoľni pamäť
```

### ČASTÉ CHYBY
```cpp
// CHYBA 1: Zabudnutý delete
void removeStudent(int id) {
    // ... našiel som uzol
    // chýba: delete node;  MEMORY LEAK!
}

// CHYBA 2: Nekontroluje nullptr
void display() {
    Node current = head;
    while (current->next != nullptr) {  // Čo ak je head nullptr?
        // ...
    }
}

// CHYBA 3: Neaktualizuje tail pri mazaní
// Ak mažeš posledný uzol, musíš aktualizovať tail!
```


---

# ÚLOHA 3: Music Playlist Manager
Circular Linked List + QuickSort

## Čo vytvoríš?

Hudobný prehrávač s playlistom v kruhovom linked liste. Keď dôjdeš na koniec, automaticky pokračuješ od začiatku (ako na repeat v Spotify). Zoradíš piesne pomocou QuickSort.

### Ako to bude vyzerať?

```
+-------------------------------------------------------------+
|   MUSIC PLAYER - Chill Vibes Playlist                   |
+-------------------------------------------------------------+

   NOW PLAYING (3/10):
  ╔-----------------------------------------------------------╗
  |  "Bohemian Rhapsody" - Queen                              |
  |   5:55  |   (5.0)  |  Played: 47x                 |
  |  [#################### ] 75%                          |
  ╚-----------------------------------------------------------╝

   UP NEXT:
   4. Hotel California - Eagles [6:30] 
   5. Stairway to Heaven - Led Zeppelin [8:02] 

    [N]ext | [P]revious | [+]Skip 5 | [-]Back 3 | [S]ort | [Q]uit
```

### ČO presne máš SPRAVIŤ?


```cpp
class Song {
private:
    string title;
    string artist;
    int durationSeconds;  // napr. 355 = 5:55
    int rating;           // 1-5 hviezdičiek
    int playCount;        // koľkokrát prehratá
    
public:
    Song(string t, string a, int dur, int rat = 5);
    
    // Základné gettery
    string getTitle() const { return title; }
    string getArtist() const { return artist; }
    int getRating() const { return rating; }
    int getPlayCount() const { return playCount; }
    
    // Užitočné metódy
    string getDurationFormatted() const {
        int mins = durationSeconds / 60;
        int secs = durationSeconds % 60;
        char buffer[10];
        sprintf(buffer, "%d:%02d", mins, secs);
        return string(buffer);
    }
    
    // Popularity score = rating × log₁₀(playCount + 1)
    double getPopularityScore() const {
        return rating  log10(playCount + 1);
    }
    
    void incrementPlayCount() { playCount++; }
    
    // Pre výpis
    friend ostream& operator<<(ostream& os, const Song& s);
};
```

#### KROK 2: Pochop CIRCULAR Linked List

```
Normálny Linked List:
+-----+    +-----+    +-----+
| A   | -> | B   | -> | C   | -> NULL
+-----+    +-----+    +-----+
                         
                       Koniec!

Circular Linked List:
     +-----+    +-----+    +-----+
  +| A   | -> | B   | -> | C   | -+
  |  +-----+    +-----+    +-----+  |
  +----------------------------------+
  
   Nikdy nekončí
   Ideálne pre playlist na repeat
   Môžeš ísť dookola donekonečna
```


```cpp
class CircularPlaylist {
private:
    struct Node {
        Song data;
        Node next;
        Node(Song s) : data(s), next(nullptr) {}
    };
    
    Node current;  // Aktuálne prehrávaná pieseň
    int size;
    
public:
    CircularPlaylist() : current(nullptr), size(0) {}
    
    // === POVINNÉ METÓDY ===
    
    void addSong(Song s) {
        Node newNode = new Node(s);
        
        if (current == nullptr) {
            // Prvá pieseň
            current = newNode;
            current->next = current;  // Ukáže na seba!
        } else {
            // Nájdi posledný uzol
            Node last = current;
            while (last->next != current) {
                last = last->next;
            }
            
            // Pridaj nový uzol
            last->next = newNode;
            newNode->next = current;  // Uzavri kruh!
        }
        size++;
    }
    
    bool removeSong(string title) {
        // TODO: Vymaž pieseň podľa názvu
        // POZOR: Musíš zachovať kruh!
        // POZOR: Ak mažeš current, posuň ho na next
    }
    
    void playNext() {
        if (!current) return;
        
        current->data.incrementPlayCount();
        current = current->next;  // Posuň sa
        
        cout << " Playing: " << current->data.getTitle() << endl;
    }
    
    void skipForward(int n) {
        // TODO: Preskočí n piesní dopredu
        for (int i = 0; i < n && current; i++) {
            current = current->next;
        }
    }
    
    void skipBackward(int n) {
        // TODO: Preskočí n piesní dozadu
        // Hint: V kruhovom zozname môžeš ísť vpred až kým nedôjdeš "dozadu"
    }
    
    Song getCurrentSong() {
        return current ? &current->data : nullptr;
    }
    
    void display() {
        // TODO: Vypíš celý playlist
        // Hint: Prejdi kruh, ale zastav keď sa vrátiš na začiatok!
    }
    
    void sortByPopularity() {
        // TODO: Implementuj QuickSort!
        // Pozri nižšie...
    }
    
    ~CircularPlaylist() {
        // TODO: Prejdi kruh a delete všetky uzly
        // POZOR: Musíš prerušiť kruh aby si nešiel donekonečna!
    }
};
```


Princíp QuickSort:
```
Nezoradené: [3, 7, 1, 9, 2]

1. Vyber PIVOT (napr. posledný prvok = 2)
2. Rozdeľ na: menšie než pivot | pivot | väčšie než pivot
   
   [1] | [2] | [3, 7, 9]
                 
  menšie pivot   väčšie

3. Rekurzívne zoraď obe strany
   
   [1] | [2] | rekurzia([3, 7, 9])
                         
                    [3] | [7, 9]
                           
                      [7] | [9]

4. Hotovo: [1, 2, 3, 7, 9]
```

Pre Circular Linked List:
```cpp
void sortByPopularity() {
    if (size <= 1) return;
    
    // 1. Prerušíme kruh (dočasne)
    Node last = current;
    while (last->next != current) {
        last = last->next;
    }
    last->next = nullptr;
    
    // 2. Aplikujeme QuickSort
    current = quickSortRecursive(current);
    
    // 3. Uzavrieme kruh späť
    last = current;
    while (last->next != nullptr) {
        last = last->next;
    }
    last->next = current;
}

Node quickSortRecursive(Node head) {
    // Báza rekurzie
    if (!head || !head->next) return head;
    
    // Vyber pivot (napr. prvý prvok)
    Node pivot = head;
    Node less = nullptr;      // Menšie než pivot
    Node greater = nullptr;   // Väčšie než pivot
    
    // Rozdeľ zoznam
    Node current = head->next;
    while (current) {
        Node next = current->next;
        
        if (current->data.getPopularityScore() >= pivot->data.getPopularityScore()) {
            // Pridaj do "menšie" (väčšia popularita = lepšie)
            current->next = less;
            less = current;
        } else {
            // Pridaj do "väčšie"
            current->next = greater;
            greater = current;
        }
        
        current = next;
    }
    
    // Rekurzívne zoraď obe strany
    less = quickSortRecursive(less);
    greater = quickSortRecursive(greater);
    
    // Spoj: less + pivot + greater
    pivot->next = greater;
    
    if (!less) return pivot;
    
    // Pripoj pivot na koniec "less"
    Node temp = less;
    while (temp->next) {
        temp = temp->next;
    }
    temp->next = pivot;
    
    return less;
}
```


```cpp
double getAverageSongLength() {
    // TODO: Prejdi všetky piesne a vypočítaj priemer
}

Song getMostPlayedSong() {
    // TODO: Nájdi pieseň s najvyšším playCount
}

int getTotalPlaytime() {
    // TODO: Súčet dĺžok všetkých piesní (v sekundách)
}
```


```cpp
int main() {
    CircularPlaylist playlist;
    
    // Vytvor playlist
    playlist.addSong(Song("Bohemian Rhapsody", "Queen", 355, 5));
    playlist.addSong(Song("Stairway to Heaven", "Led Zeppelin", 482, 4));
    playlist.addSong(Song("Hotel California", "Eagles", 390, 5));
    playlist.addSong(Song("Imagine", "John Lennon", 183, 5));
    playlist.addSong(Song("Smells Like Teen Spirit", "Nirvana", 301, 4));
    playlist.addSong(Song("Yesterday", "The Beatles", 125, 5));
    playlist.addSong(Song("Purple Haze", "Jimi Hendrix", 170, 4));
    playlist.addSong(Song("Sweet Child O' Mine", "Guns N' Roses", 356, 5));
    playlist.addSong(Song("Billie Jean", "Michael Jackson", 294, 5));
    playlist.addSong(Song("November Rain", "Guns N' Roses", 537, 4));
    
    // Simuluj prehrávanie
    cout << "=== SIMULÁCIA PREHRÁVANIA ===" << endl;
    for (int i = 0; i < 20; i++) {
        playlist.playNext();
        // Občas preskočíme
        if (i % 5 == 0) {
            playlist.skipForward(2);
        }
    }
    
    cout << "\n=== PLAYLIST PRED ZORADENÍM ===" << endl;
    playlist.display();
    
    cout << "\n=== ZORAĎUJEM PODĽA POPULARITY... ===" << endl;
    playlist.sortByPopularity();
    
    cout << "\n=== PLAYLIST PO ZORADENÍ ===" << endl;
    playlist.display();
    
    cout << "\n=== ŠTATISTIKY ===" << endl;
    cout << "Priemerná dĺžka piesne: " 
         << playlist.getAverageSongLength() << " sekúnd" << endl;
    cout << "Najprehrávanejšia: " 
         << playlist.getMostPlayedSong()->getTitle() << endl;
    
    return 0;
}
```

---

## HODNOTENIE (25 bodov)

Základná časť: 19 bodov (75%)
Kvalita kódu: 6 bodov (25%)


## KREATÍVNE ROZŠÍRENIA (+8 bodov navyše)

### (+1-2b)
- +1b Progress bar pre aktuálnu pieseň
- +1b Emoji indikátor aktuálnej piesne ()
- +2b Uloženie/načítanie playlistu zo súboru

### (+2-3b)
- +2b Shuffle - náhodne zamiešaj playlist
- +2b História posledných 10 prehratých piesní
- +3b Filter piesní (zobraz len s rating 4+)

### (+3-4b)
- +3b Repeat modes: Repeat One, Repeat All, No Repeat
- +4b BONUS za kreativitu: Vlastná fičúra!
  - Napr.: generovanie playlistu podľa nálady
  - Napr.: odporúčania na základe počúvaných piesní
  - Napr.: lyrics displayer (môžeš dať lyrics ako string)
  - Čokoľvek originálne!

---

## TIPY PRE QUICKSORT


---

# ÚLOHA 5: Mini Library System
Vlastná voľba algoritmu + Kreativita

## Čo vytvoríš?

Systém knižnice s knihami. ŠPECIÁLNE: Môžeš si vybrať aký typ linked listu a aký sorting algoritmus použiješ! Táto úloha ťa nabáda k vlastným rozhodnutiam a kreatívnemu riešeniu.

### Možný výstup:

```
╔-------------------------------------------------------------╗
|                MINI LIBRARY SYSTEM                      |
╠-------------------------------------------------------------╣
|  Total Books: 15  |  Available: 12  |  Borrowed: 3         |
╚-------------------------------------------------------------╝

ID   | Title                          | Author           | Status
-----|--------------------------------|------------------|----------
001  | To Kill a Mockingbird         | Harper Lee       |  Available
002  | 1984                           | George Orwell    | ✗ Borrowed
003  | The Great Gatsby               | F. Scott F.      |  Available
...

Search by: [T]itle | [A]uthor | [G]enre | [S]ort | [Q]uit
```

### VOĽBA JE NA TEBE!

Na rozdiel od ostatných úloh, tu máš voľné pole pôsobnosti:

#### 1️⃣ Vyber si TYP Linked Listu:
- Singly Linked List - jednoduchší, ale stačí
- Doubly Linked List - môžeš ísť dozadu, o niečo náročnejšie
- Circular Linked List - cool, ale treba si rozmyslieť prečo

 Rada: Doubly je dobrá voľba - umožní ti implementovať "predošlá kniha" feature.

#### 2️⃣ Vyber si SORTING algoritmus:
Musíš implementovať ASPOŇ JEDEN, ale môžeš aj viac!

- Bubble Sort - najjednoduchší, ale pomalý
- Selection Sort - jednoduchý, rozumná rýchlosť
- Insertion Sort - dobrý pre malé množstvo kníh
- Merge Sort - náročnejší, ale efektívny
- Quick Sort - najrýchlejší, ale implementácia je trickier
- Vlastný algoritmus - vymysli si svoj! (dostaneš extra body)

 Rada: Ak chceš istotu, rob Insertion alebo Selection. Ak chceš výzvu, skús Merge.

---

## ČO presne máš SPRAVIŤ?


```cpp
class Book {
private:
    int id;
    string title;
    string author;
    string genre;  // napr. "Fiction", "Non-fiction", "Sci-Fi"
    int year;
    bool isBorrowed;
    
public:
    Book(int id, string title, string author, string genre, int year);
    
    // Základné gettery
    int getId() const;
    string getTitle() const;
    string getAuthor() const;
    string getGenre() const;
    int getYear() const;
    bool getIsBorrowed() const;
    
    // Akcie
    void borrowBook() { isBorrowed = true; }
    void returnBook() { isBorrowed = false; }
    
    // Helpers
    string getStatus() const {
        return isBorrowed ? "✗ Borrowed" : " Available";
    }
    
    friend ostream& operator<<(ostream& os, const Book& b);
};
```


Toto je na TEBE! Tu je kostra:

```cpp
class Library {
private:
    // TODO: Definuj svoj Node
    // struct Node { ... };
    
    // TODO: Potrebné premenné (head, tail, current, size, ...)
    
public:
    Library();
    
    // === POVINNÉ METÓDY ===
    
    void addBook(Book b) {
        // TODO: Implementuj podľa tvojho typu linked listu
    }
    
    bool removeBook(int id) {
        // TODO: Vymaž knihu podľa ID
    }
    
    Book findBookById(int id) {
        // TODO: Nájdi knihu
    }
    
    vector<Book> findBooksByAuthor(string author) {
        // TODO: Vráť všetky knihy daného autora
    }
    
    vector<Book> findBooksByGenre(string genre) {
        // TODO: Vráť všetky knihy daného žánru
    }
    
    void borrowBook(int id) {
        // TODO: Označ knihu ako požičanú
        Book book = findBookById(id);
        if (book && !book->getIsBorrowed()) {
            book->borrowBook();
            cout << " Kniha požičaná!" << endl;
        }
    }
    
    void returnBook(int id) {
        // TODO: Označ knihu ako vrátenú
    }
    
    void displayAll() {
        // TODO: Vypíš všetky knihy pekne naformátované
    }
    
    void displayAvailable() {
        // TODO: Vypíš len dostupné knihy
    }
    
    void sortBooks(string criterion) {
        // TODO: Implementuj tvoj zvolený sorting algoritmus!
        // criterion môže byť: "title", "author", "year"
    }
    
    // Štatistiky
    int getTotalBooks();
    int getAvailableBooks();
    int getBorrowedBooks();
    
    ~Library();
};
```


Tu je priestor pre tvoju kreativitu!

Vyber si algoritmus a implementuj ho. Tu je príklad s Selection Sort:

```cpp
void sortBooks(string criterion) {
    if (!head || !head->next) return;
    
    // Selection Sort
    Node i = head;
    while (i) {
        Node minNode = i;
        Node j = i->next;
        
        // Nájdi minimum v zvyšku zoznamu
        while (j) {
            bool shouldSwap = false;
            
            if (criterion == "title") {
                shouldSwap = (j->data.getTitle() < minNode->data.getTitle());
            } else if (criterion == "author") {
                shouldSwap = (j->data.getAuthor() < minNode->data.getAuthor());
            } else if (criterion == "year") {
                shouldSwap = (j->data.getYear() < minNode->data.getYear());
            }
            
            if (shouldSwap) {
                minNode = j;
            }
            
            j = j->next;
        }
        
        // Swap data
        if (minNode != i) {
            Book temp = i->data;
            i->data = minNode->data;
            minNode->data = temp;
        }
        
        i = i->next;
    }
}
```

Alebo môžeš implementovať Insertion Sort:

```cpp
void sortBooksInsertion(string criterion) {
    if (!head || !head->next) return;
    
    Node sorted = nullptr;
    Node current = head;
    
    while (current) {
        Node next = current->next;
        
        // Vlož current do sorted zoznamu
        if (!sorted || compareBooks(current->data, sorted->data, criterion) <= 0) {
            current->next = sorted;
            sorted = current;
        } else {
            Node search = sorted;
            while (search->next && compareBooks(search->next->data, current->data, criterion) < 0) {
                search = search->next;
            }
            current->next = search->next;
            search->next = current;
        }
        
        current = next;
    }
    
    head = sorted;
}

int compareBooks(const Book& a, const Book& b, string criterion) {
    if (criterion == "title") {
        return a.getTitle().compare(b.getTitle());
    } else if (criterion == "author") {
        return a.getAuthor().compare(b.getAuthor());
    } else {  // year
        return a.getYear() - b.getYear();
    }
}
```


```cpp
int main() {
    Library library;
    
    // Pridaj knihy
    library.addBook(Book(1, "To Kill a Mockingbird", "Harper Lee", "Fiction", 1960));
    library.addBook(Book(2, "1984", "George Orwell", "Dystopian", 1949));
    library.addBook(Book(3, "The Great Gatsby", "F. Scott Fitzgerald", "Fiction", 1925));
    library.addBook(Book(4, "Pride and Prejudice", "Jane Austen", "Romance", 1813));
    library.addBook(Book(5, "The Catcher in the Rye", "J.D. Salinger", "Fiction", 1951));
    library.addBook(Book(6, "Animal Farm", "George Orwell", "Satire", 1945));
    library.addBook(Book(7, "Brave New World", "Aldous Huxley", "Dystopian", 1932));
    library.addBook(Book(8, "The Hobbit", "J.R.R. Tolkien", "Fantasy", 1937));
    library.addBook(Book(9, "Harry Potter", "J.K. Rowling", "Fantasy", 1997));
    library.addBook(Book(10, "The Lord of the Rings", "J.R.R. Tolkien", "Fantasy", 1954));
    
    cout << "=== KNIŽNICA PRED ZORADENÍM ===" << endl;
    library.displayAll();
    
    // Požičaj nejaké knihy
    library.borrowBook(2);
    library.borrowBook(5);
    library.borrowBook(8);
    
    cout << "\n=== DOSTUPNÉ KNIHY ===" << endl;
    library.displayAvailable();
    
    // Zoraď
    cout << "\n=== ZORADENÉ PODĽA AUTORA ===" << endl;
    library.sortBooks("author");
    library.displayAll();
    
    cout << "\n=== ZORADENÉ PODĽA ROKU ===" << endl;
    library.sortBooks("year");
    library.displayAll();
    
    // Hľadanie
    cout << "\n=== KNIHY OD GEORGE ORWELL ===" << endl;
    vector<Book> orwellBooks = library.findBooksByAuthor("George Orwell");
    for (Book book : orwellBooks) {
        cout << book << endl;
    }
    
    // Štatistiky
    cout << "\n=== ŠTATISTIKY ===" << endl;
    cout << "Celkom kníh: " << library.getTotalBooks() << endl;
    cout << "Dostupné: " << library.getAvailableBooks() << endl;
    cout << "Požičané: " << library.getBorrowedBooks() << endl;
    
    return 0;
}
```

---

## HODNOTENIE (25 bodov)

Základná časť: 19 bodov (75%)
Kvalita kódu: 6 bodov (25%)


## KREATÍVNE ROZŠÍRENIA (+10 bodov)

Toto je úloha kde môžeš NAOZAJ VYNIKNÚŤ!

### Základné rozšírenia (+1-2b)
- +1b Uloženie/načítanie kníh zo súboru
- +2b Filtrovanie (iba fiction, iba dostupné, ...)
- +2b Export do CSV
- +1b Validácia vstupov

### Rozšírenia (+2-3b)
- +2b Interaktívne menu (ako príklad vyššie)
- +3b Dva sorting algoritmy a porovnanie rýchlosti
- +2b História požičaní (kto, kedy požičal)
- +3b Odporúčania - na základe žánru/autora

### VEĽKÉ body za kreativitu (+4-6b)
- +4b Vlastný sorting algoritmus
  - Vymysli a implementuj svoj vlastný algoritmus
  - Musíš zdôvodniť prečo je dobrý
  - Porovnaj ho s klasickým algoritmom
  
- +5b User system - viac používateľov, každý môže požičať max. 3 knihy
  
- +6b ÚPLNE VLASTNÁ FIČÚRA
  - Napr.: Reservation system (rezervácia knihy)
  - Napr.: Review system (hodnotenie kníh)
  - Napr.: Recommendation engine (AI odporúčania)
  - Napr.: Overdue tracking (upomienky na neskoré vrátenie)
  - Vymysli niečo originálne!

---



# VŠEOBECNÉ POKYNY PRE VŠETKY ÚLOHY

## Štruktúra projektu

```
moj_projekt/
+-- src/
|   +-- main.cpp
|   +-- Student.cpp       (alebo Song.cpp, Book.cpp, ...)
|   +-- StudentList.cpp   (alebo Playlist.cpp, Library.cpp, ...)
|   +-- ...
+-- include/
|   +-- Student.h
|   +-- StudentList.h
|   +-- ...
+-- Makefile              (alebo compile.sh)
+-- README.md             DÔLEŽITÉ!
+-- test_output.txt       (screenshot alebo text)
```

## Ako má vyzerať README.md?

```markdown
# [Názov úlohy] - [Tvoje meno]

## Popis
Stručne popiš čo program robí (2-3 vety).

## Kompilácia
```bash
make
# alebo
g++ -std=c++17 -o program src/.cpp
```

## Spustenie
```bash
./program
```

## Implementované funkcie
- [x] Všetky povinné metódy
- [x] Sorting algoritmus: [názov]
- [x] Správa pamäte
- [x] Bonus: [čo si spravil]

## Rozhodnutia (pre úlohu 5)
- Typ linked listu: ...
- Sorting algoritmus: ...
- Prečo: ...

## Testovacie výsledky
Priložené v `test_output.txt`

## Známe problémy / Obmedzenia
- [ak sú nejaké]
```

## ODOVZDANIE

### Čo odovzdať?
```
priezvisko_uloha_X.zip
+-- src/
|   +-- .cpp
+-- include/
|   +-- .h
+-- Makefile
+-- README.md
+-- test_output.txt (alebo screenshot)
```

### Pomenovanie
- Úloha 1: `priezvisko_uloha1.zip` (napr. `novak_uloha1.zip`)
- Úloha 2: `priezvisko_uloha2.zip`
- atď.

### Kde odovzdať?
[Edupage]

### Termín
[23:59 - 25.1]

---

### Designed by Tom. Muc. 
