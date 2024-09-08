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

## Konštanty 

V určitých prípadoch môžeme chcieť mať premenné s konštantnou hodnotou, ktoré by sa nemali v priebehu programu meniť. Také premenné sa nazývajú konštanty (constants).

Aby sme zamedzili nechcenej zmene hodnoty konštanty, môžeme dátový typ premennej označiť kľúčovým slovom const, ktorý umiestnime pred1 názov dátového typu. Pokiaľ by sme sa snažili o zmenu premennej s takýmto dátovým typom, prekladač nám to nedovolí.

```csharp
const int a = 5;
a = a + 1; // chyba nejde preložiť 
```
### Dôvod používania konštant

V programoch niekedy opakovane používame konštantné hodnoty, ktoré majú pevne danú hodnotu. Pri čítaní zdrojového kódu nemusí byť jasné, čo také hodnoty znamenajú (v takom prípade sa hanlivo označujú ako "magické konštanty"). 

Aby sme takéto hodnoty pomenovali, môžeme ich uložiť do konštantnej premennej. Pri čítaní programu potom bude zrejmé, čo reprezentujú. Porovnajte variant s nepopísanými číselnými hodnotami:

```csharp
float vypocitaj_cenu(float cena) {
    return cena * (1 + 0.21);
}
float vypocitaj_odvod(float celkova_cena, bool dph) {
    if (dph) {
        return celkova_cena * 0.21;
    } else {
        return 0;
    }
}
```
Varianta využívajúca pomenovanie konštanty 

```csharp
const float DPH = 0.21; 

float vypocitaj_cenu(float cena) {
    return cena * (1 + DPH);
}
float vypocitaj_odvod(float celkova_cena, bool dph) {
    if (dph) {
        return celkova_cena * DPH;
    } else {
        return 0;
    }
}
```
Druhá varianta kódu je jasne čitatelnejšia 

# Zložený zápis 

Často potrebujeme hodnotu premennej iba trochu poupraviť, a nie do nej vyložene zapísať novú hodnotu. Bežná je napríklad operácia zvýšenia hodnoty premennej o 1 (tzv. inkrementácia premennej). Na to môžeme použiť tento príkaz:

```csharp
pocet = pocet + 1; // zvýšenie hodnoty premennej o `pocet` o 1
```
jedné o zdĺhavý proces, jazyk nám ponúka zložený zápis (compound assignment) 

- [ ] **+=**
- [ ] **-=**
- [ ] ***=**
- [ ] **/=**

Príklad : 

```csharp
int pocet = 0;
pocet += 1;   // rovnaké ako pocet = pocet + 1;
pocet *= 3;   // rovnaké ako pocet = pocet * 3; 

```
# Inkrementácia a dekriminácia 

Špeciálnym prípadom zloženého zápisu je tzv. inkrementácia (zvýšenie hodnoty premennej o jedničku) a dekrementácia (zníženie hodnoty premennej o jedničku). Tieto operácie sú tak časté, že C# obsahuje špeciálne "skratky" na ich vykonanie. Aby to nebolo také jednoduché, tak tieto skratky existujú v dvoch variantoch:

  - [ ] Postfixová: <premenná>++. Tento výraz sa najprv vyhodnotí ako hodnota danej premennej, a potom (vykoná vedľajší efekt, ktorý) zvýši hodnotu premennej o jedničku. Skúste uhádnuť, čo vypíše nasledujúci program:
        
   ```csharp
int a = 1;
int b = a++;
```
  - [ ] Prefixová: ++<premenná>. Tento výraz najprv zvýši hodnotu premennej a až potom sa vyhodnotí ako (nová, už zvýšená) hodnota danej premennej. Skúste uhádnuť, čo vypíše nasledujúci program:
        
```csharp
int a = 1;
int b = ++a;
```
Dekriminácia sa chová totožne ako inkriminácia, len s tým rodielom, že sa použije --         

# Pomenovanie premenných 

# Pravidlá pre Pomenovanie Premenných v C#

V C# existujú určité pravidlá pre pomenovanie premenných:

1. **Premenné sa nesmú volať rovnako ako kľúčové slová**: Inak by prekladač nevedel rozlíšiť, čo je názov premennej a čo kľúčové slovo (napríklad `int int;`).

2. **Názov premennej môže obsahovať iba malé (a-z) a veľké (A-Z) písmená anglickej abecedy, číslice (0-9) a podčiarknutie (_)**.

3. **Názov premennej nesmie začínať číslicou**: Tj. `5x` nie je validný názov premennej.

