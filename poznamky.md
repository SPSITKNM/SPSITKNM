![image](https://github.com/user-attachments/assets/03175d24-e0a3-4a28-ae55-b5af2b9bb98d)# Úvod do programovania pre 4. ročník 

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

# Podmienky

V programoch sa často potrebujeme rozhodnúť, čo by sa malo stať v závislosti od hodnoty nejakého výrazu:

- Ak používateľ nakúpil tovar v poslednom týždni, pošli mu e-mail.
- Zadal používateľ správne heslo? Ak áno, presmeruj ho na jeho profil. Ak nie, zobraz chybové hlásenie.
- Aké má používateľ konto? Ak je kladné, vykresli ho zelenou farbou, ak je záporné, tak červenou a ak nulové, tak čiernou.

V jazyku C# môžeme vykonávať takéto rozhodnutia pomocou podmienených príkazov (`if` a `switch`), prípadne pomocou ternárneho operátora.

# Príkaz if v C#

Základným príkazom pre tzv. podmienené vykonanie kódu v C# je príkaz `if`:

```csharp
if (<výraz typu bool>) {
    // blok kódu
}
```
Ak sa výraz v zátvorke za `if` vyhodnotí ako `true` (pravda), tak sa vykoná blok kódu za zátvorkou a potom bude program ďalej pokračovať za príkazom if. Ak sa však výraz vyhodnotí ako `false` (nepravda), tak sa blok kódu za zátvorkou vôbec nevykoná.

V nasledujúcom programe skúste zmeniť výraz v zátvorkách za `if`, aby sa blok v podmienke vykonal:

```csharp
string heslo = "tajneheslo";

if (heslo.Length > 5) {
    Console.WriteLine("Heslo je dostatočne dlhé.");
}

```

Booleovské výrazy použité v podmienených príkazoch sa označujú ako podmienky (conditions), pretože podmieňujú vykonávanie programu.

Anglické slovo `if` znamená v slovenčine "Ak". Všimnite si, že kód vyššie môžete prečítať ako vetu: Ak je dĺžka hesla väčšia než päť, tak vykonaj kód v bloku.

# Prevod medzi rôznymi dátovými typmi

Niekedy je potrebné previesť hodnoty medzi rôznymi dátovými typmi. Na tento účel slúži operátor pretypovania (cast operator), ktorý má syntax `(typ) výraz` a prevedie výraz na daný dátový typ. Napríklad `(short)1` prevedie výraz `1` z typu `int` na `short`. Je dobré si uvedomiť, čo sa môže stať pri prevode medzi rôznymi dátovými typmi:

## Oseknutie hodnoty pri menšom cieľovom dátovom type

Ak je cieľový dátový typ menší a prevádzanú hodnotu v ňom nemožno reprezentovať, dôjde k oseknutiu hodnoty. V dôsledku spôsobu reprezentácie hodnôt v počítači táto operácia zodpovedá zvyšku po delení:

```csharp
ushort a = 256;
byte b = (byte)a; // hodnota tohto výrazu je 0 (256 % 256)
```

# Vykonávanie alternatív v C#

Často v programe chceme vykonať práve jednu z dvoch (alebo viacerých) alternatív, opäť v závislosti od hodnoty nejakého výrazu (podmienky). To síce môžeme vykonať pomocou niekoľkých `if` príkazov za sebou:

```csharp
if (body > 90) { znamka = 1; }
if (body <= 90 && body > 80) { znamka = 2; }
if (body <= 80 && body > 50) { znamka = 3; }
```

To však môže byť často dosť zdĺhavé, pretože sa musíme v každej podmienke uistiť, že už nebola splnená predchádzajúca podmienka, inak by sa mohla vykonať viac než jedna alternatíva.

V C# môžeme pridať k príkazu `if` ďalší príkaz `else`, ktorý sa vykoná, iba ak podmienka if nie je splnená. Takto možno reťaziť viacero podmienok za sebou, kde v každej nasledujúcej podmienke vieme, že žiadna z predchádzajúcich nebola splnená:

```csharp
if (<výraz typu bool>) {
    // blok kódu
} else {
    // alternatívny blok
}
```
Ak za blok podmienky `if` pridáte `else`, program sa začne vykonávať za `else`, ak výraz podmienky nie je splnený. Za `else` môže nasledovať:

```csharp
if (body > 90) {
    // blok A
} else {
    // blok B
}
// X
```
Ak platí `body > 90`, vykoná sa blok A, ak nie, vykoná sa blok B. V oboch prípadoch bude program ďalej vykonávať kód od bodu X.

## Ďalšia podmienka if, ktorá je opäť vyhodnotená:

Takýchto podmienok môže nasledovať ľubovoľný počet:

```csharp
if (body > 90) {
    // blok A, viac než 90 bodov
} else if (body > 80) {
    // blok B, menej než 91 bodov, ale viac než 80 bodov
} else if (body > 70) {
    // blok C, menej než 81 bodov, ale viac než 70 bodov
}
// X

```
Takéto spojené podmienky sa vyhodnocujú postupne zhora nadol. Prvá podmienka `if`, ktorej výraz je vyhodnotený ako `true`, spôsobí, že sa vykoná blok tejto podmienky, a následne program pokračuje za celou spojenou podmienkou (bod X).

## Použitie else na konci:

Na koniec spojenej podmienky môžete pridať kľúčové slovo else s blokom bez podmienky. Tento blok sa vykoná iba v prípade, že žiadna z predchádzajúcich podmienok nie je splnená:

```csharp
if (body > 90) {
    // blok A, viac než 90 bodov
} else if (body > 80) {
    // blok B, menej než 90 bodov, ale viac než 80 bodov
} else {
    // blok C, menej než 81 bodov
}


```
Tento kód môžeme prečítať ako vetu: Ak je počet bodov vyšší než 90, vykonaj A. Ak nie, ale je vyšší než 80, vykonaj B. Inak vykonaj C.


# Príkaz `switch` v C#

V prípade, že by ste chceli vykonať odlišný kód v závislosti od hodnoty nejakého výrazu, a tento výraz (napr. hodnota premennej) môže nadobúdať väčšie množstvo rôznych hodnôt, môže byť zdĺhavé použiť množstvo `if` príkazov:

```csharp
if (a == 0) {
    ...
} else if (a == 1) {
    ...
} else if (a == 2) {
    ...
}
```
Ako skratka môže slúžiť príkaz switch. Ten má nasledujúcu syntax:

```csharp
switch (a) {
    case 0:
        // blok kódu
        break;
    case 1:
        // blok kódu
        break;
    case 2:
        // blok kódu
        break;
    default:
        // blok kódu
        break;
}
```
Tento príkaz vyhodnotí výraz v zátvorke za kľúčovým slovom `switch`. Ak sa v bloku kódu nachádza klauzula `case` s hodnotou zodpovedajúcou hodnote výrazu, program začne vykonávať blok kódu, ktorý nasleduje za touto klauzulou `case`. Potom program pokračuje sekvenčne až do konca bloku switch. Toto správanie sa nazýva `fallthrough`.

## Príklad

```csharp
int a = 5;

switch (a) {
    case 5:
        Console.WriteLine(52);
        break;
    case 6:
        Console.WriteLine(63);
        break;
}

```
Tento program vypíše `52`, pretože výraz má hodnotu `5`, takže program skočí na blok za klauzulou `case 5` a vykoná príkaz `Console.WriteLine(52)`;.

## Kľúčové slovo `default`

Do bloku príkazu `switch` je možné pridať blok označený ako `default`, na ktorý program skočí v prípade, že sa nenájde žiadna klauzula `case` s odpovedajúcou hodnotou:

```csharp
switch (a) {
    case 1:
        Console.WriteLine("Hodnota je 1");
        break;
    default:
        Console.WriteLine("Iná hodnota");
        break;
}
```
Ak hodnota premennej `a` nie je `1`, vykoná sa blok `default` a vypíše "Iná hodnota".

## Kľúčové slovo `default

Veľmi často chceme vykonať iba jeden blok kódu u jedného `case ` a nepokračovať ďalej až do konca celého bloku `switch `. Preto sa bežne za každým blokom case používa príkaz `break`, ktorý ukončí vykonávanie celého príkazu `switch`:

```csharp
switch (a) {
    case 0:
        Console.WriteLine("Nula");
        break;
    case 1:
        Console.WriteLine("Jedna");
        break;
    default:
        Console.WriteLine("Iná hodnota");
        break;
}

```
Ak hodnota premennej `a` je `0`, vykoná sa prvý blok a program následne ukončí príkaz `switch` príkazom `break`.

## Hodnota za case

Hodnota za kľúčovým slovom `case` musí byť konštantná, čo znamená, že musí byť známa už v čase prekladu programu, napríklad literál. Za `case` teda nemôže byť uvedený výraz obsahujúci názov premennej.

## Použitie príkazu switch

Použitie príkazu switch

Výraz v zátvorke za `switch` musí byť vstavaný dátový typ, v podstate sa tu dá použiť iba celé číslo. Nie je možné ho použiť napríklad na porovnávanie štruktúr či reťazcov. Jeho správanie môže byť tiež mätúce, ak sa za jednotlivými klauzulami `case` nepoužije príkaz break. Preto odporúčame na podmienené vykonávanie na začiatku používať skôr príkaz `if`.

## Ternárny operátor 

Preklad do slovenčiny:

Občas sa nám môže hodiť vytvoriť výraz, ktorý bude mať hodnotu jedného z dvoch konkrétnych výrazov, v závislosti od hodnoty nejakej podmienky. Napríklad, ak by sme chceli priradiť minimum z dvoch hodnôt do premennej, môžeme to napísať takto:

# Ternárny operátor v C#

Občas sa nám môže hodiť vytvoriť výraz, ktorý bude mať hodnotu jedného z dvoch konkrétnych výrazov, v závislosti od hodnoty nejakej podmienky. Napríklad, ak by sme chceli priradiť minimum z dvoch hodnôt do premennej, môžeme to napísať takto:

```csharp
int a = 1;
int b = 5;

int c = 0;
if (a < b) {
    c = a;
} else {
    c = b;
}
```

Všimnite si, že do premennej `c` ukladáme buď výraz `a` alebo výraz `b`, v závislosti od toho, aká je hodnota podmienky `a < b`.

Keďže je táto situácia relatívne častá a jej riešenie pomocou príkazu `if` je zdĺhavé, jazyk C# obsahuje skratku v podobe `ternárneho operátora`. Tento výraz má nasledujúcu syntax:

```csharp
<výraz X typu bool> ? <výraz A> : <výraz B>

```

Ak je výraz `X` pravdivý, ternárny operátor sa vyhodnotí ako hodnota výrazu `A`. V opačnom prípade sa vyhodnotí ako hodnota výrazu `B`.

## Príklad

Uhádnete, čo vypíše nasledujúci program?

```csharp
int a = 1;
int b = 5;
int c = (a < b) ? a : b;

Console.WriteLine(c);  // Výstup: 1

```

V tomto príklade ternárny operátor porovnáva hodnoty `a` a `b`. Ak je `a` menšie ako `b`, tak sa do premennej `c` priradí hodnota `a`. Inak sa priradí hodnota `b`.

# Cykly

Vo svojich programoch budete často chcieť vykonávať nejakú operáciu opakovane, napríklad:

- Pre každý záznam v databáze vypíš riadok do súboru.
- Pošli správu každému účastníkovi chatu.
- Načítavaj riadky zo súboru, pokiaľ nedôjdeš na koniec súboru.

Ak by sme vždy iba pridávali nové príkazy pod seba, tak, ako to zatiaľ poznáme, aby sme nejaký príkaz vykonali viackrát, tak by naše programy jednak boli pravdepodobne dosť dlhé. Pravdepodobne by sme neustále kopírovali („copy-pastovali“) veľmi podobný kód:

```csharp
Console.WriteLine("0");
Console.WriteLine("1");
Console.WriteLine("2");
```

čo by viedlo k neprehľadným programom. Ak by sme navyše našli v programe chybu, museli by sme ju opraviť na všetkých miestach, kam sme kód skopírovali.

Predstavte si, že chcete na výstup programu alebo do súboru vypísať napríklad tisíc rôznych riadkov textu.

Ani s kopírovaním kódu by sme si však nevystačili, ak by sme potrebovali vykonávať kód opakovane v závislosti na vstupe programu. Predstavte si situáciu, kedy nám užívateľ na vstup programu zadá číslo, koľkokrát má náš program vypísať nejaký riadok textu na výstup. Užívateľ sa pri každom spustení programu môže rozhodnúť pre iné číslo, 0, 1, 42, 1000. Program však zostáva stále rovnaký – už pri tvorbe (písaní) programu sa musíme rozhodnúť, koľko príkazov pre výpis do neho vložíme. Potom sa program preloží na spustiteľný súbor a už našu voľbu nemôžeme jednoducho zmeniť. Takýto program by sme teda zatiaľ (iba pomocou premenných a podmienok) nemali ako naprogramovať.

Preto programovacie jazyky ponúkajú tzv. `cykly` (loops), pomocou ktorých môžeme jednoducho povedať počítaču, aby určitý blok kódu opakoval, koľkokrát budeme chcieť. Vďaka tomu môže program aj s iba niekoľkými riadkami kódu povedať počítaču, aby vykonal množstvo inštrukcií. Jazyk C# ponúka dva základné typy cyklov, `while` a `for`.

Ďalšou motiváciou pre využitie cyklov je to, že moderné procesory počítačov majú bežne frekvencie od 1 do 4 GHz, takže za sekundu zvládnu vykonať niekoľko miliárd `taktov` a počas každého taktu navyše až `desiatky` rôznych operácií. Iste si dokážete predstaviť, že s iba sekvenčným zápisom kódu by sme tento potenciál nemohli naplno využiť. Aj keď jeden riadok C# kódu môže byť preložený až na desiatky procesorových inštrukcií, tak aj keby sme zvládli napísať program so stovkami miliónov riadkov, stále by sme takýmto programom „zabavili“ procesor na iba jednu sekundu. Bežiace programy tak obvykle trávia väčšinu času práve vykonávaním nejakého cyklu.

# Cyklus while

Najjednoduchším cyklom v C je cyklus `while` ("dokým"):

```csharp
while (<výraz typu bool>) {
    // blok cyklu
}
```


Tu je aktualizovaný obsah naformátovaný do .md súboru:

md
Kopírovať kód
# Cyklus while

Najjednoduchším cyklom v C je cyklus `while` ("dokým"):

```csharp
while (<výraz typu bool>) {
    // blok cyklu
}
```

Funguje nasledovne:

- [ ] Najprv sa vyhodnotí (Booleovský) výraz v zátvorke za while a vykoná sa bod 2.
  
  - [ ] Ak je výraz pravdivý, tak sa vykoná blok cyklu a ďalej sa pokračuje opäť bodom 1.

  - [ ] Blok cyklu sa tiež často nazýva ako telo (body) cyklu.

- [ ] Ak nie je výraz pravdivý, tak sa vykoná bod 3. Program pokračuje za cyklom while.

Inak povedané, pokiaľ bude podmienka za while splnená, budú sa opakovane vykonávať príkazy vo vnútri tela cyklu. Skúste si to na nasledujúcom príklade:

```csharp
int pocet = 0;
while (pocet < 5) {
    Console.WriteLine($"Telo cyklu sa vykonalo, hodnota premennej pocet={pocet}");
    pocet = pocet + 1;
}

```

Tento kód opäť môžeme prečítať ako vetu: Dokým je hodnota premennej `pocet` menšia než päť, vykonávaj telo cyklu. Jedno vykonanie tela cyklu sa nazýva iterácia. Cyklus v ukážke vyššie teda vykoná päť iterácií, pretože sa telo cyklu vykoná päťkrát.

Ak výraz za `while` nie je vyhodnotený ako pravdivý v momente, keď sa `while` začne vykonávať, tak sa telo cyklu nemusí vykonať ani raz (t.j. bude mať nula iterácií).

# Nekonečný cyklus

Je dôležité dávať si pozor na to, aby cyklus, ktorý použijeme, nebol nechcene nekonečný (infinite loop), inak by náš program nikdy neskončil. Skúste v kóde vyššie zakomentovať alebo odstrániť riadok `pocet = pocet + 1;` a skúste program spustiť. Keďže sa hodnota premennej `pocet` nebude nijak meniť, tak výraz `pocet < 5` bude stále pravdivý a cyklus sa bude vykonávať neustále dokola. Této situácii sa ľudovo hovorí "zacyklenie".

Ak program spúšťate v termináli a zacyklí sa, môžete ho prerušiť pomocou klávesovej skratky `Ctrl + C`. Ak ho spustíte v prehliadači, tak radšej reštartujte túto stránku pomocou `F5` :)

