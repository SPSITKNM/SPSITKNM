# Komisionálna skúška – PRO / SXG
**Škola:** Stredná priemyselná škola informačných technológií, Kysucké Nové Mesto  
**Ročník:** 4.  
**Meno a priezvisko:** _______________  
**Trieda:** _______________  
**Dátum:** _______________

---

## Pokyny

Vypracovanie skúšky nemá stanovené časové ani nástrojové obmedzenia. Študent je oprávnený zvoliť si programovací jazyk, prostredie a formu záznamu riešenia podľa vlastného uváženia, pokiaľ nie je v zadaní určené inak. Hodnotí sa správnosť riešenia, hĺbka pochopenia prezentovaných princípov a schopnosť komplexne obhájiť každé rozhodnutie obsiahnuté v odovzdanom vypracovaní. Komisia je oprávnená požiadať o ústne vysvetlenie ľubovoľnej časti riešenia.

---

## OKRUH 1 – Objektovo-orientované programovanie
*(Repozitáre: `SPSITKNM`, `oop_opakovanie`)*

---

### 1.1 – Implementácia hierarchie tried

Navrhni a implementuj sústavu tried pre **bankový systém** podľa nasledujúcej špecifikácie:

**Trieda `Klient`**
- Atribúty: `kod` (int), `meno` (string)
- Konštruktor inicializujúci oba atribúty
- Metóda `zobraz()` vypíše informácie o klientovi

**Trieda `Ucet`**
- Atribúty: `cislo` (string), `zostatok` (double), `majitel` (Klient)
- Konštruktor, metóda `zobraz()`
- Virtuálna metóda `moznoVybrat(double suma)` → vráti `true` ak `zostatok >= suma`
- Metóda `vyber(double suma)` — ak je výber povolený, odčíta ho; inak vypíše chybové hlásenie

**Trieda `UverUcet`** *(dedí od `Ucet`)*
- Pridáva atribút `uverLimit` (double)
- Prepíše `moznoVybrat()` tak, aby povolila výber aj do mínusu — maximálne do výšky `uverLimit`
- Konštruktor volajúci konštruktor rodiča

**Trieda `Banka`**
- Obsahuje zoznam (pole alebo vektor) ukazateľov na `Ucet`
- Metóda `pridajUcet(Ucet* u)`
- Metóda `spracujVybery(double suma)` — zavolá `vyber(suma)` na každom účte v zozname *(demonštruje polymorfizmus)*

**Požiadavky:**
1. V C++ implementuj destruktory tam, kde je to potrebné; zdôvodni, kde nie.
2. Demonštruj polymorfizmus: vytvor zoznam ukazateľov `Ucet*`, naplň ho objektmi rôznych typov a zavolaj na nich `vyber()`.
3. Nakresli UML diagram tried s vyznačením vzťahov IS-A a HAS-A.

---

### 1.2 – Statický čítač objektov

Implementuj triedu `PocitadloObjektov` (môže reprezentovať napr. počet aktívnych sessions, pripojení alebo objednávok), ktorá:
- Pomocou **statického atribútu** sleduje celkový počet doposiaľ vytvorených inštancií
- V konštruktore inkrementuje počítadlo, v destruktore ho dekrementuje
- Poskytuje statickú metódu `getPocet()` vracajúcu aktuálny stav

Napíš krátky `main()`, ktorý demonštruje správnosť správania pri vytváraní a rušení objektov.

---

### 1.3 – Analytické otázky (písomné zdôvodnenie)

**a)** Kedy je vhodné zvoliť **kompozíciu** namiesto **dedičnosti**? Uveď konkrétny príklad z praxe, kde by použitie dedičnosti viedlo k nesprávnemu návrhu, a vysvetli prečo.

**b)** Akú hrozbu predstavuje **hlboká dedičnostná hierarchia** (napr. 5 úrovní)? Aké problémy môže spôsobiť pri údržbe a rozširovaní kódu?

**c)** Prečo je **zapuzdrenie** základom udržiavateľného softvéru? Navrhni scenár, kde jeho absencia (napr. verejné atribúty namiesto getterov/setterov) spôsobí skrytú chybu pri rozširovaní systému.

---

