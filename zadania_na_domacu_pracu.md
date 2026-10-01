# Od analýzy k programu — implementácia vlastného projektu v OOP

Táto úloha nadväzuje na tvoj odovzdaný dokument **Systémová analýza projektu**. Nejde o nové, cudzie zadanie — je to *ten istý* projekt, ktorý si si vtedy vymyslel a rozobral (moduly, aktéri, use case, sekvenčný a triedny diagram). Vtedy sme OOP ešte nemali dotiahnuté do detailu. Teraz áno — a úlohou je ukázať to na vlastnom nápade, nie na cudzom zadaní.

---

## Cieľ

Naprogramuj **hlavný scenár tvojho hlavného Use Case, end-to-end** — od vstupu, cez spracovanie, po výstup — presne tak, ako si ho popísal v kapitole *Scenáre* svojej SA. Program má byť reálna, malá funkčná ukážka tvojho systému, nie izolované triedy bez súvislosti.

Nejde o to napísať čo najviac riadkov. Ide o to, aby bol kód **taký, ako by si ho chcel mať v skutočnom projekte, za ktorý zodpovedáš** — pretože presne to sa deje: je to tvoj nápad.

---

## Čo musí program robiť

1. **Odsimuluje hlavný scenár use case** — vstupy, ktoré aktér zadáva, spracovanie systémom, výstup, ktorý aktér vidí. Nemusí to byť graficky, konzola stačí — ide o logiku a tok, nie o dizajn obrazovky.
2. **Triedy zodpovedajú tvojmu triednemu diagramu.** Ak počas programovania zistíš, že diagram bol nepresný alebo nekompletný, uprednostni funkčný a čistý kód — rozdiel medzi diagramom a kódom v pár riadkoch krátko zdôvodni v komentári alebo v priloženej poznámke.
3. **Sekvencia volaní metód zhruba zodpovedá tvojmu sekvenčnému diagramu** — kto (aktér/objekt) o čo požiada koho a v akom poradí. Nemusí to byť volanie na volanie, ale poradie krokov má byť rozpoznateľné.

---

## Odporúčaný postup

Nie je to povinná šablóna, len poradie, v ktorom sa to zvyčajne robí ľahšie, než keď začneš rovno písať metódy:

1. **Prejdi si triedny diagram** a over, či ešte stále dáva zmysel — mená tried, atribúty, kto s kým súvisí.
2. **Navrhni verejné rozhranie skôr než detaily.** Rozhodni, aké metódy bude mať každá trieda navonok (čo od nej niekto potrebuje), až potom rieš, ako to metóda vnútri robí.
3. **Naprogramuj hlavný scenár** po krokoch tak, ako ide v sekvenčnom diagrame — objekt po objekte, volanie po volaní.
4. **Až keď to funguje na "ideálnej" ceste**, prejdi si sekcie *Použi OOP piliere*, *Zamysli sa nad konštrukciou softvéru* a *Zahraj sa na testera* nižšie a kód doladi.

---

## Použi OOP piliere — nie ako povinnosť, ale ako nástroj

Nedávam ti vzorec typu "musíš mať presne 1 dedičnosť a 1 abstraktnú metódu". Namiesto toho premýšľaj **ako by si reálne staval svoj vlastný systém**:

- **Enkapsulácia** — čo v systéme nemá byť voľne meniteľné zvonku? Kde treba validáciu?
- **Dedičnosť a polymorfizmus** — má tvoj systém prirodzene rôzne *typy* niečoho (rôzne typy modulov, aktérov, správ, úloh, zariadení...)? Ak áno, toto je presne ten prípad, kde dedičnosť dáva zmysel — nie preto, že to zadanie chce, ale preto, že to riešenie potrebuje.
- **Abstrakcia** — má zmysel mať spoločné rozhranie, cez ktoré systém pracuje s rôznymi konkrétnymi implementáciami bez toho, aby vedel, o ktorú presne ide?

Ak vo tvojom projekte žiadna z týchto vecí prirodzene nevyplýva, nesnaž sa ju tam vecpať násilne — ale skús sa nad projektom zamyslieť aspoň raz navyše: takmer každý systém s viac ako jedným typom "niečoho" (viac typov aktérov, modulov, správ...) má miesto, kde polymorfizmus ušetrí kód. A tam, kde by dedičnosť bola len umelá "je to podobné", zváž skôr **skladanie** (jedna trieda si druhú *má*, nededí od nej) — presne o tomto je odkaz nižšie na *Dedičnosť vs. skladanie*.