## Dôležité Praktiky pri Pomenovaní Premenných

V programoch je nutné neustále priraďovať názvy, čo zďaleka nie je také jednoduché, ako sa môže na prvý pohľad zdať. Okrem vyššie uvedených pravidiel je vhodné voliť názvy tak, aby boli prehľadné pre vás (a ostatných programátorov, ktorí váš zdrojový kód budú čítať). Názvy premenných ako `a` alebo `x` sú nič nehovoriace a kód s podobnými názvami je potom zložitejšie pochopiť.

### Porovnanie Kódu s Rôznymi Názvami Premenných

Porovnajte nasledujúce dva úseky kódu, ktoré sa líšia iba v použitých názvoch premenných:

#### Príklad 1: Nezrozumiteľné názvy
```csharp
int a = 5;
int b = 10;
int c = a + b;

```
VS

```csharp
int zakladna_cena = 1337;
int  zakladna_cena =  zakladna_cena - zľava;
int finalna_cenaa = zlavnena_cena * dph;
```
# Viacslovne názvy

# Štylistické Konvencie pre Názvy v C#

Existuje niekoľko zabehnutých štylistických spôsobov na zápis názvov v C, ktoré obsahujú viac slov. Tu je zoznam najpoužívanejších konvencií:

1. **Camel Case**: `mójUcet`, `prvýKlikUzivatele`
   - Prvý znak slova je malý, nasledujúce slová začínajú veľkým písmenom.
   
2. **Pascal Case**: `MójUcet`, `PrvýKlikUzivatele`
   - Všetky slová začínajú veľkým písmenom.

3. **Snake Case**: `mój_ucet`, `prvý_klik_uzivatela`
   - Slová sú oddelené podčiarknutím.

4. **Screaming Snake Case**: `MUJ_UCET`, `PRVNI_KLIK_UZIVATELE`
   - Všetky písmená sú veľké a slová sú oddelené podčiarknutím.

## Používanie Štylov v C# 

Rôzne konštrukcie v C môžu využívať rôzne štýly. Napríklad:

- **Snake Case** je častou konvenciou pre názvy premenných a funkcií.
- **Pascal Case** je častou konvenciou pre názvy štruktúr.

Ktorý štýl budete používať záleží na vašej osobnej preferencii, ale dôležité je najmä držať sa jednotného štýlu a nekombinovať rôzne štýly (pre rovnaký typ konštrukcií) v jednom programe.

# Dátové typy

Pamäť počítača pracuje s jednotlivými bytmi, avšak pre ľudí je žiaduce používať popis dát v pamäti na oveľa vyššej úrovni abstrakcie, aby sa nám o dátach jednoduchšie premýšľalo. Pokiaľ programujeme textový editor, chceme sa baviť o znakoch, odsekoch, fontoch či farbách, pokiaľ programujeme počítačovú hru, chceme sa baviť o zbraniach, brnení, kúzlach či pixeloch.

Presne na to slúžia `dátové typy`, ktoré popisujú, ako budeme interpretovať konkrétne hodnoty daného typu v pamäti, koľko bytov budú zaberať a aké operácie nad nimi budeme môcť vykonávať. Jazyk Najprv sa pozrieme na niekoľko dátových typov, ktoré sú vstavané v jazyku C#, a neskôr si ukážeme, ako si vytvoriť svoje vlastné dátové typy.

# Celočíselné datové typy

# Celočíselné dátové typy v C#

V jazyku C# sa bežne používajú celočíselné dátové typy na prácu s celými číslami. Tieto typy majú rôznu veľkosť v bajtoch, čo určuje rozsah hodnôt, ktoré môžu obsahovať. Tu je prehľad základných celočíselných typov v C#:

## Dátové typy a ich rozsahy

| Názov      | Počet bajtov | Rozsah hodnôt                              | Znamienko     |
|------------|--------------|-------------------------------------------|---------------|
| `byte`      | 1            | 0 až 255                                  | Bez znamienka |
| `sbyte`     | 1            | -128 až 127                               | So znamienkom |
| `short`     | 2            | -32 768 až 32 767                         | So znamienkom |
| `ushort`    | 2            | 0 až 65 535                               | Bez znamienka |
| `int`       | 4            | -2 147 483 648 až 2 147 483 647           | So znamienkom |
| `uint`      | 4            | 0 až 4 294 967 295                       | Bez znamienka |
| `long`      | 8            | -9 223 372 036 854 775 808 až 9 223 372 036 854 775 807 | So znamienkom |
| `ulong`     | 8            | 0 až 18 446 744 073 709 551 615         | Bez znamienka |