> **Mohlo by sa hodiť**
>
> *UML notácia tried:*
> ```
> ┌─────────────────┐
> │     Ucet        │
> ├─────────────────┤
> │ - cislo: string │   ◄── private
> │ # zostatok: dbl │   ◄── protected (prístupné potomkom)
> ├─────────────────┤
> │ + moznoVybrat() │   ◄── public/virtual
> │ + vyber()       │
> └────────┬────────┘
>          △  IS-A (dedičnosť)
> ┌────────┴────────┐
> │   UverUcet      │
> ├─────────────────┤
> │ - uverLimit:dbl │
> ├─────────────────┤
> │ + moznoVybrat() │   ◄── override
> └─────────────────┘
>
> Banka ──◆── Ucet*   (HAS-A, kompozícia/agregácia)
> Ucet  ──◆── Klient  (HAS-A)
> ```
>
> *Liskovej substitučný princíp:* Kdekoľvek v kóde použiješ `Ucet*`, musí korektne fungovať aj `UverUcet*` — inak je návrh hierarchie nesprávny.

---

## OKRUH 2 – Algoritmizácia a dátové štruktúry
*(Repozitár: `SPSITKNM` – `algoritmizacia.md`)*

---

### 2.1 – Implementácia spájaného zoznamu (Linked List)

Implementuj v C++ triedu `LinkedList` s nasledujúcimi metódami. Všetky uzly alokuj dynamicky (`new`), v destruktore pamäť uvoľni (`delete`).

| Metóda | Popis |
|---|---|
| `append(int val)` | Pridá uzol na koniec — O(1) |
| `prepend(int val)` | Pridá uzol na začiatok — O(1) |
| `deleteFirst()` | Odstráni prvý uzol |
| `deleteLast()` | Odstráni posledný uzol |
| `get(int index)` | Vráti ukazateľ na uzol na danom indexe |
| `insert(int index, int val)` | Vloží uzol na zadanú pozíciu |
| `reverse()` | Obráti zoznam in-place (bez pomocného poľa) |
| `print()` | Vypíše celý zoznam |

Po implementácii odpovedz:
- Aká je časová zložitosť `deleteLast()` a prečo nemôže byť O(1) pri jednoduchom LL?
- Ako by zmena na **dvojito spájaný zoznam (DLL)** zlepšila zložitosť `deleteLast()`?

---

### 2.2 – Stack: overenie zátvorkového výrazu

Implementuj funkciu `bool jeVyvazeny(string vyraz)`, ktorá pomocou **Stack** overí, či je zátvorkový výraz správne uzavretý. Funkcia musí správne spracovať kombináciu `()`, `[]`, `{}`.

Príklady:
- `{[()]}` → `true`
- `{[(])}` → `false`
- `(((`   → `false`

**Podmienky:** Implementuj vlastnú triedu `Stack` (nie `std::stack`), pričom Stack vnútorne využíva spájaný zoznam alebo pole.

---

### 2.3 – Queue: simulácia tlačového frontu

Implementuj program simulujúci **front tlačových úloh**:
- Trieda `TlacovaUloha` má atribúty: `id`, `nazov`, `pocetStran`
- Trieda `TlacovaFronta` implementuje Queue operácie: `enqueue(TlacovaUloha)`, `dequeue()`, `peek()`, `isEmpty()`
- `main()` pridá 5 úloh, následne ich postupne spracuje (vypíše, ktorá sa práve tlačí) — demonštruje FIFO správanie

---

### 2.4 – Analýza časovej zložitosti

Urči Big O zložitosť každého úseku a **písomne zdôvodni**:

```cpp
// (a)
for (int i = 0; i < n; i++)
    for (int j = i; j < n; j++)   // pozor: j začína od i, nie od 0
        cout << i + j;

// (b)
int x = n;
while (x > 1)
    x = x / 2;

// (c)
void funkcia(int a, int b) {
    for (int i = 0; i < a; i++) cout << i;
    for (int j = 0; j < b; j++) cout << j;
}

// (d) — čo sa deje s výrazom O(n³ + n² + n) ?
```

Analytická otázka: Pole umožňuje prístup k prvku v O(1), spájaný zoznam len v O(n). Napriek tomu existujú scenáre, kde je spájaný zoznam výhodnejší. Uveď **dva konkrétne scenáre** a vysvetli prečo.

---

