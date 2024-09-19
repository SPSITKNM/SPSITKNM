# UML Zadania na hodinu PRO 

Tento dokument obsahuje 15 zadání, každý z Vás si vyberie jedno zadanie, ktoré bude spracovávať na hodine... z výslednej práce na každý diagram vytvoríte snímok obrazovky a vložíte ho do word dokumentu.
Dokument buse niesť v názve Vaše meno, triedu a číslo zadania, ktoré spracováate. 

# Riaďte sa špecifikami uvedenými nižšie.

# 1. Use Case Diagram

Use case diagram - obsahující minimálně 5 modulů a 2 aktéry, doporučené maximum 5 modulů s využitím `include` a `extend`.

# 2. Use Case Diagram

- **Schéma triedneho diagramu**
- Diagram musí obsahovať výpočet všetkých atribútov (dbajte na atomické rozdelenie obsahu, napríklad: meno rozpísať na `Meno`, `Prostredné meno`, `Priezvisko`, `Titul pred`, `Titul za`, ak to vaša evidencia vyžaduje, to isté pre poštové adresy atď.) a metód. Doplňte, či sa jedná o `public`, `private` alebo `protected`.
- Je vhodné do schémy zahrnúť triedu `System (main)`.
- Pomenovanie tried, atribútov a metód v jednotnom jazyku (slovensky alebo anglicky) podľa požiadaviek na vývoj SW (žiadne slovenské znaky, medzery atď.).
- Pri vlastnostiach a metódach vyznačte `Public`, `Private`, `Protected`.
- **Slovný popis významu jednotlivých väzieb** uveďte pod diagramom.
- Dbajte na správne určenie kardinality a zápis na správnu stranu, na stranách s diamantom (agregácia, kompozícia), kde je kardinalita zvyčajne 1, ju písať nemusíte.
- Je vhodné, aby v diagramoch boli použité okrem klasických asociácií aj dedičnosti, kompozícia a agregácia – nie je to však nutné.

## 2. Deklarácia tried vrátane výčtu atribútov a metód

- Je vhodné deklarovať minimálne **tri najdôležitejšie triedy** z triedneho diagramu.
- Deklaráciu vpíšte priamo do odovzdaného dokumentu s formátovaním (nie ako ďalší súbor).

# 3. Sekvenčný diagram

- **Navrhnite tri netriviálne diagramy** s kódom odvodeným z diagramu, pričom aspoň 2 netriviálne metódy obsahujú prvky ako `if`, `loop` atď.
- Ak sa vo vašom riešení nevyskytuje dostatok vhodných situácií na popis stavovým diagramom, vymyslite si tému mimo systému.
- V diagramoch by sa mali objaviť prvky rozhodovania a prípadne cyklu.
- Uvedomte si, kedy do popisu vstupuje konkrétny aktér a kedy nejaká časť systému (systém ako celok alebo trieda prostredníctvom definovaných metód).

# 4. Aktivitný diagram

- **Nakreslite tri diagramy**.
- Ak sa vo vašom systéme nevyskytujú vhodné problematiky, popíšte inú aktivitu mimo váš systém.


## 1. Rezervačný systém hotelov
- **Use Case:** Rezervácia izby, kontrola dostupnosti, zrušenie rezervácie, platba.
- **Class:** Triedy pre `Rezervácia`, `Izba`, `Zákazník`, `Platba`, `Správca`.
- **Stavový:** Stavy rezervácie, ako `Vytvorená`, `Potvrdená`, `Zaplatená`, `Zrušená`.
- **Activity:** Proces rezervácie, od zadania údajov po potvrdenie a platbu.

## 2. Internetový obchod (E-shop)
- **Use Case:** Prehliadanie produktov, pridávanie do košíka, vytvorenie objednávky, platba, sledovanie zásielky.
- **Class:** `Produkt`, `Košík`, `Objednávka`, `Používateľ`, `Platba`.
- **Stavový:** Stavy objednávky, ako `Vytvorená`, `Zaplatená`, `Zaslaná`, `Doručená`.
- **Activity:** Proces nákupu od výberu produktu cez platbu až po doručenie.

## 3. Systém internetového bankovníctva
- **Use Case:** Prihlásenie, kontrola zostatku, prevod peňazí, platby faktúr, zablokovanie účtu.
- **Class:** `Účet`, `Transakcia`, `Klient`, `Kreditná karta`.
- **Stavový:** Životný cyklus účtu, ako `Aktívny`, `Blokovaný`, `Zatvorený`.
- **Activity:** Proces realizácie platby, od zadania údajov po potvrdenie transakcie.

## 4. Správa knižnice
- **Use Case:** Požičanie knihy, vrátenie knihy, pridanie novej knihy, registrácia člena.
- **Class:** `Kniha`, `Člen`, `Knižník`, `Požičanie`.
- **Stavový:** Stav knihy, ako `Dostupná`, `Vypožičaná`, `Rezervovaná`.
- **Activity:** Proces vypožičania knihy od výberu až po vrátenie.

