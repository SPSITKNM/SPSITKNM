# SMART CITY CHALLENGE

**Tímový projekt pre dvojice**  
*Riešenie reálneho mestského problému pomocou programovania a AI nástrojov*

---

**Časový rozsah:** 3 × 45 minút  
**Tím:** 2 členovia  
**Cieľ:** Vytvoriť fungujúci systém, ktorý pomôže obyvateľom Nitry

---

## ZADANIE

Mestská rada Nitry má problém: obyvatelia nevedia, kde nájsť voľné verejné priestory. Vaša úloha je vytvoriť **jednoduchý systém**, ktorý im v tom pomôže.

Nemusíte vytvoriť dokonalé riešenie - dôležité je, aby **niečo fungovalo** a ukázalo základnú myšlienku.

---

## PROBLÉM

### Čo sa deje v meste?

- Niektoré parky a ihriská sú preplnené, iné prázdne
- Ľudia nevedia, kde nájsť voľné miesto na prechádzku alebo šport
- Rodičia chodia s deťmi na plné ihrisko, hoci iné v meste je prázdne
- Mesto nevie, ktoré priestory sú skutočne využívané

### Čo by pomohlo?

Systém, ktorý:
- Povie používateľovi, kde je teraz voľno
- Odporučí mu najlepší priestor podľa toho, čo chce robiť
- Ukáže to na mape alebo v prehľadnej forme

---

## ČO MUSÍTE VYTVORIŤ

Váš projekt musí obsahovať **tieto tri časti**:

### 1. Dáta o verejných priestoroch

- Zoznam minimálne 10-15 miest v Nitre (parky, ihriská, fitness zóny)
- Pre každé miesto: názov, typ, kde sa nachádza, koľko ľudí tam je
- Môžete to mať v Exceli, CSV súbore alebo priamo v kóde

### 2. Program, ktorý odporučí najlepší priestor

- Používateľ zadá: kde je, čo chce robiť
- Program vypočíta, ktorý priestor je najlepší
- Zobrazí top 3 odporúčania s dôvodom

### 3. Jednoduché rozhranie

- Webová stránka ALEBO konzolový program
- Používateľ vie zadať svoje preferencie
- Systém zobrazí výsledky

### 4. Krátka ukážka na konci

- Ukážete fungujúci systém pred triedou (2-3 minúty)
- Vysvetlíte, ako to funguje
- Nemusíte mať PowerPoint - stačí ukázať to, čo ste vytvorili

---

## ČASOVÝ PLÁN

### 1. hodina (45 min) - Začíname

**0-10 min: Prečítajte zadanie a poradte sa**
- Čo budete robiť?
- Ako si rozdelíte prácu?
- Kto bude robiť čo?

**10-40 min: Vytvorte dáta**
- Napíšte zoznam 10-15 verejných priestorov v Nitre
- Pre každý napíšte: názov, typ, približnú polohu
- Vymyslite, koľko percent ľudí tam je (napr. 20%, 80%)
- Môžete použiť Excel, Google Sheets alebo napísať priamo do kódu

**40-45 min: Naplánujte ďalší krok**
- Čo budete robiť v druhej hodine?
- Aké nástroje použijete?

**Výstup:**
- Zoznam miest s dátami
- Jasný plán, ako budete pokračovať

---

### 2. hodina (45 min) - Programovanie

**0-35 min: Naprogramujte hlavnú funkcionalitu**

Jeden zo členov môže robiť:
- C++ alebo Python program, ktorý počíta skóre pre každý priestor
- Program vezme vstup (kde som, čo chcem) a povie, kam ísť

Druhý člen môže robiť:
- Jednoduchú webovú stránku (HTML + JavaScript)
- Alebo konzolové menu v C++/Python

Príklad jednoduchého algoritmu:
```
Skóre = 100 - (vzdialenosť_km × 20) - (obsadenosť × 50) + (ak je správny typ: +30)
```

**35-45 min: Otestujte, či to funguje**
- Skúste zadať rôzne vstupy
- Opravte chyby
- Ak niečo nefunguje, opýtajte sa ChatGPT/Claude

**Výstup:**
- Fungujúci kód, ktorý niečo počíta
- Aspoň základné rozhranie