> **Mohlo by sa hodiť**
>
> *Štruktúra uzla a vizualizácia:*
> ```
> Jednoduchý LL:   head → [10|•] → [20|•] → [30|/]  ← tail
>
> Dvojito spájaný: head → [/|10|•] ⇄ [•|20|•] ⇄ [•|30|/] ← tail
>                          (prev/next)
> ```
>
> *Algoritmus `reverse()` — three-pointer technika (smer myslenia):*
> ```
> prev = nullptr, curr = head, next = nullptr
> Iteruj: next = curr→next; curr→next = prev; prev = curr; curr = next
> Na konci: head = prev
> ```
>
> *Rastová tabuľka zložitostí:*
> ```
> O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ)
> ```
>
> *Princíp zjednodušenia:*
> — Drop constants: `O(3n)` → `O(n)`
> — Drop non-dominants: `O(n² + n)` → `O(n²)`
> — Rôzne vstupy: `O(a + b)` sa **nezjednodušuje** na `O(n)`

---

## OKRUH 3 – Git, GitHub a GitLab
*(Repozitáre: `SPSITKNM` – `GitHub_vs_GitLab.md`, `SXG` – `git_github_gitlab.md`)*

---

### 3.1 – Feature branch workflow: presné príkazy

Nasleduje scenár vývojového procesu. Pre každý krok napíš **presný git príkaz** (alebo sériu príkazov):

1. Inicializuj nový lokálny repozitár a pripoj ho k vzdialenému originu `https://gitlab.com/skola/projekt.git`
2. Vytvor vetvu `feature/user-auth` a prepni sa na ňu
3. Pridaj všetky zmenené súbory do staging area a vytvor commit so správou `"feat: add JWT authentication"`
4. Odošli vetvu na vzdialený server (prvý push novej vetvy)
5. Na vetve `main` nastala zmena; integruj ju do svojej feature vetvy bez vytvorenia merge commitu
6. Pri zlúčení nastane konflikt v súbore `auth.cpp` — popiš **postup riešenia** krok po kroku
7. Po schválení merge requestu zmaž lokálnu aj vzdialenú vetvu `feature/user-auth`

---

### 3.2 – Návrh CI/CD pipeline

Napíš funkčný súbor `.gitlab-ci.yml` pre Python aplikáciu s nasledujúcimi požiadavkami:
- **Fáza `build`:** nainštaluje závislosti (`pip install -r requirements.txt`)
- **Fáza `test`:** spustí unit testy (`pytest`)
- **Fáza `deploy`:** spustí sa **iba na vetve `main`** a vykoná nasadenie (môže byť symbolické `echo "Deploying..."`)
- Nastav, aby pipeline používala image `python:3.11-slim`

---

### 3.3 – Identifikácia anti-patterns

V nasledujúcom git workflow sú **3 závažné chyby**. Identifikuj ich a vysvetli, prečo sú problematické a ako ich napraviť:

```bash
# Vývojár pracuje priamo na main:
git checkout main
# ... edituje súbory ...
git add .
git commit -m "fix"
git push origin main

# Kolega sa pokúša synchronizovať:
git pull origin main
# Vznikne konflikt — vývojár ho "vyrieši" takto:
git reset --hard origin/main   # zahodí vlastné zmeny
git push --force origin main   # prepíše vzdialenú históriu
```

---

### 3.4 – Analytické otázky

**a)** `git merge` zachováva históriu, `git rebase` ju prepisuje. Uveď **konkrétnu situáciu** pre každý príkaz, kde je jeho použitie optimálne, a vysvetli prečo by v tej situácii druhý príkaz bol nevhodný.

**b)** CI/CD nie je len technická záležitosť — má priamy dopad na obchodné procesy. Vysvetli, aký **business benefit** prináša zavedenie CI/CD pipeline v porovnaní s manuálnym nasadzovaním.

**c)** Čo je **Personal Access Token** a prečo ho GitLab vyžaduje namiesto hesla pri HTTPS operáciách?

---

> **Mohlo by sa hodiť**
>
> *Git flow schéma:*
> ```
> main    ──●──────────────────────●── (merge)
>            \                    /
> feature     ●──●──●──●──●──●──●
> ```
>
> *Štruktúra `.gitlab-ci.yml`:*
> ```yaml
> stages:
>   - build
>   - test
>   - deploy
>
> nazov-jobu:
>   stage: build
>   image: python:3.11-slim
>   script:
>     - echo "prikaz"
>   rules:
>     - if: '$CI_COMMIT_BRANCH == "main"'
> ```
>
> *`git rebase` vs `git merge` — kľúčový rozdiel:*
> Rebase premiestni tvoje commity na vrchol cieľovej vetvy → lineárna história.
> Merge vytvorí nový "merge commit" spájajúci dve vetvy → zachovaná história vetvenia.