---

## Zamysli sa nad konštrukciou softvéru, nie len nad tým, či to "funguje"

Toto je jadro úlohy. Predtým, než odovzdáš, prejdi si vlastný kód a spýtaj sa:

- **Redundancia** — píšem niekde dvakrát to isté (dve podobné funkcie, dve podobné triedy s takmer identickým telom)? Dá sa to zjednotiť?
- **Dvojitá validácia** — kontrolujem tú istú podmienku na dvoch miestach (napr. v settri aj v konštruktore aj v `main()`)? Vyber si jedno miesto, kde má validácia bývať, a ostatné nech sa na ňu spoliehajú.
- **Opakovanie kódu (copy-paste)** — keď kopíruješ blok kódu a meníš v ňom jedno slovo, je to znak, že tam chýba funkcia/metóda, ktorá by to zjednotila.
- **Zodpovednosť triedy** — robí jedna trieda príliš veľa vecí naraz (číta vstup, aj počíta, aj vypisuje)? Skús si predstaviť, že o rok pridávaš novú funkciu — nájdeš rýchlo, kde v kóde zasiahnuť, alebo je všetko v jednej veľkej metóde?

Toto sme si ukazovali na cvičeniach — teraz je čas to aplikovať na niečo, na čom ti záleží viac než na cvičnom príklade.

---

## Zahraj sa na testera aj na bežného používateľa

Po tom, čo program funguje na "ideálnej" ceste, prepni perspektívu:

- **Ako tester:** Čo sa stane pri prázdnom vstupe? Pri zápornom čísle, kde nedáva zmysel? Pri extrémne veľkom vstupe? Skús program úmyselne "rozbiť".
- **Ako bežný používateľ:** Čo by ťa na tomto programe štvalo? Nezrozumiteľná hláška, ticho spadnutý program, chýbajúca spätná väzba po zadaní vstupu? Oprav aspoň tie najviac rušivé miesta.

Presne túto trojicu situácií si už raz popísal — v kapitole **Hranice systému** svojej SA (*ideálny scenár*, *hranične riešiteľný scenár*, *situácia, ktorú systém nezvládne*). Teraz to nie je len text — je čas ukázať to reálne v behu programu.

### Povinná demonštrácia troch scenárov

V `main()` (alebo v krátkom sprievodnom výstupe) **ukáž všetky tri situácie z tvojej kapitoly *Hranice systému*** v akcii:

1. Ideálny scenár — systém spracuje vstup bez problémov.
2. Hranične riešiteľný scenár — systém narazí na problém, ale vie ho zmysluplne ošetriť a informovať používateľa (nie crash).
3. Situácia, ktorú systém nezvládne — systém to rozpozná a **korektne to nahlási** (nie že to ignoruje, nie že to spadne bez vysvetlenia).

Ak sa medzičasom ukázalo, že tvoj pôvodný popis hraníc systému bol príliš vágny na to, aby sa dal takto demonštrovať, dopíš k nemu 1–2 vety upresnenia priamo pri odovzdaní.

---

## Môže ti pomôcť

