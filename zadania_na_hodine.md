# Zadanie 1. 

Dokončite implementáciu binárneho vyhľadávacieho stromu zo cvičenia.

Binárny strom bude konštruovaný postupnými vkladaniami celých čísel (int).

Binárny strom musí vedieť nasledujúce operácie:
- `insert(item)` – vloženie prvku,
- výpisy `inorder`, `preorder` a `postorder` na štandardný výstup (`std::cout`),
- odstránenie prvku pomocou `delete(item)`.

Výpisy `inorder`, `preorder` a `postorder` musia byť vo formáte hodnôt oddelených medzerami.

Pridajte tiež funkciu, ktorá bude vypisovať strom na štandardný výstup „po úrovniach“. Na prvom riadku bude koreň, na druhom jeho potomkovia, na treťom potomkovia potomkov atď. Usporiadanie na riadku bude rešpektovať štruktúru binárneho stromu tak, že pre riadok `A B` bude riadok pod ním vyzerať `leftChildA rightChildA leftChildB rightChildB` a analogicky pre zvyšok stromu. Na miestach, kde chýba potomek, bude `X`. Toto by nemal byť problém implementovať pomocou prehľadávania do šírky.

## Mazanie (`delete(item)`)

Funkcia `delete(item)` bude fungovať takto:
- Ak hodnota `item` nie je v strome, strom sa nezmení.
- Ak sa hodnota nachádza, odstráni jedinečný prvok `item` a správne pripojí prípadné odrezané podstromy.

Správne pripojenie v prípade uzla s dvomi potomkami sa realizuje takto:
1. Skopírujeme hodnotu in-order nasledovníka (najmenší uzol v pravom podstrome) alebo in-order predchodcu (najväčší uzol v ľavom podstrome) do uzla, ktorý chceme odstrániť.
2. Potom odstránime uzol, ktorý obsahoval pôvodnú hodnotu tohto nasledovníka alebo predchodcu.

## Testovanie

### Vstupy
Program bude brať ako vstup z príkazového riadku názov súboru, z ktorého načíta graf, tzn. `main` bude vyzerať napríklad takto:

```cpp
int main(int argc, char* argv[]) {
    std::string filename = argv[1];
```

## Výstupy
Program nech na štandardný výstup postupne vypíše:

1. Postorder,
2. Preorder,
3. Inorder,
4. Výpis „po úrovniach“.
   
Váš program nech postupne na štandardný výstup (`std::cout`) vypíše postorder, preorder a inorder, a následne aj výpis po úrovniach. (Na medzery vo výstupe nezáleží.)

## Príklady 

`Vstupy: ` 1 2 3 4 5 6 7 8 9 10

`Očakávaný výstup:`

```cpp
10 9 8 7 6 5 4 3 2 1 
1 2 3 4 5 6 7 8 9 10 
1 2 3 4 5 6 7 8 9 10 
1 
X 2 
X 3 
X 4 
X 5 
X 6 
X 7 
X 8 
X 9 
X 10 
X X 
```

`Vstupy: ` 5 1 0 6 3 2 4 8 7

`Očakávaný výstup:`

```cpp
0 2 4 3 1 7 8 6 5 
5 1 0 3 2 4 6 8 7 
0 1 2 3 4 5 6 7 8 
5 
1 6 
0 3 X 8 
X X 2 4 7 X 
X X X X X X 

```

`Vstupy: ` 15 1 14 -3 20 40 33 32 5 4 3 12 77 45 63 50 51 25

`Očakávaný výstup:`

 ```cpp
-3 3 4 12 5 14 1 25 32 33 51 50 63 45 77 40 20 15 
15 1 -3 14 5 4 3 12 20 40 33 32 25 77 45 63 50 51 
-3 1 3 4 5 12 14 15 20 25 32 33 40 45 50 51 63 77 
15 
1 20 
-3 14 X 40 
X X 5 X 33 77 
4 12 32 X 45 X 
3 X X X 25 X X 63 
X X X X 50 X 
X 51 
X X 
```

# Zadanie 2.

Úlohou je preskúmať ďalšiu z mierne bizarných úloh na prechádzanie rieky. Na jednom brehu rieky sa nachádza `n` manželských párov, ktoré je potrebné prepraviť na druhý breh. Prevoz je možný pomocou loďky, ktorá má nasledujúce pravidlá:

1. Loďka môže previezť buď jedného, alebo dvoch ľudí naraz.
2. Loďka nemôže plávať sama, musí v nej byť vždy aspoň jedna osoba.
3. Manželia sú veľmi žiarliví. Žiadny manžel neznesie, aby jeho žena bola v spoločnosti iného muža na rovnakom brehu, ak na tomto brehu nie je prítomná jeho manželka.
4. Rovnaké pravidlá platia aj v loďke. Manžel a manželka sa teda môžu prepravovať spoločne na loďke iba ak patria do toho istého páru.
5. Na začiatku sú všetky osoby na jednom brehu rieky, v cieľovom stave musia byť všetky osoby na druhom brehu.
6. Manželia sa môžu presúvať ľubovoľne, ak sú dodržané pravidlá o žiarlivosti.

Vašou úlohou je naprogramovať riešenie, ktoré určí minimálny počet prevozov potrebných na to, aby sa všetky páry úspešne prepravili na druhý breh rieky, pričom je nutné splniť všetky uvedené pravidlá. Môžete, podobne ako na cvičení, použiť prehľadávanie do šírky alebo iný spôsob, ktorý hľadá najkratšiu cestu v zodpovedajúcom stavovom grafe.

---

## Povolené a nepovolené konfigurácie

Nasledujúce konfigurácie znázorňujú, ako môžu byť jednotlivé osoby prítomné na brehu rieky:

- `wife0, wife1` – povolená konfigurácia
- `husband1, husband0` – povolená konfigurácia
- `wife0, husband1` – nepovolená konfigurácia (husband1 je na brehu s cudzou ženou a jeho vlastná manželka `wife1` nie je prítomná)
- `wife0, wife1, husband0` – povolená konfigurácia (husband0 je na brehu so svojou manželkou)
- `wife0, husband1, husband0` – povolená konfigurácia (wife0 je na brehu so svojím manželom)

---

## Testy a riešenie pre nižšie hodnoty `n`

- Pre dva manželské páry je možné dosiahnuť prevoz na druhý breh v **piatich prevozoch**.
- Pre tri páry je potrebných **deväť prevozov**.
- Pre štyri páry je to **trinásť prevozov**.

Pomocou tužky a papiera sa dá relatívne jednoducho overiť, že každý ďalší pár zvýši počet prevozov o štyri.

---

## Testovanie

Test bude len jeden, nebude mať žiadny vstup a skontroluje výstup počítaný z prvých troch inštancií problému. Na konci výpisu je prázdny riadok, aby sme sa nemuseli zaoberať špeciálnym spracovaním posledného riadku výpisu.

### Očakávaný výstup:

 ```cpp
2 pairs - 5 transports 3 pairs - 9 transports 4 pairs - 13 transports
 ```

---

## Pre zábavu

Keď budete mať prvú funkčnú verziu programu, vyskúšajte, pre aké najväčšie `n` ste schopní nájsť riešenie. Potom sa skúste zamyslieť, ako by bolo možné algoritmus vylepšiť, aby zvládol väčšie hodnoty `n`, ale stále fungoval na báze prehľadávania stavového priestoru (ak je niečo také vôbec možné).