**Poznámka:** V C# sú všetky celočíselné typy implicitne so znamienkom, okrem `byte`, `ushort`, `uint` a `ulong`, ktoré sú bez znamienka.

## Operácie s celočíselnými typmi

V C# je možné vykonávať bežné aritmetické operácie s celočíselnými typmi:

- **Sčítanie:** `a + b`
- **Odčítanie:** `a - b`
- **Násobenie:** `a * b`
- **Delenie:** `a / b` (celé číslo, zaokrúhlené nadol)
- **Zvyšok po delení:** `a % b`

### Pozor na pretečenie

Pri operáciách s celočíselnými typmi môže dôjsť k pretečeniu (overflow), ak výsledok operácie presiahne maximálnu alebo minimálnu hodnotu typu. V C# môžete použiť metódy ako `checked` a `unchecked` na riadenie toho, ako sa pretečenie bude spracovávať.

### Bitové operácie

C# tiež podporuje bitové operácie:

- **AND:** `a & b`
- **OR:** `a | b`
- **XOR:** `a ^ b`
- **NOT:** `~a`
- **Bitový posun vľavo:** `a << b`
- **Bitový posun vpravo:** `a >> b`

## Dôležité poznámky

- **Implicitná konverzia:** C# vykonáva implicitnú konverziu medzi kompatibilnými celočíselnými typmi, ale môže byť potrebné vykonať explicitnú konverziu.
- **Priorita operátorov:** Rovnako ako v matematike, operátory majú rôznu prioritu, ktorá ovplyvňuje poradie, v ktorom sa operácie vykonávajú. Používajte zátvorky na jasné určenie poradia operácií.

Tento prehľad by mal poskytnúť základný prehľad o celočíselných typoch a operáciách v C#.

# Desatinné číselné typy v C#

Ak chcete vykonávať výpočty s desatinnými číslami, môžete využiť dátové typy s tzv. plávajúcou desatinnou čiarkou (floating point numbers). Hodnoty týchto dátových typov umožňujú pracovať s číslami, ktoré sa skladajú z celej a desatinnej časti. Tieto čísla dokážu reprezentovať veľmi malé i veľmi veľké hodnoty, avšak za cenu nižšej presnosti desatinnej časti.

V C# sú dva základné zabudované dátové typy pre prácu s desatinnými číslami, ktoré sa líšia veľkosťou (a teda aj presnosťou, s ktorou dokážu reprezentovať desatinné čísla). Oba typy sú znamienkové:

## Dátové typy a ich rozsahy

| Názov    | Počet bajtov | Rozsah hodnôt                         | Presnosť        | Znamienko     |
|----------|--------------|--------------------------------------|-----------------|---------------|
| `float`  | 4            | [-3.4 × 10^38; 3.4 × 10^38]          | ~7 des. miest   | So znamienkom |
| `double` | 8            | [-1.7 × 10^308; 1.7 × 10^308]        | ~16 des. miest  | So znamienkom |

Slovo `double` pochádza z pojmu "double precision" (dvojitá presnosť). Typ `float` sa niekedy označuje ako "single precision" (jednoduchá presnosť).

## Používanie desatinných čísel

Ak chcete v programe vytvoriť výraz dátového typu `double`, stačí napísať desatinné číslo (ako desatinný oddeľovač sa používa bod, nie čiarka): `10.5`, `-0.73`. Ak chcete vytvoriť výraz typu `float`, pridajte za číslo znak `f`: `10.5f`, `-0.73f`.

## Formátovaný výstup desatinných čísel

Ak chcete vypísať hodnotu dátového typu `float` alebo `double`, môžete použiť formátovací reťazec:

```csharp
Console.WriteLine("Desatinné číslo: {0:F}", 1.0);
```

# Pravdivostní typy

Posledným základným dátovým typom, ktorý si ukážeme, je pravdivostný typ Booleovskej logiky. Hodnoty tohto dátového typu majú iba dve možné varianty - pravda (true) alebo nepravda (false). Tento typ sa hodí najmä pre rôzne logické operácie, napríklad porovnávanie hodnôt (Je a menšie ako b? - áno/nie).

V C# sa Booleovský dátový typ nazýva _Bool. Avšak tento názov je celkom krkolomný, obvykle sa preto používa skôr názov bool.

