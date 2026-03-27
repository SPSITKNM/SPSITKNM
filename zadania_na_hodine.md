# AI Workshop - Pracovný list

> Prejdite si dokument **AI_Workshop.pdf** a doplňte chýbajúce časti. Nebojte sa, nie je to test - je to nástroj na pochopenie konceptov.

---

## Úvod: Čo je AI Asistent?

### Architektúra

```
┌─────────────┐     ┌──────────────────┐     ┌─────────────┐
│  POUŽÍVATEĽ │ ←→  │   AI ASISTENT    │ ←→  │     LLM     │
│             │     │   (interface)    │     │   (model)   │
└─────────────┘     └──────────────────┘     └─────────────┘
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
- Ľahko sa _________________________  (automatizácia)
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

> **Hint:** Premýšľaj o situácii, keď sa AI "zasekne" alebo keď kontext narastie...

---

## 3. Context Window - kľúčový koncept

### Čo je context window?

Context window = maximálne množstvo textu (tokenov), ktoré LLM "vidí" naraz.

```
┌─────────────────────────────────────────────────────────┐
│                    CONTEXT WINDOW                       │
│  ┌─────────────────────────────────────────────────┐   │
│  │ System prompt (inštrukcie pre AI)               │   │
│  ├─────────────────────────────────────────────────┤   │
│  │ Informácie o nástrojoch                         │   │
│  ├─────────────────────────────────────────────────┤   │
│  │ História konverzácie                            │   │
│  ├─────────────────────────────────────────────────┤   │
│  │ Tvoj aktuálny prompt                            │   │
│  ├─────────────────────────────────────────────────┤   │
│  │ [REZERVA pre odpoveď AI]                        │   │
│  └─────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
```

### Tokeny

**Token** ≠ slovo. Token je jednotka, ktorú LLM spracováva.

Približne: **1 token ≈ 4 znaky** alebo **100 tokenov ≈ 75 slov**

Príklad:
```
"Hello world" = 2 tokeny
"Ahoj svet" = 3 tokeny (slovenčina je "drahšia")
```

### Čo sa stane, keď sa context window zaplní?

Keď konverzácia presiahne limit, AI asistent vykoná **compaction** (komprimáciu):

**Compaction** = _________________________

**Výhoda:** AI môže pokračovať v práci
**Nevýhoda:** _________________________ (niektoré detaily sa stratia)

### Prečo je dôležité rozumieť context window?

Doplň:
- Príliš dlhé konverzácie vedú k _________________________
- Nepotrebný kontext _________________________ tokeny
- Čím viac tokenov použijeme, tým _________________________ to stojí

---

## 4. Konfigurácia AI Asistentov

Väčšina AI asistentov má viacero úrovní nastavení.

### Hierarchia nastavení (od najnižšej po najvyššiu prioritu)

```
┌────────────────────────────────────────┐
│  3. LOKÁLNE (najvyššia priorita)       │  ← Moje osobné nastavenia
├────────────────────────────────────────┤
│  2. PROJEKTOVÉ                         │  ← Zdieľané v tíme
├────────────────────────────────────────┤
│  1. GLOBÁLNE (najnižšia priorita)      │  ← Platí všade
└────────────────────────────────────────┘
```

### Prečo existujú lokálne nastavenia?

Lokálne nastavenia typicky **nie sú** súčasťou Git repozitára.

Je to preto, lebo: _________________________________________________________________

> **Príklad:** V tíme 5 programátorov môže mať každý vlastné lokálne nastavenia s osobnými preferenciami, ale zdieľajú spoločné projektové nastavenia.

---

## 5. Permissions - bezpečnosť

AI asistent má prístup k tvojmu súborovému systému a môže spúšťať príkazy. To je **mocné, ale nebezpečné**.

### Typy akcií podľa rizika

| Riziko | Príklad akcie | Typicky vyžaduje povolenie? |
|--------|---------------|------------------------------|
| Nízke | Čítanie súborov | Nie |
| Stredné | Editovanie súborov v projekte | Záleží na nastavení |
| Vysoké | Spúšťanie shell príkazov | Áno |
| Vysoké | Mazanie súborov | Áno |
| Kritické | Git operácie (push, reset) | Áno |

### Auto-accept módy

Mnoho AI asistentov ponúka režim, kde automaticky schvaľujú niektoré akcie.

**Čo typicky môžu robiť bez pýtania:**
- ✅ Čítať súbory
- ✅ Editovať súbory v projekte

**Čo stále vyžaduje povolenie:**
- ❌ _________________________
- ❌ _________________________
- ❌ Operácie mimo projekt

### Sandbox - izolované prostredie

**Sandbox** = izolované prostredie, kde AI môže pracovať bez rizika poškodenia systému.

Predstav si to ako: _________________________________________________________________

> **Hint:** Pomysli na detské pieskovisko - dieťa sa môže hrať, ale piesok zostane v ohraničenom priestore.

### Prečo je Version Control (Git) dôležitý pri práci s AI?

Napíš 2 dôvody:

1. _________________________________________________________________

2. _________________________________________________________________

---

## 6. Projektové inštrukcie

Väčšina AI asistentov podporuje súbor s inštrukciami pre projekt (napr. `CLAUDE.md`, `AGENTS.md`, `.cursorrules`, atď.).

### Čo obsahuje?

```markdown
# Názov projektu
Stručný popis...