Ak sa vám niekedy stalo, že sa program, ktorý ste práve používali, "zasekol" a prestal reagovať na váš vstup, mohlo to byť práve tým, že v ňom nechcene došlo k vykonaniu nekonečného cyklu (došlo k zacykleniu).

# Riadiaca premenná

Vykonávať úplne identický kód opakovane sa niekedy hodí, ale väčšinou chceme vykonať v tele cyklu trochu iné príkazy, v závislosti na tom, ktorá iterácia sa práve vykonáva. Na tento účel môžeme použiť premennú, ktorá si bude pamätať, v akej iterácii cyklu sa nachádzame, a podľa nej sa potom vykoná príslušná operácia. Takáto premenná sa zvyčajne označuje ako riadiaca premenná (index variable).

Napríklad, ak chceme niečo vykonať iba v prvej iterácii cyklu, môžeme použiť príkaz `if` s podmienkou, v ktorej skontrolujeme aktuálnu hodnotu riadiacej premennej:

```csharp
int i = 0;
while (i < 5) {
    if (i == 0) {
        Console.WriteLine("Prvá iterácia");
    }
    Console.WriteLine($"Hodnota i={i}");
    i += 1;
}

```

Riadiaca premenná je v tomto prípade `i` – tento názov sa pre riadiace premenné často používa z dôvodu jednoduchosti.

