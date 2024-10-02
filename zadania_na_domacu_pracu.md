# Klasické herné zadania v C#

## 1. Space Invaders
Vytvor klasickú arkádovú hru, kde hráč ovláda vesmírnu loď a strieľa mimozemšťanov, ktorí postupne zostupujú dole. Hra končí, keď sa mimozemšťania dostanú k hráčovi alebo ak hráč zničí všetkých nepriateľov.

## 2. Pac-Man
Hráč ovláda postavu v bludisku a snaží sa zjesť všetky body, zatiaľ čo ho prenasledujú duchovia. Hráč môže zbierať power-upy, ktoré mu dočasne umožnia zneškodniť duchov.

## 3. Arkanoid
Hráč ovláda plošinku, odráža loptu a ničí steny zložené z tehál. Cieľom je rozbiť všetky tehly bez toho, aby lopta spadla mimo hernú plochu.

## 4. Pong
Jednoduchá dvojhráčová hra, kde každý hráč ovláda plošinku a odráža loptu. Cieľom je skórovať tým, že lopta prejde okolo súperovej plošinky.

## 5. Frogger
Hráč musí preskočiť žabou cez cestu plnú áut a potom cez rieku s pohyblivými prekážkami, aby sa dostal na druhú stranu. Ak hráč spadne do rieky alebo ho prejde auto, hra končí.

## 6. Tetris
Klasická puzzle hra, kde hráč skladá padajúce bloky rôznych tvarov tak, aby vytvoril horizontálne rady bez medzier. Keď je rada plná, zmizne a hráč získava body.

## 7. Asteroids
Hráč ovláda vesmírnu loď, ktorá sa môže otáčať a strieľať asteroidy. Cieľom je zničiť všetky asteroidy na obrazovke, pričom sa hráč musí vyhnúť zrážke s nimi.

## 8. Snake (Had)
Hráč ovláda hada, ktorý sa pohybuje po hracej ploche a zbiera jedlo. S každým jedlom had rastie a hra končí, ak narazí do steny alebo do svojho vlastného tela.

## 9. Bomberman
Hráč umiestňuje bomby, aby zničil prekážky a porazil nepriateľov v bludisku. Cieľom je eliminovať všetkých nepriateľov a nájsť cestu k východu, bez toho, aby sa hráč zranil.

## 10. Donkey Kong
Hráč ovláda postavu, ktorá sa musí vyšplhať po rebríkoch a vyhnúť sa padajúcim sudom, aby zachránila postavu uväznenú na vrchole obrazovky.

## 11. Galaga
Pokračovanie Space Invaders. Hráč ovláda vesmírnu loď a bojuje proti vlnám nepriateľov. Nepriatelia majú zložitejšie vzorce útoku a môžu hráčovi zajmúť loď, ktorú môže zachrániť.

## 12. Breakout
Hráč ovláda plošinku, ktorá odráža loptu a ničí steny. Cieľom je odstrániť všetky tehly bez straty lopty. Rôzne druhy tehál môžu vyžadovať viac zásahov alebo udeliť hráčovi bonusy.

## 13. Street Fighter
Bojová hra, kde hráč ovláda postavu, ktorá bojuje proti súperovi. Môžeš vytvoriť systém útokov, blokovania a špeciálnych pohybov a zahrnúť rôzne úrovne a súperov.

## 14. Super Mario Bros.
Hráč ovláda Maria (alebo inú postavu), ktorý behá, skáče a zbiera mince, pričom sa snaží vyhnúť nepriateľom a dosiahnuť koniec úrovne. Môžeš zahrnúť rôzne svety a úrovne s rôznymi prekážkami a nepriateľmi.

## 15. Tank 1990 (Battle City)
Hráč ovláda tank, ktorý chráni svoju základňu a ničí nepriateľské tanky. Hra končí, keď je hráčov tank zničený alebo ak nepriatelia zničia jeho základňu.

---

# Herné požiadavky pre vývoj projektov

