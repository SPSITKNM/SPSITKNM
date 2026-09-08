# Algoritmizácia a dátové štruktúry

Skriptá k analýze zložitosti (Big O) a k základným dátovým štruktúram —
spojkový zoznam, obojsmerný spojkový zoznam, zásobník a fronta — s implementáciou
v C++. Kódové ukážky sú tak, ako sme ich písali na hodine; niektoré obsahujú
zámerné chyby, na ktorých sme si ukazovali ladenie.

---

## Big O notácia

### Čo to je

Big O je spôsob, ako porovnať dva kusy kódu, ktoré robia to isté. Ak sú funkčne
totožné, potrebujeme kritérium, ktorým ich porovnáme voči sebe — jeden môže byť
čitateľnejší, ale nás zaujíma, **ako efektívne bežia**.

Keby sme merali stopkami, jeden kód by trval napríklad 15 sekúnd a druhý celú
minútu. Tomu hovoríme **časová zložitosť (time complexity)**. Vtip je v tom, že
sa nemeria v sekundách: keby sme ten istý kód spustili na dvakrát rýchlejšom
počítači, čas sa zmení, ale zložitosť nie. Big O opisuje, ako rastie počet
operácií v závislosti od veľkosti vstupu.

### Najhorší, priemerný a najlepší prípad

- **Ω (omega)** — najlepší prípad
- **Θ (theta)** — priemerný prípad
- **O** — najhorší prípad

Príklad: máme pole o 7 prvkoch a sledujeme počet iterácií pri hľadaní.

- najlepší prípad: hľadané číslo je hneď prvé
- najhorší prípad: hľadané číslo je posledné (7.)
- priemerný prípad: číslo je niekde uprostred (4.)

> **Pozor — na skúške:** keď niekto povie „average / worst / best case Big O",
> nie je to celkom presné. Technicky Big O je vždy **najhorší prípad**.

### O(n) — lineárny čas

```cpp
void printItems(int n) {  // void funkcia preberajúca ako parameter n
  for (size_t i{0}; i < n; i++)  // for loop, ktorý beží n-krát
    cout << i << endl;
}
```

Ak `n = 10`, funkcia vypíše 0 – 9. Hovoríme, že je **O(n)** — počet operácií
rastie priamo úmerne so vstupom.

Na grafe: os x je veľkosť vstupu `n`, os y je počet operácií. O(n) je vždy
priamka (proporcionálny rast).

### Pravidlo 1: zahoď konštanty (drop constants)

```cpp
void printItems2(int n) {
  for (size_t i{0}; i < n; i++)
    cout << i << endl;

  for (size_t j{0}; j < n; j++)
    cout << j << endl;
}
```

Dva samostatné for-loopy, každý beží `n`-krát → `n + n = 2n`. Napísali by sme
teda O(2n), ale konštantu **zahodíme** a dostaneme O(n).

Prečo? Chceme širokú kategóriu, do ktorej rýchlosť rastu padá. Aj `100n` rastie
lineárne — čo je úplne iná trieda než niečo, čo rastie exponenciálne.

**Prvé pravidlo zjednodušovania: drop constants.**

### O(n²) — kvadratický čas

```cpp
void printItemsOnaDruhu(int n) {  // jeden for loop vnorený do druhého
  for (size_t i{0}; i < n; i++) {
    for (int j = 0; j < n; j++) {
      cout << i << j << endl;
    }
  }
}
```

Vnorené for-loopy bežia `n * n`-krát → výsledkom je **O(n²)**. Na grafe rastie
oveľa rýchlejšie než O(n), je teda menej efektívne. Keď dostaneme na výber,
oveľa lepšia voľba je O(n).

### Pravidlo 2: zahoď nedominantné členy (drop non-dominants)

Ak máme vnorený for-loop a za ním samostatný for-loop, výsledok je O(n² + n).
Pýtame sa, ktorý člen je **dominantný** → `n²`. Člen `n` je nedominantný.

Keby `n = 100`, tak `n²` je 10 000 a `n` je zanedbateľné. Preto zjednodušujeme
zahodením `n` a ponecháme len `n²`.

### O(1) — konštantný čas