---

## OKRUH 4 – Operačné systémy a Linux
*(Repozitár: `SXG` – `Uvod_do_operacnych_sistemov.md`, `Linux Commands Cheat Sheet.md`, `fedora_commands.md`)*

---

### 4.1 – Implementácia: fork() a pipe()

Napíš kompletný **program v jazyku C**, ktorý:
1. Vytvorí komunikačný kanál pomocou `pipe()`
2. Zavolá `fork()` na vytvorenie potomka
3. **Rodič** zapíše do pipe správu: `"Správa od rodiča: [PID rodiča]"` a uzavrie write-end
4. **Potomok** prečíta správu z pipe, vypíše ju na stdout a uzavrie read-end
5. Rodič počká na ukončenie potomka pomocou `wait()` a vypíše návratový kód

Program musí korektne zatvárať neupotrené file descriptory a ošetriť prípad, kedy `fork()` zlyhá.

Po implementácii odpovedz: čo je **zombie proces**, ako vzniká a akú rolu hrá `wait()` pri jeho prevencii?

---

### 4.2 – Stavový diagram procesu

Nakresli **stavový diagram** procesu so stavmi:
`NEW → READY → RUNNING → WAITING → TERMINATED`

Pre každý prechod (šípku) uveď **konkrétnu udalosť**, ktorá ho spôsobuje (napr. „plánovač vyberie proces", „I/O operácia", „process exit").

Doplň: Čo obsahuje **PCB (Process Control Block)** a prečo ho OS potrebuje pri **prepínaní kontextu (context switch)**? Vymenuj minimálne 5 položiek PCB.

---

### 4.3 – Linux príkazy: scenáre

Pre každý scenár napíš **presný príkaz** (prípadne reťazec príkazov pomocou `|`):

| Scenár | Príkaz |
|---|---|
| Zobraz všetky bežiace procesy so stĺpcami PID, USER, CPU%, MEM%, CMD | |
| Nájdi všetky riadky obsahujúce slovo `ERROR` v súbore `system.log` a ulož ich do `chyby.txt` | |
| Zobraz posledných 50 riadkov `system.log` a sleduj nové záznamy v reálnom čase | |
| Rekurzívne nájdi všetky súbory `.conf` v `/etc` | |
| Nastav práva súboru `deploy.sh` na `rwxr-xr--` pomocou octal notácie | |
| Zobraz aktívne sieťové rozhrania a ich IP adresy | |
| Ukončí proces s názvom `nginx` bez znalosti jeho PID | |
| Zobraz zaťaženie CPU a pamäte v reálnom čase (interaktívny nástroj) | |
| Skopíruj adresár `projekt/` na vzdialený server `192.168.1.10` do `/home/admin/` | |
| Zoraď riadky súboru `data.csv` podľa druhého stĺpca (oddelovač `,`) | |

---

### 4.4 – Analytické otázky

**a)** Pipe (rúra) ako IPC mechanizmus je jednosmerná a pracuje s FIFO princípom. Porovnaj pipe so **zdieľanou pamäťou (shared memory)** ako alternatívnym IPC mechanizmom — uveď výhody a nevýhody každého prístupu.

**b)** Prečo file descriptory 0, 1 a 2 majú špeciálny status? Ako súvisia so `stdin`, `stdout` a `stderr` a čo sa stane, keď ich vývojár v programe uzavrie?

---

> **Mohlo by sa hodiť**
>
> *Kostra programu s `fork()` a `pipe()`:*
> ```c
> #include <unistd.h>
> #include <sys/wait.h>
> #include <stdio.h>
>
> int main() {
>     int pipefd[2];   // pipefd[0] = read end, pipefd[1] = write end
>     pipe(pipefd);
>     pid_t pid = fork();
>     if (pid == 0) {
>         // potomok — čítanie
>     } else {
>         // rodič — zápis + wait()
>     }
> }
> ```
>
> *File descriptory:*
> ```
> 0 = stdin  (klávesnica)
> 1 = stdout (terminál)
> 2 = stderr (terminál – chybový výstup)
> ```
>
> *Reťazenie príkazov:*
> ```bash
> cat log.txt | grep "ERROR" | sort | uniq -c
> # pipe (|) presmeruje stdout jedného príkazu na stdin ďalšieho
> ```