Všetko nižšie je v repozitári [SPSITKNM/oop_opakovanie](https://github.com/SPSITKNM/oop_opakovanie) a čitateľné priamo cez čítačku (odkazy nižšie vedú rovno na konkrétnu kapitolu):

**OOP piliere** — [prehľad predmetu OOP](https://spsitknm.github.io/predmet.html?s=oop)
- [Enkapsulácia](https://spsitknm.github.io/citacka.html?s=oop&doc=oop-opakovanie#enkapsulacia-zapuzdrenie-v-c-prvy-pilier-oop) · jej [najčastejšie chyby](https://spsitknm.github.io/citacka.html?s=oop&doc=oop-opakovanie#najcastejsie-chyby)
- [Dedičnosť](https://spsitknm.github.io/citacka.html?s=oop&doc=oop-opakovanie#dedicnost-v-c-druhy-pilier-oop) · [dedičnosť vs. skladanie (JE vs. MÁ)](https://spsitknm.github.io/citacka.html?s=oop&doc=oop-opakovanie#dedicnost-vs-skladanie-je-vs-ma) — presne na rozhodnutie, kde dedičnosť *nie* je správna odpoveď
- [Abstrakcia](https://spsitknm.github.io/citacka.html?s=oop&doc=oop-opakovanie#abstrakcia-v-c-treti-pilier-oop) · [rozhranie (interface)](https://spsitknm.github.io/citacka.html?s=oop&doc=oop-opakovanie#rozhranie-interface) · [abstrakcia vs. enkapsulácia](https://spsitknm.github.io/citacka.html?s=oop&doc=oop-opakovanie#abstrakcia-vs-enkapsulacia)
- [Polymorfizmus](https://spsitknm.github.io/citacka.html?s=oop&doc=oop-opakovanie#polymorfizmus-v-c-stvrty-pilier-oop) · [tri podmienky polymorfizmu](https://spsitknm.github.io/citacka.html?s=oop&doc=oop-opakovanie#tri-podmienky-polymorfizmu)
- [Vzťahy medzi objektmi — asociácia, agregácia, kompozícia](https://spsitknm.github.io/citacka.html?s=oop&doc=oop-opakovanie#vztahy-medzi-objektmi-asociacia-agregacia-kompozicia) — ak si nie si istý, či má byť medzi dvoma triedami dedičnosť alebo len "má v sebe"

**Diagramy z tvojej SA** (rovnaké skriptá, z ktorých si vychádzal pri Systémovej analýze):
- [Use case diagram](https://spsitknm.github.io/citacka.html?s=oop&doc=uvod-do-si#use-case-diagram)
- [Sekvenčný diagram](https://spsitknm.github.io/citacka.html?s=oop&doc=uvod-do-si#sekvencny-diagram)
- [Od požiadavky po test](https://spsitknm.github.io/citacka.html?s=oop&doc=uvod-do-si#od-poziadavky-po-test) — presne to, čo teraz robíš pri demonštrácii troch hraničných scenárov

Ak si niečo z toho vôbec nepamätáš, je normálne sa tam vrátiť — tieto skriptá presne na to slúžia.

---

## Ako budem hodnotiť

- **Súlad s tvojou SA** — trieda v kóde ↔ modul/aktér z SA, tok v `main()` ↔ hlavný scenár use case, poradie volaní ↔ sekvenčný diagram (alebo zdôvodnená odchýlka).
- **Zmyselné použitie OOP pilierov** — nie mechanicky navecpané, ale tam, kde to riešenie skutočne potrebuje.
- **Čistota kódu** — bez zbytočnej duplicity, bez dvojitej validácie tej istej podmienky, jasná zodpovednosť každej triedy.
- **Robustnosť** — všetky tri scenáre z kapitoly *Hranice systému* reálne demonštrované, žiadny nečakaný crash na bežnom vstupe.
- **Mapovacia poznámka** — viem si z nej rýchlo overiť, čo v kóde zodpovedá čomu v SA.

---

## Čo odovzdať

- Zdrojový kód (`.cpp`, prípadne rozdelený do `.h`/`.cpp` ak to dáva zmysel pre veľkosť projektu).
- Krátka mapovacia poznámka (pár riadkov, stačí komentár na začiatku súboru alebo samostatný `.md`):
  - ktoré triedy v kóde zodpovedajú ktorým modulom/aktérom z SA,
  - kde v kóde nájdeš hlavný scenár use case,
  - čo sa oproti pôvodnému triednemu/sekvenčnému diagramu zmenilo a prečo.

Odovzdáva sa opäť do otvorenej úlohy na EduPage.

---

## Čo bude nasledovať

Na najbližších hodinách sa budeme venovať **návrhovým vzorom (design patterns)**. Táto úloha je vedomý medzikrok: chcem, aby si najprv poriadne cítil, *kde* v tvojom vlastnom kóde bolí redundancia, duplicitná validácia a nejasná zodpovednosť tried — presne v tých miestach potom uvidíš, ako presne ti návrhový vzor pomôže. Kód, ktorý teraz odovzdáš, sa nezahodí — budeme sa k nemu vracať a **refaktorovať ho vzormi** tam, kde to bude mať zmysel.

Konkrétne úpravy a odporúčania k tvojmu kódu prídu vo forme feedbacku k tomuto odovzdaniu.

---

# Usmernenia

## Dôležité informácie

### Riešenia
- Riešenia žiadam odovzdávať do otvorenej úlohy na EduPage.

### Plagiát
- Plagiát štýlu 1:1 od kolegu je hodnotený automaticky známkou 5.
- Využitie zdrojov je voľné, vrátane AI je povolené.
- AI ti nevymyslí, kde v *tvojom* projekte dáva zmysel dedičnosť alebo kde duplicitne validuješ — to je časť úlohy, ktorú musíš prejsť sám.

### Termíny
- Každý deň po deadline znamená o stupeň horšiu známku!

## Veľa šťastia,
**TM**
