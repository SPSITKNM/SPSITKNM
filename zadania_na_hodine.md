# SMART CITY CHALLENGE

**Tímový projekt pre dvojice**  
*Riešenie reálneho mestského problému pomocou programovania a AI nástrojov*

---

**Časový rozsah:** 3 × 45 minút  
**Tím:** 2 členovia  
**Cieľ:** Vytvoriť fungujúci systém, ktorý pomôže obyvateľom Nitry

---

## ZADANIE

Mestská rada Nitry má problém: obyvatelia nevedia, kde nájsť voľné verejné priestory. Vaša úloha je vytvoriť **fungujúci systém**, ktorý im v tom pomôže.

Využite svoje programátorské znalosti a doplňte ich o AI nástroje tam, kde to urýchli vašu prácu alebo vám pomôže s časťami, ktoré nepoznáte tak dobre.

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
- Pre každé miesto: názov, typ, kde sa nachádza, simulovaná obsadenosť
- Formát: Excel/CSV, JSON, databáza alebo priamo v kóde

### 2. Odporúčací algoritmus

- Používateľ zadá: polohu, typ aktivity, preferencie
- Program vypočíta skóre pre každý priestor
- Zobrazí top 3 odporúčania s odôvodnením
- Implementácia v C++, Python alebo inom jazyku

### 3. Používateľské rozhranie

- Webová aplikácia (HTML/CSS/JS, React, Vue)
- Desktop aplikácia (C++/Qt, Python/Tkinter)
- Alebo kvalitné konzolové rozhranie s menu
- Musí byť použiteľné a prehľadné

### 4. Ukážka funkčnosti

- 2-3 minútová demonštrácia pred triedou
- Vysvetlenie algoritmu a architektúry
- Live ukázka na reálnych príkladoch

---

## ČASOVÝ PLÁN

### 1. hodina (45 min) - Návrh a dátová príprava

**0-15 min: Architektúra a rozdelenie práce**
- Navrhite štruktúru systému
- Rozhodnite sa o technológiách (C++, Python, web stack)
- Rozdeľte si úlohy podľa silných stránok
- Vytvorte si repository / zdieľaný workspace

**15-40 min: Dataset a dátový model**
- Definujte dátovú štruktúru (class/struct/object)
- Vytvorte dataset 10-15 verejných priestorov
- Implementujte načítanie dát (zo súboru alebo hardcoded)
- Otestujte, že sa dáta správne čítajú

**40-45 min: Review a plánovanie**
- Skontrolujte dátovú štruktúru
- Naplánujte implementáciu algoritmu
- Dohodnite sa na API/rozhraní medzi časťami

**Výstup:**
- Funkčná dátová vrstva
- Jasný návrh systému
- Rozdelené úlohy

---

### 2. hodina (45 min) - Implementácia jadra

**0-35 min: Vývoj algoritmu a rozhrania**

**Backend/Algoritmus:**
- Implementujte skórovaciu funkciu
- Vytvorte funkciu na triedenie a filtrovanie priestorov
- Napíšte unit testy pre kritické funkcie
- Overujte výsledky na testovacích dátach

**Frontend/Rozhranie:**
- Vytvorte základné UI (web/desktop/konzola)
- Implementujte vstupné formuláre/dialógy
- Pripravte zobrazenie výsledkov
- Testujte používateľskú cestu

**35-45 min: Integrácia a testovanie**
- Prepojte algoritmus s rozhraním
- Vyskúšajte rôzne scenáre
- Opravte kritické chyby
- Zdokumentujte API ak treba

**Výstup:**
- Fungujúci prototyp
- Prepojené komponenty
- Základná funkcionalita

---

### 3. hodina (45 min) - Finalizácia a prezentácia

**0-30 min: Vylepšenia a bug fixing**
- Otestujte edge cases
- Vylepšite výpočet skóre ak treba
- Doplňte validácie vstupov
- Vylepšite UX (error handling, loading states)
- Code cleanup a komentáre

**30-40 min: Príprava demonštrácie**
- Pripravte si 2-3 demo scenáre
- Otestujte celý workflow
- Pripravte vysvetlenie algoritmu
- Vytvorte stručnú dokumentáciu (README)

**40-45 min: Prezentácia**
- Krátka ukážka systému
- Vysvetlenie riešenia a technológií
- Live demo na pripravených príkladoch