---

### 3. hodina (45 min) - Dokončenie

**0-30 min: Spravte to pekné a funkčné**
- Spojte dáta + algoritmus + rozhranie
- Vyskúšajte celý systém
- Opravte problémy

**30-40 min: Pripravte ukážku**
- Čo poviete triede?
- Aký príklad ukážete?
- Vyskúšajte si to raz

**40-45 min: Ukážete to triede**
- Krátka ukážka (2-3 minúty na tím)
- Povedzete: aký bol problém, čo ste vytvorili, ukážete ako to funguje

**Výstup:**
- Fungujúci systém
- Úspešná ukážka

---

## AKO SI ROZDELIŤ PRÁCU?

Nie je nutné mať presné role. Tu sú možnosti:

### Možnosť A
- **Jeden člen:** Dáta + algoritmus (C++/Python kód)
- **Druhý člen:** Webová stránka alebo rozhranie

### Možnosť B  
- **Spoločne:** Naplánujete a vytvoríte dáta
- **Samostatne:** Jeden robí výpočty, druhý rozhranie
- **Spoločne:** Spojíte to a testujete

### Možnosť C
- **Obaja:** Pracujete na tom istom, pomáhate si
- Jeden píše kód, druhý testuje a hľadá chyby

**Dôležité:** Komunikujte! Pýtajte sa navzájom, pomáhajte si.

---

## NÁSTROJE, KTORÉ MÔŽETE POUŽIŤ

### AI Asistenti (použite ich naplno!)

**ChatGPT alebo Claude:**
- "Napíš mi C++ program, ktorý vypočíta vzdialenosť medzi dvoma miestami"
- "Tento kód mi hádže chybu, pomôž mi"
- "Vytvor mi HTML stránku s formulárom"
- "Vygeneruj mi zoznam 15 parkov v Nitre s vymyslenými dátami"

**Claude Artifacts:**
- Napíšete: "Vytvor webovú stránku s mapou a formulárom"
- Okamžite dostanete fungujúcu stránku
- Môžete ju upravovať priamo v prehliadači

### Programovacie jazyky

**C++** (ak to poznáte z hodín)
- Konzolový program
- Načítanie vstupu od používateľa
- Výpočty a výpis výsledkov

**Python** (jednoduchší než C++)
- Ľahko sa učí
- AI vám pomôže napísať kód
- Ideálne pre začiatočníkov

**JavaScript + HTML** (pre webové rozhranie)
- Vytvoríte stránku
- Formulár pre vstup
- Zobrazenie výsledkov

### Online nástroje (nemusíte nič inštalovať)

**Replit.com**
- Programujte priamo v prehliadači
- C++, Python, JavaScript
- Okamžite vidíte výsledky

**CodePen / JSFiddle**
- Pre HTML/CSS/JavaScript
- Skvelé na webové prototypy

**Google Sheets / Excel**
- Pre dáta
- Grafy a tabuľky

---

## PRÍKLADY, ČO VYTVORIŤ

### Jednoduchá verzia (ak nemáte veľa skúseností)

**Dáta v kóde:**
```python
priestory = [
    {"nazov": "Park Sihoť", "typ": "park", "vzdialenost_km": 1.2, "obsadenost": 30},
    {"nazov": "Ihrisko Chrenová", "typ": "ihrisko", "vzdialenost_km": 0.8, "obsadenost": 80},
    {"nazov": "Fitness Kalvária", "typ": "fitness", "vzdialenost_km": 2.1, "obsadenost": 10}
]
```

**Jednoduchý výpočet:**
```python
def vypocitaj_skore(priestor, preferovany_typ):
    skore = 100
    skore = skore - (priestor["vzdialenost_km"] * 20)
    skore = skore - (priestor["obsadenost"] * 0.5)
    
    if priestor["typ"] == preferovany_typ:
        skore = skore + 30
    
    return skore
```

