# C++ Úlohy na precvičenie designed by Tom. (Starky) Muc.

## Úloha 1: Lambda Kalkulačka s `auto`

Napíš program, ktorý umožní používateľovi zadať dve čísla a operáciu (`+`, `-`, `*`, `/`). Program použije **lambda funkcie** s **automatickou dedukciou typu (`auto`)** na vykonanie výpočtov.

### Rozšírenia:
- ✅  Definuj štyri **lambda funkcie** pre základné operácie s použitím `auto`.
- ✅  Použi **`std::map<char, auto>`** na mapovanie operácií na lambda funkcie.
- ✅  Ošetri **delenie nulou**.
- ✅  Použi **`try-catch` blok** na zachytávanie chýb.
- ✅  Po výpočte program umožní **používateľovi zadať novú operáciu** bez reštartu.

---

## Úloha 2: Fibonacciho sekvencia so špeciálnym cyklom

Napíš program, ktorý vypočíta prvých `n` čísel Fibonacciho sekvencie pomocou **range-based for cyklu**, ktorý je špecifický pre C++.

### Rozšírenia:
- ✅ Použi **`std::vector`** na uchovávanie Fibonacciho čísel.
- ✅  Generuj Fibonacciho čísla **pomocou range-based for loop**.
- ✅  Program vypíše **len tie Fibonacciho čísla, ktoré sú párne**.
- ✅  Použi **`std::transform`** na výpočet ďalších hodnôt v sekvencii.
- ✅  Použi **`constexpr`** pre efektívnejšiu prácu s hodnotami.

---

## Úloha 3: Triedenie reťazcov s vlastnou porovnávacou funkciou

Napíš program, ktorý načíta `n` reťazcov a zotriedi ich pomocou vlastnej **porovnávacej funkcie**, ktorá:

1. **Prioritizuje kratšie reťazce**.
2. Ak majú rovnakú dĺžku, zoradí ich **lexikograficky vzostupne**.
3. Ak obsahujú **číselné hodnoty**, umiestni ich **na koniec zoznamu**.

### Rozšírenia:
- ✅ Použi **`std::sort`** s vlastným **lambda porovnávačom**.
- ✅ Na rozpoznanie čísiel v reťazcoch použi **`std::any_of`** a `isdigit()`.
- ✅ Použi **`std::vector<std::string>`** na uchovanie reťazcov.
- ✅ Program umožní **používateľovi zadať ľubovoľný počet reťazcov**.
  
---

## Úloha 4: Rozšírená práca so súbormi – Čítanie, zápis a vyhľadávanie

### Zadanie:
Napíš program, ktorý umožní používateľovi vykonávať operácie so súborom obsahujúcim mená a veky ľudí.

### Rozšírenia:
- ✅ Používateľ si vyberie režim: zápis nových údajov alebo prehľadanie súboru.
- ✅ Použiť `std::ofstream` (append mode) na pridávanie údajov bez straty existujúcich.
- ✅ Použiť `std::ifstream` na načítanie údajov a ich vypísanie.
- ✅ Implementovať vyhľadávanie osoby podľa mena – ak sa nenájde, vypísať správu.
- ✅ Ošetriť chyby pri otváraní súboru a nesprávne formátované dáta.

### Koncepty:
Súbory, streamy, vyhľadávanie v texte, spracovanie vstupu, error handling.

---

## Úloha 5: Práca s referenciami a ukazovateľmi – Dynamická alokácia

### Zadanie:
Napíš program, ktorý nielen vymení hodnoty dvoch premenných, ale aj pracuje s dynamicky alokovanou pamäťou.

### Rozšírenia:
- ✅ Okrem `swapByReference` a `swapByPointer` pridaj `swapBySmartPointer`, ktorý využije `std::unique_ptr`.
- ✅ Implementuj vstup od používateľa na výmenu hodnôt namiesto pevne definovaných premenných.
- ✅ Použiť dynamickú alokáciu (`new` a `delete`) pri ukazovateľovej verzii.
- ✅ Ošetriť použitie `nullptr` v ukazovateľovej verzii.

### Koncepty:
Referencie, ukazovatele, smart pointre, dynamická pamäť.

---

## Úloha 6: Pokročilá evidencia známok – Triedenie a štatistika

