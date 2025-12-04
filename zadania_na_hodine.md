# Linked Lists - Cvičenia

Sada praktických úloh na precvičenie linked listov by Tom. Muc.

---

## Linked List: Intro

**Téma:** Základné pochopenie linked listu

**Zadanie:**
Predstav si, že organizuješ párty a chceš si zapísať poradie, v akom prišli hostia. Každý hosť dostane číslo a vie, kto prišiel po ňom.

Vytvor jednoduchý linked list, ktorý reprezentuje prvých 5 hostí s číslami: 1, 2, 3, 4, 5. Každý uzol (hosť) obsahuje jeho číslo a odkaz na ďalšieho hosťa. Vypíš všetkých hostí v poradí.

**Výstup:**
```
Hosť #1 -> Hosť #2 -> Hosť #3 -> Hosť #4 -> Hosť #5 -> None
```

---

## LL: Big O

**Téma:** Analýza časovej zložitosti operácií v linked liste

**Zadanie:**
Máš playlist s pesničkami. Porovnaj, aký rozdiel je medzi:
- Pridaním pesničky na začiatok playlistu (linked list)
- Pridaním pesničky na začiatok poľa (array)

Napíš program, ktorý:
1. Vytvorí linked list a pridá 1000 pesničiek na začiatok
2. Vytvorí array a pridá 1000 pesničiek na začiatok (použitím `insert(0, ...`)
3. Zmeria čas oboch operácií
4. Vysvetlí, prečo je linked list rýchlejší

**Otázka na zamyslenie:**
Aká je časová zložitosť pridania prvku na začiatok linked listu? A do poľa?

---

## LL: Under the Hood

**Téma:** Vnútorná štruktúra linked listu

**Zadanie:**
Vlak sa skladá z vagónov. Každý vagón vie, ktorý vagón je za ním, ale nevie, ktorý je pred ním.

Vytvor vlastnú implementáciu tried `Node` a `LinkedList` od základov. Trieda `Node` musí obsahovať:
- `data` - údaje v uzle (číslo vagónu)
- `next` - odkaz na ďalší uzol

Trieda `LinkedList` musí obsahovať:
- `head` - odkaz na prvý uzol
- metódu `add_to_beginning(data)` - pridá vagón na začiatok vlaku
- metódu `display()` - zobrazí celý vlak

Vytvor vlak s vagónmi: 5 -> 3 -> 7 -> 2

---

## LL: Constructor

**Téma:** Vytvorenie konštruktora pre linked list

**Zadanie:**
Chceš vytvoriť hru, kde hráči stoja v rade. Prvý hráč v rade je vždy aktívny.

Implementuj konštruktor pre `LinkedList`, ktorý:
1. Ak sa vytvorí prázdny linked list, `head` je `None`
2. Ak sa vytvorí s hodnotou, automaticky sa vytvorí prvý uzol

Príklad použitia:
```python
prazdny_zoznam = LinkedList()          # head = None
zoznam_s_prvkom = LinkedList(100)      # head -> Node(100)
```

Otestuj oba prípady a vypíš obsah listov.

---

## Coding Exercises (Important)

**Téma:** Precvičenie základov

**Zadanie:**
Vytvor linked list reprezentujúci tvoj obľúbený playlist s aspoň 5 piesňami. Každý uzol obsahuje názov piesne.

Následne naprogramuj:
1. Pridanie novej piesne na koniec playlistu
2. Vypísanie všetkých piesní
3. Zistenie počtu piesní v playliste

**Príklad:**
```
Playlist:
1. Believer -> 2. Bones -> 3. Thunder -> 4. Radioactive -> 5. Demons
```

---

## LL: Print List

**Téma:** Prechádzanie a výpis linked listu

**Zadanie:**
Máš cukráreň a eviduješ zákazníkov v rade. Každý zákazník má meno.

Vytvor linked list so zákazníkmi: "Anna", "Branislav", "Cyril", "Danka", "Erik"

Napíš funkciu `print_list()`, ktorá vypíše všetkých zákazníkov v tvare:
```
Zákazníci v rade:
1. Anna
2. Branislav
3. Cyril
4. Danka
5. Erik
```