```cpp
int addItem(int n) {
  return n + n;
  return n + n + n;  // aj keby tu boli 2 operácie (O(2)), stále to voláme O(1)
}
```

Počet operácií sa nemení podľa veľkosti vstupu. Či je `n` rovné 1 alebo milión,
máme stále jednu operáciu (sčítanie). Výsledkom je **O(1)** — najefektívnejšia
trieda. Na grafe je to vodorovná priamka.

### O(log n) — logaritmický čas

Na demonštráciu vezmeme utriedené pole a hľadáme v ňom číslo najefektívnejším
spôsobom: zoznam rozdelíme na polovice a pýtame sa, či je číslo v prvej alebo
druhej polovici. To opakujeme, kým číslo nenájdeme.

Ak sme na nájdenie potrebovali 3 kroky, tak `2³ = 8`, čo je to isté ako
`log₂(8) = 3`. `log₂(8)` sa pýta: koľkokrát musím vydeliť 8 dvojkou, aby som
sa dostal na jednotku? Trikrát.

Skutočná sila je pri veľkých číslach: `log₂(miliarda)` ≈ 31 — na nájdenie
ľubovoľného prvku v miliarde utriedených prvkov stačí ~31 rozpolení.

Na grafe je O(log n) veľmi plochá, takmer ako O(1). Je oveľa efektívnejšia než
O(n²) aj O(n).

### O(n log n)

Ešte jedna trieda, ktorú využívajú niektoré triediace algoritmy — napr.
**merge sort** alebo **quick sort**. Na grafe leží medzi O(n) a O(n²). Je to
najefektívnejšie, ako sa dá spraviť všeobecné triedenie.

### Rôzne premenné pre rôzne vstupy

Keď funkcia preberá dva parametre namiesto jedného:

```cpp
void suka(int a, int b) {
  for (size_t i{0}; i < a; i++)
    cout << i << endl;

  for (int j{0}; j < b; j++)
    cout << j << endl;
}
```

Prvý for-loop beží `a`-krát, druhý `b`-krát. Chyba, ktorú ľudia robia, je, že
dajú do jedného vreca a povedia O(n). Správne je **O(a) + O(b)**, čo
zjednodušíme na **O(a + b)**.

Podobne vnorený for-loop s dvoma premennými je **O(a · b)**. Rôzne premenné pre
rôzne vstupy musíme ukázať samostatne.

### Big O pre vektory a polia

Vektor vyzerá napríklad `[11, 3, 23, 7]` — na indexe 0 je 11 atď.

```cpp
int main(int args, char *argv[]) {
  // n je počet prvkov v poli / vektore

  std::vector<int> myVector = {11, 3, 23, 7};
  myVector.push_back(12);
  myVector.pop_back();               // odstráni posledný prvok
  myVector.erase(myVector.begin());  // parameter myVector.begin() = začiatok
  myVector.insert(myVector.begin(), 11);
  myVector.insert(myVector.begin() + 1, 69);

  for (int var : myVector)
    cout << var << endl;
}
```

- **Pridanie / odstránenie na konci:** nemusíme sa dotknúť žiadneho iného prvku
  → **O(1)**.
- **Pridanie / odstránenie na začiatku alebo v strede:** musíme prereindexovať
  všetky nasledujúce prvky → **O(n)**. Aj keby to bolo `½n`, konštantu
  zahodíme.
- **Vyhľadanie podľa hodnoty:** musíme prejsť prvky → **O(n)**.
- **Vyhľadanie podľa indexu:** ideme priamo na miesto → **O(1)**.

### Zhrnutie

Pri `n = 100`:

| Trieda | Počet operácií |
|---|---|
| O(1) | 1 |
| O(log n) | ~7 |
| O(n) | 100 |
| O(n²) | 10 000 |

Rozdiel je ešte výraznejší, keď `n` rastie. O(1) sa nemení. O(n²) je len
vnorený loop a rastie veľmi rýchlo — keď vieme kód prepísať na O(n), je to
veľký skok v efektivite. O(log n) uvidíme pri „divide and conquer". O(n²) je
najhoršia bežná trieda; O(n log n) uvidíme v niektorých triediacich algoritmoch.

---

