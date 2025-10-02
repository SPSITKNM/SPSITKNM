
# Názov projektu (+ meno riešiteľa a login)
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
