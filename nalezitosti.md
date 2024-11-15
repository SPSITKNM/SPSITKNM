# Začíname s vývojom v C# vo Visual Studio Code

Táto príručka vás prevedie nastavením vývojového prostredia, aby ste mohli začať pracovať s C# vo Visual Studio Code. Postupujte podľa nasledujúcich krokov na inštaláciu .NET, Visual Studio Code a potrebného rozšírenia pre C#.

---

## 1. Inštalácia .NET SDK

Na vytváranie a spúšťanie C# aplikácií potrebujete nainštalovať .NET SDK.

### Kroky:

- Stiahnite si .NET SDK z oficiálnej stránky pomocou tohto odkazu:  
  [Stiahnuť .NET SDK](https://bit.ly/dotnetcoresdk_techdecode)

- Po stiahnutí postupujte podľa inštalačných krokov pre váš operačný systém (Windows, macOS alebo Linux).

### Overenie inštalácie:

Po úspešnej inštalácii otvorte terminál alebo príkazový riadok a napíšte:

```bash
dotnet --version
```

## 2. Inštalácia .NET SDK

Ďalej si nainštalujte Visual Studio Code, ľahký a výkonný editor, ktorý podporuje vývoj v C#.

### Kroky:

- Stiahnite si Visual Studio Code pomocou tohto odkazu:
  [Stiahnuť VS Code](https://code.visualstudio.com/)
  
- Nasledujte inštalačné kroky podľa vášho operačného systému.

## 3. Inštalácia rozšírenia pre C# vo Visual Studio Code

Po inštalácii Visual Studio Code si nainštalujte rozšírenie C#, C# extension pre podrhávanie aby ste mohli pracovať s C#.

1. Otvorte Visual Studio Code.
2. Prejdite do zobrazenia Rozšírenia kliknutím na ikonu Rozšírenia na bočnom paneli alebo stlačením `Ctrl+Shift+X`.
3. Do vyhľadávacieho poľa napíšte C# a vyberte rozšírenie od spoločnosti Microsoft.
4. Kliknite na Inštalovať.

Týmto povolíte funkcie, ako zvýraznenie syntaxe, IntelliSense (návrhy kódu) a podporu ladenia pre C#.

## 4. Vytvorenie vášho prvého C# projektu

Keď je všetko nainštalované, môžete vytvoriť svoj prvý C# projekt.

### Kroky:

1. Otvorte terminál vo VS Code alebo použite systémový terminál.
2. Prejdite do priečinka, kde chcete vytvoriť projekt.
3. Spustite nasledujúci príkaz na vytvorenie novej konzolovej aplikácie:

```bash
dotnet new console
```
Týmto sa vytvorí nový priečinok s jednoduchým projektom "Hello World".

## 5. Zostavenie a spustenie C# projektu

Po vytvorení projektu postupujte podľa týchto krokov na jeho zostavenie a spustenie:

### Zostavenie projektu:

Ak je váš projekt súčasťou riešenia, môžete ho zostaviť pomocou nasledujúceho príkazu:

```bash
dotnet build YourSolutionName.sln
```
Ak nemáte súbor riešenia, stačí v priečinku projektu spustiť dotnet build.

### Spustenie projektu:

```bash
dotnet run
```

Týmto sa spustí vaša konzolová aplikácia a v termináli by ste mali vidieť text "Hello, World!".

## 6. Video Tutoriál 

Ak preferujete video návod, pozrite si tento tutoriál:

[Tutoriál](https://www.youtube.com/watch?v=CO4BGZOuUkM)


---

*Pojetí ekonomie jako vědy, její cíl, metody a vývoj. Ekonomické předpoklady a souvislosti výroby. Potřeby a zdroje. Produkce a spotřeba. Výrobní faktory a jejich vzácnost. Oceňování výrobních faktorů. Pojetí racionality v ekonomii. Náklady obětované příležitosti. Fyzická a institucionální hranice produkčních možností.*

---
# Zápisy done:

- [ ] Pojetí ekonomie jako vědy [[#^bbc047]]
- [ ] Cíl Ekonomie [[#^a2367e]]
- [ ] Vývoj ekonomie [[#^7dd16d]]
- [ ] Popis jednotlivých období a hlavních ekonomických objevů [[#^7dd16d]]
- [ ] Seznámení s osobnostmi a trochu o nich [[#^7dd16d]]
- [ ] Metody Ekonomie [[#^7bc192]]
- [ ] Potřeby a zdroje [[#^ef75c4]]
- [ ] Produkce a spotřeba [[#^b40542]]
- [ ] Oceňování výrobních faktorů [[#^17dca5]]
- [ ] Racionalita v ekonomice [[#^17dca5]]
- [ ] Náklady obětované příležitosti [[#^9d2fa8]]
- [ ] Fyzická a Institucionální hranice produkčních možností [[#^4e79a4]]

# Ekonomie (věda o volbě, neboli o rozhodování)
- Je ==**společenská věda**== zabývající se popisem a analýzou výroby, distribuce a spotřeby ekonomických statků (zboží, služby a peníze).  ^bbc047
- Studuje chování jednotlivců, firem a vlád v reakci na podměty v **ekonomickém prostoru**, tedy na omezenost zdrojů pro výrobu a poskytování služeb, fungování trhu -> tedy nabídky a poptávky, a tvorbě ceny. ^89bb5e

- **Cílem** je porozumění a analýza způsobů, jak jsou omezené zdroje využívány k uspokojení lidských potřeb. To znamená **studovat rozhodnutí** o výrobě, spotřebě a distribuci statků, **analyzovat** jak různé ekonomické systémy ovlivňují chování a výkonnost celkové ekonomiky, **identifikovat** a **nabízet** řešení pro jednotlivé ekonomické problémy (inflace, nezaměstnanost) ^a2367e

---

# Historie vývoje Ekonomie:

^7dd16d
## Vývoj ekonomie jako takové mimo období:

### 1. Dělba práce: 
- Hlavně u pravěkých kmenů
- Každý měl svou práci určenou k přežití kmene
- Každý poté dostal svůj díl odměny v závislosti na druhu práce
### 2 Specializace:
- Rozvojem civilizace a myšlení komunit přišly specializace
- Každý jedinec se specializoval na určitý typ práce
- **Vznik řemesel a profesí**
- **Vznik potřeby peněz**, jelikož barter již nestačil pro ukojení potřeb

## Typy platitel / směňování:

**Funkce peněz:**
- Prostředek směny
- Zúčtovací jednotka
- Uchovatel hodnoty

### 1. Barter (Naturální směna):
- **Neexistovala žádná měna, bez peněz**
- Vyměňuje se přímo jeden druh zboží za jiný
- **Oboustranný souhlas:** Proběhne jen a pouze, když obě strany zboží druhého potřebují

## 2. Komoditní peníze:
- Jakožto měna se používaly komodity -> statky, které obecně každý může chtít
- Každá komodita má vlastní hodnotu 
- Hodnota se odvíjela od vzácnosti, použitelnosti atd.
- **Příklady**: Sůl, Hedvábí, Koření, Dobytek, Mušle

## 3. Drahé kovy a plnohodnotné peníze
- Hodnota peněz byla často odvíjena od skutečné hodnoty kovu, ze kterých byly raženy **(nominální hodnota)**
- Hlavní výhodou byla skladnost a stabilita měn, jelikož kovy udržují svou cenu
## 4. Neplnohodnotné peníze 
- Peníze, jejichž hodnota je určena vírou v ně a měnou obecně
- Nejčastěji bankovky

## 5. Bezhotovostní peníze:
- Peníze na účtech

## 6. Kryptoměny
- Prostě krypto


## 1. Antická filozofie:
- Položeny základy ekonomie jakožto vědy
- Ekonomické otázky byly zkoumány z hlediska morálky, spravedlnosti a ideálního uspořádání společnosti. -> **Etický pohled**
- Ekonomická témata jako obchod, rozdělování bohatství a spravedlnost byly tedy často spojena s morálními otázkami
### Platón: 
- Autor díla: **Ústava (Politeia)**, které popisuje ideální stát
- **Ideální stát dle Ústavy**: Společnost rozdělena do tříd, kde každá plní svou specifickou úlohu (Pracující, vojáci a vládci)
- Zdůrazňoval **dělbu práce** pro maximalizaci efektivity a prosperujícího státu
- **Odmítal bohatství a majetkové rozdíly** -> Jen pracující by měli disponovat vlastnictvím, jelikož vojákům a vládnoucím jen podlamuje morálku a vede k touze po zbytečném bohatství
### Aristotelés:
- Žák Platóna
- Rozděloval **Ekonomiku** a **Chrematistiku** -> tedy vlastnictví **přirozené** a **nepřirozené**.
- **Ekonomika (přirozené vlastnictví)**: Vede k dobrému hospodáření a tím ukojení potřeb
- **Chrematistika (nepřirozené vlastnictví)**: Vede ke spekulativnímu hromadění za účelem výdělku
- Vymyslel koncept **Spravedlivé výměny**, kde hodnota statků je založena na užitné hodnotě
### Xenofón:
- Žák Sokrata
- Sepsal dílo: **O hospodaření**, které formou rozhovorů pojednává a radí, jak dobře hospodařit, jedná se o první dílo pojednávající o **Ekonomii jako takové**
- Zastánce autoritářského vedení státu, stranil se demokracie, která mu zabila učitele

### Římská filozofie a právo:
- Přispěla zásadním rozvojem ekonomického myšlení, zejména v otázkách vlastnictví a smluv.
- Ekonomické myšlení Římanů bylo více praktické a právně orientované, zaměřené na **majetkové vztahy**, **obchodní smlouvy** a **vlastnictví půdy**.

## 2. Středověké myšlení:
- Ovlivněno církví prostřednictvím **Scholastiky**
- Ekonomické myšlení založeno na **etických otázkách** spravedlivého obchodu
- Striktně zakazovalo **lichvu** -> tedy půjčování peněz za nemorální úrok
- Tržní ceny, které byly příliš **vysoké / nízké** byly považovány za neetické
- **Cena** tedy měla reflektovat **náklady práce a výroby, bez nadměrné marže**
- **Obchod měl sloužit k zajištění spravedlivého života**, nikoliv k hromadění bohatství
- Rozvoj mezinárodního obchodu -> **Hedvábná stezka**
### Svatý Tomáš Akvinský (1225 - 1274)
- Vrcholný katolický filosof a teolog scholastické kultury
- Jeho dílo definovalo ekonomické myšlení středověku
- Definoval **Spravedlivou cenu, odmítal lichvu, etiku obchodu**
- Dílo: **Souhrn teologie** ->Definuje teologii jako vědu a rozebírá etické zásady víry
### Feudalismus:
- Organizování vztahu mezi vlastníky půdy a rolníky
- Ekonomika byla založena na **naturální směně**, kdy rolníci odváděli část své produkce vlastníkům půdy a vládcům výměnou za ochranu a právo obdělávat půdu
- Půda byla považována za hlavní zdroj bohatství, což omezovalo ekonomickou mobilitu a rozvoj trhů
### Cechy a Hanza:
#### Hanza: 
- **Společenství měst**, které společně prosazovaly své ekonomické cíle 
- Tvořily **obchodní síť** **bezpečného** a **efektivního** obchodu mezi členskými městy
- Spolupráce při ochraně obchodních cest a konkurenci, sjednocování obchodních pravidel
- **Výsadní postavení:** Zvláštní privilegia od vládnoucí moci -> monopol na obchod, nebo lepší podmínky k jeho provádění
- **Každé město** bylo autonomní na druhém ve vedení -> nejednalo se o stát, pouze se na společných sjezdech dohodli na podmínkách a pravidlech spolupráce atd.
#### Cechy:
- **Společenství řemeslníků** či **obchodníků**, které hájilo členské zájmy
- Dohlíželo taktéž na **jakost** (kvalitu) a **cenu** služeb a výrobků, **výchovu učedníků** a skládání mistrovských zkoušek. 
- Plnily taktéž úlohu zastupování v obchodních, společenských a náboženských záležitostech
- První výskyt **zdravotního a sociálního pojištění**!
### Manufaktury a Obchodní společnosti:
#### Manufaktury:
- První koncept organizované výroby určitého produktu ve větším měřítku
- Měly zásadní dopad na konečnou cenu a množství produktů v oběhu

#### Obchodní společnosti:
- Organizace pozdního středověku, které umožňovaly obchodníkům a investorům spojovat své prostředky pro dálkový obchod nebo velké obchodní podniky, které by sami neufinancovali
- **Společné riziko a zisky**: Snižovaly riziko ztráty z obchodu
- **Některé měly dokonce právní status**, což vedlo k uzavírání smluv, vlastnit majetek a žalovat jiné jakožto celek, nikoliv jako jednotlivec
- **Příklad:** Benátské a janovské obchodní společnosti, Východoindické společnosti
- Položily základy **kapitalismu** -> tedy rozvojem **ranného kapitalismu**

## 3. Merkantilismus

- První buržoazní (měšťanské) ekonomická teorie vzniklá přelomem 16. a 17. stol
- Klade důraz na maximalizaci ekonomického vývozu (exportu) státu do jiných ekonomik
- Víra spočívající v bohatství v drahých kovech (zlato, stříbro) a jiných luxusních statkách
- Obchod byl prováděn pouze a jen tehdy, pokud-li docházelo k pozitivní obchodní bilanci (zisku) v těchto drahých kovech či luxusních statkách
- **Regulace ekonomiky:** Stát měl hrát aktivní roli v ekonomice, tedy řídit obchodní politiku a kontrolovat domácí výrobu i mezinárodní obchod -> Cílem tedy bylo maximalizovat produkci domácích odvětví a minimalizovat dovoz (Např. cly, daněmi)
- **Kolonializmus:** Národy dobývaly kolonie pro zajištění levných surovin (zdrojů) a jakožto odbytiště pro zboží -> Maximalizace zisků. (Anglie, Francie, Španělsko, Portugalsko
### Jean-Baptiste Colbert
- **Francouzský ministr financí za vlády Ludvika XIV.**
- **Rozšířil ve Francii Merkantilismus**, díky čemuž **oživil** skomírající francouzskou ekonomiku
- **Podporoval zakládání manufaktur, rozšiřování dopravní sítě a zakládání nových přístavů**.
- Za jeho vlády bylo vybudováno **3. největší loďstvo**, kterým **následně usilovali o nové kolonie** na severu Afriky, přední Indii a Madagaskaru
- Osvícencem, založil mnoho vědeckých a uměleckých institucí -> **Francouzská akademie věd**
###  Thomas Mun
- Anglický spisovatel zaměřující se na ekonomii -> **Stanovil teorii rovnováhy trhu**
- **První merkantilista** -> věřil, že import by měl být nižší jak export. Bohatství státu spočívá ve zlatě, které stát vlastní
- Zvolen do čela Britské Východoindické společnosti
- Dílo:  **Englands’s Treasure by Forraign Trade** -> Obhajuje merkantilismus a popisuje jeho fungování a dopad na ekonomický výsledek.
## 4. Fyziokratismus
- Ekonomický směr vzniklý ve Francii v polovině 18. stol.
- Zdůrazňoval primární **roli zemědělství** jako zdroje bohatství
- Vznikl jako reakce na vznik Merkantilismu
- Princip**"Laissez-faire"** -> zásada volného trhu bez státních zásahů.
- Víra, že svobodná konkurence povede k optimálnímu zprostředkování zdrojů
- Negativně hleděli na obchod a průmysl, jelikož pouze přerozděloval již existující bohatství.
### François Quesnay
- Francouzský ekonom
- Představitel první ekonomické školy fyziokratů
- Autor **Ekonomické tabulky** -> první pokus o modelování ekonomického koloběhu, který popisoval vztahy mezi třídami: zemědělci, vlastníky půdy a ostatními (obchodníky, průmyslníky)
## 5. Klasická ekonomie:
- Ekonomický směr vyvinutý v **18. až 19**. století
- Položil základy moderní ekonomické teorie.
- Zaměřovala se na **volný trh, soukromé vlastnictví a ekonomické zákony** fungující bez státních zásahů
- Víra v **hodnotě práce** potřebné k výrobě -> základem teorie pracovní hodnoty
- Minimalizace státních zásahů -> Stát by měl zajišťovat pouze ochranu a spravedlnost
- **Víra v akumulaci kapitálu a růst** -> Kapitál vzniklý z úspor a investic je klíčový k růstu produktivity
- **Mzdový fond** -> Teorie, podle níž existuje pevný fond kapitálu (peněz), který je určen čistě pro účely vyplácení mezd pracovníkům v průběhu výroby
#### Adam Smith
- Skotský ekonom a filozof, zakladatel moderní ekonomie
- Vymyslel **Neviditelnou ruku trhu**: -> myšlenka, dle níž jednotlivci sledující vlastní zájmy nepřímo **podporují obecné blaho společnosti**, to vede k efektivnímu fungování trhu
- Zdůrazňoval význam **dělby práce** -> vede k vyšší efektivitě
- **Teorie hodnoty**: Smithova **teorie pracovní hodnoty** říká, že hodnota zboží je určena množstvím práce potřebným k jeho výrobě.
- Hlavní dílo – **"Bohatství národů"** a **"Pojednání o podstatě a původu bohatství národů"**, v těchto knihách položil základy pro ekonomickou teorii volného trhu
#### Thomas Robert Malthus
- Anglický ekonom a pastor
- Dílo **"Esej o principu populace"**: -> Teorie na populačním růstu, kdy populace roste exponenciálně a produkce potravin lineárně -> z tohoto vztahu vyplývá nevyhnutelnost krize nevyhnutelného vyčerpání zdrojů -> počet lidí přesáhne kapacitu Země uživit je.
- **Malthusiánská past**: Varování, že populační růst vede k chudobě a hladomoru
- Rozlišoval proto **Prevenci** (snížení porodnosti) a **Restrikční faktory** (přirozené brzdy pop. růstu)
#### David Ricardo
- Britský politický ekonom
- **Teorie komparativních výhod**: Státy mohou profitovat z mezinárodního obchodu, kdy by země měly produkovat jen ty statky, kde mají **relativní výhodu** -> například lepší přístupnost daných zdrojů
- **Teorie pozemkové renty**: Renta je tedy výsledkem **relativní úrodnosti** mezi různými typy půdy. Majitelé nejúrodnější půdy získávají rentu díky tomu, že je jejich půda produktivnější než méně úrodná půda.
- **Zákon klesajících výnosů**: S každým dalším vstupem bude půda produkovat menší výnos.
- Zastánce **Volného obchodu** a **Zrušení obilních zákonů** -> poškozování ekonomiky a zvyšování cen potravin
#### John Stuard Mill
- Britský ekonom a filozof
- Dílo "**O Svobodě"** -> Obhajoba svobody jednotlivce před zásahem státu, pokud není ohrožením pro ostatní. Podpora myšlenky **svobody projevu a myšlení** 
- Podpora **sociálních reforem** -> zlepšení životních podmínek pracujících vede přes zlepšení vzdělávacího systému
- **Průkopník za ženská práva**: dílem "**Poddanství žen**" argumentoval za rovnoprávnost žen
- Připouštěl **úlohu vlády**, která by měla zasahovat tam, kde trh selhává (monopoly)

## 6. Francouzský utopický socialismus:
- Založen ve Francii na počátku 19. století
- Ranný pokus o vytvoření ideální společnosti založené na principech rovnosti, spravedlnosti a sociální harmonie bez třídních rozdílu prostřednictvím dobrovolné spolupráce a plánovaného hospodářství
- **Důraz na sociální rovnost** -> ekonomická a sociální nerovnost vede ke konfliktům a nespravedlnosti. 
- **Plánovaná společnost** -> Návrh komunit založených na plánované výrobě a následném přerozdělování
- **Odmítání násilné revoluce** -> Víra, že společnost lze změnit bez krveprolití pomocí vzdělání
- **Víra v lidskou dobrotu** -> morální transformace společnosti změní hodnoty a vědomí k harmonii
### Henri de Saint-Simon
- Francouzský šlechtic a osvícenec, jeden z prvních myslitelů moderního socialismu
- Věřil, že společnost by měla být řízena **vědci, inženýry a odborníky**, kteří by plánovali ekonomiku na základě **racionálních a vědeckých principů**
- Usiloval o **průmyslovou společnost**, která by eliminovala chudobu a nerovnosti

## 7. Historická německá škola:
- Založena jakožto ekonomický směr v Německu v 19. století
- Odmítala univerzální ekonomické zákony, věřila totiž, že ekonomické jevy nelze vysvětlovat pouze abstraktními teoriemi, ale musí být pochopeny v kontextu **historického vývoje, kultury a institucí**
- **Důraz na historii** -> Každé historické období a kulturní prostředí měl jiná pravidla
- **Metodický přístup** -> Ekonomie jakožto věda, která musí být založena na faktickém studiu reálných událostí vývoje, nikoliv na abstraktních modelech a teoriích
- **Odmítala Volný Trh** -> Zdůrazňovala roli státu v regulaci ekonomiky
- **Ekonomie jakožto společenská věda** -> Není jen o jednotlivcích, ale o společnosti jako celku
### Max Weber
- Jeden z nejvýznamnějších německých myslitelů, ekonomů, sociologů a filozofů 19. a 20. stol
- Svou prací položil základy pro **moderní sociologii** a pochopení procesům **racionalizace** a **byrokratizace** společnosti
- Vnímal kapitalismus jakožto **důsledek kultury a idejí**
- Dílo **Protestantská etika a duch kapitalismu**: Pojednává o protestantské pracovní etice, která hrála klíčovou roli při vzniku kapitalismu. 
- **Teorie Byrokracie**: Popis byrokracie jakožto formy organizace moderní společnosti, která se vyznačovala:
	- **Hierarchií 
	- Pravidly s jasně definovanými kompetencemi 
	- Neosobností k rozhodování a výkonu práce**
- Taktéž varoval před **nebezpečím nadměrné Byrokracie**, které vedlo k odcizení a ztráty svobody
- **Identifikoval** 3 typy legitimní moci: 
	- **Charismatická** -> Moc založená na osobních kvalitách vůdce
	- **Tradiční** -> Moc založená na tradicích a zvycích
	- **Legálně-racionální** -> Moc založená na pravidlech a zákonech
- **Teorie Sociálního jednání**: Lidské jednání **není jen výsledkem vnějších podnětů**, ale **cílevědomé a smysluplné**. Lidé tedy jednají dle svého výkladu situace a mají různé motivace

### Werner Sombart
- Německý ekonom a sociolog
- **Teorie Kapitalismu** ->Analýza vzniku Kapitalismu jakožto historického procesu, který je ovlivňován kulturními, sociálními a psychologickými faktory
- Rozlišoval Kapitalismus na dva typy:
	- **Moderní kapitalismus:** charakteristický racionalizací a velkým průmyslem
	- **Předmoderní kapitalismus**:  charakteristický obchodem a řemeslnou výrobou
- Zkoumal Náboženský vliv na ekonomický rozvoj
- Kritizoval Materialismus -> ekonomie by měla brát v úvahu i hodnoty a motivace jednotlivců
- Dílo: **Der moderne Kapitalismus** -> Analýza vývoje moderního kapitalismu
- Dílo: **Die Juden und das Wirtschaftsleben** ->Zkoumá ekonomickou roli Židů v historii

## 8. Marxismus:
- Socioekonomická a politická teorie vyvinutá Karlem Marxem a Friedrichem Engelsem v 19. století.
- Základem je analýza kapitalistické společnosti, jejich struktur a dynamiky, která se zaměřuje na konflikty mezi třídami.
- Snaží se pochopit historický vývoj společnosti a navrhnout alternativní model uspořádání, který by překonal nedostatky kapitalismu
- **Klíčové myšlenky:**
	- **Třídní boj:** Přesvědčení, že historie všech dosavadních společností je historií třídních bojů. U kapitalismu se odehrává konflikt mezi buržoazií (kapitalisti) a proletariátem (pracující)
	- **Teorie Hodnoty:** Hodnota statku se odvíjí od práce potřebné k jeho vytvoření
	- **Kritika Kapitalismu:** jakožto systému, který vytváří nerovnost a sociální nespravedlnost
	- **Historický Materialismus:** Koncept, který tvrdí, že ekonomické a materiální podmínky jsou určující pro vývoj společnosti a její kultury
	- **Sociální změna a revoluce:** Proletariát musí povstat v revoluci proti buržoazii, aby dosáhl socialismu, ve kterém budou výrobní prostředky ve vlastnictví komunity.
	- **Zrušení soukromého vlastnictví:** Výrobní prostředky ve společném vlastnictví komunit

### Karl Marx
- Německý filozof, ekonom, historik a teoretik
- Na jeho myšlenkách se zakládá celý Marxismus
- Dílo **Komunistický manifest** -> Spolu F. Engelsem shrnuje hlavní myšlenky Marxismu
- Dílo **Kapitál** -> Hlavní ekonomické dílo, kde analyzuje kapitalismus a jeho konflikty

### Friedrich Engels
- Německý filozof, sociolog a ekonom, spoluzakladatel Marxismu
- Zasadil se šíření komunistické myšlenky a zakládal socialistická hnutí
- Dílo: **Původ rodiny, soukromého vlastnictví a státu** -> Analýza vztahu mezi rodinou, vlastnictvím a sociálními strukturami


## 9. Rakouska škola
- Vznikl na konci 19. století ve Vídni
- Klade důraz na individualismus, subjektivní teorii hodnoty a svobodná trh. 
- Zaměřuje se více na mikroekonomické základy chování jednotlivců a přirozený vývoj tržních procesů, přičemž odmítá zásahy státu do ekonomiky jako takové
- **Hlavní myšlenky:**
	- **Hodnota** zboží je **určována subjektivně každým jedincem** dle jeho potřeb
	- **Marginalismus**: klade důraz na **mezní užitek** -> hodnotu statku určuje jeho poslední spotřebovaná jednotka, nikoliv jeho množství
	- **Ekonomická role jednotlivce:** Trh je výsledkem individuálních rozhodnutí a spontánních interakcí jednotlivců
	- **Teorie Nákladů obětované příležitosti:** náklady spojené s produkcí, kdy člověk má možnost alternativně produkovat jiné statky, proto musí ale obětovat statky jiné.
### Carl Menger
- Rakouský ekonom a zakladatel Rakouské ekonomické školy
- Průkopník **marginalismu** 
- Zavedl pojem **subjektivní hodnoty**
- Zavedl **Teorii mezního užitku**
- Ekonomické procesy jsou výsledkem jednání jednotlivců, kteří chtějí maximalizovat svůj užitek
- **Teorie peněz**: Zkoumal vznik peněz, které vznikly spontánně v důsledku potřeby směnit
###  Hermann Heinrich Gossen
 - Německý ekonom
 - **Zákon klesajícího mezního užitku:** Každá další jednotka spotřebovaného statku snižuje užitek
 - **2. Gossenův zákon:** Spotřebitel maximalizuje svůj celkový užitek, pokud investuje do různých statků tak, aby poslední jednotka každého statku měla stejný mezní užitek. ^1ea538
 - Dílo: **Vývoj zákonů lidského jednání a pravidel lidského soužití** ->formuloval své zákony

## 10. Keynesovství:
- Ekonomický směr vycházející z myšlenek britského ekonoma **Johna Keynese**
- Zaměřuje se na vládní zásahy do ekonomiky a význam **Agregátní poptávky**, kdy celková poptávka po zboží a službách určuje celkový objem výroby a zaměstnanosti
- Návrhy pro **aktivní zásahy vlády**, aby stimulovala poptávku v období hospodářských krizí
- Spotřeba je určována především příjmem domácností 
- Investice jsou závislé na očekávání podnikatelů a úrokových sazbách
- **Multiplikátor vládních výdajů** -> pojem popisuje, že každá investovaná koruna zvyšuje ekonomickou aktivitu o více než tuto částku díky zvýšené spotřebě
- **Fiskasní ekonomika v období recese** -> Stát má investovat i za cenu zadlužení pro podporu poptávky a tím se ekonomika stabilizovala

## 11. Neoklasická ekonomie
- Dominantní směr od konce 19. století
- Zaměřuje se na tržní rovnováhu, cenu a alokaci zdrojů prostřednictvím nabídky a poptávky
- Klade důraz na maximalizaci užitku pro obě strany obchodu
- **Racionální uvažování:** -> Spotřebitel maximalizovat užitek, firmy zisk
- **Margintalismus** (Mezní analýza) -> vysvětlení chování firem a jednotlivců
- **Teorie produkce a nákladů** ->Založena na kombinaci výrobních faktorů, firmy zvažují mezní produktivitu těchto faktorů, pro optimalizaci své produkce a zisku
### Milton Friedman:
- Americký ekonom a nositel Nobelovy ceny za ekonomii
- **Monetarismus:** víra, že množství peněz v oběhu ovlivňuje inflaci
- **Odmítal aktivní vládní zásahy** do ekonomiky -> trh se prý sám vyrovná
- **Přirozená míra nezaměstnanosti:** koncept ekonomiky vracející se v dlouhém období k určité úrovni nezaměstnanosti
- **Inflace jako peněžní jev**: inflace je vždy a všude -> je způsobena nedostatkem peněz v oběhu
- Dílo **Kapitalismus a svoboda**: Obhajova volného trhu bez vládních zásahů
- Dílo **Monetární historie Spojených států**: detailní analýza vztahu mezi peněžní zásobou a ekonomickou aktivitou trhu

---

# Metody používané v ekonomii:

^7bc192

**Sběr dat -> Analýza  trendů -> Předpovídání vývoje -> Testování hypotéz a modelů**
## 1. Pozorování: 
**Proces shromažďování, sledování a analyzování dat** o různých ekonomických jevech a procesech s cílem získat informace o tom, jak fungují ekonomiky, trhy, spotřebitelé, firmy či vládní instituce.
## 2. Srovnání:
**Proces porovnávání ekonomických ukazatelů, výkonů či výsledků mezi dvěma nebo více subjekty** (státy, regiony, firmy, sektory), za účelem analýzy rozdílů a podobností v jejich ekonomické výkonnosti či struktuře.
## 3. Abstrakce:
Je **myšlenkový proces**, při kterém **ekonomové zjednodušují složité ekonomické jevy tím, že ignorují nepodstatné detaily a zaměřují se na klíčové vlastnosti a vztahy**. Tento proces umožňuje vytvářet modely a teorie, které pomáhají vysvětlovat základní mechanismy fungování ekonomiky.
## 4. Analýza:
Proces rozboru složitých jevů nebo situací tím, že je rozdělíme na jednotlivé části, abychom lépe pochopili jejich vzájemné vztahy a fungování. Ekonomická analýza se často odehrává v rámci pohybu od **abstraktního ke konkrétnímu**, což znamená, že začíná zjednodušenými teoretickými modely a postupně přechází ke konkrétním reálným situacím.
## 5. Syntéze:
Proces, při kterém se jednotlivé části nebo prvky, které byly analyzovány odděleně, znovu kombinují do **jednoho celku**. Jde o integraci zjištěných poznatků do širšího ekonomického systému či teorie, aby vznikl celkový obraz nebo systémový pohled na ekonomický jev.
## 6. Indukce:
Myšlenkový proces, který postupuje od konkrétních pozorování nebo empirických faktů k formulaci obecných závěrů a pravidel. V ekonomii se indukce používá k vytváření teorií a zákonitostí na základě reálných dat a zkušeností.
## 7. Dedukce:
Myšlenkový **proces, při kterém se z obecných pravidel, teorií nebo zákonitostí vyvozují konkrétní závěry za dodržení logických pravidel.** V ekonomii se dedukce používá k aplikaci již existujících teorií na specifické situace nebo problémy.
## 8. Modelování:
Znamená vytváření zjednodušených obrazů nebo abstrakcí reálného světa, které pomáhají analyzovat a pochopit komplexní ekonomické jevy. Ekonomické modely se soustředí na klíčové proměnné a vztahy, zatímco ignorují méně podstatné detaily, aby bylo možné lépe studovat vzorce a predikovat výsledky.
## 9. Experiment:
**Proces praktického testování a ověřování ekonomických modelů nebo teorií za kontrolovaných podmínek**. Jeho cílem je zjistit, zda se předpoklady a závěry modelu shodují s reálným chováním ekonomických subjektů, jako jsou spotřebitelé, firmy nebo vlády.

# Ekonomický přístup ke zkoumání reality
### Mikroekonomie
- Věda zkoumající jednotlivé subjekty ekonomického prostoru (firmy, domácnosti, vlády), jejich chování a rozhodování
-  **Cílem** je analýza rozhodovacích procesů a alokace zdrojů, studování interakce mezi nabídkou a poptávkou a tím i tvorbu cen a množství statků a služeb na trhu
### Makroekonomie:
- Věda zkoumající ekonomiku jakožto celek, analyzuje např. inflaci, nezaměstnanost nebo hospodářský růst
- **Cílem** je analyzovat agregátní ekonomické ukazatele (HDP, inflace atd.), jak politická rozhodnutí ovlivňují celkovou ekonomickou výkonnost a stabilitu, ekonomické cykly a výkyvy. ^f5d8e4
### Pozitivní ekonomie:
- Zaměřuje na popis a analýzu ekonomických jevů a vztahů bez hodnocení a osobních názorů. Tato disciplína se snaží objektivně a vědecky porozumět tomu, jak ekonomické systémy fungují, a jaké důsledky mají různé ekonomické aktivity a politiky.
### Normativní ekonomie:
- Opak pozitivní
- Zaměřuje na hodnotové soudy, názory a doporučení týkající se ekonomických politik a rozhodnutí. Na rozdíl od pozitivní ekonomie vyjadřuje, jak by věci měly být, a hodnotí ekonomické situace na základě etických, sociálních nebo politických kritérií.
---


# Potřeby a zdroje:

^ef75c4
### Potřeby
- Každý jednotlivec má své potřeby
- Uspokojíme je pomocí výrobků a služeb
### Zdroje

^17dca5

- Jsou výrobní faktory pro výrobu nebo poskytnutí služby
- **Půda:** -> Někde musíte výrobu / poskytování služby dělat (pronájem, pozemky atd.)
- **Kapitál:** -> Pro poskytnutí služby / výrobu musíte mít finanční prostředky (Stroje, materiál)
- **Práce:** -> Každá služba nebo výrobek potřebuje lidskou sílu (Zaměstnanci)
- **Vzácnost zdrojů:** -> Volba nejlepší možnosti pro výrobu / poskytování (Jaké zdroje použijeme?)
- **Alternativní náklady:**  -> **Hodnota ušlého zisku** z nerealizované druhé nejlepší varianty
- **Efektivnost a Racionalita** při plánování a přerozdělování zdroje
- **Racionálně** se snažíme produkovat a nakupovat jen to, co skutečně prodáme / potřebujeme

![[Pasted image 20241012152558.png]]
**Vstupní veličiny** (Práce, Kapitál, Půda) se snažíme minimalizovat
Naopak **výstupní veličiny** (Množství prodaného zboží) se snažíme maximalizovat

# Hranice produkčních možností (PPF):

^b40542

**Production-Possibility Frontier**
- Hranice mezi **efektivní** a **neefektivní** výrobou v rámci daných zdrojů
- Jinými slovy: **Snažíme se maximalizovat produkci produkci z omezených zdrojů, přičemž zvýšení produkce jednoho statku ovlivní produkci statku druhého.**
- **Volíme možnosti produkce na základě spotřeby**, jestliže produkované nedokážeme prodat, přicházíme o možné zisky

![[Pasted image 20241012152613.png]]
### Produkční možnosti farmy:
- Farma je schopna ze svých aktuálních zdrojů vyprodukovat **40 tun kukuřice**, anebo **65 tun brambor.** 
- Taktéž má možnost zvolit si kombinaci, kdy bude pěstovat obě tyto plodiny **zároveň**.
- Musíme si však uvědomit **omezenost zdrojů farmy**, kdy pěstování jedné plodiny, ovlivní množství vypěstované druhé plodiny

**A**: -> Farma tedy produkuje ze všech svých zdrojů jen **40 tun kukuřice**
**B**: -> Farma tedy produkuje ze všech svých zdrojů **30 tun kukuřice**, ale i **38 tun brambor**
**C:** -> Farma tedy produkuje ze všech svých zdrojů **20 tun kukuřice**, ale i **52 tun brambor**
**D**: -> Farma tedy produkuje ze všech svých zdrojů **10 tun kukuřice**, ale i **65 tun brambor**
**E**: -> Farma tedy produkuje ze všech svých zdrojů jen **65 tun brambor**

### Alternativní náklady:

^9d2fa8

- Představme si, že doposud farmář pěstoval pouze 40 tun kukuřice a chce pěstovat i brambory
- Z toho vyplývá, že má možnost výběru z možností **B C D**
- Zvolí **možnost B**, proto ale musel **obětovat** 10 tun Kukuřice, jelikož již tuto kukuřici neměl kde vysadit
- To samé by se stalo, i kdyby si farmář po roce rozmyslel a zvolil možnost C. Musel tedy obětovat dalších 10 tun kukuřice, aby získal **navíc 14 tun brambor**
![[Pasted image 20241012151236.png]]
- Farmář tedy je schopen vyprodukovat za rok **20 Tun kukuřice a 52 tun brambor**
- **Alternativním nákladem oproti možnosti A je obětování 20 Tun kukuřice** *ve prospěch 52 tun brambor*
- **Alternativním nákladem oproti možnosti B je obětování 10 Tun kukuřice** *ve prospěch 14 tun brambor, jelikož už jsme 38 tun brambor pěstovali*

### Mezní míra Transformace (MRT):
**Marginal Rate of Transformation**
- Měříme **sklon Hranice Produkčních Možností PPF**
- Ukazuje, jak lze nahradit výrobu jednoho produktu výrobou produktu jiného *(Modrá šipka)*
- Výsledek MRT tedy ukáže, kolik jednotek jednoho produktu musíme obětovat, abychom získali určité množství jednotek produktu druhého
![[Pasted image 20241012155756.png]]
**ΔY** ->představuje změnu množství 1. produktu, ze kterého budeme ubírat
**(y2 - y1 -> Nové množství - Původní množství)**
**ΔX** -> představuje změnu množství 2. produktu, který budeme přidávat
**(x2 - x1 -> Nové množství - Původní množství)**

Příklad: **B -> C** MRT = (20 - 30) / (52-38) = **-10 / 14**
Příklad: **A -> C** MRT = (20 - 40) / (52 - 0) = **-20 / 52**

### Ekonomický růst vyjádřený posunem PPF
- Firma je postupem času schopna získat více zdrojů a tím zvýšit svou PPF
![[Pasted image 20241012151812.png]]
**Černá čára:** Aktuální Produkční možnosti firmy ze zdrojů, které aktuálně má
**Červená čára**: Firma investovala do nových zdrojů, tudíž produkční možnosti se zvýší
**Žluté pole:** Jen vizualizace o kolik si vlastně firma investicemi do zdrojů přilepší oproti současnosti

### Fyzické a institucionální produkční možnosti ekonomiky

^4e79a4

**Fyzické:** -> Jsou možnosti, kdy firma zcela a absolutně využívá k produkci všechny své zdroje
**Institucionální:** -> Jsou možnosti, kdy firma je nucena omezit o určité množství využívání svých zdrojů k produkci *(například obědová přestávka zaměstnancům)*
![[Pasted image 20241012161405.png]]


# Poznámky a Vysvětlivky:

[[#^89bb5e]] **Ekonomický prostor** -> je komplexní koncept, který zohledňuje veškeré ekonomické, sociální a politické faktory, které mohou ovlivnit ekonomickou činnost v daném regionu.

[[#^f5d8e4]] **Agregátní** -> celková nabídka zboží a služeb v národní ekonomice v určitém časovém období, vyjádřenou v penězích. 
 




  