# Riadenie toku cyklu

V cykloch môžete využiť dva špeciálne príkazy, ktoré fungujú iba vnútri tela (bloku kódu) nejakého cyklu:

- Príkaz `continue;` spôsobí, že sa prestane vykonávať telo cyklu a program bude pokračovať vo vykonávaní na začiatku cyklu (t.j. pri `while` na vyhodnotenie výrazu). `continue` možno chápať ako skok na ďalšiu iteráciu cyklu. Skúste uhádnuť, čo vypíše nasledujúci kód:

```csharp
for (int i = 0; i < 5; i++) {
    if (i == 2) {
        continue;
    }
    Console.WriteLine($"Hodnota i={i}");
}
```

Tento kód v C# vykoná nasledujúce:

- [ ] Keď i je rovné 2, príkaz continue spôsobí preskočenie zvyšku tela cyklu a pokračovanie na začiatok cyklu.

- [ ] Všetky ostatné hodnoty i budú vypísané.

```csharp
int pocet = 0;
while (pocet < 10) {
    pocet = pocet + 1;

    if (pocet < 5) {
        continue;
    }

    Console.WriteLine($"Hodnota: {pocet}");
}
```


Príkaz `break;` spôsobí, že sa cyklus prestane vykonávať a program začne vykonávať kód, ktorý nasleduje za cyklom. Cyklus sa tak úplne preruší. Skúste uhádnuť, čo vypíše nasledujúci kód:

```csharp
for (int i = 0; i < 10; i++) {
    if (i == 5) {
        break;
    }
    Console.WriteLine($"Hodnota i={i}");
}
```
## Typ pre návh cyklu while

# Riadenie toku cyklu

Príkaz `break` môžete tiež niekedy použiť na uľahčenie návrhu cyklov. Ak potrebujete napísať `while` cyklus s nejakou zložitou podmienkou ukončenia, z ktorej sa vám točí hlava, skúste najprv vytvoriť "nekonečný" cyklus pomocou `while (1) { … }`, ďalej vytvorte telo cyklu a až nakoniec vymyslite podmienku, ktorá cyklus ukončí pomocou príkazu `break`:

```csharp
while (true) {
    // Telo cyklu

    if (/* podmienka na ukončenie cyklu */) {
        break;
    }
}
```

Nemusíte hneď zo začiatku vymýšľať výraz pre `while`, na čom by ste sa mohli zaseknúť.

Namiesto `while (1)` môžete použiť aj `while (true)`. Nezabudnite ale na vloženie príkazu `break` na ukončenie cyklu, keď bude podmienka splnená.

# Vnorovanie cyklov

