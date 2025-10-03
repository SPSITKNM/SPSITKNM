
# Názov projektu (+ meno riešiteľa)
- **Názov projektu**: [Názov projektu]
- **Meno riešiteľa**: [Meno študenta]
- **Login**: [Login]

---

## Seznam kapitol - částí projektu
1. Úvod
2. Dôvod a okolnosti zavedenia riešenia
3. Popis projektu (slovné zadanie, popis od zákazníka)
4. Analýza požiadaviek
5. Systémové požiadavky (FURPS)
6. Kritické situácie
7. Hranice systému
8. Kontext prostredia
9. Charakteristika aktérov
10. Use Case diagram
11. Scenáre (Implementácia Use Case)
12. Sekvenčný diagram
13. Triedny diagram
14. Záver

---

## Popis zmien v dokumentu
Tento dokument reflektuje všetky zmeny a vylepšenia, ktoré boli vykonané v predchádzajúcich verziách, ako aj aktualizácie implementácie a návrhu systému.

---

## Dôvod a okolnosti zavedenia riešenia
Tento projekt je navrhnutý s cieľom zlepšiť proces diagnostiky automobilov. Zavedenie jednotného systému pre diagnostiku umožní mechanikom a technikom prístup k rôznym riadiacim jednotkám a ich diagnostickým kódom bez nutnosti používať rozličné doplnkové softvéry. Cieľom je zvýšiť efektivitu, minimalizovať chyby a ušetriť čas pri diagnostike vozidiel.

---

## Slovné zadanie, popis projektu od zákazníka
Cieľom tohto projektu je vytvoriť prehľadný a intuitívny diagnostický systém pre správu automobilov. Tento systém bude slúžiť na diagnostiku závad na vozidlách a analýzu dát z riadiacich jednotiek (ECU). Funkcionality budú zahŕňať: čítanie diagnostických kódov, zobrazovanie meraných hodnôt, testovanie aktuátorov a predikciu údržbových upozornení.

---

## Seznam modulů projektu a jejich významných atributů
1. **Modul pre čítanie diagnostických kódov (DTC)**
   - Atribúty: diagnostické kódy, stav vozidla, počet chýb
   - Unikátna identifikácia objektov: Kód chyby, ID vozidla

2. **Užívateľské rozhranie (UI)**
   - Atribúty: grafické rozhranie, interaktívne prvky
   - Unikátna identifikácia objektov: ID užívateľa, ID diagnostického nástroja

3. **Komunikačný modul**
   - Atribúty: pripojenie k OBD-II, synchronizácia s externými zariadeniami
   - Unikátna identifikácia objektov: Komunikačné protokoly, ID zariadení

4. **Dátový analytický modul**
   - Atribúty: analýza dát, predikčné modely
   - Unikátna identifikácia objektov: Predikčný model, ID analýzy

5. **Modul pre aktualizácie softvéru**
   - Atribúty: verzia softvéru, súbor na aktualizáciu
   - Unikátna identifikácia objektov: Verzia systému, ID aktualizácie

---

## Systémové požiadavky FURPS
1. **Funkčnosť (Functionality - F)**
   - Možnosť zobraziť pamäť závad
   - Čítanie meraných hodnôt z ECU
   - Testovanie aktuátorov a resetovanie parametrov

2. **Vhodnosť k použitiu (Usability - U)**
   - Užívateľsky prívetivý rozhranie
   - Intuitívne ovládanie pre profesionálov aj laikov

3. **Spoľahlivosť (Reliability - R)**
   - Nízka miera zlyhaní, konzistentná diagnostika
   - Obnovenie systému v prípade zlyhania

4. **Výkon (Performance - P)**
   - Rýchla diagnostika s nízkou spotrebou zdrojov

5. **Schopnosť údržby (Supportability - S)**
   - Jednoduché aktualizácie a testovanie systému
   - Podpora pre nové modely vozidiel

---

## Kritické situácie
1. **Systémové**
   - Výpadok napájania: Systém nie je schopný vykonať diagnostiku bez napájania.
   - Zlyhanie hardware: Poškodenie senzorov alebo ECU vedie k nepresnej diagnostike.