## 5. Systém správy zdravotných záznamov
- **Use Case:** Registrácia pacienta, záznam návštevy, predpis liekov, plánovanie kontrol.
- **Class:** `Pacient`, `Lekár`, `Záznam o návšteve`, `Predpis`.
- **Stavový:** Stavy pacienta, ako `Registrovaný`, `Na liečbe`, `Vyliečený`.
- **Activity:** Proces vytvorenia zdravotného záznamu, od diagnostiky po liečbu.

## 6. Systém riadenia študentov
- **Use Case:** Registrácia študenta, zápis na predmet, zadanie známok, vydávanie certifikátov.
- **Class:** `Študent`, `Predmet`, `Skúška`, `Zamestnanec školy`.
- **Stavový:** Stav študenta, ako `Registrovaný`, `Aktívny`, `Absolvent`.
- **Activity:** Proces zápisu študenta na predmet a získavanie hodnotenia.

## 7. Systém online učenia (E-learning)
- **Use Case:** Registrácia, prihlásenie do kurzu, absolvovanie lekcií, ukončenie kurzu.
- **Class:** `Používateľ`, `Kurz`, `Lekcia`, `Certifikát`.
- **Stavový:** Stavy kurzu, ako `Otvorený`, `Prebiehajúci`, `Dokončený`.
- **Activity:** Proces absolvovania kurzu od registrácie po získanie certifikátu.

## 8. Systém správy úloh (Task Management)
- **Use Case:** Vytvorenie úlohy, aktualizácia úlohy, priradenie úlohy, ukončenie úlohy.
- **Class:** `Úloha`, `Používateľ`, `Projekt`, `Komentár`.
- **Stavový:** Stav úlohy, ako `Nová`, `Priradená`, `Dokončená`.
- **Activity:** Proces priradenia úlohy a jej dokončenia.

## 9. Systém na rezerváciu leteniek
- **Use Case:** Rezervácia letenky, zrušenie rezervácie, kontrola letu, online check-in.
- **Class:** `Letenka`, `Cestujúci`, `Let`, `Rezervácia`.
- **Stavový:** Stav rezervácie, ako `Rezervovaná`, `Zaplatená`, `Zrušená`.
- **Activity:** Proces rezervácie letenky od výberu letu po potvrdenie rezervácie.

## 10. Personálny systém
- **Use Case:** Registrácia zamestnanca, plánovanie zmien, správa pracovného času.
- **Class:** `Zamestnanec`, `Oddelenie`, `Plán zmien`, `Výplata`.
- **Stavový:** Stav zamestnanca, ako `Aktívny`, `Na dovolenke`, `Vypovedaný`.
- **Activity:** Proces schvaľovania dovolenky.

## 11. Systém rezervácie reštaurácie
- **Use Case:** Rezervácia stola, úprava rezervácie, zrušenie rezervácie, objednávka jedla.
- **Class:** `Rezervácia`, `Stôl`, `Zákazník`, `Objednávka`.
- **Stavový:** Stavy rezervácie, ako `Vytvorená`, `Potvrdená`, `Zrušená`.
- **Activity:** Proces rezervácie stola a následná objednávka jedla.

## 12. Systém predaja vstupeniek
- **Use Case:** Prehliadanie udalostí, nákup vstupeniek, storno vstupenky, kontrola vstupu.
- **Class:** `Vstupenka`, `Udalosť`, `Zákazník`, `Platba`.
- **Stavový:** Stav vstupenky, ako `Rezervovaná`, `Zaplatená`, `Použitá`.
- **Activity:** Proces nákupu vstupenky od výberu udalosti po platbu.

## 13. Systém sledovania zásielok
- **Use Case:** Vytvorenie zásielky, sledovanie zásielky, doručenie zásielky.
- **Class:** `Zásielka`, `Kuriér`, `Zákazník`, `Sklad`.
- **Stavový:** Stav zásielky, ako `Na sklade`, `Na ceste`, `Doručená`.
- **Activity:** Proces sledovania a doručenia zásielky.

## 14. Systém riadenia skladu
- **Use Case:** Príjem tovaru, uskladnenie, vyskladnenie, kontrola zásob.
- **Class:** `Tovar`, `Sklad`, `Dodávateľ`, `Objednávka`.
- **Stavový:** Stav tovaru, ako `Na sklade`, `Rezervovaný`, `Vyskladnený`.
- **Activity:** Proces vyskladnenia tovaru.

## 15. Systém na správu udal
- **Use Case:** Organizácia udalosti, registrácia účastníka, zasielanie pozvánok, zrušenie udalosti.
- **Class:** `Udalosť`, `Účastník`, `Organizátor`, `Pozvánka`.
- **Stavový:** Stavy udalosti, ako `Naplánovaná`, `Prebiehajúca`, `Zrušená`.
- **Activity:** Proces registrácie a účasti na udalosti.