**Výstup:**
- Odladený systém
- Úspešná prezentácia
- Dokumentácia

---

## AKO SI ROZDELIŤ PRÁCU

### Odporúčané delenie podľa skills:

**Varianta 1: Backend/Frontend split**
- Člen A: Dátový model, algoritmus, API/logika
- Člen B: UI/UX, vizualizácia, integrácia

**Varianta 2: Full-stack rotácia**
- Obe strany pracujú na celom stacku
- Pair programming na zložitých častiach
- Code review navzájom

**Varianta 3: Vertical split**
- Člen A: Dáta + algoritmus + konzolové rozhranie
- Člen B: Webové rozhranie + vizualizácia + mapa

**Kľúčové:**
- Definujte jasné rozhrania medzi časťami
- Používajte version control (Git)
- Komunikujte o zmenách v API/štruktúrach
- Testujte integráciu priebežne

---

## TECHNOLÓGIE A NÁSTROJE

### Programovacie jazyky (vyberte podľa preferencie)

**C++**
- Výhody: výkon, OOP, znalosti z hodín
- Použitie: algoritmy, core logika
- Knižnice: Qt (GUI), nlohmann/json (JSON parsing)

**Python**
- Výhody: rýchly vývoj, veľa knižníc
- Použitie: prototyping, data processing, web backend
- Knižnice: pandas (dáta), Flask/FastAPI (backend), Tkinter (GUI)

**JavaScript/TypeScript**
- Výhody: web native, interaktivita
- Použitie: frontend, full-stack web app
- Frameworky: React, Vue, vanilla JS

### Frontend technológie

**Webové rozhranie:**
- HTML/CSS/JavaScript - základ
- Leaflet.js / Google Maps API - interaktívne mapy
- Chart.js / D3.js - grafy a vizualizácie
- Tailwind CSS / Bootstrap - styling
- React / Vue - ak chcete komponentovú architektúru

**Desktop aplikácia:**
- Qt (C++) - cross-platform GUI
- Tkinter (Python) - jednoduchšie GUI
- Electron (JS) - web technológie ako desktop app

### Backend a dáta

**Databázy (voliteľné):**
- SQLite - jednoduchá embedded DB
- JSON files - ľahký prístup
- In-memory - najrýchlejšie pre prototyp

**API štruktúra:**
- REST API - ak rozdeľujete frontend/backend
- Funkčné volania - ak je všetko v jednom jazyku

### AI nástroje - kedy a ako ich použiť

**Využite AI pre urýchlenie rutinných úloh:**
- Generovanie testovacích dát
- Boilerplate kód a setup projektu
- Debug zložitých errorov
- Syntax v jazykoch/frameworkoch, ktoré menej poznáte
- CSS/styling kde nemáte skúsenosti

**Vlastnú prácu a logiku si programujte sami:**
- Architektúra systému
- Core algoritmus a výpočty
- Kritická biznis logika
- Integrácia komponentov

**Inteligentné použitie AI:**
- Nechajte si vysvetliť koncepty, ktoré nepoznáte
- Konzultujte prístupy a riešenia
- Využite na code review a optimalizáciu
- Učte sa z vygenerovaného kódu, neskopírujte slepé

**Príklad rozumného workflow:**
```
1. Navrhnite si algoritmus sami na papieri
2. Implementujte ho
3. Ak narážate na problém: debugujte, potom sa opýtajte AI
4. Pochopte riešenie, ktoré AI navrhne
5. Integrujte to do svojho kódu vlastným spôsobom
```

---

## DATASET - ŠTRUKTÚRA DÁT

### Dátový model

**C++ štruktúra:**
```cpp
struct Priestor {
    string nazov;
    string typ; // "park", "ihrisko", "fitness", "oddych"
    double lat;
    double lon;
    int kapacita;
    int obsadenost; // 0-100%
    int kvalita; // 1-5
    vector<string> vybavenie;
};
```

**Python class:**
```python
class Priestor:
    def __init__(self, nazov, typ, lat, lon, kapacita, obsadenost, kvalita):
        self.nazov = nazov
        self.typ = typ
        self.lat = lat
        self.lon = lon
        self.kapacita = kapacita
        self.obsadenost = obsadenost
        self.kvalita = kvalita
        self.vybavenie = []
```