Rovnako ako podmienky, aj cykly sú príkazy a môžete ich používať ľubovoľne v blokoch C kódu a tiež ich vnoriať. Chovanie vnorených cyklov môže byť zo začiatku trochu neintuitívne, preto je dobré si ich precvičiť. Skúste si pomocou debuggéra krokovať nasledujúci kód, aby ste pochopili, ako sa vykonáva, a skúste odhadnúť, aké hodnoty budú postupne nabývať premenné `i` a `j`. Potom odkomentujte výpisy `printf` a overte, či bol váš odhad správny:

```csharp
int i = 0;
while (i < 3)
{
    // Console.WriteLine($"i: {i}");
    int j = 0;
    while (j < 4)
    {
        // Console.WriteLine($"  j: {j}");
        j = j + 1;
    }

    i = i + 1;
}
Console.WriteLine("Konec programu");
```
Pre každú iteráciu "vonkajšieho" cyklu while sa vykonajú štyri iterácie "vnútorného" cyklu while. Dohromady sa tak vykoná celkom 3 * 4 iterácií

# Cyklus do while v C#

Cyklus `while` má aj alternatívu nazvanú `do while`. Tento cyklus má nasledujúcu syntaxu:

```csharp
do
{
    // telo cyklu
}
while (<výraz typu bool>);
```
Tento kód môžeme čítať ako: `"Vykonávaj <telo cyklu>, pokým platí <výraz>"`.

Jediný rozdiel medzi while a do `while` je ten, že v cykle `do while` sa výraz, ktorý určuje, či sa má vykonať ďalšia iterácia cyklu, vyhodnocuje až na konci cyklu. Telo cyklu sa tak vykoná vždy aspoň raz (aj keď je výraz na začiatku nepravdivý).

Ak na to nemáte zvláštny dôvod, asi nie je potrebné tento typ cyklu používať.

# Cyklus for 

V programoch veľmi často potrebujeme vykonať nejaký blok kódu presne n-krát:

- Prejdi n riadkov zo vstupného súboru a spočítaj ich hodnoty.
- Pošli správu všetkým n účastníkom chatu.
- Vystreľ presne trikrát zo zbrane.

Aj keď pomocou cyklu `while` môžeme vyjadriť vykonanie n iterácií, je to relatívne zdĺhavé, pretože je k tomu potrebné aspoň tri riadky kódu:

1. **Inicializácia cyklu:** vytvorenie riadiacej premennej, ktorá sa bude kontrolovať v cykle.
2. **Kontrola výrazu:** kontrola, či už riadiaca premenná dosiahla požadovanú hodnotu.
3. **Operácia na konci cyklu:** zmena hodnoty riadiacej premennej.

Pre zjednodušenie takýchto úloh ponúka jazyk C# cyklus `for`, ktorý umožňuje všetky tieto úkony skombinovať do jedného príkazu. 

Tento cyklus má nasledujúcu syntax:

```csharp
int i = 0; 
while (i < 10) { 
    // tělo cyklu
    i += 1; 
}

```
Cyklus `for` existuje, aby túto častú situáciu zjednodušil. Kód vyššie by sa dal pomocou cyklu `for` prepisovať takto:

```csharp
for (int i = 0; i < 10; i++)
{
    // telo cyklu
}
```

Ako je vidieť, cyklus `for` kombinuje inicializáciu cyklu, kontrolu výrazu a vykonanie príkazu po každej iterácii. Všeobecná syntax tohto cyklu vyzerá takto:

```csharp
for (<príkaz A>; <výraz typu bool>; <príkaz B>)
{
    // telo cyklu
}
```

Takýto cyklus sa vykonáva nasledovne:

1. Ako prvé sa vykoná príkaz A. Tu sa typicky vytvorí riadiaca premenná s nejakou počiatočnou hodnotou.
2. Skontroluje sa výraz. Ak nie je pravdivý, cyklus končí a program pokračuje za cyklom `for`. Ak je pravdivý, vykoná sa telo cyklu a program pokračuje bodom 3.
3. Vykoná sa príkaz B a program pokračuje bodom 2.

Výraz v príkaze `for` môže chýbať, v takom prípade sa automaticky predpokladá ako `true`. Rovnako platí, že bodkočiarka (`;`) môže vyjadrovať tzv. prázdny príkaz, ktorý nič nevykoná. Všetky tri časti cyklu `for` môžu teda chýbať, a v tom prípade sa jedná o nekonečný cyklus:

```csharp
for (;;)
{
    // telo cyklu
}
```

# Relatívna cesta

Cesta k súboru zadávaná v `#include` by mala byť relatívna, čiže nie je dobrý nápad používať niečo podobné ako:

```cpp
#include "C:/Users/Kamil/Desktop/upr/muj_soubor.h"
```

Takýto program by totiž určite nefungoval na inom počítači než na vašom. Z ktorého adresára sa táto relatívna cesta vyhodnotí, je popísané nižšie.

# Rozdiel medzi `#include <…>` a `#include "…"`

Rozdiel medzi týmito dvoma variantami nie je pevne definovaný, avšak väčšina preprocesorov (resp. prekladačov) funguje nasledovne:

- **`#include <…>`** najprv hľadá zadanú cestu v tzv. systémových cestách. Ide o známe adresáre, v ktorých sú uložené súbory štandardnej knižnice C a ďalšie knižnice, ktoré máte nainštalované v systéme. Ak sa daný súbor nenájde v systémových cestách, až potom sa cesta vyhodnotí relatívne k zdrojovému súboru, v ktorom bol `#include` použitý.

  Zoznam systémových ciest si môžete vypísať pomocou príkazu:

  ```bash
  echo | gcc -E -Wp,-v -
  ```
v Linuxovom termináli. Do tohto zoznamu môžete pridať ďalšie adresáre, ak `gcc` odovzdáte parameter `-I`.

Ak sa súbor, ktorý chcete vložiť do vášho kódu, nachádza v externej knižnici, ktorá nepatrí do vášho projektu, je bežné používať práve `#include <>`.

`#include "…"` sa nepozerá do systémových ciest, ale rovno hľadá zadanú cestu relatívne k súboru, v ktorom bol #include použitý. Tento formát používajte, ak vkladáte súbory z vášho projektu.

# Práca s pamäťou

V sekcii o pamäti sme sa dozvedeli, že operačnú pamäť počítača je možné adresovať pomocou číselných adries. Zatiaľ sme však v našich programoch s adresami výslovne nepracovali, iba sme vytvárali premenné, ktorých pamäť bola spravovaná automaticky. V tejto sekcii sa dozviete základy toho, ako tzv. správa pamäte (*memory management*) funguje.

Práca s pamäťou je kľúčovou časťou programovacích jazykov, ako je napríklad C. V jazyku C# však správa pamäte funguje odlišne vďaka automatickému uvoľňovaniu pamäte (*garbage collection*). V C# sa o alokáciu a uvoľňovanie pamäte stará práve tento mechanizmus, čím odpadá potreba manuálne riadiť pamäť ako v jazyku C. Napriek tomu je dôležité chápať základy správy pamäte, aby vaše programy fungovali efektívne a správne.


# Adresný priestor programu