```csharp
using System;

class Program
{
    static void Main()
    {
        bool venkuJeHezky = true;
        bool uprJeSlozite = false;

        // Vytlačiť hodnoty priamo
        Console.WriteLine(venkuJeHezky ? 1 : 0);
        Console.WriteLine(uprJeSlozite ? 1 : 0);
    }
}

```

Ako je možné v ukážke vyššie vidieť, true reprezentuje pravdivý Booleovský výraz a false nepravdivý Booleovský výraz a bool hodnoty je možné vytlačiť na výstup rovnakým spôsobom ako celočíselné hodnoty.1 Hodnoty Booleovského typu obvykle zaberajú v pamäti jeden byte.

# Logické operácie

## Logické operace

V (Booleovské) logice existují tři základní operátory:

- **Logický součin (AND):** Platí X a zároveň Y.
- **Logický součet (OR):** Platí X nebo Y.
- **Logická negace (NOT):** Neplatí X.

### Operátory v C#

V jazyce C# se tyto logické operace provádějí pomocí následujících operátorů:

- **AND:** `&&`
- **OR:** `||`
- **NOT:** `!`

### Příklad použití v C#

```csharp
using System;

class Program
{
    static void Main()
    {
        bool x = true;
        bool y = false;

        // Logické operace
        bool andResult = x && y; // true && false -> false
        bool orResult = x || y;  // true || false -> true
        bool notResult = !x;     // !true -> false

        // Výpis výsledků
        Console.WriteLine($"AND (x && y): {andResult}");
        Console.WriteLine($"OR (x || y): {orResult}");
        Console.WriteLine($"NOT (!x): {notResult}");
    }
}
```
## Pravdivostná tabuľka

Pre pripomenutie, tu je pravdivostná tabuľka pre logické operátory:

| X     | Y     | X && Y | X || Y | !X   |
|-------|-------|--------|--------|------|
| false | false | false  | false  | true |
| false | true  | false  | true   | true |
| true  | false | false  | true   | false|
| true  | true  | true   | true   | false|

Táto tabuľka zobrazuje výsledky logických operácií AND, OR a NOT pre všetky možné kombinácie vstupných hodnôt `X` a `Y`.

## Porovnávanie hodnôt

Pri programovaní často potrebujete porovnať hodnoty medzi sebou:

- Má Jarda viac bodov než Kamil?
- Má používateľovo heslo viac než 5 znakov?
- Má Lenka na účte aspoň 100 dolárov?

Na tento účel slúži šesť základných porovnávacích operátorov:

- **Rovná sa:** `==`
  > Pozor na rozdiel medzi `=` (priradenie hodnoty) a `==` (porovnanie dvoch hodnôt). Zámena týchto dvoch operátorov je častou začiatočníckou chybou a môže viesť k ťažko nájdeným chybám.
- **Nerovná sa:** `!=`
- **Väčšie:** `>`
- **Väčšie alebo rovné:** `>=`
- **Menšie:** `<`
- **Menšie alebo rovné:** `<=`

Porovnávať medzi sebou môžete akékoľvek hodnoty dvoch rovnakých dátových typov. Výsledkom porovnania je výraz dátového typu `bool`.

### Príklad v C#

```csharp
using System;

class Program
{
    static void Main()
    {
        int jardaPoints = 10;
        int kamilPoints = 8;
        string password = "mypassword";
        int accountBalance = 150;

        // Porovnanie hodnôt
        bool isJardaHigher = jardaPoints > kamilPoints;        // 10 > 8 -> true
        bool isPasswordLongEnough = password.Length > 5;       // "mypassword".Length > 5 -> true
        bool hasSufficientBalance = accountBalance >= 100;     // 150 >= 100 -> true

        // Výpis výsledkov
        Console.WriteLine($"Jarda má viac bodov než Kamil: {isJardaHigher}");
        Console.WriteLine($"Heslo má viac než 5 znakov: {isPasswordLongEnough}");
        Console.WriteLine($"Lenka má na účte aspoň 100 dolárov: {hasSufficientBalance}");
    }
}
```

## Pozor na použitie operátorov

Dávajte si ovšem pozor na to, že iba operátory `==` a `!=` môžete použiť univerzálne na všetky dátové typy. Napríklad použiť operátor `<` pre porovnanie dvoch Booleovských hodnôt obvykle nedáva veľký zmysel. Operátory `<`, `<=`, `>` a `>=` sú obvykle využívané iba pre porovnanie čísel.

## Kombinovanie porovnávania s logickými operátormi

Porovnávanie hodnôt môžete kombinovať s logickými operátormi pre vyhodnocovanie komplexných pravdivostných výrazov:

### Príklad v C#

```csharp
using System;

class Program
{
    static void Main()
    {
        int age = 25;
        double balance = 120.50;
        bool hasJob = true;

        // Kombinovanie porovnávania s logickými operátormi
        bool isEligible = (age > 18 && balance >= 100) || hasJob;

        // Výpis výsledku
        Console.WriteLine($"Osoba je spôsobilá: {isEligible}");
    }
}
```
## Tabuľka logických operátorov

Pre lepšiu orientáciu je tu tabuľka s logickými operátormi. Typ výsledku týchto operátorov je vždy `bool`.

| Operátor | Popis                           | Príklad                     |
|----------|---------------------------------|-----------------------------|
| `&&`     | Logický súčin (AND)              | `a == b && c >= d`          |
| `||`     | Logický súčet (OR)               | `a < b || c == d`           |
| `!`      | Logická negácia (NOT)            | `!(a > b && c < d)`         |
| `==`     | Rovná sa                         | `a == 5`                    |
| `!=`     | Nerovná sa                       | `a != 5`                    |
| `>`      | Väčší než                        | `a > 5`                     |
| `>=`     | Väčší alebo rovný                | `a >= 5`                    |
| `<`      | Menší než                        | `a < 5`                     |
| `<=`     | Menší alebo rovný                | `a <= 5`                    |

## Skrátené vyhodnocovanie

Pri vyhodnocovaní Booleovských výrazov s logickými operátormi sa v jazyku C používa tzv. skrátané vyhodnocovanie (short-circuit evaluation). Napríklad, ak sa vyhodnocuje výraz `a || b`, môže dôjsť k nasledujúcej situácii:

1. Počítač vykonáva vyhodnocovanie krok po kroku, tj. najprv vyhodnotí `a`.
2. Ak má výraz `a` hodnotu `true`, je už jasné, že celý výraz `a || b` bude mať hodnotu `true`.
3. Vyhodnotenie výrazu `b` sa teda nevykoná, pretože je to zbytočné.

Toto správanie môže zrýchliť vykonávanie programu, pretože preskočí vykonávanie zbytočných príkazov. Môže to však tiež spôsobiť neočakávané chyby. Ak by napríklad vyhodnocovanie výrazu `b` obsahovalo nejaké vedľajšie efekty, ktoré sa prejavia pri jeho vykonaní (napríklad zmena hodnoty v pamäti), môže byť problém, ak sa vyhodnotenie tohto výrazu úplne preskočí. Ak si pamätáte na inkrementáciu, tá je jedným z prípadov výrazov, ktoré majú vedľajší efekt (zmenu hodnoty premennej).

# Riadenie toku 

Ak by počítače program vždy iba vykonávali od začiatku do konca a vykonávali by zakaždým tie isté operácie, neboli by veľmi užitočné. Síce by zvládli niečo rýchlo vypočítať, ale už by sa nevedeli rozhodnúť, akú operáciu majú vykonať, alebo vykonať operáciu opakovane, čo sú veľmi užitočné vlastnosti.

Inštrukcie programu sa bežne vykonávajú ("tečú") jedna po druhej ("zhora nadol"). Jazyk C# obsahuje príkazy na tzv. riadenie toku (control flow), ktoré môžu toto vykonávanie inštrukcií ovplyvniť:

## Podmienky
Podmienky umožňujú vykonať kus kódu iba vtedy, ak platí nejaký výraz (Booleovského typu). Vďaka tomu sa program môže rozhodnúť, či má nejakú operáciu vykonať alebo nie, v závislosti od vstupu.

## Cykly
Cykly umožňujú vykonávať kus kódu opakovane. Vďaka tomu môžeme napríklad vykonať nejakú operáciu pre všetky prvky zo vstupu programu alebo ju vykonávať, až kým nedôjde k splneniu nejakej podmienky.

Aj keď sa to možno nezdá, tak použitie výrazov, premenných, podmienok a cyklov bohato stačí na to, aby ste boli schopní napísať ľubovoľný počítačový program. Pomocou týchto troch jednoduchých konštrukcií by ste tak teoreticky mohli vytvoriť napríklad textový editor, hru alebo aj celý operačný systém.

Avšak, ak by sme využívali iba tieto konštrukcie, vo väčších programoch by bolo náročné sa orientovať a boli by dosť neefektívne. V nasledujúcich sekciách sa preto dozviete o niekoľkých ďalších konštrukciách, ktoré vám môžu programovanie uľahčiť.