**Konzolový výstup:**
```
Čo chcete robiť? (park/ihrisko/fitness): park
Hľadám najlepšie miesto pre vás...

Top 3 odporúčania:
1. Park Sihoť (skóre: 91)
   - Vzdialenosť: 1.2 km
   - Obsadenosť: 30%
   
2. Fitness Kalvária (skóre: 53)
   - Vzdialenosť: 2.1 km
   - Obsadenosť: 10%

3. Ihrisko Chrenová (skóre: 30)
   - Vzdialenosť: 0.8 km
   - Obsadenosť: 80%
```

### Stredná verzia (ak máte základné skúsenosti)

- Dataset v Excel súbore alebo CSV
- C++ alebo Python program, ktorý načíta dáta zo súboru
- Jednoduchá webová stránka s formulárom
- Program vypočíta výsledky a zobrazí ich

### Pokročilá verzia (ak chcete ísť ďalej)

- Interaktívna mapa s Google Maps alebo Leaflet.js
- Grafy obsadenosti
- Filtre (vzdialenosť, typ, kvalita)
- Pekný dizajn s CSS

---

## DATASET - ČO POTREBUJETE

Pre každý verejný priestor zapíšte:

**Základné informácie:**
- Názov (napr. "Park na Sihoti")
- Typ (park, ihrisko, fitness zóna, oddychová zóna)
- Približná poloha (adresa alebo GPS súradnice)

**Simulované dáta:**
- Obsadenosť v percentách (vymyslite realistické čísla)
- Vzdialenosť od centra Nitry (v km)
- Kvalita (môžete dať 1-5 hviezdičiek)

**Príklad tabuľky:**

| Názov | Typ | Vzdialenosť (km) | Obsadenosť (%) | Kvalita |
|-------|-----|------------------|----------------|---------|
| Park Sihoť | park | 1.2 | 30 | 4 |
| Ihrisko Chrenová | ihrisko | 0.8 | 80 | 3 |
| Fitness Kalvária | fitness | 2.1 | 10 | 5 |
| Park Zobor | park | 1.5 | 45 | 4 |
| Oddychová zóna Centrum | oddych | 0.3 | 90 | 3 |

Stačí 10-15 takýchto záznamov. Čísla si môžete vymyslieť - nejde o presnosť, ale o to, aby mal algoritmus s čím pracovať.

---

## ALGORITMUS - AKO ROZHODNÚŤ, ČO JE NAJLEPŠIE?

### Základná myšlienka

Každý priestor dostane **skóre**. Čím vyššie skóre, tým lepšie.

### Čo ovplyvňuje skóre?

**1. Vzdialenosť (čím bližšie, tým lepšie)**
- Blízko (0-1 km): výborne
- Stredne ďaleko (1-2 km): ok
- Ďaleko (2+ km): horšie

**2. Obsadenosť (čím menej ľudí, tým lepšie)**
- 0-30%: takmer prázdne, super
- 30-70%: normálne obsadené
- 70-100%: preplnené, radšej nie

**3. Typ priestoru (musí sedieť s tým, čo chcete robiť)**
- Ak chcete cvičiť, fitness zóna je lepšia než park
- Ak chcete s deťmi, ihrisko je lepšie než lavička

**4. Kvalita (ak to máte v dátach)**
- Novšie, lepšie udržiavané = vyššie skóre

### Jednoduchý vzorec

```
Skóre = 100 - (vzdialenosť × 20) - (obsadenosť × 0.5) + bonus_za_typ + bonus_za_kvalitu

Kde:
- vzdialenosť: v kilometroch
- obsadenosť: v percentách (0-100)
- bonus_za_typ: +30 ak sedí, 0 ak nie
- bonus_za_kvalitu: +10 ak je kvalita 5, +5 ak je 4, atď.
```

**Príklad:**
```
Park Sihoť:
- vzdialenosť: 1.2 km
- obsadenosť: 30%
- typ: park (zhoduje sa s "chcem ísť do parku")
- kvalita: 4

Skóre = 100 - (1.2 × 20) - (30 × 0.5) + 30 + 5
Skóre = 100 - 24 - 15 + 30 + 5 = 96
```

Nemusíte použiť presne tento vzorec - môžete si vymyslieť vlastný! Dôležité je, aby dával zmysel.

---

## WEBOVÉ ROZHRANIE - MOŽNOSTI

### Verzia 1: Superjednoduchá (HTML + JavaScript)