Keď spustíte svoj program, operačný systém pre neho vytvorí tzv. adresný priestor (*address space*), čo je oblasť pamäte, s ktorou môže program pracovať. Tento priestor je vďaka mechanizmu virtuálnej pamäte súkromný pre váš bežiaci program – ostatné bežiace programy do neho nemajú prístup, pokiaľ im to výslovne nepovolíte.

Typicky je tento priestor rozdelený na niekoľko častí, pričom každá z nich slúži pre rôzne typy dát. Rôzne operačné systémy alebo behové prostredia môžu umiestňovať jednotlivé oblasti v adresnom priestore rôzne, preto je obrázok adresného priestoru iba ilustratívny.

### Zásobník
Táto časť uchováva automaticky spravované dáta, najmä lokálne premenné a parametre funkcií. Túto oblasť popisuje sekcia o automatickej pamäti.

### Halda
Túto časť môžete využiť na dynamickú alokáciu pamäte. To nám umožňujú ukazovatele, vďaka ktorým môžeme explicitne pracovať s adresami v pamäti. Túto oblasť adresného priestoru popisuje sekcia o dynamickej pamäti.

### Globálne dáta
Táto časť obsahuje globálne premenné, ktoré žijú počas celej doby behu programu.

### Inštrukcie programu
Do tejto časti pamäte sa pri spustení programu skopírujú jeho inštrukcie zo spustiteľného súboru na disku. Nachádza sa v nej preložený kód funkcií vášho programu. Procesor potom číta inštrukcie, ktoré má vykonať, práve z tejto časti pamäte. Táto pamäť je obvykle chránená proti zápisu a slúži iba na čítanie.

# Pole

Teraz už poznáme základy alokovania pamäte v jazyku C, avšak stále pracujeme iba s jednotlivými premennými. Počítače slúžia na (rýchle) spracovanie veľkého objemu dát a aby sme ich naplno využili, potrebujeme spracovávať mnoho premenných naraz. Napríklad:

- V dokumente otvorenom vo Worde môžeme mať uložené tisíce rôznych znakov.
- Na server v online hre môže byť v danom momente pripojené veľké množstvo hráčov a všetkým musíme posielať informácie o stave hry.
- Obrázky sa bežne v programoch reprezentujú ako dvojrozmerná mriežka pixelov. Napríklad obrázok v odtieňoch šedej s rozmermi 1024x1024 vyžaduje v pamäti 1048576 bajtov (čísel) reprezentujúcich jednotlivé pixely.

V jazyku C# môžeme pracovať s týmito veľkými objemami dát pomocou polí. Pole je dátová štruktúra, ktorá nám umožňuje uchovávať viacero hodnôt rovnakého typu pohromade a pristupovať k nim pomocou indexov.

#### Príklad použitia poľa v C#:

```csharp
using System;

class Program
{
    static void Main()
    {
        // Pole celých čísel s 5 prvkami
        int[] cisla = new int[5];

        // Priraďovanie hodnôt do poľa
        cisla[0] = 10;
        cisla[1] = 20;
        cisla[2] = 30;
        cisla[3] = 40;
        cisla[4] = 50;

        // Výpis hodnôt poľa
        for (int i = 0; i < cisla.Length; i++)
        {
            Console.WriteLine($"Hodnota na indexe {i} je {cisla[i]}");
        }

        // Môžeme vytvoriť aj pole s preddefinovanými hodnotami
        int[] preddefinovaneCisla = { 1, 2, 3, 4, 5 };

        // Pole znakov (napr. na uchovávanie textu)
        char[] znaky = { 'A', 'B', 'C', 'D', 'E' };

        // Dvojrozmerné pole (napr. na reprezentáciu obrázka)
        int[,] obrazok = new int[1024, 1024];  // 1024x1024 pixelov
    }
}
```

# Pole

Predstavte si, že pre reprezentáciu obrázka by sme si s premennými, ktoré sme používali doposiaľ, nevystačili. Ak by sme po jednej vytvárali premenné `pixel1`, `pixel2`, `pixel3`, náš zdrojový kód by bol obrovský a ťažko čitateľný. Navyše, veľkosť obrázka by nemohla závisieť na vstupe programu, pretože počet premenných (pixelov) by bol "zakódovaný" priamo v zdrojovom kóde.

Chceli by sme teda napísať kód, ktorý zvládne spracovať ľubovoľný počet hodnôt – či už 1, 2, 100, alebo 1000 – bez toho, aby sme museli kód meniť.

Najjednoduchším a najbežnejším spôsobom, ako v pamäti počítača uchovávať väčšie množstvo hodnôt, je uložiť ich jednu za druhou v pamäti. Tento koncept ukladania dát sa nazýva **pole** (*array*), a je tak bežný, že ho programovacie jazyky priamo podporujú vo svojej syntaxi. Jazyk C#, podobne ako jazyk C, nie je výnimkou.

# Statické polia

Polia v automatickej pamäti (na zásobníku) sa označujú ako **statické polia** (*static arrays*). Môžeme ich vytvoriť tak, že pri definícii premennej za jej názov pridáme hranaté zátvorky s číslom udávajúcim počet prvkov v poli. Napríklad takto vytvoríme pole celých čísel s tromi prvkami:

```csharp
int[] pole = new int[3];
```

# Statické polia

Takáto premenná bude obsahovať pamäť pre 3 celé čísla (teda pravdepodobne na vašom počítači dohromady 12 bajtov). Počet prvkov v poli sa označuje ako jeho veľkosť (*size*).

Dôležité je si dávať pozor, že hranaté zátvorky sa uvádzajú za názov premennej, nie za názov dátového typu. Preto je `int[3] pole;` nesprávne.

#### Príklad:

```csharp
int[] pole = new int[3]; // Správne: deklarácia poľa s 3 prvkami
```

# Statické polia

V určitom zmysle je pole iba zobecnením bežnej premennej. Ak vytvoríte pole o veľkosti jedna (`int a[1];`), v pamäti bude reprezentované úplne rovnako ako klasická premenná (`int a;`).

Pole je možné vytvoriť aj na halde pomocou dynamickej alokácie pamäte. Všetky nižšie popísané koncepty sú platné aj pre dynamické polia, avšak budeme ich demonštrovať na statických poliach, pretože ich je jednoduchšie vytvoriť.

# Statické polia

Hodnota zadaná v hranatých zátvorkách by mala byť **konstantným výrazom**, teda buď priamo číselná hodnota, alebo číselná hodnota pochádzajúca z makra. Ak budete potrebovať pole dynamickej veľkosti, mali by ste použiť dynamickú alokáciu pamäte.

**Poznámka:** Dokonca ani **konštantná premenná** nie je v jazyku C považovaná za "konstantný výraz".

Jazyk C od verzie C99 síce umožňuje dávať do hranatých zátvoriek aj "dynamické" hodnoty, teda výrazy, ktorých hodnota nemusí byť známa v čase prekladu:

```csharp
int velikost = ...; // velikost sa načíta napr. zo súboru
int[] pole = new int[velikost];
```
Táto funkcionalita, nazývaná VLA (variable-length array), je však určená pre veľmi špecifické použitie a nesie so sebou rôzne nevýhody.

