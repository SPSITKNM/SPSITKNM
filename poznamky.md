# Úvod do programovania 

V tomto repozitári pre predemt PRO pre 4.ročník nájdete stručnú oporu vo formáte skrípt k preberanej problematike na hodinách PRO... Ďalšou podstatnou oporou je YT kanál nášho predmetu na ktorom teoretické poznatky aplikujeme v praxi tak aby študent bol schopný zvládnuť úlohy a projekty v priebehu roka... 

## Čo nás čaká v najbližších hodinách ? 

- [ ] **Syntax** 
- [ ]  Výrazy 
- [ ] Premenné 
  - [ ] Čo je to Stack a Heap, kde je aká premenná ukladaná ?
  - [ ] Globálne premenné v jazykoch ako je C a C++ kde je rozdiel oproti jazyku C#
  - [ ] Functionl, Curly Bracet notácia a assigment notácia.
  - [ ] LifeTime, živnostnosť premennej, čo je to Garbage collector
- [ ] Predefinované dátové typy
  - [ ] Celočíselné typy
  - [ ] Desatinné typy
  - [ ] Pravdivostné typy
  - [ ] Text
    - [ ] ASCI, Znaky, Reťazec
  - [ ] Konverzie
  - [ ] Auto pri C++ vs Var pri C#
  - [ ] Vlastné dátové typy
  - [ ] Práca s pameťou, padding, zarovananie
- [ ] Operácie na dátach
  - [ ] Aritmetické operácie na číslach
  - [ ] Operácie na reťazcoch
  - [ ] Logické operácie
- [ ] Riadenie toku
  - [ ] Podmienky
  - [ ] Cykly
- [ ] Funckie
- [ ] Pole
  - [ ] Statické
  - [ ] Dynamické
  - [ ] Viacrozmerné

# Syntax

C,C++ či C# ( V tychto skriptách sa Pythonu venovať nebudeme, ten bude implementovaný na hodinách tak aby nás nemiatol ) ma svoje pravidlá, napr v slovenčine musíme dodržať nijaký formát pravidiel aby nám bol text pochopiteľný... takisto v jazykoch C,C++, C# musíme tieto náležitosti dodržať... Poďme sa teda spoločne pozrieť na najkradší program v jazyku C#

Jednoduchý program, ktorý vracia `0` na indikaciu úspešného dokončenia.

```csharp
class Program
{
    static int Main()
    {
        return 0;
    }
}

```
## Komentáre 

Aby sme mohli v nasledujúcich sekciách popisovať kusy kódu, ukážeme si teraz komentáre. Ide o text v zdrojovom kóde, ktorý je určený pre programátorov, a nie pre prekladač, ktorý ich úplne ignoruje. Bez komentárov by sme nemohli do zdrojového kódu dodávať poznámky, pretože prekladač by inak mal snahu ich interpretovať ako C# kód. Komentáre v kóde zvyčajne spoznáte ľahko, pretože ich váš editor bude vykresľovať inou farbou ako zvyšok kódu.

Na našich hodinách budeme používať extension pre farebnosť so znakmy ako ! či ? 

## Jednoriadkový komentár

```csharp
class Program
{
    static void Main()
    {
        // Toto je jednoriadkový komentár
        Console.WriteLine("Hello, World!"); // Tento komentár je za kódom
    }
}
```
## Viacriadkový komentár 

```csharp
class Program
{
    static void Main()
    {
        /*
         Toto je viacriadkový komentár.
         Môže sa použiť na dlhšie vysvetlenia kódu.
        */
        Console.WriteLine("Hello, World!");
    }
}
```
## Kľúčové slová 

Kľúčové slová (keywords) sú vstavané názvy, ktorým prekladač priraďuje špeciálny význam. V textovom editore ich typicky spoznáte tak, že budú zafarbené inou farbou ako názvy vytvorené programátorom. Napríklad v tomto kóde sú int a return kľúčové slová:

```csharp
class Program
{
    static int Main()
    {
        return 0;
    }
}

```
## Špeciálne znaky

