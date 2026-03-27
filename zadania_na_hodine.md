# AI Workshop - Pracovný list

> Prejdite si dokument **AI_Workshop.pdf** a doplňte chýbajúce časti. Tento pracovný list vám pomôže pochopiť kľúčové koncepty práce s AI asistentmi.

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

## 3. Context Window - kľúčový koncept

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

## 4. Konfigurácia AI Asistentov

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

## 5. Permissions - bezpečnosť

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

### Dangerous Mode

Niektorí asistenti ponúkajú režim, ktorý preskočí všetky povolenia.

**Riziká:**
- AI môže _________________________ git históriu
- AI môže _________________________ súbory
- AI môže spustiť _________________________ skripty

### Sandbox - izolované prostredie

**Sandbox** = izolované prostredie, kde AI môže pracovať bez rizika poškodenia systému.

Existujú dva typy:
- **Docker sandbox** - beh v Docker kontajneri
- **Natívny sandbox** - vstavaný v AI asistentovi

Predstav si sandbox ako: _________________________________________________________________

---

## 6. Version Control a Undo

### Prečo je Git dôležitý pri práci s AI?

1. _________________________________________________________________

2. _________________________________________________________________

### Možnosti vrátenia zmien

| Metóda | Popis |
|--------|-------|
| Git revert/reset | Klasické git príkazy |
| IDE diff nástroje | Porovnanie "pred" a "po" |
| Zabudované undo | Vlastný mechanizmus asistenta |

---

## 7. Projektové inštrukcie

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

## 8. Špecifikačné dokumenty

### Rozdiel medzi inštrukciami a špecifikáciou

| Súbor | Účel | Veľkosť |
|-------|------|---------|
| CLAUDE.md | Pravidlá pre AI | Stručný |
| SPEC.md | Detailný popis funkcionality | Môže byť dlhší |

### Stratégia použitia

V inštrukciách môžeš napísať:
```
Keď implementuješ novú funkcionalitu, pozri sa do @SPEC.md
```

**Prečo je to lepšie?** _________________________________________________________________

---

## 9. Context Engineering

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

---

## 11. Thinking Mode

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

## 12. Nástroje (Tools)

AI asistenti môžu mať prístup k rôznym nástrojom:

### Základné nástroje

| Nástroj | Čo robí |
|---------|---------|
| File Read | Číta obsah súborov |
| File Write | Zapisuje/upravuje súbory |
| Shell/Bash | Spúšťa terminálové príkazy |
| Web Search | Vyhľadáva na internete |
| Web Fetch | Načítava obsah webových stránok |

### MCP - Model Context Protocol

**MCP** = štandard pre pridávanie nových nástrojov a zdrojov pre AI asistentov.

Príklad: MCP server pre dokumentáciu umožňuje AI ľahšie _________________________.

---

## 13. Skills

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

**Dôležité:** Vždy si preštuduj skill predtým, než ho použiješ - môžeš ho upraviť podľa svojich potrieb.

---

## 14. Custom Commands

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

## 15. Hooks

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

## 16. Plugins

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

## 17. Feedback Loops

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

## 18. Multi-Agent systémy (Ralph Loops)

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

## 19. IDE Integrácie

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

## 20. Práca s dokumentáciou

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

## 21. Zhrnutie konceptov

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

*AI Workshop | SPSIT*