## Vector vs LinkedList

```cpp
#include <iostream>
using namespace std;

int main(int args, char *argv[]) {
  // Dátová štruktúra sa najčastejšie porovnáva k poľu / vektoru.
  // Vektor aj linked list sú dynamické vo svojej dĺžke.
  // Vektor má priamu indexáciu — vieme priamo pristúpiť na index. Linked list nie.
  // V linked liste sú jednotlivé nody na rôznych miestach v pamäti.
  // Máme premennú, ktorá pointuje na prvú nodu — head.
  // A poslednú — tail — ktorá pointuje na poslednú nodu.
  // Každá noda pointuje na ďalšiu, posledná pointuje na nullptr.
  // Pri poli / vektore sú prvky za sebou v spojitej pamäti (continuous memory).

  // --- Linked list, Big O ---
  // Pridanie nody na koniec: posledná noda ukáže na novú, tail ukáže na novú.
  // n = počet nôd. Nezáleží, či ich má 4 alebo milión — rovnaký počet operácií.
  // => konštantný čas, O(1).

  // Odstránenie poslednej nody: musíme začať pri head a iterovať cez celý list,
  // kým sa nedostaneme k pointru na danú nodu, potom nastavíme tail. => O(n).

  // Pridanie na začiatok: nová noda = head pointer, head presunieme na novú nodu.
  // Nezáleží na počte nôd. => O(1) — pri pridávaní aj odoberaní zo začiatku.

  // Pridanie nody do stredu:
  // 11 --> 3 --> 23 --> 7 ; chceme pridať 4 hneď za 23
  // 1. preiterovať k danej node
  // 2. nová noda pointuje na to isté ako 23
  // 3. 23 nastavíme tak, aby pointovala na 4
  // Musíme iterovať cez list => O(n).

  // Odstránenie nody zo stredu: dostať sa k nej (iterácia), pointer z 23 = pointer
  // zo štvorky, odstrániť 4. => O(n).

  // Linked listy nemajú vstavané indexy — na check hodnoty aj na prístup podľa
  // indexu musíme iterovať. Pri linked liste je to vždy O(n).

  // Základný rozdiel: remove last je pri linked liste O(n), pri vektore O(1).
  // Keď chceš check podľa indexu, vektor je lepšia voľba.
}
```

---

## LinkedList — pod kapotou

Noda je kombinácia **hodnoty a pointra**. Dosť podobné dvojici v `unordered_map`:

```
value: 4,
next: nullptr
```

Nech linked list vyzerá takto: `11 --> 3 --> 23 --> 7`. Sedmička je ako
posledný záznam. Linked list je vlastne reťaz vzájomne pointujúcich nôd. Máme
premennú `head`, ktorá pointuje na začiatok, a `tail`, ktorá pointuje na koniec.

---

## Konštrukcia LinkedListu

Funkcie `append`, `prepend` a `insert` majú jednu spoločnú vec — všetky
vytvárajú novú nodu. Preto si spravíme samostatnú triedu `Node`.

```cpp
#include <iostream>
#include <fstream>
#include <unordered_map>
#include <vector>
#include <string>
#include <algorithm>
#include <iterator>

using namespace std;

class Node
{

public:
    int value{};
    Node *next;

    // ? dôvod prečo pouzivame this je jednoduchy potrebujeme jasne determinovať že sa jedna o value ktore je v member časti našej classy

    Node(int value)
    {
        this->value = value; // ? je to vlastne a len this->value je z membra, vlastne berieme niečo z vonku a assignujeeme to našej member functione
        next = nullptr;      // ? .this tam byt nemusime nemame next ako parameter funkcie
    }
};

class LinkedLIst
{

private:
    Node *head; // ? pointer to a node
    Node *tail; // ? pointer to a node
    size_t length{};

    // ? vytvormne si konštruktor

public:
    LinkedLIst(int value)
    {

        Node *newNode = new Node(value); // ? vďaka new keyworde vyhradi c++ pamät na heape, kde sa bude uchovvať objekt, nemusime teda presne determinovať jej velkosť
        head = newNode;                  // newNode je len pointer, ktory ukazuje na heap kde je vytvorena nova noda; head je tiez pointer, hovorime teda: ukazuj na tu istu nodu ako newNode
        tail = newNode;                  // to iste pre tail
        length = 1;                      // mame len jednu vytvorenu nodu, dlzka je teda 1
    }
};

int main(int argc, char *argv[])
{

    LinkedLIst *myLinkedList = new LinkedLIst(4);
    // vytvárame nový linked list niekde na heape;
    // po spustení máme nodu s hodnotou 4, ukazuje na ňu head aj tail
}
```