2. **Aplikačné**
   - Problémy s komunikáciou medzi diagnostickým zariadením a OBD-II portom vozidla.

---

## Tri situácie definujúce hranice systému
1. **Ideálny scenár**
   - Systém úspešne vykoná diagnostiku, zobrazuje chybové kódy a poskytuje potrebné informácie pre opravu vozidla.

2. **Hranične riešiteľný scenár**
   - Systém nedokáže identifikovať konkrétnu závadu, ale poskytne návrh na ďalšiu diagnostiku.

3. **Situácie, ktoré systém nezvládne**
   - Systém nie je schopný vykonať diagnostiku v prípade úplného zlyhania ECU alebo riadiacej jednotky.

---

## Kontext prostredia
Systém bude implementovaný ako samostatné riešenie, ktoré nebude závislé od existujúcich systémov. Bude musieť zohľadňovať rôzne environmentálne faktory, ako je teplota, vlhkosť a typ terénu, ktoré môžu ovplyvniť diagnostiku.

---

## Charakteristika aktérov a prostredia
- **Aktéri**: Mechanik, technik, výrobca automobilov, majiteľ vozidla
- **Prostredie**: Auto servis, mobilné zariadenia, diagnostické nástroje

---

## Use Case diagram
- **Minimálne 5 modulov a 2 aktéry**
- Doporučené maximum: 5 modulov s využitím `include` a `extend` vzťahov.

---

## Scenáre - konkrétna implementácia Use Case

**1. Vyhľadávanie kódového chybového hlásenia**  
   - **Názov**: Vyhľadanie chybového kódu P0300  
   - **Kontext**: Mechanik chce diagnostikovať problém s motorom vozidla.  
   - **Level zanoření Use Case**: Hlavný scénar  
   - **Aktéri**: Mechanik  
   - **Stakeholdeři a zájmové osoby**: Mechanici, majitelia vozidiel  
   - **Vstupné podmienky**: Mechanik má prístup k OBD-II diagnostickej jednotke  
   - **Výstupné podmienky**: Zobrazenie chybového kódu  
   - **Minimálny výstup**: Zobrazenie chybového kódu  
   - **Ideálny výstup**: Zobrazenie detailných informácií o závade

**Hlavný scénár**:  
1. Mechanik pripojí OBD-II jednotku k vozidlu.  
2. Systém vykoná diagnostiku a zobraziť chybový kód.

**Rozšírenie**:  
- Ak diagnostika zlyhá, zobrazí sa chybová hláška a mechanik sa musí pripojiť manuálne.

---

## Sekvenčný diagram
- Vytvorte sekvenčný diagram, ktorý ukáže interakcie medzi mechanikom, diagnostickým nástrojom a vozidlom.

---

## Triedny diagram
- Zobraziť triedy ako `Vehicle`, `ECUDiagnosticTool`, `OBD2_Codes` a ich vzťahy.

---


# Rozšírenie FURPS analýzy pre projekt diagnostického softvéru pre automobily

## 1. **S.M.A.R.T. Ciele (Specific, Measurable, Achievable, Relevant, Time-bound)**
Táto metodika pomáha definovať jasné a merateľné ciele, ktoré by mal systém splniť. Použitie tejto analýzy môže byť veľmi užitočné na určenie konkrétnych cieľov pre implementáciu systému:
- **Specific (Špecifické)**: Čo presne má systém robiť? (napr. čítanie diagnostických kódov)
- **Measurable (Merateľné)**: Ako budeme hodnotiť úspech? (napr. doba odozvy systému pri diagnostike)
- **Achievable (Dosiahnuteľné)**: Je tento cieľ realistický s dostupnými zdrojmi?
- **Relevant (Relevantné)**: Má tento cieľ skutočne hodnotu pre používateľov systému?
- **Time-bound (Časovo ohraničené)**: Kedy by mal byť cieľ dosiahnutý?

---