Pri programovaní (ako už v C, tak aj v iných jazykoch) budete používať množstvo symbolov, ktoré bežne asi často nevyužívate (napríklad [, ], {, }, <, >, =, %, #, &, *, ;, \, ", '). Obzvlášť ak pre programovanie budete používať českú klávesnicu, je dobré si zo začiatku nájsť nejaký ťahák (napr. tento), aby ste nemuseli zakaždým zdĺhavo spomínať, na ktorom klávese sa daný znak nachádza.

# Vykonávanie programu 

Ako už vieme, programy sú sekvencie príkazov pre počítač, ktorý ich vykonáva inštrukciu po inštrukcii (resp. riadok po riadku). Akonáhle počítač vykoná jeden riadok vášho programu, tak skočí na riadok nižšie, kým nedôjde na koniec programu. 

## Výrazy 

Ako už vyplýva z jeho názvu, hlavnou funkciou počítača je niečo počítať. Jedným zo základných konštrukcií prog jazyka C# (aj iných programovacích jazykov, ktoré si na hodinách ukážeme) tak je možnosť vypočítať rôzne hodnoty. Niečo, čo sa dá vypočítať (tak, aby výsledkom bola nejaká hodnota), sa nazýva výraz (expression). Príkladom asi najjednoduchšieho výrazu je číslo, napr. 5. Takýto výraz už nie je nutné ďalej vyhodnocovať, jeho hodnota je jednoducho 5. Ak v programe použijete priamo hodnotu nejakého čísla (popr. niečoho iného, ​​ako uvidíme neskôr), tak sa takýto výraz označuje ako literál (literal).

V C# môžeme s výrazmi vykonávať rôzne operácie pomocou operátorov. Môžeme napríklad použiť operátor + s dvoma výrazmi, čím vznikne zložitejší výraz: 5 + 5, ktorý sa v programe vyhodnotí na hodnotu 10. O operátoroch si viac povieme v kapitole o dátových typoch.

## Výpis výrazov 

Aby ste si zo začiatku mohli jednoducho zobraziť hodnoty výrazov, tak si ukážeme kód, pomocou ktorého môžete vypísať text na výstup programu (do terminálu). Na výpis textu môžete použiť jednu z týchto metód : 

V C#, je viacero metód ako vypísať výraz do konzoly. Tu je zhrnutie tých najčastejších :

### 1. `Console.WriteLine()`
Vytlačí zadanú hodnotu a presunie kurzor na ďalší riadok.

**Príklad 1**:
```csharp
Console.WriteLine("Hello, World!");
```
### 2. `Console.Write()`
Vytlačí zadanú hodnotu bez presunu kurzora na nový riadok. Ďalší výstup bude pokračovať na rovnakom riadku.

**Príklad 3**:
```csharp
Console.Write("Hello, ");
Console.Write("World!");
```
### 3. `String.Format()`
Vloží premenné alebo výrazy do reťazca. Často sa kombinuje s Console.WriteLine().

**Príklad 4**:
```csharp
int age = 25;
Console.WriteLine(String.Format("I am {0} years old.", age));
```
### 4. `Pužitie string interpolacie`
**Príklad 5**:
```csharp
int age = 25;
Console.WriteLine($"I am {age} years old.");

```
# Premenné 

# Premenné v Programovaní

Aby programy mohli riešiť nejaký úkol, tak si skoro vždy musím niečo zapamätať. K tomu slúži tzv. **premenné** (variables). Premenné nám umožňujú pracovať s pamäťou počítača (RAM) intuitívnym spôsobom - časť pamäte si pomenujeme nejakým menom a ďalej sa na ňu týmto menom odkazujeme. Do tejto zmeny potom môžeme uložiť nejakú hodnotu, čím si ju počítač "zapamätá". Túto hodnotu môžeme neskôr v programe prečítať alebo ju zmeniť.

## Príklady použitia premenných:

1. **Webová aplikácia**: Číselná premenná si pamätá počet návštevníkov. Pri zobrazení stránok sa hodnota zvyšuje o 1.
   
2. **Hra**: Číselná premenná si pamätá počet životov hráčovej postavy. Ak dôjde k zásahu postavy nepriateľom, tak sa počet životov zníži o poškodenie nepriateľovej zbrane. Ak hráč získa liekárničku, tak sa počet jeho životov opäť zvýši.

3. **Terminál**: Premenná reprezentujúca znaky si pamätá text, ktorý bol zadaný na klávesnici.

## Definícia 

Premenné sú z najzákladnejších a najčastejšie používaných stavebných kameňov väčšinou programov, počas semestra sa s nimi budeme neustále setkávať. Nie je tak náhodou, že jeden z najzákladnejších príkazov v C je práve vytvorenie proměnné. Tím povieme počítač, aby vyčlenil (tzv. naalokoval) miesto v pamäti, ktoré si v programe nejako pomenujeme a ďalej sa naňho pomocou jeho mien môžeme odkazovať1.

Takto vypadá príkaz definicie (vytvorený) premenne s názvom vek s dátovým typom int : 

```csharp
int age;
```
Hneď teraz nadefinujeme, tak z nej môžeme buď čítať alebo zapisovať pamäť, ktorú táto premenná reprezentuje, podľa jej názvu (zde vek).

## Dátový typ 

int pred promennými udáva jej datový typ, o ktorom pojednáva nasledujúcu kapitolu. Prozatím si řekněme, že int je zkratka pro integer, tedy celé číslo. Tím říkáme programu, že má túto premennú (resp. pamäť, ktorú premenná reprezentuje) interpretovať ako celé číslo sa známym.

## Inicializácia 

Do premennej by sme mali pri jej vytvorení rovno uložiť nejaký výraz, ktorý musí byť rovnakého dátového typu ako je typ premennej:

```csharp
int a = 10;
int b = 10 + 15;
```
Obecná syntax pre definíciu premennej je : 

```csharp
<dátový typ> <názov> = <výraz>;
```
! Nikdy nezabudnúť bodkočiarku na konci príkazu ! 

## Vždy inicializujte premenné 

Je naozaj dôležité do premennej vždy pri jej definícii priradiť nejakú úvodnú hodnotu. Pokiaľ to neurobíme, tak jej hodnota bude nedefinovaná (undefined). Čítanie hodnoty takejto nedefinovanej premennej spôsobuje nedefinované správanie (undefined behaviour, UB)2 programu. Pokiaľ k tomu dôjde, tak si prekladač s vaším programom môže urobiť, čo sa mu zachce, a váš program sa potom môže správať nepredvídateľne.

## Definícia viacerých premenných rovnakého typu

```csharp
<int x = 10, y = 20, z = 30;
```