### 1. Herná logika:
- Každá hra by mala byť rozdelená na hlavné komponenty: **hráč**, **nepriatelia**, **scéna/herné prostredie** a **hráčove ciele** (výhra/prehra).
- Herná logika by mala byť implementovaná v zmysle hlavného **herného cyklu**, ktorý neustále spracováva vstupy hráča, aktualizuje herný stav a vykresľuje obrazovku.

### 2. Ovládanie:
- Hry by mali poskytovať používateľsky priateľské ovládanie, ktoré je **intuitívne** a prispôsobené typu hry (napr. klávesnica pre **Space Invaders** alebo šípky pre **Pac-Man**).
- Ovládanie by malo byť optimalizované pre odozvu hráča, minimalizovať **oneskorenie** medzi vstupom a akciou v hre.

### 3. Herné stavy:
Každá hra by mala mať jasne definované **herné stavy**, ako sú:
- **Hlavné menu**: výber hry alebo úrovne, možnosti nastavení.
- **In-Game stav**: aktuálny stav hry, kde hráč hrá.
- **Pause stav**: hra je pozastavená a čaká na obnovu.
- **Game Over stav**: hráč buď vyhral, alebo prehral.
- **Výsledková tabuľka**: ak je relevantné.

### 4. AI a nepriatelia:
- Ak sú v hre prítomní nepriatelia, ich správanie by malo byť spracované buď jednoduchou, alebo zložitejšou formou **umelej inteligencie**.  
Niektoré príklady:
  - **Náhodné pohyby**: napr. had v **Snake** hre.
  - **Skriptované vzory**: napr. v **Space Invaders** alebo **Galaga**.
  - **Sofistikované správanie**: napr. duchovia v **Pac-Man** s rôznymi vzorcami správania.

### 5. Grafika a animácie:
- Každá hra by mala používať **2D** alebo **3D grafiku**, ktorá je optimalizovaná pre danú platformu.
- Jednoduché **animácie** (napr. pohyb nepriateľov, explózie, zhromažďovanie bodov) by mali byť zahrnuté, aby hra pôsobila dynamicky a živá.

### 6. Výkon a optimalizácia:
- Hry by mali byť optimalizované tak, aby hladko bežali aj na menej výkonných zariadeniach, s minimálnymi problémami ako sú **lagy** alebo padanie aplikácie.
- **Optimalizácia hernej logiky** a zníženie záťaže na **CPU** a pamäť sú dôležité, najmä pre hry s veľkým počtom nepriateľov alebo objektov na obrazovke.

### 7. Skórovací systém a ciele hry:
- Každá hra by mala mať definované **cieľové podmienky** (ako vyhrať alebo prehrať).
- **Skórovací systém** by mal odmeňovať hráča za jeho výkony, či už formou bodov, postupov do vyšších úrovní alebo iným spôsobom.

### 8. Úrovne a obtiažnosť:
- Hry môžu obsahovať rôzne **úrovne** alebo zvyšujúcu sa obtiažnosť, aby hráč mal motiváciu zlepšovať svoje schopnosti (napr. zrýchlenie nepriateľov v **Space Invaders**, väčšia rýchlosť lopty v **Arkanoide**).

### 9. Ukladanie progresu (voliteľné):
- V niektorých hrách môže byť implementované **ukladanie hry** alebo uchovanie výsledkov (najmä pre komplexnejšie hry ako **Tetris** alebo **Bomberman**).

### 10. Dobrý kód a modularita:
- Kód by mal byť písaný v zmysle princípov **OOP** (objektovo orientovaného programovania), čo znamená, že hráči, nepriatelia, projektily a iné herné entity by mali byť **triedami**, ktoré majú jasne definované zodpovednosti.
- Kód by mal byť dobre **modulárny**, čo umožní jednoduché prispôsobenie a údržbu hry.

### 11. Testovanie:
- Hry by mali byť dôkladne **testované** na rôzne scenáre (kolízie, pohybové chyby, bugy v hernej logike) a mala by byť zabezpečená ich stabilita.

---

Implementáciou týchto podmienok sa zabezpečí, že každá hra bude funkčná, zábavná a dobre zvládne základy hernej mechaniky, pričom hráčovi poskytne plynulý a zábavný herný zážitok.