```html
<!DOCTYPE html>
<html>
<head>
    <title>Nájdi voľný priestor v Nitre</title>
</head>
<body>
    <h1>Kam chceš ísť?</h1>
    
    <label>Typ aktivity:</label>
    <select id="typ">
        <option>park</option>
        <option>ihrisko</option>
        <option>fitness</option>
    </select>
    
    <button onclick="najdiPriestor()">Nájdi najlepší priestor</button>
    
    <div id="vysledok"></div>
    
    <script>
        function najdiPriestor() {
            // Tu bude váš algoritmus
            document.getElementById("vysledok").innerHTML = 
                "Odporúčame: Park Sihoť (skóre: 96)";
        }
    </script>
</body>
</html>
```

### Verzia 2: S mapou (použite Leaflet.js alebo Google Maps)

- Mapa Nitry
- Body pre každý priestor
- Kliknutie zobrazí detail
- Farebné označenie (zelená = voľno, červená = plné)

### Verzia 3: S AI pomocou (Claude Artifacts)

Napíšte do Claude:
```
Vytvor webovú stránku pre Smart City Challenge.
Stránka musí mať:
- Formulár kde používateľ vyberie typ aktivity
- Tlačidlo "Hľadaj"
- Zobrazenie top 3 odporúčaní
- Jednoduchý, moderný dizajn
```

Claude vám vygeneruje celú stránku, ktorú môžete hneď použiť a upravovať.

---

## HODNOTENIE

**Celkovo: 100 bodov**

### Fungujúci systém (60 bodov)

**Dáta (15 bodov):**
- Máte aspoň 10 miest
- Dáta dávajú zmysel
- Sú správne použité v programe

**Algoritmus (25 bodov):**
- Program funguje
- Vypočíta skóre pre priestory
- Výsledky dávajú zmysel
- Zobrazí top 3 odporúčania

**Rozhranie (20 bodov):**
- Používateľ vie zadať vstup
- Systém zobrazí výsledky
- Je to použiteľné a funguje to

### Kvalita riešenia (25 bodov)

**Kód (15 bodov):**
- Kód je čitateľný
- Funguje bez veľkých chýb
- Je rozumne štruktúrovaný

**Dizajn (10 bodov):**
- Rozhranie vypadá rozumne
- Je prehľadné a zrozumiteľné
- Dáta sú dobre zobrazené

### Ukážka pred triedou (10 bodov)

- Ukázali ste funkčný systém
- Vysvetlili ste, ako to funguje
- Demo prešlo bez veľkých problémov

### Práca v tíme (5 bodov)

- Viditeľne ste spolupracovali
- Obaja ste niečo robili
- Pomáhali ste si

### Bonusy (až +20 bodov)

**Mapa (+5 bodov)**
- Interaktívna mapa s priestormi

**Grafy (+3 body)**
- Graf obsadenosti alebo iný vizuál

**Výnimočný dizajn (+3 body)**
- Naozaj pekné a profesionálne rozhranie

**Pokročilý algoritmus (+5 bodov)**
- Zohľadňuje viac faktorov
- Použili ste zaujímavý prístup

**Kreativita (+4 body)**
- Pridali ste niečo naviac, čo nebolo v zadaní
- Prišli ste s vlastným nápadom

---

## TIPY A RADY

### Ak ste nikdy neprogramovali

**Nepanikárte!** AI nástroje vám pomôžu:

1. Otvorte ChatGPT alebo Claude
2. Napíšte: "Potrebujem vytvoriť program pre Smart City Challenge. Program má..."
3. AI vám napíše kód
4. Skopírujte ho, vyskúšajte
5. Ak niečo nefunguje, opýtajte sa: "Tento kód mi hádže chybu..."

**Príklad konverzácie s AI:**
```
Vy: Napíš mi Python program, ktorý má zoznam parkov v Nitre. 
    Každý park má názov, vzdialenosť a obsadenosť. 
    Program spýta používateľa, aký typ miesta hľadá, 
    a odporučí mu 3 najlepšie možnosti.

AI: [vygeneruje kompletný kód]

Vy: Super! Teraz pridaj, aby to zohľadňovalo aj vzdialenosť.

AI: [upraví kód]
```