---

## OKRUH 5 – Virtualizácia
*(Repozitár: `SXG` – `VirtualBox Guide.md`, `kvm.md`, `docker.md`)*

---

### 5.1 – Dockerfile pre produkčnú aplikáciu

Napíš `Dockerfile` pre **Python Flask API** aplikáciu s nasledujúcimi požiadavkami:
- Základný image: `python:3.11-slim`
- Pracovný adresár: `/app`
- Skopíruje `requirements.txt` a nainštaluje závislosti pred kopírovaním zvyšného kódu *(zdôvodni toto poradie — súvisí s layerovaním)*
- Skopíruje celý zdrojový kód
- Exponuje port `5000`
- Spustí aplikáciu príkazom `flask run --host=0.0.0.0`
- Nastav premennú prostredia `FLASK_ENV=production`

Po implementácii vysvetli: prečo je výhodné kopírovať `requirements.txt` **pred** zvyšným kódom z pohľadu Docker cache?

---

### 5.2 – Docker Compose: viacservisná aplikácia

Napíš `docker-compose.yml` pre systém skladajúci sa z:
- Služby `web` (tvoj Flask image z 5.1, port 5000 mapovaný na host port 8080)
- Služby `db` (image `postgres:15`, s nastavenými premennými `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_DB`)
- Obidve služby sú v spoločnej sieti `backend-net`
- Dáta databázy sú perzistentné pomocou named volume `pgdata`
- Služba `web` čaká na `db` (`depends_on`)

---

### 5.3 – VBoxManage automatizácia

Napíš sekvenciu príkazov `VBoxManage`, ktorá automatizovane:
1. Vytvorí VM s názvom `TestVM`, typom `Linux`, variantom `Ubuntu_64`
2. Nastaví 2048 MB RAM a 2 CPU
3. Pridá virtuálny disk (VDI, dynamicky alokovaný, 20 GB)
4. Nastaví sieťový adaptér na `bridged` mod
5. Spustí VM v headless režime

---

### 5.4 – KVM konfigurácia

Napíš príkazy, ktoré:
1. Overia, či CPU podporuje hardvérovú virtualizáciu (VT-x / AMD-V)
2. Skontrolujú, či sú načítané príslušné kernel moduly
3. Overia celkovú vhodnosť systému pre QEMU/KVM hosting
4. Nastavia optimalizačný profil `virtual-host` pomocou nástroja `tuned`

---

### 5.5 – Analytické otázky

**a)** Kontajner (Docker) a virtuálny stroj (VM) poskytujú rôznu úroveň izolácie. Porovnaj ich z hľadiska:
- Izolácie (čo zdieľajú s hostiteľom)
- Výkonnostného overheadu
- Vhodného use-case scenára

**b)** Uveď **tri výhody** Docker Compose oproti manuálnemu spúšťaniu kontajnerov príkazmi `docker run`.

**c)** Vysvetli, prečo sa na produkčných serveroch preferuje KVM pred VirtualBoxom. Uveď aspoň 2 technické dôvody.

---

> **Mohlo by sa hodiť**
>
> *Docker architektúra:*
> ```
> Docker CLI (klient)
>       │  REST API
>       ▼
> Docker Daemon (dockerd)
>   ├── Images   (šablóny – read-only vrstvy)
>   ├── Containers (bežiace inštancie)
>   └── Volumes  (perzistentné úložisko)
> ```
>
> *Docker Compose sieťovanie:*
> ```
> Host
> └── bridge network: backend-net
>     ├── web  (dostupný ako "web" v rámci siete)
>     └── db   (dostupný ako "db" v rámci siete)
> ```
>
> *KVM overenie CPU a modulov:*
> ```bash
> lscpu | grep -i virtualization
> lsmod | grep kvm
> virt-host-validate qemu
> tuned-adm list
> tuned-adm profile virtual-host
> ```
>
> *Dockerfile layer cache:* Každá inštrukcia je vrstva. Ak sa zmení vrstva, všetky nasledujúce sa invalidujú. Preto `COPY requirements.txt` + `RUN pip install` pred `COPY . .` — závislosti sa rebuildujú len ak sa zmení `requirements.txt`.

---

## OKRUH 6 – Monitoring a OpenTelemetry
*(Repozitár: `SXG` – `otel.md`)*