**Bonus:** Vypíš aj celkový počet čakajúcich zákazníkov.

---

## LL: Destructor

**Téma:** Mazanie celého linked listu

**Zadanie:**
Hra sa skončila a potrebuješ vymazať všetkých hráčov zo zoznamu.

Napíš metódu `destroy()`, ktorá:
1. Prejde celým linked listom
2. Vymaže všetky uzly
3. Nastaví `head` na `None`

Pred a po zavolaní metódy vypíš stav listu, aby si videl rozdiel.

**Príklad:**
```
Pred: 10 -> 20 -> 30 -> 40
Po: Zoznam je prázdny
```

---

## LL: Append

**Téma:** Pridanie prvku na koniec

**Zadanie:**
Organizuješ turnaj a prihlasujú sa nový hráči. Každý nový hráč sa pridá na koniec zoznamu.

Implementuj metódu `append(data)`, ktorá pridá nového hráča na koniec linked listu.

Otestuj na príklade:
1. Začni s prázdnym zoznamom
2. Pridaj hráčov: "Lukáš", "Martin", "Nina", "Ondrej"
3. Vypíš zoznam po každom pridaní

**Časová zložitosť:** Aká je časová zložitosť tvojho riešenia? O(1) alebo O(n)?

---

## LL: Delete Last (Intro)

**Téma:** Úvod do mazania posledného prvku

**Zadanie:**
V rade na autobus je posledná osoba nervózna a odchádza.

Najprv pochop problém: Ako nájdeš predposledný uzol v linked liste, ak každý uzol pozná len nasledujúci, nie predchádzajúci?

Napíš funkciu, ktorá:
1. Nájde predposledný uzol
2. Vypíš jeho hodnotu
3. Vysvetli, prečo potrebuješ nájsť práve predposledný uzol

Test na linked liste: 15 -> 23 -> 7 -> 42 -> 31

---

## LL: Delete Last (Code)

**Téma:** Implementácia mazania posledného prvku

**Zadanie:**
Posledný cestujúci v autobuse vystúpil na konečnej.

Implementuj metódu `delete_last()`, ktorá:
1. Ak je list prázdny, vráti `None`
2. Ak je v liste len jeden prvok, vymaže ho
3. Ak je viac prvkov, vymaže posledný a aktualizuje predposledný

Otestuj na linked liste: "Jablko" -> "Banán" -> "Citrón" -> "Dáta"

Vymaž posledný prvok a vypíš nový zoznam.

---

## LL: Delete Last (Rewrite)

**Téma:** Optimalizácia delete_last metódy

**Zadanie:**
Tvoja pôvodná funkcia na mazanie posledného prvku funguje, ale chceš ju prepísať elegantnejšie.

Prepíš metódu `delete_last()` tak, aby:
1. Používala lepšie názvy premenných (napr. `current`, `previous`)
2. Bola čitateľnejšia s komentármi
3. Ošetrovala všetky špeciálne prípady (prázdny list, jeden prvok)

Porovnaj obe verzie kódu a zdôvodni, ktorá je lepšia.

---

## LL: Prepend

**Téma:** Pridanie prvku na začiatok

**Zadanie:**
VIP hosť prišiel na párty a chce ísť na začiatok radu (samozrejme 😄).

Implementuj metódu `prepend(data)`, ktorá pridá nový uzol na začiatok linked listu.

**Kroky:**
1. Vytvor nový uzol s hodnotou
2. Nastav jeho `next` na aktuálny `head`
3. Aktualizuj `head` na nový uzol

Otestuj: Začni s listom [5, 10, 15] a pridaj 1 na začiatok.

**Výsledok:** 1 -> 5 -> 10 -> 15

---

## LL: Delete First

**Téma:** Odstránenie prvého prvku

**Zadanie:**
Prvý zákazník v rade dostal svoju objednávku a odchádza.

Implementuj metódu `delete_first()`, ktorá:
1. Ak je list prázdny, vráti `None`
2. Odstráni prvý uzol
3. Aktualizuje `head` na druhý uzol
4. Vráti odstránený uzol (aby si vedel, kto odišiel)

