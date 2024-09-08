# Úvod do programovania 

V tomto repozitári pre predemt PRO pre 4.ročník nájdete stručnú oporu vo formáte skrípt k preberanej problematike na hodinách PRO... Ďalšou podstatnou oporou je YT kanál nášho predmetu na ktorom teoretické poznatky aplikujeme v praxi tak aby študent bol schopný zvládnuť úlohy a projekty v priebehu roka... 

## Čo nás čaká v najbližších hodinách ? 

- [ ] **Syntax** 
- [ ] Príkazy a výrazy 
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