## 2. **SWOT analýza (Strengths, Weaknesses, Opportunities, Threats)**
SWOT analýza je skvelý nástroj na hodnotenie silných a slabých stránok systému, ako aj príležitostí a hrozieb, ktoré môžu ovplyvniť jeho úspešnosť:
- **Strengths (Silné stránky)**: Aké sú hlavné výhody systému (napr. vysoká spoľahlivosť)?
- **Weaknesses (Slabé stránky)**: Kde má systém slabiny (napr. obmedzená podpora pre staršie modely vozidiel)?
- **Opportunities (Príležitosti)**: Aké príležitosti existujú pre rozšírenie systému (napr. pripojenie na mobilné aplikácie)?
- **Threats (Hrozby)**: Aké externé faktory by mohli ohroziť systém (napr. technológie konkurentov)?

---

## 3. **Risk Analysis (Analýza rizík)**
Risk analýza sa zameriava na identifikáciu a hodnotenie potenciálnych rizík spojených s vývojom a implementáciou systému:
- **Technologické riziká**: Napríklad problémy s integráciou nových modelov vozidiel alebo zmeny v OBD-II protokole.
- **Projektové riziká**: Napríklad oneskorenie v implementácii alebo nepredvídané náklady.
- **Bezpečnostné riziká**: Riziká spojené s ochranou dát a citlivých informácií.

---

## 4. **UML (Unified Modeling Language) Diagramy**
Okrem FURPS analýzy môžu študenti využiť aj rôzne UML diagramy, ako sú:
- **Triedne diagramy**: Ukazujú štruktúru systému a jeho komponenty (triedy a objekty) s atribútmi a metódami.
- **Sekvenčné diagramy**: Ukazujú časovú posloupnosť udalostí a interakcií medzi rôznymi komponentami systému.
- **Stavové diagramy**: Zobrazujú rôzne stavy systému a prechody medzi nimi na základe určitých podmienok.
- **Aktivitné diagramy**: Vizualizujú tok aktivít v systéme a rozhodovanie medzi rôznymi operáciami.

---

## 5. **Agilné metodiky (Scrum, Kanban)**
Pre projektový manažment je možné použiť agilné metodiky na riadenie vývoja systému. Tieto metodiky sú obzvlášť užitočné pri dynamických projektoch, kde sa môže meniť rozsah a požiadavky:
- **Scrum**: Metodika, ktorá sa zameriava na pravidelné iterácie a tým aj rýchlejšie nasadzovanie nových funkcií.
- **Kanban**: Vizualizuje pracovný tok a umožňuje sledovať stav jednotlivých úloh v reálnom čase.

---

## 6. **Testovacia analýza (Testovanie kvality)**
Kvalitné testovanie je neoddeliteľnou súčasťou každého systému. Testovacia analýza by mala zahŕňať:
- **Unit Testing (Jednotkové testy)**: Testovanie jednotlivých komponentov systému.
- **Integration Testing (Integračné testy)**: Testovanie interakcie medzi rôznymi časťami systému.
- **Acceptance Testing (Akceptačné testy)**: Overenie, či systém spĺňa požiadavky používateľa a obchodné ciele.

---

## 7. **Vývojový životný cyklus (SDLC - Software Development Life Cycle)**
Pre štruktúrovaný vývoj môže byť užitočné dodržiavať niektorý z modelov vývojového životného cyklu:
- **Waterfall**: Tradičný prístup s fázami ako analýza, návrh, implementácia a testovanie.
- **Agile**: Flexibilnejší prístup s častými iteráciami a zlepšovaním systému.

---

# Zhrnutie
Na obohatenie tvojej video analýzy FURPS môžeš zvážiť pridanie ďalších metodík a nástrojov ako:
- **S.M.A.R.T. Ciele** na definovanie konkrétnych a merateľných cieľov.
- **SWOT analýza** na hodnotenie silných a slabých stránok systému.
- **Risk Analysis** na identifikáciu a hodnotenie potenciálnych rizík.
- **UML diagramy** na vizualizáciu a detailnejšie pochopenie systému.
- **Agilné metodiky** na riadenie projektu a iteratívny vývoj.
- **Testovacia analýza** na zabezpečenie kvality systému.
- **SDLC modely** na riadenie vývoja.

Tieto metódy a analýzy môžu študentom pomôcť lepšie pochopiť rôzne aspekty systému a jeho vývoja, čo je veľmi užitočné pri implementácii skutočných softvérových riešení.