### Ak máte nejaké skúsenosti

- Začnite s najjednoduchšou verziou, čo funguje
- Potom postupne pridávajte funkcie
- Testujte často (po každej zmene)
- Používajte AI na urýchlenie práce

### Časté problémy a riešenia

**"Nevieme, čo robiť"**
- Začnite s dátami - vytvorte Excel s 10 miestami
- Potom skúste jednoduchý výpočet v Pythone
- Postupujte krok po kroku

**"Kód nám nefunguje"**
- Skopírujte chybovú hlášku
- Vložte ju do ChatGPT s otázkou "Ako to opravím?"
- Skúste navrhované riešenia

**"Nevieme, ako spojiť dáta a program"**
- Začnite s dátami priamo v kóde
- Až keď to funguje, skúste načítať zo súboru
- Opýtajte sa AI: "Ako načítam CSV súbor v Pythone?"

**"Nestíhame"**
- Zjednodušte - stačí základná verzia
- Funkčnosť je dôležitejšia než krása
- Radšej jednoduché, čo funguje

**"Nevieme, ako rozdeliť prácu"**
- Prvú hodinu pracujte spolu
- Druhú hodinu: jeden kód, druhý rozhranie
- Tretiu hodinu zas spolu - spájanie a testovanie

### Ako využiť AI nástroje efektívne

**Buďte konkrétni:**
- Nie: "Potrebujem pomoc s kódom"
- Áno: "Potrebujem Python funkciu, ktorá zoradí zoznam podľa skóre"

**Iterujte:**
- Začnite so základnou verziou
- Postupne vylepšujte: "Teraz pridaj..." , "Zmeň toto..."

**Testujte výsledky:**
- AI nie je dokonalá
- Vždy skúste, či kód funguje
- Ak nie, pýtajte sa ďalej

**Učte sa z toho:**
- Nechajte si AI vysvetliť, ako kód funguje
- "Vysvetli mi tento kód riadok po riadku"
- Nabudúce to pochopíte lepšie

---

## KONTROLNÝ ZOZNAM PRED ODOVZDANÍM

Skontrolujte si, že máte:

**Dáta:**
- [ ] Aspoň 10-15 verejných priestorov
- [ ] Každý má názov, typ, vzdialenosť, obsadenosť
- [ ] Dáta sú v Exceli / CSV / v kóde

**Algoritmus:**
- [ ] Program funguje bez kritických chýb
- [ ] Vypočíta skóre pre každý priestor
- [ ] Zobrazí top 3 odporúčania
- [ ] Výsledky dávajú zmysel

**Rozhranie:**
- [ ] Používateľ vie zadať preferencie
- [ ] Systém zobrazí výsledky
- [ ] Je to použiteľné (aspoň základne)

**Ukážka:**
- [ ] Máte pripravený príklad, čo ukážete
- [ ] Vyskúšali ste, že to funguje
- [ ] Viete vysvetliť, ako to funguje

**Spolupráca:**
- [ ] Obaja členovia tímu niečo urobili
- [ ] Viete povedať, kto čo robil

---

## NA ZÁVER

**Toto je vaša príležitosť vyskúšať si niečo reálne!**

Nemusíte vytvoriť dokonalý systém. Dôležité je:
- Aby niečo fungovalo
- Aby to riešilo problém (aspoň čiastočne)
- Aby ste sa pri tom niečo naučili
- Aby ste si to užili

### Pamätajte:

**Používajte AI nástroje naplno**
- Sú tu preto, aby vám pomohli
- Nie je to podvádzanie, ale moderný spôsob práce

**Komunikujte medzi sebou**
- Pýtajte sa partnera, ako mu to ide
- Pomáhajte si vzájomne
- Dvaja vymyslia viac než jeden

**Jednoduché, čo funguje > komplikované, čo padá**
- Radšej základná verzia, ktorá beží
- Než ambiciózna, ktorá nefunguje

**Testujte priebežne**
- Po každej zmene vyskúšajte, či to funguje
- Nečakajte do poslednej chvíle

**Nebojte sa pýtať**
- Učiteľa, spolužiakov, AI
- Lepšie sa opýtať než strácať čas

---

**Veľa šťastia a bavte sa!**