# Počítanie od nuly

Pozície jednotlivých prvkov v poli sa označujú ako ich **indexy** (*array indices*). Tieto pozície sa číslujú od hodnoty 0 (teda nie od jednotky, ako možno poznáte z iných oblastí). Prvý prvok poľa je teda na nultej pozícii (indexe), druhý na prvej pozícii atď. (pozri obrázok vyššie). Počítanie od nuly (*zero-based indexing*) je vo svete programovania bežné a budete si naň musieť zvyknúť. Jeden z dôvodov, prečo sa prvky počítajú práve od nuly, sa dozviete nižšie.

Z tohto vyplýva jedna dôležitá vlastnosť: posledný prvok poľa je vždy na indexe `<veľkosť poľa> - 1`. Ak by ste sa pokúsili pristúpiť k prvku na indexe `<veľkosť poľa>`, pristupujete mimo pamäť poľa, čo spôsobí pamäťovú chybu.

# Inicializácia poľa

Rovnako ako pri bežných lokálnych premenných platí, že ak pole neinicializujete, bude obsahovať nedefinované hodnoty. V takom prípade nesmiete hodnoty v poli žiadnym spôsobom čítať, inak by došlo k nedefinovanému správaniu 💣! Na inicializáciu poľa môžete použiť zložené zátvorky so zoznamom hodnôt oddelených čiarkami, ktoré budú do poľa uložené. Ak nezadáte dostatok hodnôt na vyplnenie celého poľa, zvyšok hodnôt bude nastavený na nulu.

#### Príklady:

```csharp
int[] a = new int[3];         // pole bez definovanej hodnoty, nepoužívať!
int[] b = { 0, 0, 0 };        // pole s hodnotami 0, 0, 0
int[] c = { 1, 0, 0, 0 };     // pole s hodnotami 1, 0, 0, 0
int[] d = { 2, 3 };           // pole s hodnotami 2, 3
```
Hodnoty samozrejme nemôžete zadať viac, než je veľkosť poľa.

Ak využijete inicializáciu statického poľa, môžete vynechať veľkosť poľa v hranatých zátvorkách. Kompilátor v tomto prípade dopočíta veľkosť za vás:

```csharp
int[] p = { 1, 2, 3 }; // p je pole s tromi číslami, kompilátor si odvodí int p[3]
```

# Prístup k prvkom poľa

Aby sme využili toho, že nám pole umožňuje vytvoriť väčšie množstvo pamäte naraz, musíme mať možnosť pristupovať k jednotlivým prvkom v poli. V C# sa na prístup k prvkom poľa používa priamo syntaktická notácia s hranatými zátvorkami.

V C# sa pole správa ako sekvencia prvkov a každý prvok je prístupný pomocou indexu. Prvok na i-tom indexe môžeme získať prístupom cez hranaté zátvorky. Napríklad, ak máme pole `pole` a chceme pristúpiť k prvku na druhom indexe, použijeme `pole[2]`.

#### Príklad v C#:

```csharp
int[] pole = { 10, 20, 30, 40, 50 };

// Prístup k prvkom poľa
int prvyPrvek = pole[0]; // Prvý prvok: 10
int druhyPrvek = pole[1]; // Druhý prvok: 20
int tretiPrvek = pole[2]; // Tretí prvok: 30

// Môžeme priamo priraďovať hodnoty
pole[3] = 100; // Zmena štvrtého prvku na 100

Console.WriteLine(pole[3]); // Výpis štvrtého prvku: 100
```

Všimnite si, že na prístup k ďalším prvkom v poli používame jednoducho indexy, a preto nie je potrebné pracovať s ukazateľmi ako v jazyku C. C# automaticky spravuje interné podrobnosti.

Prečo počítať od nuly?
Indexovanie od nuly má svoje výhody, najmä pri práci s ukazateľmi v nižších programovacích jazykoch. Indexovanie od nuly znamená, že prístup k prvkom sa stáva veľmi jednoduchým výpočtom: ak máte ukazateľ na začiatok poľa a chcete prístup k prvku na i-tom indexe, adresa tohto prvku sa jednoducho vypočíta ako začiatok poľa plus i.

V C# to však zjednodušuje prístup k prvkom a prácu s poľami, pretože sa nevyžaduje manuálne spravovanie ukazateľov.

# Operátor prístupu k poľu

V C# sa prístup k prvkom poľa uskutočňuje pomocou operátora prístupu k poľu, ktorý využíva hranaté zátvorky. Tento operátor, známy ako "array subscription operator", umožňuje jednoducho a prehľadne pristupovať k jednotlivým prvkom v poli. 

Syntax operátora prístupu k poľu je:

```csharp
<výraz a>[<výraz b>]
```

Kde `<výraz a>` predstavuje pole a `<výraz b>` predstavuje index prvku, ku ktorému chceme pristúpiť.

```csharp
int[] pole = { 1, 2, 3 };

// Prístup k prvkom poľa
pole[0] = 5;     // Nastavíme prvý prvok poľa na hodnotu 5
int c = pole[2]; // Nastavíme c na hodnotu posledného (tretieho) prvku poľa

```

`V tomto príklade : `

- [ ] pole[0] je ekvivalentné výraz *(pole + 0) v jazyku C, kde pole je ukazovateľ na začiatok poľa.
- [ ] pole[5] je ekvivalentné výraz *(pole + 5).
      
Používanie hranatých zátvoriek je prehľadnejšie a jednoduchšie než používanie ukazovateľov a operátora dereferencovania. Preto sa odporúča používať túto syntaktickú skratku na prístup k prvkom poľa, pokiaľ je to možné.

Je dôležité si uvedomiť, že operátor prístupu k poľu a definícia poľa používajú hranaté zátvorky, ale ide o odlišné kontexty. Zatiaľ čo hranaté zátvorky pri definícii poľa určujú veľkosť poľa, pri prístupe k prvkom poľa označujú konkrétny index.

# Použitie polí s cyklami

Ak by sme k poľu pristupovali po jednotlivých prvkoch, nemohli by sme využiť jeho plný potenciál. Aj keď môžeme jedným riadkom kódu vytvoriť napríklad 100 rôznych hodnôt (napr. `int[] pole = new int[100];`), ak by sme museli písať `pole[0]`, `pole[1]` atď. pre prístup k jednotlivým prvkom, efektívna práca s poľom by bola veľmi zložitá. Účelom polí je umožniť spracovanie veľkého množstva dát jednotným spôsobom pomocou krátkeho kódu. Inými slovami, chceme mať rovnaký kód, ktorý dokáže spracovať pole veľkosti 2 aj 1000. K tomu môžeme efektívne využiť cykly.

Často je praktické použiť riadiacu premennú cyklu na indexovanie poľa. Napríklad, ak máme pole s veľkosťou 10, môžeme ho "prechádzať" pomocou cyklu `for`:

#### Príklad v C#:

```csharp
int[] pole = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

// Prechádzame celé pole a vypisujeme jeho hodnoty
for (int i = 0; i < pole.Length; i++)
{
    Console.WriteLine(pole[i]);
}
```

V tomto príklade:

- [ ] pole.Length nám poskytuje veľkosť poľa, čo je 10 v tomto prípade.
- [ ] Cyklus for prechádza celé pole a prístupom k prvkom pole[i] vykonáva požadované operácie (v tomto prípade vypisuje hodnoty na konzolu).
      
Situácie, kedy pomocou cyklu prechádzame pole, sú veľmi časté a určite sa s nimi mnohokrát stretnete a využijete ich. Odporúča sa túto techniku precvičiť napríklad pomocou rôznych úloh.

# Predávanie polí do funkcií

Pole môžeme (rovnako ako hodnoty iných dátových typov) predávať ako argumenty do funkcií. Pri tom si však musíme dávať pozor najmä na dve veci:

1. **Pole sa predáva ako ukazateľ**: Keď predávame pole do funkcie, nepredávame celé pole, ale iba ukazateľ na jeho prvý prvok. To znamená, že ak zmeníme hodnoty v poli vo funkcii, tieto zmeny sa prejavia aj v pôvodnom poli.

2. **Nemáme informáciu o veľkosti poľa**: Funkcia, ktorá prijíma pole ako argument, nepozná jeho veľkosť. Je na nás, aby sme veľkosť poľa predali ako samostatný argument alebo použili iný spôsob, ako funkcii oznámiť, ako dlho má s poľom pracovať.

# Výpočet veľkosti poľa

Aby ste pri zmene veľkosti statického poľa nemuseli ručne upravovať jeho veľkosť na viacerých miestach v kóde, môžete vo funkcii, kde definujete statické pole, vypočítať jeho veľkosť pomocou operátora `sizeof`:

```csharp
using System;

class Program
{
    static void Main()
    {
        int[] pole = { 1, 2, 3 };
        
        // Veľkosť poľa v bajtoch
        Console.WriteLine("Veľkosť poľa v bajtoch: " + (pole.Length * sizeof(int)));
        
        // Počet prvkov v poli
        Console.WriteLine("Počet prvkov v poli: " + pole.Length);
    }
}
```

V tomto príklade:

- [ ] sizeof(int) vracia veľkosť typu int v bajtoch. V C# sa však priamo sizeof nepoužíva na polia ako v C/C++, preto použijeme pole.Length na získanie počtu prvkov.
- [ ] Veľkosť poľa môžete vypočítať ako pole.Length * sizeof(int), kde sizeof(int) je veľkosť typu int.

`Poznámka` : V C# sa operátor sizeof používa na získanie veľkosti základných dátových typov, ale nie na polia. Preto v C# na získanie počtu prvkov v poli použijeme vlastnosť Length poľa.

# Dynamické pole v C#

V C# se dynamická pole vytvářejí pomocí kolekcí z .NET knihovny, jako je `List<T>`. Na rozdíl od C, kde se dynamická paměť alokuje přímo na haldě pomocí funkce `malloc`, C# poskytuje vyšší úroveň abstrakce a automatickou správu paměti.

## Příklady použití `List<T>`:

### 1. Vytvoření a inicializace dynamického pole:

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // Vytvoření dynamického pole typu int
        List<int> pole = new List<int>();

        // Přidání prvků do pole
        pole.Add(1);
        pole.Add(2);
        pole.Add(3);

        // Výpis prvků
        foreach (int prvek in pole)
        {
            Console.WriteLine(prvek);
        }
    }
}
```

# Viacerozměrná pole v C#

Někdy potřebujeme v programech reprezentovat struktury, které jsou přirozeně vícerozměrné. Typickým příkladem jsou obrázky, které lze reprezentovat jako dvourozměrnou mřížku pixelů. V C# to lze jednoduše dosáhnout pomocí vícerozměrných polí.

Paměťové adresy mají pouze jeden rozměr, protože jsou reprezentovány jedním číslem. Jak tedy můžeme do jednorozměrné paměti uložit vícerozměrné hodnoty? Jednoduchým způsobem je "vyskládat" jednotlivé rozměry za sebou v paměti. Například, pokud máme dvojrozměrné pole s rozměry 5x5, uložíme data do paměti řádek po řádku.

## Příklady:

### 1. Dvourozměrné pole

```csharp
using System;

class Program
{
    static void Main()
    {
        // Vytvoření dvourozměrného pole 5x5
        int[,] matice = new int[5, 5];

        // Inicializace prvků
        for (int i = 0; i < 5; i++)
        {
            for (int j = 0; j < 5; j++)
            {
                matice[i, j] = i * 5 + j + 1;
            }
        }

        // Výpis prvků
        for (int i = 0; i < 5; i++)
        {
            for (int j = 0; j < 5; j++)
            {
                Console.Write(matice[i, j] + "\t");
            }
            Console.WriteLine();
        }
    }
}
```

# Spôsob vyskladania dimenzií v C#

Pri práci s viacrozmernými poľami môžeme zvoliť rôzne spôsoby, ako ich uložiť do pamäte. Dva najbežnejšie prístupy sú:

1. **Row Major Ordering (Ukladanie po riadkoch)**:
   - Pri tomto spôsobe sú prvky ukladané do pamäte po riadkoch. To znamená, že najprv uložíme všetky prvky prvého riadku, potom druhého riadku a tak ďalej.

2. **Column Major Ordering (Ukladanie po stĺpcoch)**:
   - Pri tomto spôsobe sú prvky ukladané do pamäte po stĺpcoch. To znamená, že najprv uložíme všetky prvky prvého stĺpca, potom druhého stĺpca a tak ďalej.

Oba prístupy majú svoje výhody a nevýhody, ale je dôležité sa držať jedného prístupu, aby sa predišlo zmätkom v indexovaní. Nižšie predpokladáme používanie `row major ordering`.

## Příklady:

### 1. Row Major Ordering

```csharp
using System;

class Program
{
    static void Main()
    {
        // Vytvorenie dvojrozmerného poľa 3x3
        int[,] pole = new int[3, 3];

        // Inicializácia prvkov
        int hodnota = 1;
        for (int i = 0; i < 3; i++)
        {
            for (int j = 0; j < 3; j++)
            {
                pole[i, j] = hodnota++;
            }
        }

        // Výpis prvkov
        Console.WriteLine("Row Major Ordering:");
        for (int i = 0; i < 3; i++)
        {
            for (int j = 0; j < 3; j++)
            {
                Console.Write(pole[i, j] + "\t");
            }
            Console.WriteLine();
        }
    }
}
```

# Indexovanie v C#

Pri práci s viacrozmernými poľami musíme často prevádzať medzi viacrozmerným a jednorozmerným indexom. Tento postup je dôležitý, keď pracujeme s 1D poliami v jazykoch, ktoré ukladajú viacrozmerné polia ako jednorozmerné polia. Pre ilustráciu si ukážeme, ako prevádzať medzi 2D a 1D indexmi.

## Prevody medzi 2D a 1D indexmi

**Prevádzanie z 2D do 1D**

Pre prevod 2D indexu na 1D index použijeme nasledujúci vzorec:
- `index_2d_na_1d` = radek * sirka + sloupec

Tento vzorec nám umožňuje previesť dvojrozmerný index (radek, sloupec) na jednorozmerný index, kde `sirka` je počet stĺpcov v dvojrozmernom poli.

**Prevádzanie z 1D do 2D**

Pre prevod 1D indexu na 2D index použijeme nasledujúci vzorec:
- radek = index / sirka
- sloupec = index % sirka

Tento vzorec nám umožňuje zistiť, na akom riadku a stĺpci sa nachádzame, ak máme jednorozmerný index a počet stĺpcov.

## Příklady v C#

### Prevádzanie z 2D do 1D

```csharp
using System;