---

## printList a gettery

```cpp
class LinkedLIst
{

private:
    Node *head;
    Node *tail;
    size_t length{};

public:
    void printList()
    {
        Node *temp = head;      // ukazujeme na prvú
        while (temp != nullptr) // stačilo by aj len `temp`
        {
            cout << temp->value << endl; // hodnota, na ktorú temp pointuje
            temp = temp->next;           // posunie temp na ďalšiu nodu
        }
        // pri poslednej iterácii dôjde k rovnosti s nullptr, čo nás breakne z while
    }

    void getHead()
    {
        cout << "This is the head : " << head->value << endl;
    }

    void getTail()
    {
        cout << "This is the head : " << head->value << endl;
    }

    void getLength()
    {
        cout << "This is the head : " << length << endl;
    }

    LinkedLIst(int value)
    {
        Node *newNode = new Node(value);
        head = newNode;
        tail = newNode;
        length = 1;
    }
};

int main(int argc, char *argv[])
{
    LinkedLIst *myLinkedList = new LinkedLIst(4);
    myLinkedList->getHead();
    myLinkedList->getTail();
    myLinkedList->getLength();
    myLinkedList->printList();

    /*
    Požadovaný výstup:
    This is the head : 4
    This is the head : 4
    This is the head : 1
    4
    */
}
```

---

## Deštruktor

```cpp
~LinkedLIst() // deštruktor
    {
        Node *temp = head;
        while (head != nullptr)
        {
            head = head->next; // posun
            delete temp;       // vymaže prvú nodu
            temp = head;       // temp opäť nastavíme na head
        }
    }
    // head, tail, length maže base deštruktor
};

int main(int argc, char *argv[])
{
    LinkedLIst *myLinkedList = new LinkedLIst(4);

    // delete myLinkedList; -> spustí deštruktor pre triedu.
    // Ak deštruktor nemáme definovaný, spustí sa defaultný.

    /*
    Sú tu dve triedy: LinkedLIst a Node.
    Defaultný deštruktor vymaže len head, tail a length; nody ostanú v pamäti.
    */
}
```

---

## append

```cpp
  void append(int value)
    {
        Node *newNode = new Node(value); // najprv vytvoríme nodu

        if (head == nullptr) // zoznam je prázdny (aj length == 0)
        {
            head = newNode; // nový uzol je prvý aj posledný
            tail = newNode;
        }
        else // keď už máme prvky v liste
        {
            tail->next = newNode; // pointer posledného uzla ukáže na nový
            tail = newNode;       // tail sa posunie na nový uzol
        }

        length++;
    }

int main(int argc, char *argv[])
{
    LinkedLIst *myLinkedList = new LinkedLIst(4);
    myLinkedList->append(5);
    myLinkedList->printList();
}
```

---

## deleteLast (Delete Last)

```cpp
void deleteTail()
    {
        if (head = nullptr) // pozor: priradenie, nie porovnanie — zámerná chyba
        {
            cout << "the ll is empty" << endl;
            return;
        }
        if (head == tail) // len jedna noda (head aj tail ukazujú na ňu)
        {
            cout << " there is only one node " << endl;
            delete head;
        }
        else
        {
            Node *temp = head;
            // takto nájdeme posledný uzol
            while (temp->next != tail)
            {
                temp = temp->next;
            }
            delete tail;          // zmaž posledný uzol
            tail = temp;          // predposledný sa stane posledným
            tail->next = nullptr; // nový posledný ukazuje na nič
        }
    }

    // ? sekundárna metóda

    void deleteTail_secondary()
    {
        if (length == 0)
            return;

        Node *temp = head;
        Node *pre = head;
        while (temp->next != nullptr) // pôjde až po koniec
        {
            pre = temp;
            temp = temp->next;
            // temp je vždy o jedno popredu
        }
        tail = pre; // v pre je predposledná pozícia
        tail->next = nullptr;
        length--;
        if (length == 0)
        {
            head = nullptr;
            tail = nullptr;
        }
        delete temp;
    }
};
```

