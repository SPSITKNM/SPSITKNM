# Zadanie pre konzolovú aplikáciu v .NET 8

Vašou úlohou je vytvoriť konzolovú aplikáciu, ktorá bude načítavať pole produktov zo súboru, vykoná nad týmto poľom výpočty a výsledok vypíše na štandardný výstup (do konzoly). Vstupný súbor sa načíta ako argument pri spustení aplikácie.

## Metóda Main

Vstupný súbor bude predaný ako parameter pri spustení aplikácie. Vaša metóda `Main` by mala začínať nasledovným kódom:

```csharp
Thread.CurrentThread.CurrentCulture = CultureInfo.GetCultureInfo("sk-SK");
Console.OutputEncoding = System.Text.Encoding.UTF8;

string data = File.ReadAllText(args[0]);

Product[] products = ParseData(data);

double sum = GetTotalProductsPrice(products);
double averageWeight = GetAverageItemWeight(products);

// TODO: doplniť ďalší kód...
```

## Trieda Product
Vytvorte triedu `Product`, ktorá bude reprezentovať jeden produkt. Vlastnosti produktu:
- **Názov produktu** – typ `string`
- **Cena jedného kusu** – typ `double`
- **Počet kusov** - typ `int?` (počet kusov nemusí byť známy)
- **Váha** – štruktúra obsahujúca jednotku (výčtový typ) a hodnotu (typ `double`)

## Metódy

1. **ParseData**
   - Predá sa jej obsah súboru (text).
   - Vracia pole produktov.
   - Implementujte vlastné parsovanie vstupného súboru a mapovanie dát na produkty. Použite metódu `ParseWeight` pre parsovanie váhy.

2. **ParseWeight**
   - Predá sa jej text obsahujúci váhu.
   - Vracia štruktúru obsahujúcu jednotku (výčtový typ) a hodnotu váhy v danej jednotke.

3. **GetTotalProductsPrice**
   - Vykonáva výpočet celkovej ceny všetkých produktov.
   - Ak nie je počet kusov známy, produkt sa nezapočítava.
   - Vracia číslo (`double`).

4. **GetAverageItemWeight**
   - Vykonáva výpočet priemernej hmotnosti jedného kusu produktu v kilogramoch.
   - Vracia priemernú hmotnosť zaokrúhlenú na 3 desatinné miesta (`double`).
   - Štruktúra reprezentujúca váhu by mala obsahovať metódu `GetNormalizedValue`, ktorá vracia váhu v kilogramoch.

## Výpis výsledku
Vypíšte do konzoly:
- Zoznam všetkých produktov
- Celkovú cenu
- Priemernú váhu

Ukážkový výstup:

```
Produkty:
Jablká Golden: 100 ks; 30 €
Banány: neznáme množstvo; 25 €
Hrušky: 60 ks; 40,5 €
...

Celková cena produktov: 65401 €
Priemerná váha položky: 0,364 kg
```

## Metódy, ktoré sa môžu hodiť
- `IndexOf`: [Dokumentácia](https://learn.microsoft.com/sk-sk/dotnet/api/system.string.indexof?view=net-8.0)
- `Substring`: [Dokumentácia](https://learn.microsoft.com/sk-sk/dotnet/api/system.string.substring?view=net-8.0)
- `IsNullOrEmpty`: [Dokumentácia](https://learn.microsoft.com/sk-sk/dotnet/api/system.string.isnullorempty?view=net-8.0)
- `Split`: [Dokumentácia](https://learn.microsoft.com/sk-sk/dotnet/api/system.string.split?view=net-8.0)
- `StartsWith`: [Dokumentácia](https://learn.microsoft.com/sk-sk/dotnet/api/system.string.startswith?view=net-8.0)
- `TryParse`: [Dokumentácia](https://learn.microsoft.com/sk-sk/dotnet/api/system.int64.tryparse?view=net-8.0)
- `Trim`: [Dokumentácia](https://learn.microsoft.com)
