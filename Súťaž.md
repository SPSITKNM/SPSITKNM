# **OZNÁMENIE O SKUPINOVEJ SÚŤAŽI** 

Dňa **22. novembra 2024** sa počas dnešnej hodiny uskutoční **skupinová súťaž** zameraná na riešenie **algoritmicky orientovaných úloh**. 

## **Podrobnosti o súťaži:**
- **Téma:** Advent of SPŠIT DEMO – riešenie logických a algoritmických úloh
- **Forma:** 
  - Súťažiť budete v **malých skupinách** (2-3 študenti na tím).
  - Každý tím bude mať pridelenú úlohu, pričom sa kladie dôraz na efektivitu ( BIG O ) .
- **Cieľ:** Nájsť najlepšie možné riešenie úlohy v obmedzenom časovom limite.

## **Poznámka:**
Keďže nám napadol **prvý sneh**, rozhodli sme sa inšpirovať sviatočnou atmosférou a využiť **Advent of Code** ako ideálny nástroj na praktické precvičenie algoritmického myslenia.

**Tešíme sa na vaše zapojenie!**

---
*Pripomienka: Nezabudnite si pripraviť potrebné vývojové prostredia. Hodina bude interaktívna, a preto odporúčame byť včas na mieste.*



# 1. Cesta k zimnému zápočtu

Niečo je zle s globálnou produkciou snehu a teba vybrali, aby si sa na to pozrel. Elfovia ti dokonca dali mapu, na ktorej hviezdičkami označili päťdesiat najpravdepodobnejších miest s problémami.

Už máš s týmto skúsenosti, a preto vieš, že na obnovenie snehovej produkcie potrebuješ do 25. decembra skontrolovať všetkých päťdesiat hviezdičiek.

Zbieraj hviezdičky riešením úloh. Každý deň v adventnom kalendári budú dostupné dve úlohy; druhá úloha sa odomkne, keď vyriešiš prvú. Každá úloha ti prinesie jednu hviezdičku. Veľa šťastia!

Snažíš sa spýtať, prečo jednoducho nemôžu použiť stroj na počasie ("nie je dosť výkonný"), kam ťa vlastne posielajú ("do neba") a prečo tvoja mapa vyzerá väčšinou prázdna ("toľko otázok si kladieš")... a počkaj, vážne povedali do neba? ("Samozrejme, odkiaľ si myslíš, že pochádza sneh?"), keď si uvedomíš, že Elfovia ťa už pripútavajú do katapultu ("prosím, zostaňte v pokoji, potrebujeme vás pripútať").

Počas posledných úprav zistia, že ich kalibračný dokument (tvoj vstup do úlohy) bol "vylepšený" mladým elfom, ktorý bol zjavne nadšený ukázať svoje umelecké schopnosti. V dôsledku toho majú Elfovia problém čítať hodnoty v dokumente.

Novovylepšený kalibračný dokument pozostáva z riadkov textu; každý riadok pôvodne obsahoval konkrétnu kalibračnú hodnotu, ktorú teraz musia Elfovia získať. Na každom riadku sa kalibračná hodnota nachádza spojením prvej a poslednej číslice (v tomto poradí), čím sa vytvorí dvojciferné číslo.

### Príklad

```text
1abc2
pqr3stu8vwx
a1b2c3d4e5f
treb7uchet
```

V tomto príklade sú kalibračné hodnoty nasledovné: 12, 38, 15 a 77. Súčet týchto hodnôt je 142.

Zober celý kalibračný dokument. Aký je súčet všetkých kalibračných hodnôt?

---

# --- Cesta do Ostravi ---

Trajekt ťa rýchlo prepraví na Ostrov ostrova. Po vypytovaní zistíš, že sa tu normálne nachádza veľká kopa piesku, ale nevidíš nič okrem veľa vody a malého ostrova, kde trajekt zakotvil.

Keď sa snažíš zistiť, čo robiť ďalej, všimneš si plagát na stene blízko prístavu trajektov. "Závody lodí! Otvorené pre verejnosť! Hlavná cena: zájazd na Púštny ostrov so všetkými nákladmi hradenými!" To musí byť miesto, odkiaľ pochádza piesok! Najlepšie na tom je, že závody lodí začínajú už o pár minút.

Stihneš sa prihlásiť ako súťažiaci v závodoch lodí práve včas. Organizátor vysvetľuje, že nejde o tradičný závod – namiesto toho dostaneš pevne stanovený čas, počas ktorého musí tvoja loď prejsť čo najďalej, a vyhráš, ak tvoja loď prejde najväčšiu vzdialenosť.