**JSON formát:**
```json
{
  "priestory": [
    {
      "id": 1,
      "nazov": "Park Sihoť",
      "typ": "park",
      "lat": 48.3069,
      "lon": 18.0864,
      "kapacita": 50,
      "obsadenost": 30,
      "kvalita": 4,
      "vybavenie": ["lavičky", "stromy", "chodníky"]
    }
  ]
}
```

### Minimálne dáta

Vytvorte aspoň 10-15 priestorov s:
- Realistické názvy a GPS súradnice Nitry
- Rôzne typy (mix parkov, ihrísk, fitness zón)
- Variabilná obsadenosť (10-90%)
- Rôzna kvalita a vybavenie

---

## ALGORITMUS - IMPLEMENTÁCIA

### Základný prístup

**1. Vstupné parametre:**
```cpp
struct UzivatelskePoziadavky {
    double mojLat;
    double mojLon;
    string typAktivity;
    double maxVzdialenost; // km
    int priorita; // 1=vzdialenost, 2=kvalita, 3=volne_miesto
};
```

**2. Výpočet vzdialenosti:**

Použite Manhattan distance pre jednoduchosť alebo Haversine formula pre presnosť:

```cpp
double vypocitajVzdialenost(double lat1, double lon1, double lat2, double lon2) {
    // Manhattan aproximácia (jednoduchšie):
    double km_per_degree_lat = 111.0;
    double km_per_degree_lon = 111.0 * cos(lat1 * PI / 180.0);
    double dlat = abs(lat2 - lat1) * km_per_degree_lat;
    double dlon = abs(lon2 - lon1) * km_per_degree_lon;
    return dlat + dlon;
}
```

**3. Skórovacia funkcia:**
```cpp
double vypocitajSkore(const Priestor& priestor, const UzivatelskePoziadavky& poziadavky) {
    double skore = 100.0;
    
    // 1. Vzdialenosť (čím ďalej, tým horšie)
    double vzdialenost = vypocitajVzdialenost(
        poziadavky.mojLat, poziadavky.mojLon,
        priestor.lat, priestor.lon
    );
    skore -= vzdialenost * 15;
    
    // 2. Obsadenosť (preferujeme menej preplnené)
    skore -= priestor.obsadenost * 0.4;
    
    // 3. Typ match (bonus ak sedí typ aktivity)
    if (priestor.typ == poziadavky.typAktivity) {
        skore += 25;
    }
    
    // 4. Kvalita (lepšia údržba = vyššie skóre)
    skore += priestor.kvalita * 3;
    
    return max(0.0, skore);
}
```

**4. Triedenie a výber top 3:**
```cpp
vector<Priestor> najdiNajlepsiePriestory(vector<Priestor>& priestory, 
                                         UzivatelskePoziadavky& poziadavky) {
    // Vypočítaj skóre pre každý priestor
    vector<pair<double, Priestor>> skorovane;
    for (auto& p : priestory) {
        double skore = vypocitajSkore(p, poziadavky);
        skorovane.push_back({skore, p});
    }
    
    // Zoraď podľa skóre (zostupne)
    sort(skorovane.begin(), skorovane.end(), 
         [](auto& a, auto& b) { return a.first > b.first; });
    
    // Vráť top 3
    vector<Priestor> vysledok;
    for (int i = 0; i < min(3, (int)skorovane.size()); i++) {
        vysledok.push_back(skorovane[i].second);
    }
    return vysledok;
}
```

### Pokročilé vylepšenia (voliteľné)

- Váhy pre priority (ak užívateľ uprednostňuje vzdialenosť vs kvalitu)
- Časová predikovateľnosť (ak je 17:00, ihriská budú plnešie)
- Multi-kriteriálne rozhodovanie (Pareto optimalizácia)
- Clustering podobných priestorov

---

## POUŽÍVATEĽSKÉ ROZHRANIE

### Minimálne požiadavky

**Vstup:**
- Výber typu aktivity (dropdown/radio buttons)
- Zadanie polohy (GPS alebo výber z mapy)
- Voliteľné: maximálna vzdialenosť, priority

**Výstup:**
- Top 3 odporúčania s:
  - Názov a typ priestoru
  - Vzdialenosť a čas chôdze
  - Aktuálna obsadenosť
  - Skóre a dôvod odporúčania