---

## deleteFirst (Delete First)

```cpp
    void deleteFirst()
    {
        Node *temp = head;
        if (head == nullptr) // prázdny
            return;
        if (length == 1)
        {
            head = nullptr;
            tail = nullptr;
        }

        head = head->next;

        delete temp;
        length--;
    }
};

int main(int argc, char *argv[])
{
    LinkedLIst *myLinkedList = new LinkedLIst(5);
    myLinkedList->append(4);
    myLinkedList->append(4);
    myLinkedList->printList();
    myLinkedList->deleteFirst();
    myLinkedList->printList();
}
```

---

## get

```cpp
Node* get(int index){
        if(index < 0 && index >= length){ // test, či je index v správnom rozsahu
            return nullptr;
        }
        Node *temp = head; // temporary variable
        for (size_t i = 0; i < index; i++) { // iteruj po zadanú dĺžku
            temp = temp->next;
        }
        return temp;
    }
```

### get — sekundárna možnosť

```cpp
Node* get_demo(int index) {
        if (index < 0 && index >= length) { // indexácia je v štýle length - 1
            return nullptr;
        }
        Node* temp = head;
        for (size_t i = 0; i < index; i++) {
            temp = temp->next;
        }
        if (temp != nullptr) {
            cout << temp->value << endl;
        }
        return temp;
    }
```

---

## set

### set — cez get

```cpp
    bool set(int index, int value) {
        Node* temp = get(index); // využijeme už implementovanú funkciu get
        if (temp) {
            // môže byť aj temp != nullptr
            temp->value = value;
            return true;
        }
        return false; // ak je nullptr, tak false
    }
```

### set — sekundárna implementácia

```cpp
 Node* set_function(int index, int value) {
        if (index < 0 && index >= length) {
            cout << "index out of range" << endl;
            return nullptr;
        }
        Node *temp = head;
        for (size_t i  = 0; i < index; i++) {
            temp = temp->next;
        }
        if (temp != nullptr) {
            temp->value = value;
            cout << " this is the new value " << temp->value << " of index " << temp << endl;
        }
    }
```

---

## insert

```cpp
  bool insert(int index, int value) {
        if (index < 0 || index > length) { // 1. if statement: mimo rozsahu
            return false;
        }
        if (index == 0) { // na začiatok
            prepand (value);
            return true;
        }
        if (index == length) { // na koniec
            append(value);
            return true;
        }
        Node* newNode = new Node(value);
        Node* temp = get(index - 1); // chceme ukazovať na predošlú nodu
        newNode->next = temp; // ukáž tam, kde temp
        temp->next = newNode;
        length++;
        return true;
    }
```

---

## reverse

```cpp
void reverse()
    {
        // Prvá vec: prehodíme ukazovateľ na začiatok a koniec
        Node *temp = head;
        head = tail;
        tail = head;

        Node *after = temp->next; // nachádza sa za tempom
        Node *before = nullptr;

        // before --- temp --- after

        for (size_t i = 0; i < length; i++)
        {
            after = temp->next;
            temp->next = before; // prehodíme, kam ukazuje — ukazuje opačne
                                 // tu sme si rozbili spojitosť v linked liste
            before = temp;
            temp = after;        // vďaka after premennej to posunieme
        }
    }
};
```

---

## Doubly Linked List — základ

Každá noda má navyše pointer `prev` na predchádzajúcu nodu.

```cpp
#include <iostream>
using namespace std;

class Node
{
public:
    int value;
    Node *next;
    Node *prev;

    Node(int value)
    {
        this->value = value;
        next = nullptr;
        prev = nullptr;
    }
};

class DoubleLinkedListto
{

private: // všetko je private by default
    Node *head;
    Node *tail;
    size_t length;

public:
    DoubleLinkedListto(int value)
    {
        Node *newNode = new Node(value);
        head = newNode;
        tail = newNode;
        length = 1;
    }

    void printlist()
    {
        Node *temp = head;

        while (temp != nullptr)
        {
            cout << temp->value << endl;
            temp = temp->next;
        }
    }
};

int main(int args, char *argv[])
{
    DoubleLinkedListto *myDDL = new DoubleLinkedListto(7);
    myDDL->printlist();
}
```