Ako súčasť registrácie dostaneš list papiera (tvoj vstupný hádankový súbor), ktorý obsahuje čas povolený pre každý závod a najlepšiu dosiahnutú vzdialenosť v tomto závode. Aby si zaručil víťazstvo, musíš sa uistiť, že prejdeš v každom závode ďalej než aktuálny držiteľ rekordu.

Organizátor ťa privedie na miesto, kde sa konajú závody lodí. Lode sú oveľa menšie, než si čakal – sú to vlastne hračkárske lode, každá s veľkým tlačidlom na vrchu. Držaním tlačidla sa loď nabíja a uvoľnením tlačidla sa loď pohybuje. Lode sa pohybujú rýchlejšie, ak bolo tlačidlo držané dlhšie, ale čas držania tlačidla sa odpočítava od celkového času závodu. Tlačidlo môžeš držať len na začiatku závodu a lode sa nepohnú, kým tlačidlo neuvoľníš.

### Príklad:


```Čas: 7 15 30 Vzdialenosť: 9 40 200```


Tento dokument popisuje tri závody:

- Prvý závod trvá 7 milisekúnd. Rekordná vzdialenosť v tomto závode je 9 milimetrov.
- Druhý závod trvá 15 milisekúnd. Rekordná vzdialenosť v tomto závode je 40 milimetrov.
- Tretí závod trvá 30 milisekúnd. Rekordná vzdialenosť v tomto závode je 200 milimetrov.

Tvoja hračkárska loď má počiatočnú rýchlosť nula milimetrov za milisekundu. Za každú celú milisekundu, ktorú stráviš držaním tlačidla na začiatku závodu, sa rýchlosť lode zvýši o jeden milimeter za milisekundu.

### Možnosti pre prvý závod:

- Nedržať tlačidlo vôbec (0 milisekúnd). Loď sa nepohne; celková vzdialenosť je 0 milimetrov.
- Držať tlačidlo 1 milisekundu. Loď sa pohybuje rýchlosťou 1 mm/ms počas 6 milisekúnd, celkovo 6 milimetrov.
- Držať tlačidlo 2 milisekundy. Rýchlosť 2 mm/ms počas 5 milisekúnd, celkovo 10 milimetrov.
- Držať tlačidlo 3 milisekundy. Rýchlosť 3 mm/ms počas 4 milisekúnd, celkovo 12 milimetrov.
- Držať tlačidlo 4 milisekundy. Rýchlosť 4 mm/ms počas 3 milisekúnd, celkovo 12 milimetrov.
- Držať tlačidlo 5 milisekúnd. Rýchlosť 5 mm/ms počas 2 milisekúnd, celkovo 10 milimetrov.
- Držať tlačidlo 6 milisekúnd. Rýchlosť 6 mm/ms počas 1 milisekundy, celkovo 6 milimetrov.
- Držať tlačidlo 7 milisekúnd. Celý čas závodu je využitý na držanie tlačidla, loď sa nepohne, vzdialenosť 0 milimetrov.

Keďže aktuálny rekord je 9 milimetrov, existujú 4 rôzne spôsoby, ako môžeš vyhrať: držať tlačidlo 2, 3, 4 alebo 5 milisekúnd.

### Ďalšie závody:

- V druhom závode môžeš držať tlačidlo aspoň 4 milisekundy a najviac 11 milisekúnd, celkovo 8 rôznych spôsobov.
- V treťom závode môžeš držať tlačidlo aspoň 11 milisekúnd a najviac 19 milisekúnd, celkovo 9 rôznych spôsobov.

### Výpočet:
Aby si zistil, koľko priestoru na chybu máš, urči počet spôsobov, ako môžeš prekonať rekord v každom závode. V tomto príklade, ak tieto hodnoty vynásobíš, dostaneš **288** (4 * 8 * 9).

### Zadanie:
Urči počet spôsobov, ako môžeš prekonať rekord v každom závode. Čo dostaneš, ak tieto hodnoty medzi sebou vynásobíš?


---

# 4. Decembrový predtermín 

Lanovka ťa vezie hore. Čo je zvláštne, zem akoby s tebou nevystupovala; nešplháš sa na horu. Keď kruh Snehového ostrova mizne pod tebou, náhle sa nad tebou objaví úplne nový ostrov! Lanovka ťa dopraví na povrch nového ostrova a trhne vo svojej stanici.

Keď vystúpiš z lanovky, prvá vec, ktorú si všimneš, je, že vzduch tu je omnoho teplejší ako na Snehovom ostrove. Je tu aj dosť vlhko. Je toto miesto zdrojom vody?