# Pravidlá
- Používaj TypeScript
- Nepoužívaj any typ
- Píš testy pre každú funkciu

# Architektúra
- /src - zdrojové súbory
- /tests - testy
- ...
```

### Kedy sa načíta?

Tento súbor sa **automaticky načíta** pri každej novej session a stáva sa súčasťou _________________________.

### Prečo má byť stručný?

_________________________________________________________________

> **Hint:** Spomeň si na context window a tokeny...

---

## 7. Context Engineering

**Context Engineering** = umenie poskytnúť AI správny kontext pre najlepší výsledok.

### Základné princípy

| Princíp | Vysvetlenie |
|---------|-------------|
| Relevantnosť | Pridávaj len _________________________ informácie |
| Stručnosť | Menej je viac - šetri _________________________ |
| Štruktúra | Používaj formátovanie pre _________________________ |

### Ako ukázať AI na konkrétny súbor?

Väčšina asistentov podporuje syntax ako `@súbor.js` alebo explicitné "pozri sa na súbor X".

### Štruktúrovaný vstup - XML tagy

Keď vkladáš dlhší kód alebo chybovú hlášku, je dobré ho ohraničiť:

```xml
<error>
TypeError: Cannot read property 'map' of undefined
    at UserList.js:15
</error>
```

**Prečo je to lepšie?** _________________________________________________________________

> **Hint:** LLM modely boli trénované na veľkom množstve XML/HTML...

---

## 8. Plan Mode - najprv premýšľaj, potom konaj

Mnoho AI asistentov ponúka **Plan Mode** (plánovací režim).

### Ako to funguje?

```
┌─────────────────────────────────────────────────────────┐
│                     PLAN MODE                           │
│                                                         │
│  1. AI analyzuje požiadavku                            │
│  2. Kladie upresňujúce otázky                          │
│  3. Navrhuje plán riešenia                             │
│  4. Čaká na tvoje schválenie                           │
│  5. AŽ POTOM začne implementovať                       │
│                                                         │
│  ⚠️  V Plan Mode AI NEMÔŽE robiť zmeny!                │
└─────────────────────────────────────────────────────────┘
```

### Kedy použiť Plan Mode?

Doplň situácie:
- Pri _________________________ úlohách
- Keď si _________________________ výsledkom
- Pri úlohách, ktoré ovplyvňujú _________________________

### Výhody

1. Predídeš zbytočným _________________________
2. Môžeš ovplyvniť riešenie _________________________ než je implementované
3. AI lepšie _________________________ tvoje požiadavky

---

## 9. Nástroje a rozšírenia

AI asistenti môžu mať prístup k rôznym **nástrojom (tools)**:

### Základné nástroje

| Nástroj | Čo robí |
|---------|---------|
| File Read | Číta obsah súborov |
| File Write | Zapisuje/upravuje súbory |
| Shell/Bash | Spúšťa terminálové príkazy |
| Web Search | Vyhľadáva na internete |
| Web Fetch | Načítava obsah webových stránok |

### MCP - Model Context Protocol

**MCP** je štandard pre pridávanie nových nástrojov a zdrojov pre AI asistentov.

Príklad: MCP server pre dokumentáciu umožňuje AI ľahšie _________________________.

### Prečo sú nástroje dôležité?

Bez nástrojov je LLM len "chatbot". S nástrojmi sa stáva _________________________.

---

## 10. Zhrnutie konceptov

Spoj pojem s definíciou:

| Pojem | | Definícia |
|-------|---|-----------|
| Context Window | | A. Automatická kompresia konverzácie |
| Token | | B. Izolované bezpečné prostredie |
| Compaction | | C. Maximálna kapacita "pamäte" LLM |
| Session | | D. Najmenšia jednotka textu pre LLM |
| Sandbox | | E. Jedna súvislá konverzácia |
| Plan Mode | | F. Režim plánovania pred implementáciou |

---

## Reflexia

**Čo ťa z workshopu najviac zaujalo alebo prekvapilo?**

_________________________________________________________________

_________________________________________________________________

**Ako by si mohol využiť AI asistenta vo svojich projektoch?**

_________________________________________________________________

_________________________________________________________________

---

*AI Workshop | SPSIT*