class Program
{
    static void Main()
    {
        int radek = 2;
        int sloupec = 3;
        int sirka = 5; // Počet stĺpcov

        int index1D = Index2DNa1D(radek, sloupec, sirka);
        Console.WriteLine($"2D index ({radek}, {sloupec}) na 1D index: {index1D}");
    }

    static int Index2DNa1D(int radek, int sloupec, int sirka)
    {
        return radek * sirka + sloupec;
    }
}
```

# Viacrozmerné pole na zásobníku v C#

V C# môžeme vytvárať viacrozmerné polia podobným spôsobom ako v C. Ak poznáme rozmer a veľkosť viacrozmerného poľa v čase prekladu, môžeme použiť viacrozmerné statické polia. Tieto polia sa vytvárajú pomocou hranatých zátvoriek pre každý rozmer.

## Vytváranie a používanie viacrozmerného poľa

Ak chceme vytvoriť 2D pole s rozmermi 3x3, môžeme to urobiť nasledovne:

```csharp
using System;

class Program
{
    static void Main()
    {
        // Vytvorenie 2D poľa s rozmermi 3x3
        int[,] pole = new int[3, 3];
        
        // Priradenie hodnôt do poľa
        pole[0, 0] = 1;
        pole[1, 1] = 2;
        pole[2, 2] = 3;

        // Výpis hodnôt z poľa
        for (int i = 0; i < pole.GetLength(0); i++)
        {
            for (int j = 0; j < pole.GetLength(1); j++)
            {
                Console.Write($"{pole[i, j]} ");
            }
            Console.WriteLine();
        }
    }
}
```

Vyskladanie polí v pamäti
Viacrozmerné polia sú v pamäti uložené postupne podľa jednotlivých dimenzií zľava. Pre 2D pole, kde považujeme prvý index za index riadku, je toto vyskladanie v súlade s "row-major" poriadkom. To znamená, že prvky sú uložené po riadkoch. Napríklad v poli int[,] pole = new int[3, 3]; bude v pamäti uložené nasledovne:

- [ ] pole[0, 0], pole[0, 1], pole[0, 2]
- [ ] pole[1, 0], pole[1, 1], pole[1, 2]
- [ ] pole[2, 0], pole[2, 1], pole[2, 2]

# Viacrozmerné pole na halde v C#

Ak potrebujeme dynamické viacrozmerné pole, môžeme alokovať pamäť na haldě pre všetky rozměry. V C# sa používa dynamická alokácia pamäti pre viacrozmerné polia trochu odlišne než v C. Tu je spôsob, ako môžeme vytvoriť dynamické viacrozmerné pole a manipulovať s ním.

## Vytvorenie dynamického 2D poľa

V C# sa na alokáciu pamäti pre viacrozmerné polia používa `new` operátor. Môžeme vytvoriť dynamické 2D pole, ktoré umožňuje priradiť hodnoty a pristupovať k nim podobne ako v C.

```csharp
using System;

class Program
{
    static void Main()
    {
        // Rozmery 2D poľa
        int vyska = 4;
        int sirka = 5;

        // Vytvorenie dynamického 2D poľa
        int[,] pole = new int[vyska, sirka];

        // Priradenie hodnôt do poľa
        for (int i = 0; i < vyska; i++)
        {
            for (int j = 0; j < sirka; j++)
            {
                pole[i, j] = i * sirka + j;
            }
        }

        // Výpis hodnôt z poľa
        for (int i = 0; i < vyska; i++)
        {
            for (int j = 0; j < sirka; j++)
            {
                Console.Write($"{pole[i, j]} ");
            }
            Console.WriteLine();
        }
    }
}
```

# Zubaté pole v C#

Občas môžete naraziť na situáciu, kedy potrebujete vytvoriť viacrozmerné pole, kde niektoré dimenzie nemajú fixnú veľkosť. Napríklad, prvý riadok môže mať dva stĺpce, druhý riadok tri stĺpce, tretí riadok žiadny stĺpec a pod.

V takom prípade môžete vytvoriť tzv. zubaté pole (jagged array alebo ragged array). Zubaté pole je v podstate "pole polí" – vytvoríte (dynamické) pole riadkov, pričom každý riadok bude opäť dynamické pole stĺpcov. 

## Vytvorenie a prístup k zubatému poľu

V C# sa zubaté pole vytvára pomocou dvojitého syntaxu poľa. Najprv vytvoríte pole riadkov a potom každému riadku priradíte pole stĺpcov.

### Príklad vytvorenia a použitia zubatého poľa

Nasledujúci kód vytvorí pole piatich študentov, kde každý študent má rôzny počet ID predmetov:

```csharp
using System;

class Program
{
    static void Main()
    {
        // Vytvorenie zubatého poľa s 5 študentmi
        int[][] studenti = new int[5][];

        // Priradenie rôzne veľkých polí predmetov pre každého študenta
        studenti[0] = new int[] { 101, 102 };
        studenti[1] = new int[] { 201, 202, 203 };
        studenti[2] = new int[] { 301 };
        studenti[3] = new int[] { 401, 402, 403, 404 };
        studenti[4] = new int[] { };  // Tento študent nemá žiadne predmety

        // Výpis predmetov pre každého študenta
        for (int i = 0; i < studenti.Length; i++)
        {
            Console.Write($"Študent {i + 1} predmety: ");
            for (int j = 0; j < studenti[i].Length; j++)
            {
                Console.Write($"{studenti[i][j]} ");
            }
            Console.WriteLine();
        }
    }
}
```

## Prístup k prvkom zubatého poľa

K prvkom zubatého poľa pristupujeme klasicky cez hranaté zátvorky. Napríklad studenti[2] vráti pole predmetov tretieho študenta, a nad týmto poľom môžeme opäť použiť hranaté zátvorky na prístup k konkrétnemu predmetu.

```csharp
int tretieID = studenti[1][2];  // Získa tretí predmet druhého študenta (ID = 203)
```

## Uvoľňovanie pamäti

V C# sa správa o pamäť vykonáva automaticky prostredníctvom garbage collectora, takže nie je potrebné manuálne uvoľňovať pamäť ako v C. Je však dobré mať na pamäti, že ak vytvárate a manipulujete s dynamickými poľami, garbage collector sa postará o uvoľnenie pamäti, keď už nebude používaná.