### Zadanie:
Napíš program, ktorý umožní používateľovi zadávať mená študentov a ich známky a poskytne podrobnejšie štatistiky.

### Rozšírenia:
- ✅ Použiť `std::map<std::string, std::vector<int>>`, ale s možnosťou odstránenia študenta.
- ✅ Implementovať triedenie známok študenta pomocou `std::sort`.
- ✅ Vypočítať medián známok spolu s priemerom.
- ✅ Použiť `std::minmax_element` na zistenie najlepšej a najhoršej známky každého študenta.
- ✅ Ak má študent menej ako 3 známky, upozorniť na nedostatok dát pre štatistiky.

### Koncepty:
Kontajnery (`std::map`, `std::vector`), triedenie (`std::sort`), algoritmy (`std::accumulate`, `std::minmax_element`), spracovanie dát.

---

# Úloha 7 : Implementácia zásobníka s `std::stack` a šablónami

## Zadanie:
Napíš program, ktorý implementuje **zásobník** (stack) pomocou `std::stack` a umožní používateľovi vykonávať operácie:

1. **Push** – Pridať prvok na vrchol zásobníka.
2. **Pop** – Odstrániť prvok z vrcholu.
3. **Top** – Zobraziť vrchný prvok bez odstránenia.
4. **Empty** – Skontrolovať, či je zásobník prázdny.

## Rozšírenia:
- ✅ Implementuj **šablónovú triedu (`template<class T>`)** pre zásobník.
- ✅ Použi **`std::stack<T>`** na implementáciu interných operácií.
- ✅ Používateľ si môže vybrať typ údajov, ktorý bude zásobník uchovávať (int, double, string).
- ✅ Ošetri **výnimky**, keď sa pokúša vybrať prvok z prázdneho zásobníka.
- ✅ Implementuj **iteráciu cez zásobník** pomocou vlastného iterátora.

## Koncepty:
- **Šablóny (`template`)**
- **Kontajnery (`std::stack`)**
- **Výnimky (`try-catch`)**
- **Iterátory**

---

# Úloha 8 : Implementácia fronty / rady / queue s `std::queue` a šablónami

## Zadanie:
Napíš program, ktorý implementuje **frontu** (queue) pomocou `std::queue` a umožní používateľovi vykonávať operácie:

1. **Enqueue** – Pridať prvok na koniec fronty.
2. **Dequeue** – Odstrániť prvok zo začiatku fronty.
3. **Front** – Zobraziť prvý prvok bez odstránenia.
4. **Empty** – Skontrolovať, či je fronta prázdna.

## Rozšírenia:
- ✅ Implementuj **šablónovú triedu (`template<class T>`)** pre frontu.
- ✅ Použi **`std::queue<T>`** na implementáciu interných operácií.
- ✅ Používateľ si môže vybrať typ údajov, ktorý bude fronta uchovávať (int, double, string).
- ✅ Ošetri **výnimky**, keď sa pokúša vybrať prvok z prázdnej fronty.
- ✅ Implementuj **iteráciu cez frontu** pomocou vlastného iterátora.

## Koncepty:
- **Šablóny (`template`)**
- **Kontajnery (`std::queue`)**
- **Výnimky (`try-catch`)**
- **Iterátory**

---

## Bonusová úloha 

# Úloha : Paralelné spracovanie dát s `std::thread`

## Zadanie:
Napíš program, ktorý spracuje veľké množstvo čísel paralelne pomocou **viacerých vlákien** (`std::thread`). Program vykoná tieto operácie:

1. **Spočíta súčet všetkých čísel**.
2. **Spočíta počet nepárnych čísel**.
3. **Nájde maximum v poli**.

Každá operácia bude spracovaná v samostatnom vlákne.

## Rozšírenia:
- ✅ Použi **std::vector<int>** na uchovanie čísel.
- ✅ Použi **std::thread** na paralelné výpočty.
- ✅ Synchronizuj výstup pomocou **`std::mutex`** na zabránenie race condition.
- ✅ Použi **std::future a std::async** na alternatívne spracovanie.
- ✅ Generuj veľké množstvo náhodných čísel na testovanie výkonu.

## Koncepty:
- **Vlákna (`std::thread`)**
- **Synchronizácia (`std::mutex`)**
- **Asynchrónne operácie (`std::future`, `std::async`)**
- **Dátové štruktúry (`std::vector`)**