Ďalšia vec, ktorú si všimneš, je elf sediaci na podlahe naprieč stanicou v akomsi kôpke farebných štvorcových kariet.

„Och! Ahoj!“ Elf vzrušene pribehne k tebe. „Ako ti môžem pomôcť?“ Opýtaš sa na zdroje vody.

„Netuším; ja iba obsluhujem lanovku. Ale to znie ako niečo, čo by sme tu mohli mať – veď je to predsa Ostrovný ostrov! Myslím, že záhradník by o tom mohol vedieť. Ten je však na inom ostrove – teda na tom malom obklopenom vodou, nie na tom plávajúcom. Fakt by sme potrebovali lepšie pomenovať veci. Čo keby: ak mi pomôžeš s niečím rýchlym, požičiam ti svoju loď a môžeš záhradníka navštíviť. Dostal som všetky tieto žreby ako darček, ale neviem zistiť, čo som vyhral.“

Elf ťa vedie ku kôpke farebných kariet. Tam objavíš desiatky žrebov, všetky už majú zoškrabaný nepriehľadný povrch. Keď jeden zdvihneš, vidíš, že každá karta má dva zoznamy čísel oddelené zvislou čiarou (|): zoznam výherných čísel a zoznam čísel, ktoré máš. Informácie si zorganizuješ do tabuľky (tvoj vstup do úlohy).

Podľa Elfa treba zistiť, ktoré z čísel, ktoré máš, sa nachádzajú v zozname výherných čísel. Prvá zhoda má hodnotu jedného bodu a každá ďalšia zhoda zdvojnásobí bodovú hodnotu tejto karty.

### Príklad

```text
Karta 1: 41 48 83 86 17 | 83 86  6 31 17  9 48 53
Karta 2: 13 32 20 16 61 | 61 30 68 82 17 32 24 19
Karta 3:  1 21 53 59 44 | 69 82 63 72 16 21 14  1
Karta 4: 41 92 73 84 69 | 59 84 76 51 58  5 54 83
Karta 5: 87 83 26 28 32 | 88 30 70 12 93 22 82 36
Karta 6: 31 18 13 56 72 | 74 77 10 23 35 67 36 11
```

# Výpočet bodov pre jednotlivé karty

### Príklad:
- **Karta 1**  
  - Výherné čísla: `41, 48, 83, 86, 17`  
  - Tvoje čísla: `83, 86, 6, 31, 17, 9, 48, 53`  
  - Zhodné výherné čísla: `48, 83, 17, 86`  
  - **Hodnota karty:**  
    - 1 bod za prvú zhodu  
    - 3 × zdvojnásobené za každú ďalšiu zhodu  
    - **Spolu: 8 bodov**  

- **Karta 2**  
  - Výherné čísla: `32, 61`  
  - Zhodné výherné čísla: `32, 61`  
  - **Hodnota karty: 2 body**

- **Karta 3**  
  - Výherné čísla: `1, 21`  
  - Zhodné výherné čísla: `1, 21`  
  - **Hodnota karty: 2 body**

- **Karta 4**  
  - Výherné čísla: `84`  
  - Zhodné výherné čísla: `84`  
  - **Hodnota karty: 1 bod**

- **Karta 5**  
  - Výherné čísla: _(žiadne)_  
  - Zhodné výherné čísla: _(žiadne)_  
  - **Hodnota karty: 0 bodov**

- **Karta 6**  
  - Výherné čísla: _(žiadne)_  
  - Zhodné výherné čísla: _(žiadne)_  
  - **Hodnota karty: 0 bodov**

---

## Celková hodnota kôpky žrebov: **13 bodov**


### Koľko bodov majú dokopy ? 

---

# --- 3. Bouchalove termíny a záhada matematickej analýzy 1 ---


Stále jazdíš na ťave cez Ostrov púšte, keď zrazu spozoruješ, že sa k tebe rýchlo blíži piesočná búrka. Keď sa otočíš, aby si varoval elfku, zmizne ti priamo pred očami! Pravdupovediac, len pred pár minútami ťa varovala pred duchmi.

Jedna z ťavích brašní je označená "mapy" – a naozaj, je plná dokumentov (tvoj vstupný hádankový súbor), ktoré popisujú, ako sa orientovať v púšti. Teda, aspoň si myslíš, že to tak je; jeden z dokumentov obsahuje zoznam pokynov vľavo/vpravo a zvyšné dokumenty akoby popisovali nejakú sieť označených uzlov.

Zdá sa, že máš použiť tieto pokyny na orientáciu v sieti. Možno ak ťava bude postupovať podľa týchto pokynov, dokážeš uniknúť zo strašidelnej pustatiny!