---

## Doubly Linked List — kompletná implementácia

Preberaná funkcionalita zo single linked listu, rozšírená o `prev`. Metóda
`get` využíva `prev` — ak je index v druhej polovici, iteruje od `tail` dozadu.

```cpp
#include <iostream>
using namespace std;

class Node {
public:
    int value;
    Node *next;
    Node *prev;

    Node(int value) {
        this->value = value;
        next = nullptr;
        prev = nullptr;
    }
};

class DoubleLinkedListto {
private:
    Node *head;
    Node *tail;
    int length;

public:
    DoubleLinkedListto(int value) {
        Node *newNode = new Node(value);
        head = newNode;
        tail = newNode;
        length = 1;
    }

    void printlist() {
        Node *temp = head;
        while (temp != nullptr) {
            cout << temp->value << endl;
            temp = temp->next;
        }
    }

    // začínajú DLL metódy
    void append(int value) {
        Node *newNode = new Node(value);
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

    void deleteLast() {
        if (head == nullptr || tail == nullptr) {
            cout << "The list is empty." << endl;
            return;
        }
        Node *temp = tail;
        if (length == 1) {
            head = nullptr;
            tail = nullptr;
        } else {
            tail = tail->prev;
            tail->next = nullptr;
        }
        delete temp;
        length--;
    }

    void prepand(int value) {
        Node *newNode = new Node(value);
        if (head == nullptr) {
            head = newNode;
            tail = newNode;
        } else {
            newNode->next = head;
            head->prev = newNode;
            head = newNode;
        }
        length++;
    }

    Node* get(int index) {
        if (index < 0 || index >= length) {
            return nullptr;
        }
        Node *temp = head;
        if (index < length / 2) {
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

    void deleteFirst() {
        if (head == nullptr) {
            cout << "The list is empty." << endl;
            return;
        }
        Node *temp = head;
        if (length == 1) {
            head = nullptr;
            tail = nullptr;
        } else {
            head = head->next;
            head->prev = nullptr;
        }
        delete temp;
        length--;
    }
    bool set( int index, int value) {
    Node* temp = get(index);
    if (temp != nullptr){// číslo nemôže byť záporné
    temp->value = value;
        return true;

    }

};

int main(int args, char *argv[]) {
    DoubleLinkedListto *myDDL = new DoubleLinkedListto(7);
    myDDL->append(1);
    myDDL->append(2);
    myDDL->append(3);

    cout << "List after appending:" << endl;
    myDDL->printlist();

    cout << "Value at index 2: " << myDDL->get(2)->value << endl;

    myDDL->deleteFirst();
    cout << "List after deleting the first node:" << endl;
    myDDL->printlist();

    myDDL->deleteLast();
    cout << "List after deleting the last node:" << endl;
    myDDL->printlist();

    myDDL->deleteFirst();
    myDDL->deleteFirst();
    myDDL->deleteFirst(); // Attempt to delete from an empty list
    cout << "List after deleting all nodes:" << endl;
    myDDL->printlist();

    return 0;
}
```

---

## Stack (zásobník)

Zásobník je LIFO — pridávame aj odoberáme z jedného konca (`top`, ekvivalent
`head` v linked liste). `push` aj `pop` sú O(1).