- Voliteľne: zobrazenie na mape

### Webová aplikácia - odporúčaná štruktúra

**HTML štruktúra:**
```html
<div class="container">
    <h1>Nájdi voľný priestor v Nitre</h1>
    
    <form id="searchForm">
        <select id="typAktivity">
            <option value="park">Park</option>
            <option value="ihrisko">Ihrisko</option>
            <option value="fitness">Fitness</option>
        </select>
        <button type="submit">Hľadať</button>
    </form>
    
    <div id="vysledky"></div>
    <div id="mapa"></div>
</div>
```

**JavaScript logika:**
```javascript
// Načítanie dát
fetch('data/priestory.json')
    .then(response => response.json())
    .then(data => inicializuj(data));

// Výpočet skóre (môže byť aj na backende)
function vypocitajSkore(priestor, poziadavky) {
    let skore = 100;
    skore -= priestor.vzdialenost * 15;
    skore -= priestor.obsadenost * 0.4;
    if (priestor.typ === poziadavky.typ) skore += 25;
    skore += priestor.kvalita * 3;
    return Math.max(0, skore);
}

// Zobrazenie výsledkov
function zobrazVysledky(topPriestory) {
    const container = document.getElementById('vysledky');
    container.innerHTML = topPriestory.map((p, i) => `
        <div class="priestor">
            <h3>${i+1}. ${p.nazov}</h3>
            <p>Vzdialenosť: ${p.vzdialenost.toFixed(1)} km</p>
            <p>Obsadenosť: ${p.obsadenost}%</p>
            <p>Skóre: ${p.skore.toFixed(0)}</p>
        </div>
    `).join('');
}
```

### Konzolové rozhranie - ak nechcete web

```cpp
int main() {
    vector<Priestor> priestory = nacitajPriestory();
    
    cout << "=== SMART CITY NITRA ===\n\n";
    cout << "Typ aktivity:\n";
    cout << "1. Park\n2. Ihrisko\n3. Fitness\n";
    cout << "Vyberte (1-3): ";
    int vyber;
    cin >> vyber;
    
    UzivatelskePoziadavky poziadavky;
    poziadavky.typAktivity = (vyber == 1) ? "park" : 
                             (vyber == 2) ? "ihrisko" : "fitness";
    poziadavky.mojLat = 48.3081;  // centrum Nitry
    poziadavky.mojLon = 18.0873;
    
    vector<Priestor> top = najdiNajlepsiePriestory(priestory, poziadavky);
    
    cout << "\n=== TOP 3 ODPORUČANIA ===\n";
    for (int i = 0; i < top.size(); i++) {
        cout << "\n" << (i+1) << ". " << top[i].nazov << "\n";
        cout << "   Typ: " << top[i].typ << "\n";
        cout << "   Obsadenosť: " << top[i].obsadenost << "%\n";
        cout << "   Kvalita: " << top[i].kvalita << "/5\n";
    }
    
    return 0;
}
```

---

## HODNOTENIE

**Celkovo: 100 bodov**

### Technická implementácia (60 bodov)

**Dátová vrstva (15 bodov):**
- Správna štruktúra dát
- Načítanie a spracovanie
- Validácia dát

**Algoritmus (25 bodov):**
- Funkčnosť a správnosť výpočtov
- Zohľadnenie všetkých kritérií
- Kvalita kódu (čitateľnosť, štruktúra)
- Efektivita riešenia

**Rozhranie (20 bodov):**
- Funkčnosť a použiteľnosť
- Error handling
- UX kvalita
- Integrácia s algoritmom

### Kvalita kódu (25 bodov)

**Architektúra (10 bodov):**
- Modulárnosť a separation of concerns
- Čistý kód, konvencie
- Rozumné použitie OOP/funkcií

**Dokumentácia (8 bodov):**
- Komentáre v kóde
- README s inštrukciami
- API dokumentácia ak relevantné

**Testing (7 bodov):**
- Testovanie edge cases
- Validácia vstupov
- Robustnosť

### Prezentácia (10 bodov)

- Jasné vysvetlenie riešenia
- Úspešné live demo
- Odpovede na otázky

### Tímová práca (5 bodov)

- Git history (commity od oboch)
- Rozumné rozdelenie práce
- Code reviews