---

### 6.1 – Návrh observability stratégie

Máš trojvrstvovú webovú aplikáciu:
- `frontend` (React SPA)
- `api` (REST API v Pythone)
- `databaza` (PostgreSQL)

Navrhni **komplexnú observability stratégiu** s využitím OpenTelemetry. Pre každú vrstvu uveď:
- Čo budeš sledovať pomocou **Traces** (a prečo práve traces, nie metriky?)
- Aké **Metrics** nastavíš (vymenuj minimálne 3 konkrétne metriky pre `api` vrstvu s popisom, čo merajú)
- Aké udalosti budú zaznamenávané ako **Logs** a na akej severity úrovni

Zdôvodni každé rozhodnutie — prečo si zvolil daný pilier pre daný typ pozorovania.

---

### 6.2 – Analýza bottlenecku z trace diagramu

Nasleduje zjednodušený distribuovaný trace pre jednu HTTP požiadavku:

```
[HTTP Request] ────────────────────────────── 850ms ──┐
  │                                                    │
  ├─[span: api.auth]              12ms                 │
  │                                                    │
  ├─[span: api.getUserData]       780ms  ◄── !!!       │
  │   └─[span: db.query]          775ms  ◄── !!!       │
  │                                                    │
  └─[span: api.renderResponse]    55ms                 │
                                                       ┘
```

**a)** Kde nastáva bottleneck? Zdôvodni na základe údajov v trace.

**b)** Aké sú možné príčiny toho, že `db.query` trvá 775ms? Vymenuj aspoň 3 hypotézy.

**c)** Aké **metriky** by si monitoroval na databázovej vrstve, aby si tieto hypotézy potvrdil alebo vyvrátil?

---

### 6.3 – Analytické otázky

**a)** Kedy je vhodné použiť **auto-instrumentáciu** a kedy **manuálnu instrumentáciu**? Uveď scenár pre každý prístup a vysvetli kompromisy (development effort vs. granularita dát).

**b)** Span reprezentuje jednu operáciu v rámci trace. Vysvetli, ako distribuovaný trace **prepája spany naprieč viacerými službami** — aký mechanizmus sa na to používa (context propagation)?

**c)** Prečo nestačí logovanie (Logs) na diagnostiku výkonnostných problémov v distribuovanom systéme? Čo pridávajú Traces, čo logy nedokážu poskytnúť?

---

> **Mohlo by sa hodiť**
>
> *Schéma distribuovaného trace:*
> ```
> User request
>    │
>    ▼
> [frontend span]
>    │ HTTP call
>    ▼
> [api span]─────────────────────────────── trace ID propagovaný cez HTTP header
>    │ SQL query
>    ▼
> [db span]
> ```
>
> *Tri piliere observability — kedy ktorý:*
> ```
> Traces  → Prečo je požiadavka pomalá? Kde je bottleneck?
> Metrics → Aký je trend? Rastie počet chýb? Klesá throughput?
> Logs    → Čo presne sa stalo v danom momente? Aká bola chybová správa?
> ```
>
> *Príklady metric exporterov a nástrojov:*
> Prometheus (scraping metrík), Grafana (vizualizácia), Datadog (komerčné all-in-one),
> Jaeger / Zipkin (trace vizualizácia), OpenTelemetry Collector (agregácia a routing)

---

## Hodnotiace kritériá

| Okruh | Praktické úlohy | Analytické otázky | Max. bodov |
|---|---|---|---|
| 1 – OOP | 15 | 5 | 20 |
| 2 – Algoritmizácia | 20 | 5 | 25 |
| 3 – Git / GitLab | 10 | 5 | 15 |
| 4 – OS a Linux | 15 | 5 | 20 |
| 5 – Virtualizácia | 10 | 5 | 15 |
| 6 – OpenTelemetry | 5 | 5 | 10 |
| **Celkom** | **75** | **30** | **105** |

*(5 bodov tvorí bonus za výnimočnú argumentačnú kvalitu v analytických otázkach)*

**Klasifikačná stupnica:**
| Percentá | Klasifikácia |
|---|---|
| 95 – 100 % | 1 – výborný |
| 80 – 94 % | 2 – chválitebný |
| 60 – 79 % | 3 – dobrý |
| 40 – 59 % | 4 – dostatočný |
| 0 – 39 % | 5 – nedostatočný |

---

*Autor: Tomáš Mucha*
