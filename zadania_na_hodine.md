# AI Workshop - Pracovný list

> Prejdite si materiály a doplňte chýbajúce časti. Tento pracovný list vám pomôže pochopiť kľúčové koncepty práce s AI asistentmi.

### Primárne zdroje

| Zdroj | Odkaz |
|-------|-------|
| PDF dokument | **AI_Workshop.pdf** |
| YouTube playlist | [Claude Code Workshop](https://youtube.com/playlist?list=PLJW-oHbyRDeL62yOcaqjex7cKnzcEYQXi&si=JUX_Bc2piFMk1NwJ) |
| GitHub dokumentácia | [github.com/Kames003/Claude-](https://github.com/Kames003/Claude-) |

---

## Úvod: Čo je AI Asistent?

### Architektúra

```
+-------------+     +------------------+     +-------------+
| POUZIVATEL  | <-> |   AI ASISTENT    | <-> |     LLM     |
|             |     |   (interface)    |     |   (model)   |
+-------------+     +------------------+     +-------------+
     Ty                 Prostredník            "Mozog"
```

**LLM (Large Language Model)** je samotný jazykový model - "mozog", ktorý generuje odpovede. Príklady: GPT-4, Claude, Gemini, Llama...

**AI Asistent** je vrstva medzi tebou a LLM. Je to softvér, ktorý:
- Prijíma tvoje požiadavky
- Pridáva kontext (systémové inštrukcie, informácie o projekte)
- Posiela to do LLM
- Prijíma odpoveď a môže vykonávať akcie (editovať súbory, spúšťať príkazy)

### Prečo potrebujeme AI Asistenta?

Samotný LLM je len "textový generátor". AI Asistent mu dáva:

| Schopnosť | Popis |
|-----------|-------|
| **Nástroje (Tools)** | Možnosť čítať/písať súbory, spúšťať príkazy |
| **Kontext** | Informácie o tvojom projekte, pravidlá |
| **Pamäť** | Uchovávanie histórie konverzácie |
| **Bezpečnosť** | Systém povolení, sandbox |

### Coding AI Asistenti

Existuje viacero coding AI asistentov:
- **CLI nástroje** (príkazový riadok) - napr. Claude Code, Aider, Cursor CLI
- **IDE rozšírenia** - napr. GitHub Copilot, Cursor, Windsurf
- **Webové rozhrania** - napr. ChatGPT, Claude.ai

Koncepty, ktoré sa naučíš v tomto workshope, sú **univerzálne** a aplikovateľné na väčšinu z nich.

---

# ČASŤ 1: Setup a základy

## 1. CLI vs GUI

Mnoho AI asistentov funguje ako **CLI** nástroj.

**CLI** znamená _________________________ a znamená to, že s nástrojom komunikujeme cez _________________________.

**GUI** znamená _________________________ - klasické okná, tlačidlá, myš.

### Výhody CLI pre programátorov

Doplň výhody:
- Rýchlejšie pre skúsených používateľov
- Ľahko sa _________________________ (automatizácia)
- Funguje cez _________________________ (SSH)
- Menej náročné na _________________________

---

## 2. Sessions - konverzácie s AI

AI asistent si pamätá konverzáciu v tzv. **session** (sedenie/relácia).

### Čo je session?

Session = jedna súvislá konverzácia s AI asistentom. Obsahuje:
- Tvoje správy (prompty)
- Odpovede AI
- Vykonané akcie
- Zdieľaný kontext

### Správa sessions

| Akcia | Čo to znamená |
|-------|---------------|
| Nová session | Začínam "s čistým stolom" - AI nevie nič o predošlej práci |
| Pokračovanie v session | AI si pamätá celú predošlú konverzáciu |
| Vymazanie session | Zahodím históriu a začnem odznova |

### Kedy začať novú session?

Napíš 2 dôvody, prečo by si chcel začať novú session:

1. _________________________________________________________________

2. _________________________________________________________________

---

# ČASŤ 2: Base usage a IDE integrácia

## 3. Konfigurácia AI Asistentov

Väčšina AI asistentov má viacero úrovní nastavení.

### Hierarchia nastavení (od najnižšej po najvyššiu prioritu)

```
+----------------------------------------+
|  3. LOKÁLNE (najvyššia priorita)       |  <- Moje osobné nastavenia
+----------------------------------------+
|  2. PROJEKTOVÉ                         |  <- Zdieľané v tíme
+----------------------------------------+
|  1. GLOBÁLNE (najnižšia priorita)      |  <- Platí všade
+----------------------------------------+
```

### Prečo existujú lokálne nastavenia?

Lokálne nastavenia typicky **nie sú** súčasťou Git repozitára.

Je to preto, lebo: _________________________________________________________________

---

## 4. Context Window a Tokeny

### Čo je context window?

Context window = maximálne množstvo textu (tokenov), ktoré LLM "vidí" naraz.

```
+-----------------------------------------------------------+
|                    CONTEXT WINDOW                         |
|  +-----------------------------------------------------+  |
|  | System prompt (inštrukcie pre AI)                   |  |
|  +-----------------------------------------------------+  |
|  | Informácie o nástrojoch                             |  |
|  +-----------------------------------------------------+  |
|  | História konverzácie                                |  |
|  +-----------------------------------------------------+  |
|  | Tvoj aktuálny prompt                                |  |
|  +-----------------------------------------------------+  |
|  | [REZERVA pre odpoveď AI]                            |  |
|  +-----------------------------------------------------+  |
+-----------------------------------------------------------+
```

### Tokeny

**Token** nie je to isté ako slovo. Token je jednotka, ktorú LLM spracováva.

Približne: **1 token = cca 4 znaky** alebo **100 tokenov = cca 75 slov**

### Compaction (komprimácia)

Keď konverzácia presiahne limit, AI asistent vykoná **compaction**:

**Compaction** = _________________________

**Výhoda:** AI môže pokračovať v práci

**Nevýhoda:** _________________________ (niektoré detaily sa stratia)

---

## 5. IDE Integrácie

Mnoho AI asistentov má integrácie s IDE (napr. VS Code).

### Čo poskytujú?

| Funkcia | Popis |
|---------|-------|
| Diff viewer | Porovnanie zmien pred/po |
| Inline akceptácia | Schválenie zmien priamo v editore |
| Sync | Synchronizácia medzi CLI a IDE |

### Prečo ich používať?

Ľahšie sa _________________________ zmeny pred ich akceptovaním.

---

# ČASŤ 3: Advance Permissions Management

## 6. Permissions - bezpečnosť

AI asistent má prístup k tvojmu súborovému systému. To je **mocné, ale nebezpečné**.

### Typy akcií podľa rizika

| Riziko | Príklad akcie | Vyžaduje povolenie? |
|--------|---------------|---------------------|
| Nízke | Čítanie súborov | Nie |
| Stredné | Editovanie súborov v projekte | Záleží na nastavení |
| Vysoké | Spúšťanie shell príkazov | Áno |
| Kritické | Git operácie (push, reset) | Áno |

### Auto-accept módy

**Čo typicky môže AI robiť bez pýtania:**
- Čítať súbory
- Editovať súbory v projekte

**Čo stále vyžaduje povolenie:**
- _________________________
- _________________________
- Operácie mimo projekt

---

## 7. Dangerous Mode

Niektorí asistenti ponúkajú režim, ktorý preskočí všetky povolenia.

**Riziká:**
- AI môže _________________________ git históriu
- AI môže _________________________ súbory
- AI môže spustiť _________________________ skripty

### Kedy by sa to mohlo hodiť?

Pri použití v kombinácii so _________________________ prostredím.

---

## 8. Sandbox - izolované prostredie

**Sandbox** = izolované prostredie, kde AI môže pracovať bez rizika poškodenia systému.

### Typy sandboxov

| Typ | Popis |
|-----|-------|
| Docker sandbox | Beh v Docker kontajneri |
| Natívny sandbox | Vstavaný v AI asistentovi |

Predstav si sandbox ako: _________________________________________________________________

---

# ČASŤ 4: Version Control a Undo

## 9. Vracanie zmien

### Prečo je Git dôležitý pri práci s AI?

1. _________________________________________________________________

2. _________________________________________________________________

### Možnosti vrátenia zmien

| Metóda | Popis |
|--------|-------|
| Git revert/reset | Klasické git príkazy |
| IDE diff nástroje | Porovnanie "pred" a "po" |
| Zabudované undo | Vlastný mechanizmus asistenta |

### Dôležité

Pred väčšími zmenami je **VŽDY** dobré urobiť _________________________.

---

# ČASŤ 5: Plan Mode

## 10. Plan Mode

**Plan Mode** = plánovací režim pred implementáciou.

### Ako to funguje?

```
+-----------------------------------------------------------+
|                     PLAN MODE                             |
|                                                           |
|  1. AI analyzuje požiadavku                               |
|  2. Kladie upresňujúce otázky                             |
|  3. Navrhuje plán riešenia                                |
|  4. Čaká na tvoje schválenie                              |
|  5. AŽ POTOM začne implementovať                          |
|                                                           |
|  POZOR: V Plan Mode AI NEMÔŽE robiť zmeny!                |
+-----------------------------------------------------------+
```

### Kedy použiť Plan Mode?

- Pri _________________________ úlohách
- Keď si _________________________ výsledkom
- Pri úlohách ovplyvňujúcich _________________________

### Výhody

1. Predídeš zbytočným _________________________
2. Môžeš ovplyvniť riešenie _________________________ než je implementované
3. AI lepšie _________________________ tvoje požiadavky

---

# ČASŤ 6: Context Engineering a projektové inštrukcie

## 11. Špecifické inštrukcie a SPEC.md

### Čo je SPEC.md?

SPEC.md = dokument so špecifikáciou projektu/funkcionality.

### Rozdiel medzi inštrukciami a špecifikáciou

| Súbor | Účel | Veľkosť |
|-------|------|---------|
| Inštrukcie (CLAUDE.md) | Pravidlá pre AI | Stručný |
| SPEC.md | Detailný popis funkcionality | Môže byť dlhší |

### Stratégia použitia

V inštrukciách môžeš napísať:
```
Keď implementuješ novú funkcionalitu, pozri sa do @SPEC.md
```

**Prečo je to lepšie?** _________________________________________________________________

---

## 12. Projektové inštrukcie (CLAUDE.md)

Väčšina AI asistentov podporuje súbor s inštrukciami (napr. `CLAUDE.md`, `.cursorrules`).

### Čo obsahuje?

```markdown
# Názov projektu
Stručný popis...

# Pravidlá
- Používaj TypeScript
- Píš testy pre každú funkciu

# Architektúra
- /src - zdrojové súbory
- /tests - testy
```

### Kedy sa načíta?

Tento súbor sa **automaticky načíta** pri každej session a stáva sa súčasťou _________________________.

### Prečo má byť stručný?

_________________________________________________________________

### Vnorené inštrukcie

```
projekt/
  CLAUDE.md           <- načíta sa vždy
  frontend/
    CLAUDE.md         <- načíta sa len pri práci vo frontend/
  backend/
    CLAUDE.md         <- načíta sa len pri práci v backend/
```

---

## 13. Context Engineering

**Context Engineering** = umenie poskytnúť AI správny kontext.

### Základné princípy

| Princíp | Vysvetlenie |
|---------|-------------|
| Relevantnosť | Pridávaj len _________________________ informácie |
| Stručnosť | Šetri _________________________ |
| Štruktúra | Používaj formátovanie pre _________________________ |

### XML tagy pre štruktúru

```xml
<error>
TypeError: Cannot read property 'map' of undefined
    at UserList.js:15
</error>
```

**Prečo je to lepšie?** _________________________________________________________________

---

# ČASŤ 7: Nástroje a rozšírenia

## 14. Nástroje (Tools)

AI asistenti môžu mať prístup k rôznym nástrojom:

### Základné nástroje

| Nástroj | Čo robí |
|---------|---------|
| File Read | Číta obsah súborov |
| File Write | Zapisuje/upravuje súbory |
| Shell/Bash | Spúšťa terminálové príkazy |
| Web Search | Vyhľadáva na internete |
| Web Fetch | Načítava obsah webových stránok |

---

## 15. Thinking Mode

**Thinking Mode** = režim, kde AI "premýšľa nahlas" a ukazuje svoj myšlienkový proces.

### Výhody a nevýhody

| Výhody | Nevýhody |
|--------|----------|
| Vidíš ako AI uvažuje | Spotrebuje viac _________________________ |
| Kvalitnejšie odpovede | _________________________ odpoveď |
| Odhalíš chyby v uvažovaní | |

### Kedy ho vypnúť?

Pri _________________________ úlohách, kde nepotrebujeme detailné uvažovanie.

---

## 16. Práca s dokumentáciou

AI asistenti môžu pristupovať k externej dokumentácii:

| Spôsob | Popis |
|--------|-------|
| Web search | AI vyhľadá na internete |
| Web fetch | AI načíta konkrétnu URL |
| MCP servery | Špecializované nástroje |
| Copy-paste | Manuálne vložíš do promptu |

### Tip: Markdown dokumentácia

Väčšina dokumentácií ponúka Markdown verziu. Je lepšia, pretože:
- Menej "šumu"
- Šetrí _________________________
- Lepšie sa _________________________

---

## 17. MCP - Model Context Protocol

**MCP** = štandard pre pridávanie nových nástrojov a zdrojov pre AI asistentov.

Príklad: MCP server pre dokumentáciu umožňuje AI ľahšie _________________________.

### Ako funguje?

```
+------------------+     +------------------+     +------------------+
|   AI ASISTENT    | <-> |   MCP SERVER     | <-> |  EXTERNÝ ZDROJ   |
+------------------+     +------------------+     +------------------+
```

---

# ČASŤ 8: Skills a Custom Commands

## 18. Skills

**Skills** = rozšírené schopnosti AI asistenta pre špecifické úlohy.

### Čo sú skills?

Skills sú v podstate "balíčky" obsahujúce:
- Špecifické inštrukcie
- Definované nástroje
- Workflow pre konkrétnu úlohu

### Ako fungujú?

AI asistent ich môže:
- Automaticky objaviť a použiť keď sú potrebné
- Spustiť na základe tvojej výzvy

### Third-party skills

Existujú platformy so zdieľanými skills (napr. skills.sh).

**Výhoda používania hotových skills:** _________________________________________________________________

---

## 19. Custom Commands

**Custom Commands** = znovu použiteľné prompty, ktoré si vytvoríš sám.

### Prečo ich používať?

Predstav si, že často robíš code review s rovnakým promptom. Namiesto opakovania môžeš vytvoriť command.

### Štruktúra custom command

```yaml
description: Popis čo command robí
allowed-tools: [Read]  # Obmedzenie nástrojov
---
Tvoj prompt tu...
$ARGUMENTS  # Placeholder pre argumenty
```

### Príklad použitia

Command `/review` s argumentom:
```
/review src/components/Button.js
```

### Kde ich uložiť?

- **Lokálne** - v projekte (zdieľané s tímom)
- **Globálne** - na tvojom počítači (osobné)

---

# ČASŤ 9: Hooks a Plugins

## 20. Hooks

**Hooks** = automatické reakcie na udalosti AI asistenta.

### Ako fungujú?

```
+------------------+     +------------------+     +------------------+
|  AI VYKONÁ       | --> |     HOOK SA      | --> |   SPUSTÍ SA      |
|  AKCIU           |     |    AKTIVUJE      |     |   TVOJ KÓD       |
+------------------+     +------------------+     +------------------+
```

### Typy hookov

| Typ | Kedy sa spustí |
|-----|----------------|
| PreToolUse | Pred použitím nástroja |
| PostToolUse | Po použití nástroja |

### Príklad použitia

Po každej úprave súboru automaticky spustiť formátovač kódu.

**Hook sa spustí po:** _________________________

**Vykoná:** _________________________

---

## 21. Plugins

**Plugins** = hotové balíčky rozširujúce funkcionalitu AI asistenta.

### Čo môžu obsahovať?

- MCP servery
- Custom commands
- Skills
- Hooks

### Kde ich nájsť?

- Oficiálny marketplace
- Interné firemné repozitáre
- GitHub

**Výhoda:** Nemusíš všetko nastavovať od začiatku - použiješ hotové riešenie.

---

# ČASŤ 10: Feedback Loops a Multi-Agent systémy

## 22. Feedback Loops

**Feedback Loop** = mechanizmus, kde AI sama overuje svoju prácu.

### Prečo je to dôležité?

AI môže robiť chyby. Feedback loop jej umožňuje:
1. Vykonať zmenu
2. _________________________ výsledok
3. Opraviť chyby
4. Opakovať

### Typy feedback loops

| Typ | Popis |
|-----|-------|
| Unit testy | AI spustí testy a opraví zlyhania |
| Browser testing | AI otvorí prehliadač a skontroluje UI |
| Linting | AI skontroluje kvalitu kódu |

### Príklad: Playwright

Playwright umožňuje AI otvoriť prehliadač a _________________________ webstránku.

**Nevýhoda feedback loops:** Vyššia spotreba _________________________

### Pozor na testy písané AI

AI má tendenciu písať testy, ktoré _________________________.

Preto je dobré testy buď písať pred implementáciou alebo ich _________________________.

---

## 23. Multi-Agent systémy (Ralph Loops)

**Multi-Agent systém** = viacero AI agentov pracujúcich spoločne alebo AI bežiaca v slučke.

### Ralph Loop - koncept

```
+-----------------------------------------------------------+
|                      RALPH LOOP                           |
|                                                           |
|  while (tasks_remaining && iterations < MAX):             |
|      1. Agent si vyberie task zo zoznamu                  |
|      2. Implementuje riešenie                             |
|      3. Spustí testy                                      |
|      4. Označí task ako hotový                            |
|      5. Pokračuje na ďalší task                           |
|                                                           |
+-----------------------------------------------------------+
```

### Ako to funguje?

1. Vytvoríš zoznam úloh (napr. v PRD súbore)
2. Spustíš agenta v slučke
3. Agent si vyberá a plní úlohy automaticky
4. Ty len kontroluješ výsledky

### Výhody

- Menej manuálnej práce
- Vhodné pre _________________________

### Nevýhody

- Menšia _________________________ nad procesom
- Agent sa môže "zaseknúť"
- Stále potrebuješ dobrý _________________________ a jasné úlohy

### Čo je potrebné pre úspešný Ralph Loop?

1. Dobre definované _________________________
2. Funkčné _________________________
3. Sandbox prostredie pre _________________________
4. Kvalitný project _________________________

---

# Zhrnutie

## 24. Prehľad konceptov

Spoj pojem s definíciou:

| Pojem | | Definícia |
|-------|---|-----------|
| Context Window | | A. Automatická kompresia konverzácie |
| Compaction | | B. Izolované bezpečné prostredie |
| Sandbox | | C. Maximálna kapacita "pamäte" LLM |
| Skills | | D. Znovu použiteľné prompty |
| Custom Commands | | E. Rozšírené schopnosti pre špecifické úlohy |
| Hooks | | F. Automatické reakcie na udalosti |
| Feedback Loop | | G. AI overuje svoju vlastnú prácu |
| Ralph Loop | | H. Agent pracujúci v automatickej slučke |

---

## Reflexia

**Čo ťa z workshopu najviac zaujalo alebo prekvapilo?**

_________________________________________________________________

_________________________________________________________________

**Aké sú podľa teba najväčšie výhody používania AI asistentov?**

_________________________________________________________________

_________________________________________________________________

**Aké sú podľa teba najväčšie riziká?**

_________________________________________________________________

_________________________________________________________________

**Ako by si mohol využiť tieto koncepty vo svojich projektoch?**

_________________________________________________________________

_________________________________________________________________

---

# Prehľad všetkých otázok

> Klikni na otázku pre presmerovanie na príslušnú sekciu v dokumente.

---

## ČASŤ 1: Setup a základy

### [1. CLI vs GUI](#1-cli-vs-gui)
- [ ] Čo znamená CLI?
- [ ] Cez čo komunikujeme s CLI nástrojom?
- [ ] Čo znamená GUI?
- [ ] Ako sa CLI ľahko... (automatizácia)?
- [ ] Cez čo funguje CLI vzdialene?
- [ ] Na čo je CLI menej náročné?

### [2. Sessions](#2-sessions---konverzácie-s-ai)
- [ ] Dva dôvody, prečo začať novú session

---

## ČASŤ 2: Base usage a IDE integrácia

### [3. Konfigurácia](#3-konfigurácia-ai-asistentov)
- [ ] Prečo lokálne nastavenia nie sú v Git repozitári?

### [4. Context Window a Tokeny](#4-context-window-a-tokeny)
- [ ] Čo je compaction?
- [ ] Aká je nevýhoda compaction?

### [5. IDE Integrácie](#5-ide-integrácie)
- [ ] Prečo používať IDE integrácie? (ľahšie sa...)

---

## ČASŤ 3: Advance Permissions Management

### [6. Permissions](#6-permissions---bezpečnosť)
- [ ] Čo stále vyžaduje povolenie? (2 odpovede)

### [7. Dangerous Mode](#7-dangerous-mode)
- [ ] Čo môže AI urobiť s git históriou?
- [ ] Čo môže AI urobiť so súbormi?
- [ ] Aké skripty môže AI spustiť?
- [ ] S akým prostredím sa dangerous mode kombinuje?

### [8. Sandbox](#8-sandbox---izolované-prostredie)
- [ ] Ako si predstaviť sandbox? (prirovnanie)

---

## ČASŤ 4: Version Control a Undo

### [9. Vracanie zmien](#9-vracanie-zmien)
- [ ] Dva dôvody, prečo je Git dôležitý pri práci s AI
- [ ] Čo je dobré urobiť pred väčšími zmenami?

---

## ČASŤ 5: Plan Mode

### [10. Plan Mode](#10-plan-mode)
- [ ] Pri akých úlohách použiť Plan Mode?
- [ ] Kedy si... výsledkom?
- [ ] Aké úlohy ovplyvňujú...?
- [ ] Čomu predídeš zbytočným...?
- [ ] Kedy môžeš ovplyvniť riešenie?
- [ ] Čo AI lepšie...?

---

## ČASŤ 6: Context Engineering a projektové inštrukcie

### [11. SPEC.md](#11-špecifické-inštrukcie-a-specmd)
- [ ] Prečo je lepšie odkazovať na SPEC.md z CLAUDE.md?

### [12. Projektové inštrukcie](#12-projektové-inštrukcie-claudemd)
- [ ] Súčasťou čoho sa stáva CLAUDE.md pri načítaní?
- [ ] Prečo má byť CLAUDE.md stručný?

### [13. Context Engineering](#13-context-engineering)
- [ ] Aké informácie pridávať? (relevantnosť)
- [ ] Čo šetríme stručnosťou?
- [ ] Prečo používať formátovanie?
- [ ] Prečo sú XML tagy lepšie?

---

## ČASŤ 7: Nástroje a rozšírenia

### [15. Thinking Mode](#15-thinking-mode)
- [ ] Čo spotrebuje thinking mode viac?
- [ ] Aká je odpoveď s thinking mode?
- [ ] Pri akých úlohách ho vypnúť?

### [16. Práca s dokumentáciou](#16-práca-s-dokumentáciou)
- [ ] Čo šetrí Markdown dokumentácia?
- [ ] Ako sa lepšie... Markdown?

### [17. MCP](#17-mcp---model-context-protocol)
- [ ] Čo umožňuje MCP server pre dokumentáciu?

---

## ČASŤ 8: Skills a Custom Commands

### [18. Skills](#18-skills)
- [ ] Výhoda používania hotových skills?

---

## ČASŤ 9: Hooks a Plugins

### [20. Hooks](#20-hooks)
- [ ] Po čom sa hook spustí? (príklad)
- [ ] Čo hook vykoná? (príklad)

---

## ČASŤ 10: Feedback Loops a Multi-Agent systémy

### [22. Feedback Loops](#22-feedback-loops)
- [ ] Čo robí AI v kroku 2 feedback loop?
- [ ] Čo umožňuje Playwright?
- [ ] Aká je nevýhoda feedback loops? (spotreba)
- [ ] Aké testy má AI tendenciu písať?
- [ ] Čo robiť s testami písanými AI?

### [23. Multi-Agent systémy](#23-multi-agent-systémy-ralph-loops)
- [ ] Pre čo sú Ralph Loops vhodné?
- [ ] Čo je menšie pri Ralph Loops? (kontrola)
- [ ] Čo stále potrebuješ? (plán)
- [ ] 4 veci potrebné pre úspešný Ralph Loop

---

## Zhrnutie

### [24. Prehľad konceptov](#24-prehľad-konceptov)
- [ ] Spoj 8 pojmov s definíciami (A-H)

### [Reflexia](#reflexia)
- [ ] Čo ťa najviac zaujalo/prekvapilo?
- [ ] Najväčšie výhody AI asistentov?
- [ ] Najväčšie riziká?
- [ ] Ako využiť vo svojich projektoch?

---


*AI Workshop | SPSIT | Tom. Muc.*
