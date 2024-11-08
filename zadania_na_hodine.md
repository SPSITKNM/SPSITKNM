# Zadanie pre konzolovú aplikáciu v .NET 8

Vašou úlohou je vytvoriť konzolovú aplikáciu, ktorá bude načítavať pole produktov zo súboru, vykoná nad týmto poľom výpočty a výsledok vypíše na štandardný výstup (do konzoly). Vstupný súbor sa načíta ako argument pri spustení aplikácie.

## Metóda Main

Vstupný súbor bude predaný ako parameter pri spustení aplikácie. Vaša metóda `Main` by mala začínať nasledovným kódom:

```csharp
Thread.CurrentThread.CurrentCulture = CultureInfo.GetCultureInfo("cs-CZ");
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
Jahody: 30 ks; 60 €
Broskyne: 75 ks; 35,2 €
Avokádo: 50 ks; 55,9 €
Mrkva: 120 ks; 15 €
Zemiaky: neznáme množstvo; 20 €
Cibuľa: 150 ks; 18 €
Cesnak: 90 ks; 40 €
Paradajky: 180 ks; 28 €
Uhorky: 110 ks; 25 €
Papriky: 70 ks; 30 €
Baklažán: 50 ks; 45,9 €
Šalát: 100 ks; 20 €
Špenát: 60 ks; 40 €
Kapusta: 90 ks; 35 €
Reďkovky: neznáme množstvo; 22 €
Petržlen: 140 ks; 12,2 €
Kaleráb: 130 ks; 18 €
Karfiol: 40 ks; 50 €
Brokolica: neznáme množstvo; 48 €
Zeler: 90 ks; 22 €
Zázvor: 30 ks; 80 €
Citróny: 100 ks; 30 €
Pomaranče: 85 ks; 35 €
Grapefruit: 70 ks; 38,9 €
Mango: 40 ks; 60 €
Kiwi: 60 ks; 25 €
Ananás: 25 ks; 75 €

Celková cena produktov: 65401 €
Priemerná váha položky: 0,364 kg
```

## Testovací súbor

Pre otestovanie vašej implementácie môžete použiť tento súbor: `data.txt`

Súbor ideálne stiahnite pravým tlačidlom myši a "Uložiť súbor ako..." (ak budete len kopírovať text, hrozí, že poškodíte jeho štruktúru).

Pri čítaní súboru si uvedomte, že existuje viac možných oddeľovačov riadkov (CRLF).

Súbor môže tiež končiť prázdnym riadkom.

Súbor bude vždy začínať riadkom "products:". Nasledovať budú jednotlivé produkty. Názov produktu je vždy odsadený 1 tabulátorom nasledovaným pomlčkou. Za názvom produktu je dvojbodka. Vlastnosti produktu sú vždy odsadené 2 tabulátormi nasledovanými medzerou a pomlčkou. Tieto vlastnosti môžu byť v ľubovoľnom poradí!

Vlastnosť "quantity" nemusí byť vždy uvedená (v tom prípade nie je známy počet kusov).

Vlastnosť "weight" obsahuje váhu jedného kusu. Táto váha môže byť v gramoch, dekagramoch alebo kilogramoch.

## Metódy, ktoré sa môžu hodiť

- `IndexOf`: [Dokumentácia](https://learn.microsoft.com/cs-cz/dotnet/api/system.string.indexof?view=net-8.0)
- `Substring`: [Dokumentácia](https://learn.microsoft.com/cs-cz/dotnet/api/system.string.substring?view=net-8.0)
- `IsNullOrEmpty`: [Dokumentácia](https://learn.microsoft.com/cs-cz/dotnet/api/system.string.isnullorempty?view=net-8.0)
- `Split`: [Dokumentácia](https://learn.microsoft.com/cs-cz/dotnet/api/system.string.split?view=net-8.0)
- `StartsWith`: [Dokumentácia](https://learn.microsoft.com/cs-cz/dotnet/api/system.string.startswith?view=net-8.0)
- `TryParse`: [Dokumentácia](https://learn.microsoft.com/cs-cz/dotnet/api/system.int64.tryparse?view=net-8.0)
- `Trim`: [Dokumentácia](https://learn.microsoft.com/cs-cz/dotnet/api/system.string.trim?view=net-8.0)

--

## Ako má vyzerať vstup ? 


```Ukážkový vstup:
products:
	 - Jablka Golden:
		 - price: 30
		 - quantity: 100
		 - weight: 200 g
	 - Banány:
		 - price: 25
		 - weight: 150 g
	 - Hrušky:
		 - price: 40.5
		 - quantity: 60
		 - weight: 250 g
	 - Jahody:
		 - price: 60
		 - quantity: 30
		 - weight: 500 g
	 - Broskve:
		 - price: 35.2
		 - quantity: 75
		 - weight: 30 dkg
	 - Avokádo:
		 - price: 55.9
		 - quantity: 50
		 - weight: 250 g
	 - Mrkev:
		 - price: 15
		 - quantity: 120
		 - weight: 100 g
	 - Brambory:
		 - price: 20
		 - weight: 1 kg
	 - Cibule:
		 - price: 18
		 - quantity: 150
		 - weight: 90 g
	 - Česnek:
		 - price: 40
		 - quantity: 90
		 - weight: 30 g
	 - Rajčata:
		 - price: 28
		 - quantity: 180
		 - weight: 80 g
	 - Okurky:
		 - price: 25
		 - quantity: 110
		 - weight: 350 g
	 - Papriky:
		 - price: 30
		 - quantity: 70
		 - weight: 180 g
	 - Lilek:
		 - price: 45.9
		 - quantity: 50
		 - weight: 400 g
	 - Salát:
		 - price: 20
		 - quantity: 100
		 - weight: 250 g
	 - Špenát:
		 - price: 40
		 - quantity: 60
		 - weight: 50 dkg
	 - Kapusta:
		 - price: 35
		 - quantity: 90
		 - weight: 400 g
	 - Ředkvičky:
		 - price: 22
		 - weight: 50 g
	 - Petržel:
		 - price: 12.2
		 - quantity: 140
		 - weight: 80 g
	 - Kedlubna:
		 - price: 18
		 - quantity: 130
		 - weight: 300 g
	 - Květák:
		 - price: 50
		 - quantity: 40
		 - weight: 1.2 kg
	 - Brokolice:
		 - price: 48
		 - weight: 1 kg
	 - Celer:
		 - price: 22
		 - quantity: 90
		 - weight: 400 g
	 - Zázvor:
		 - price: 80
		 - quantity: 30
		 - weight: 100 g
	 - Citrony:
		 - price: 30
		 - quantity: 100
		 - weight: 120 g
	 - Pomeranče:
		 - price: 35
		 - quantity: 85
		 - weight: 200 g
	 - Grapefruit:
		 - price: 38.9
		 - quantity: 70
		 - weight: 350 g
	 - Mango:
		 - price: 60
		 - quantity: 40
		 - weight: 500 g
	 - Kiwi:
		 - price: 25
		 - quantity: 60
		 - weight: 100 g
	 - Ananas:
		 - price: 75
		 - quantity: 25
		 - weight: 1.5 kg


```