Test na linked liste s číslami: 100 -> 200 -> 300 -> 400

Vymaž prvý prvok a vypíš nový zoznam.

---

## LL: Get

**Téma:** Získanie prvku na konkrétnom indexe

**Zadanie:**
Chceš zistiť, kto je na 3. mieste v rade (indexuješ od 0).

Implementuj metódu `get(index)`, ktorá:
1. Prejde linked listom až po daný index
2. Vráti uzol na danom indexe
3. Ak index neexistuje, vráti `None`

Test: V linked liste [10, 20, 30, 40, 50], zisti hodnotu na indexe 2.

**Očakávaný výsledok:** 30

---

## LL: Set

**Téma:** Zmena hodnoty na konkrétnom indexe

**Zadanie:**
Zákazník na 4. mieste v rade zmenil objednávku.

Implementuj metódu `set(index, value)`, ktorá:
1. Nájde uzol na danom indexe (použi metódu `get()`)
2. Zmení jeho hodnotu
3. Vráti `True` ak úspech, `False` ak index neexistuje

Test: V linked liste ["Pizza", "Burger", "Salát", "Wrap"] zmeň položku na indexe 1 na "Hot Dog".

**Výsledok:** ["Pizza", "Hot Dog", "Salát", "Wrap"]

---

## LL: Insert

**Téma:** Vloženie prvku na konkrétny index

**Zadanie:**
Nový zákazník prišiel a chce sa vložiť na 3. miesto v rade (kámoš mu ho nechal).

Implementuj metódu `insert(index, value)`, ktorá:
1. Ak je index 0, použi `prepend()`
2. Ak je index na konci, použi `append()`
3. Inak nájdi uzol pred daným indexom a vlož nový uzol medzi

Test: Do linked listu [1, 3, 4, 5] vlož číslo 2 na index 1.

**Výsledok:** [1, 2, 3, 4, 5]

---

## LL: Delete Node

**Téma:** Zmazanie uzla na konkrétnom indexe

**Zadanie:**
Zákazník na 3. pozícii v rade sa unavil čakať a odišiel.

Implementuj metódu `delete_node(index)`, ktorá:
1. Ak je index 0, použi `delete_first()`
2. Ak je posledný index, použi `delete_last()`
3. Inak nájdi uzol pred indexom a preskočíme uzol na indexe

Test: Z linked listu ["A", "B", "C", "D", "E"] vymaž prvok na indexe 2.

**Výsledok:** ["A", "B", "D", "E"]

---

## LL: Reverse

**Téma:** Otočenie linked listu

**Zadanie:**
Potrebuješ otočiť poradie hráčov v zozname - posledný sa stane prvým.

Implementuj metódu `reverse()`, ktorá otočí linked list "in-place" (bez vytvárania nového).

**Hint:** Potrebuješ tri pointre: `previous`, `current`, `next_node`

Test: Otoč linked list [1, 2, 3, 4, 5]

**Výsledok:** [5, 4, 3, 2, 1]

**Bonus:** Nakresli si diagram, ako sa menia pointre počas otáčania!

---

## Quiz 2: Linked List Big O

**Téma:** Časová zložitosť operácií

**Zadanie kvízu:**

Urči časovú zložitosť (Big O) pre nasledujúce operácie v linked liste:

1. **Append** (pridanie na koniec) - ?
2. **Prepend** (pridanie na začiatok) - ?
3. **Delete First** (zmazanie prvého) - ?
4. **Delete Last** (zmazanie posledného) - ?
5. **Get** (získanie prvku na indexe) - ?
6. **Set** (zmena hodnoty na indexe) - ?
7. **Insert** (vloženie prvku na index) - ?
8. **Delete Node** (zmazanie uzla na indexe) - ?

Pre každú operáciu zdôvodni svoju odpoveď a porovnaj s operáciami v poli (array).

**Bonusová otázka:** 
Kedy je lepšie použiť linked list a kedy array? Uveď konkrétne príklady použitia.

S pozdravom, 
Tomáš M.