```cpp
#include <iostream>
using namespace std;
// identické s Node triedou pre linked list

class Node
{
public:
    int value{};
    Node *next;

    Node(int value)
    {
        this->value = value;
        next = nullptr;
    }
};

class Stack
{
private:       // triedy sú by default private
    Node *top; // ekvivalent headu v linked liste
    int height;

public:
    Stack(int value)
    {
        Node *newNode = new Node(value); // vytvor nodu s odovzdanou hodnotou
        top = newNode;                   // to isté ako head = jedna noda v linked liste
        height += 1;
    }

    void printStack()
    {
        Node *temp = top;
        while (temp)
        {
            cout << temp->value << endl;
            temp = temp->next;
        }
    }
    void push(int value)
    {
        Node *newNode = new Node(value);

        newNode->next = top;
        top = newNode;
        height++;
    }

    int pop()
    { // podobné delete first
        if (height == 0)
        {
            return INT_MIN; // najmenšie možné int
        }
        Node *temp = top;
        int popped_value = temp->value;
        top = top->next;
        temp->next = nullptr;
        delete temp;
        return popped_value;
        height--;
    }

public:
    int getHeight()
    {
        cout << "this is the height" << height << endl;
    }
};

int main(int agrs, char *argv[])
{
    Stack *kraken = new Stack(7);
    kraken->push(2);
    kraken->printStack();
    kraken->pop();
    kraken->printStack();
    kraken->getHeight();
}
```

---

## Stack + Queue — základné operácie (push / pop, enqueue / dequeue)

Fronta je FIFO — pridávame na koniec (`enqueue`), odoberáme zo začiatku
(`dequeue`).

```cpp
#include <iostream>
using namespace std;

class Node
{
public:
    int value{};
    Node *next = nullptr;

    Node(int value)
    {
        this->value = value;
        next = nullptr;
    }
};

class LinkedList
{
private:
    Node *tail;
    Node *head;
    int length = 0;

public:
    LinkedList(int value)
    {
        Node *newNode = new Node(value);
        head = newNode;
        tail = newNode;
        length++;
    }

    void printList()
    {
        Node *temp = head;
        while (temp != nullptr)
        {
            cout << " this is the temp value : " << temp->value << endl;
            temp = temp->next;
        }
    }

    void append(int value)
    {
        Node *newNode = new Node(value);
        tail->next = newNode;
        tail = newNode; // Oprava
        length++;
    }
};

class Stack
{
public:
    Node *top;
    int height{};

    Stack() : top(nullptr), height(0) {}

    void push(int value)
    {
        Node *newNode = new Node(value);
        newNode->next = top;
        top = newNode;
        height++;
    }

    void pop()
    {
        if (top == nullptr)
        {
            return;
        }
        Node *temp = top;
        top = temp->next;
        temp->next = nullptr;
        delete temp;
    }

    void vypisStack()
    {
        size_t localVar{};
        Node *temp = top;
        while (temp)
        {
            localVar++;
            cout << "Iteration: " << localVar << " Value: " << temp->value << endl;
            temp = temp->next;
        }
    }
};

class Queue
{
private:
    Node *first;
    Node *last;
    int length;

public:
    Queue(int value)
    {
        Node *newNode = new Node(value);
        first = newNode;
        last = newNode;
        length = 1;
    }

    void enqueue(int value)
    { // Oprava názvu
        Node *newNode = new Node(value);
        if (length == 0)
        {
            first = newNode;
            last = newNode;
        }
        else
        {
            last->next = newNode;
            last = newNode;
        }
        length++;
    }

    void print()
    {
        Node *temp = first;
        while (temp)
        {
            cout << temp->value << " ";
            temp = temp->next;
        }
        cout << endl;
    }

    int dequeue()
    {
        if (length == 0)
        {
            return INT_MIN;
        }
        Node *temp = first;
        int dequeuedValue = first->value;
        if (length == 1)
        {
            first = nullptr;
            last = nullptr;
        }
        else
        {
            first = first->next;
        }
        delete temp;
        length--;
        return dequeuedValue;
    }
};

int main()
{
    LinkedList *linkList = new LinkedList(2);
    linkList->append(3);
    linkList->printList();
    delete linkList; // uvoľnenie pamäte

    Stack *stack_ptr = new Stack();
    stack_ptr->push(2);
    stack_ptr->push(5);
    stack_ptr->vypisStack();
    delete stack_ptr;

    cout << "------fronta-----" << endl;
    Queue *ptr_fronta = new Queue(5);
    ptr_fronta->enqueue(4);
    ptr_fronta->enqueue(7);
    ptr_fronta->print();
    ptr_fronta->dequeue();
    ptr_fronta->print();
    delete ptr_fronta;

    return 0;
}
```