Po chvíli skúmania máp ťa zaujmú dva uzly: **AAA** a **ZZZ**. Máš pocit, že **AAA** je miesto, kde sa práve nachádzaš, a musíš postupovať podľa pokynov vľavo/vpravo, až kým sa nedostaneš k **ZZZ**.

### Formát uzlov
Každý uzol siete je definovaný individuálne. Napríklad:

```
RL

AAA = (BBB, CCC) BBB = (DDD, EEE) CCC = (ZZZ, GGG) DDD = (DDD, DDD) EEE = (EEE, EEE) GGG = (GGG, GGG) ZZZ = (ZZZ, ZZZ)
```


Začni v **AAA** a vyber ďalší prvok na základe nasledujúceho pokynu vľavo/vpravo. V tomto príklade začni v **AAA** a choď doprava (**R**) výberom pravého prvku z **AAA**, teda **CCC**. Potom znamená **L** výber ľavého prvku z **CCC**, teda **ZZZ**. Po nasledovaní pokynov **RL** sa dostaneš do **ZZZ** za **2 kroky**.

Samozrejme, nemusíš hneď nájsť **ZZZ**. Ak ti dôjdu pokyny vľavo/vpravo, opakuj celú sekvenciu pokynov podľa potreby: **RL** v skutočnosti znamená **RLRLRLRLRLRLRL**... a tak ďalej. Napríklad tu je situácia, kde sa do **ZZZ** dostaneš za **6 krokov**:

```
LLR

AAA = (BBB, BBB) BBB = (AAA, ZZZ) ZZZ = (ZZZ, ZZZ)
```


### Zadanie
Začni v **AAA** a postupuj podľa pokynov vľavo/vpravo. Koľko krokov je potrebných na dosiahnutie **ZZZ**?


---


# --- Nedostatok kreditov na ďalší semester ---

Láva začína prudko tiecť, keď je Závod na výrobu lávy plne funkčný. Keď odchádzaš, sob ti ponúkne padák, ktorý ti umožní rýchlo sa dostať na Ostrov ozubených kolies.

Počas klesania máš z vtáčej perspektívy jasný pohľad na Ostrov ozubených kolies, čo vysvetľuje, prečo si nikoho nestretol cestou hore: polovica Ostrova ozubených kolies je prázdna, ale pod tebou sa nachádza obrovské továrenské mesto!

Pristávaš blízko postupne sa napĺňajúceho jazera lávy na úpätí nového lávového vodopádu. Lávovody časom rozvedú lávu po celom meste, no aby sa dala využiť okamžite, Elfovia ju nakladajú do veľkých mobilných kotlov.

Tieto kotly majú ťažisko vysoko a sú tlačené ručne. Bohužiaľ, pri vyšších rýchlostiach sa stávajú veľmi ťažko ovládateľnými, a preto je ťažké udržať ich na rovnej trase na dlhší čas.

Aby sa na Ostrov púšte dostali čo najskôr potrebné strojové diely, musíš nájsť najlepší spôsob, ako dopraviť kotol z jazera lávy do továrne na strojové diely. Musíš minimalizovať stratu tepla a zároveň si vybrať trasu, ktorá nevyžaduje, aby kotol išiel príliš dlho rovno.

Našťastie majú Elfovia mapu (tvoj vstupný hádankový súbor), ktorá používa dopravné vzorce, okolitú teplotu a stovky ďalších parametrov na výpočet presnej hodnoty straty tepla pre každý blok mesta, do ktorého kotol vstúpi.

### Príklad:

```
2413432311323
3215453535623
3255245654254
3446585845452
4546657867536
1438598798454
4457876987766
3637877979653
4654967986887
4564679986453
1224686865563
2546548887735
4322674655533
```


Každý mestský blok je označený jednociferným číslom, ktoré predstavuje množstvo straty tepla, ak kotol vstúpi do tohto bloku. Počiatočný bod, jazero lávy, je v ľavom hornom rohu; cieľ, továreň na strojové diely, je v pravom dolnom rohu. (Keďže už začínaš v bloku v ľavom hornom rohu, táto strata tepla sa nezapočítava, pokiaľ tento blok neopustíš a znovu sa doň nevrátiš.)

Pretože je ťažké udržať kotol s vysokým ťažiskom v rovnom pohybe príliš dlho, môže sa posunúť najviac o **tri bloky v jednom smere**, než musí odbočiť o 90 stupňov doľava alebo doprava. Kotol sa tiež nemôže vrátiť späť; po vstupe do každého bloku môže iba zabočiť doľava, pokračovať rovno, alebo zabočiť doprava.

### Príklad cesty:

```
2>>34^>>>1323
32v>>>35v5623
32552456v>>54
3446585845v52
4546657867v>6
14385987984v4
44578769877v6
36378779796v>
465496798688v
456467998645v
12246868655<v
25465488877v5
43226746555v>
```


Táto cesta nikdy nejde rovno viac ako tri po sebe nasledujúce bloky a spôsobí stratu tepla iba **102**.

### Zadanie:
Nájdi najlepšiu trasu, ktorá dopraví kotol z jazera lávy do továrne na strojové diely, pričom sa nikdy neposunie viac ako tri po sebe nasledujúce bloky rovno. Aká je minimálna strata tepla, ktorú možno dosiahnuť?



# --- Hľadanie dôvodu pokračovanie štúdia ---

Stále bez snehu sa vydávaš na posledné miesto, ktoré si ešte neprešiel: stred Snežného ostrova, priamo pod vodopádom.

Tu niekto očividne skúšal problém vyriešiť. Všade naokolo sú rozhádzané stovky meteorologických strojov, almanachov, komunikačných modulov, stopy kopýt, strojové súčiastky, zrkadlá, šošovky a podobne.

Všetko je nejako zapojené do masívneho zariadenia na výrobu snehu, ale nič nefunguje. Skontroluješ malú obrazovku na jednom z komunikačných modulov: **Chyba 2023**. Neuvádza sa, čo táto chyba znamená, ale je na nej vytlačené telefónne číslo na podporu.

"Vitajte na linke podpory spoločnosti Weather Machines And So On, Inc. Ako vám môžeme pomôcť?" Vysvetlíš situáciu.

"Chyba 2023, hovoríte? To je chyba preťaženia, samozrejme! Znamená to, že máte pripojených príliš veľa komponentov. Skúste odpojiť niektoré komponenty a--" Vysvetlíš, že je tu stovky komponentov a ponáhľaš sa.

"No, pozrime sa, ako zlé to je; vidíte niekde veľké červené tlačidlo na resetovanie? Malo by byť na samostatnom module. Ak ho stlačíte, pravdepodobne nič neopraví, ale zobrazí, aké veľké je preťaženie." Po chvíli nájdeš tlačidlo resetovania; je také veľké, že na jeho stlačenie musíš použiť obe ruky. Na jeho obrazovke sa objaví:

```
SYSTÉMOVÉ PREŤAŽENIE!

Pripojené komponenty by vyžadovali výkon rovnajúci sa aspoň 100 hviezdam!

```


"Počkajte, koľko komponentov ste povedali, že je pripojených? S takým množstvom vybavenia by ste mohli vyrobiť sneh pre celé--" Zložíš hovor.

Ani zďaleka nemáš toľko hviezd – potrebuješ nájsť spôsob, ako odpojiť aspoň polovicu vybavenia, ale už sú Vianoce! Máš čas odpojiť len **tri drôty**.

Našťastie tu niekto nechal schému zapojenia (tvoj vstupný hádankový súbor), ktorá ukazuje, ako sú komponenty prepojené. Napríklad:


```
jqt: rhn
xhk nvd
rsh: frs pzl lsr
xhk: hfx
cmg: qnr nvd lhk bvb
rhn: xhk bvb hfx
bvb: xhk hfx pzl:
lsr hfx nvd qnr:
nvd ntq:
jqt hfx bvb xhk
nvd:lhk
lsr: lhk
rzs: qnr cmg lsr rsh
frs: qnr lhk lsr

```


Každý riadok ukazuje názov komponentu, dvojbodku a potom zoznam ďalších komponentov, ku ktorým je tento komponent pripojený. Pripojenia nie sú smerové; `abc: xyz` a `xyz: abc` predstavujú tú istú konfiguráciu. Každé spojenie medzi dvoma komponentmi je reprezentované len raz, takže niektoré komponenty sa môžu objaviť iba na ľavej alebo pravej strane dvojbodky.

V tomto príklade, ak odpojíš drôt medzi `hfx/pzl`, drôt medzi `bvb/cmg` a drôt medzi `nvd/jqt`, rozdelíš komponenty na dve oddelené skupiny:

- **9 komponentov:** `cmg, frs, lhk, lsr, nvd, pzl, qnr, rsh, rzs`
- **6 komponentov:** `bvb, hfx, jqt, ntq, rhn, xhk`

Vynásobením veľkostí týchto skupín dostaneš **54**.

### Zadanie:
Nájdi tri drôty, ktoré musíš odpojiť, aby si rozdelil komponenty na dve samostatné skupiny. Aké číslo dostaneš, keď vynásobíš veľkosti týchto dvoch skupín?