### Bonusy (až +20 bodov)

**Interaktívna mapa (+5 bodov)**
- Leaflet.js / Google Maps integrácia
- Zobrazenie priestorov na mape

**Pokročilá vizualizácia (+4 body)**
- Grafy obsadenosti
- Dashboard s metrikami

**Databáza (+3 body)**
- SQLite / MongoDB integrácia
- CRUD operácie

**Unit testy (+3 body)**
- Test coverage základných funkcií
- Automatizované testovanie

**Pokročilý algoritmus (+5 bodov)**
- Machine learning predikovateľnosť
- Multi-objective optimization
- Zaujímavé features

---

## TIPY PRE EFEKTÍVNU PRÁCU

### Architektúra

**Separation of concerns:**
```
data/          - Dataset, data loading
core/          - Algoritmus, business logika
ui/            - Rozhranie (web/desktop/console)
utils/         - Helper funkcie
tests/         - Unit testy
```

**Design patterns ktoré sa hodia:**
- Strategy pattern pre rôzne skórovacie algoritmy
- Repository pattern pre dátovú vrstvu
- MVC pre webové aplikácie

### Vývojový workflow

**1. Test-driven development:**
```cpp
void testVypocetVzdialenosti() {
    double dist = vypocitajVzdialenost(48.3, 18.0, 48.4, 18.1);
    assert(dist > 0 && dist < 20);
}
```

**2. Implementujte po častiach:**
- Najprv dátová vrstva
- Potom algoritmus (otestujte konzolovo)
- Nakoniec UI

**3. Refaktorujte priebežne:**
- DRY principle
- Extract functions
- Čistý naming

### Best practices

**Git workflow:**
```bash
git checkout -b feature/algoritmus
# Programujte
git commit -m "Implementovaná skórovacia funkcia"
git push
# Pull request + review od partnera
```

**Komentáre:**
```cpp
// Vypočíta skóre priestoru na základe viacerých kritérií
// @param priestor - údaje o priestore
// @param poziadavky - požiadavky používateľa
// @return skóre 0-100, vyššie je lepšie
double vypocitajSkore(const Priestor& priestor, 
                     const UzivatelskePoziadavky& poziadavky);
```

**Error handling:**
```python
def vypocitaj_skore(priestor, poziadavky):
    if priestor is None:
        raise ValueError("Priestor nemôže byť None")
    if poziadavky.maxVzdialenost < 0:
        raise ValueError("Vzdialenosť musí byť kladná")
    # ...
```

---

## KONTROLNÝ ZOZNAM

**Pred odovzdaním skontrolujte:**

**Kód:**
- [ ] Všetky funkcie fungujú
- [ ] Nie sú tam hardcoded hodnoty, ktoré by mali byť konfigurovateľné
- [ ] Kód je naformátovaný konzistentne
- [ ] Komentáre pre nečitateľné časti
- [ ] Žiadne TODO alebo FIXME v produkčnom kóde

**Funkcionalita:**
- [ ] Algoritmus vracia zmysluplné výsledky
- [ ] Edge cases sú ošetrené (prázdny dataset, žiadny match)
- [ ] UI je použiteľné a intuitívne
- [ ] Všetko je otestované

**Dokumentácia:**
- [ ] README.md s inštrukciami na spustenie
- [ ] Popis architektúry
- [ ] Zoznam použitých technológií
- [ ] Známe limitácie ak nejaké sú

**Prezentácia:**
- [ ] Demo scenár pripravený
- [ ] Vysvetlenie algoritmu
- [ ] Screenshots / video záloha ak by zlyhalo live

---

## NA ZÁVER

Toto je príležitosť ukázať svoje programátorské skills na reálnom probléme. 

**Kľúčové zásady:**

**Píšte profesionálny kód**
- Clean code principles
- Proper naming, structure
- Testujte a validujte

**AI ako nástroj, nie náhrada**
- Využite na rutinné úlohy a učenie
- Core logika je vaša práca
- Pochopte každý riadok kódu vo svojom projekte

**Iterujte a testujte**
- Malé kroky s testovaním
- Refaktorujte priebežne
- Code review navzájom

**Komunikujte v tíme**
- Git workflow
- Jasné rozhrania medzi časťami
- Pair programming na zložitých častiach

---

**Veľa úspechov!**
