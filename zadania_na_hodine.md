# Operačné Systémy - Domáca Úloha: Procesy a správa úloh

**Deadline:** 24.10.2025  
**Prostredie:** Linux/Unix (VirtualBox s Fedorou)  
**Jazyk:** C++ (g++ kompilátor)  
**Materály:** Prezentácia "Operačné systémy - Procesy a správa úloh", skriptá, videá vytvorené pre účely predmetu

---

## Príprava prostredia

### Krok 1: Inštalácia Fedory vo VirtualBox

Postupujte presne podľa tutoriálu:
- **Video:** [VirtualBox Setup](https://www.youtube.com/watch?v=8RdA9mQFr10&list=PLJW-oHbyRDeJt24tw-RaHJwxbXUCh3GrQ&index=5)
- **Skriptá:** [VirtualBox Guide](https://github.com/SPSITKNM/SXG/blob/main/VirtualBox%20Guide.md)

**Čo budete potrebovať:**
- VirtualBox nainštalovaný na vašom počítači
- ISO súbor Fedory

### Krok 2: Základná orientácia v Linuxovom termináli

Naučte sa základné príkazy:
- **Video:** [Linux Commands](https://www.youtube.com/watch?v=NE3r0i5cENI&list=PLJW-oHbyRDeJt24tw-RaHJwxbXUCh3GrQ&index=6)
- **Cheat Sheet:** [Linux Commands Guide](https://github.com/SPSITKNM/SXG/blob/main/Linux%20Commands%20Cheat%20Sheet.md)

### Krok 3: Inštalácia vývojových nástrojov

V termináli spustite:

```bash
sudo dnf update
sudo dnf install gcc g++ make gdb valgrind
```

**Overenie inštalácie:**
```bash
g++ --version
gcc --version
gdb --version
valgrind --version
```

### Krok 4: Výber editora

Môžete používať **ľubovoľný editor**, ktorý preferujete:

**Možnosti:**
- **VS Code** - Odporúčaný (inštalácia: https://code.visualstudio.com/)
  - Extension: C/C++ (Microsoft)
  - Remote - SSH (na prácu s VirtualBox)
- **CLion** - Profesionálny IDE (platený, ale študenti majú prístup zadarmo ak máte ISIC)
- **Nano** - Jednoduchý, vstavený v termináli: `nano file.cpp`
- **Vim** - Pokročilý editor v termináli: `vim file.cpp`
- **Gedit/Kate** - Grafické editory: `gedit file.cpp` alebo `kate file.cpp`

**Ak používate VS Code s VirtualBox:**

Inštalujte VS Code extension "Remote - SSH" a pripojte sa priamo do VM.

---

## Pripomenutie: Kľúčové koncepty z hodiny PRO v piatok 17.10.2025 

Skôr, ako začnete s úlohami, zopakujte si tieto koncepty z prezentácie:

### Program vs Proces
- **Program:** Pasívna entita - statický súbor na disku (chrome.exe, python3)
- **Proces:** Aktívna entita - program, ktorý sa VYKONÁVA s pridelenými zdrojmi (CPU čas, pamäť, súbory)
- Jeden program → viacero procesov (napr. 3 okná Chromu = 3 procesy)

### Štruktúra procesu
Každý proces má:
1. **Kód programu** - z binárneho súboru
2. **Pamäť (RAM)** - premenné, stack (funkcie), heap (malloc/new)
3. **Otvorené súbory** - stdin, stdout, stderr, dáta
4. **Registre CPU** - Program Counter (PC), aktuálny stav

### Stavy procesu (Process Lifecycle)
```
NEW → READY → RUNNING → WAITING → TERMINATED
```

- **NEW:** Proces sa vytvára
- **READY:** Čaká na CPU (v rade u schedulera)
- **RUNNING:** Beží na CPU
- **WAITING:** Čaká na I/O operáciu (disk, sieť, klávesnica)
- **TERMINATED:** Proces skončil

### Scheduler a Preemption
- **Scheduler:** Časť OS, ktorá rozhoduje, ktorý proces dostane CPU a na ako dlho
- **Preemption:** Schopnosť OS prerušiť bežiaci proces a odobrať mu CPU (moderné OS)

### Parent a Child procesy
- **PID 1 (init/systemd):** Koreň všetkých procesov
- **Parent:** Proces, ktorý vytvoril child pomocou `fork()`
- **Child dedí:** Otvorené súbory, environment variables, aktuálny adresár, práva

### Fork + Exec vzor
```
fork() → vytvorí kópiu procesu
exec() → nahradí proces iným programom
wait() → rodič čaká na ukončenie potomka
```

### Špeciálne stavy procesov

**Zombie proces (Z):**
- Proces, ktorý už skončil, ale záznam zostáva v tabuľke procesov
- Vzniká, keď parent NEZAVOLÁ `wait()`
- Zaberá len PID, nie RAM/CPU
- V `ps aux` vyzerá ako: `<defunct>`

**Orphan proces:**
- Parent zomrie skôr ako child
- Child zostane bez rodiča
- PID 1 (init/systemd) ho automaticky adoptuje
- Child pokračuje normálne

**Sleeping proces (S):**
- Proces v stave WAITING - čaká na udalosť (I/O, sieť, klávesnica)
- Interruptible sleep - dá sa prebudiť signálom (Ctrl+C)
- Automaticky sa prebudí, keď udalosť príde

---

## Praktické príkazy pre debugging

Používajte tieto príkazy pri práci:

```bash
# Zobrazenie všetkých procesov
ps aux

# Vyhľadávanie konkrétneho procesu
ps aux | grep <nazov_programu>

# Zobrazenie PID aktuálneho procesu/shellu
echo $$
ps

# Monitorovanie procesov v reálnom čase
top
htop  # (vyžaduje inštaláciu: sudo dnf install htop)

# Strom procesov (hierarchia parent-child)
pstree
pstree -p  # s PIDmi

# Posielanie signálov
kill -9 <PID>           # Násilne ukončenie
kill -STOP <PID>        # Zastaví proces (STOPPED - T)
kill -CONT <PID>        # Pokračuje proces

# Prevádzanie procesu do pozadia
./program &
jobs
fg %1
bg %1

# Hľadanie zombie procesov
ps aux | grep defunct
ps aux | grep Z

# Sledovanie procesov v reálnom čase
watch -n 1 'ps aux | grep <program>'
```

---

## Úloha 1 – Jednoduchý potomek

### Cieľ
Pochopenie základného fungovania `fork()` a rozdiel medzi parent a child procesom. Praktické overenie konceptov "Program vs Proces" a "Parent a Child procesy" z prednášky.

### Zadanie

Napíšte program `task1.cpp`, ktorý:

1. Vytvorí jedného potomka pomocou `fork()`
2. **Child proces** vypíše na výstup text:
   ```
   Já jsem potomek, PID: <pid>
   ```
3. **Parent proces** vypíše na výstup text:
   ```
   Já jsem rodič, PID: <pid>, dítě: <pid_child>
   ```
4. Rodič počka na ukončenie potomka pomocou `wait()`

### Očakávaný výstup

```
Já jsem potomek, PID: 1234
Já jsem rodič, PID: 1233, dítě: 1234
```

### Pokyny

- Používajte `getpid()` pre získanie aktuálneho PID
- Používajte `getppid()` pre získanie PID rodiča
- Overovanie s príkazom: `ps aux | grep task1`
- **Koncept z hodín :** Ukazuje, že jeden program (task1) vytvára dva procesy (parent + child)

### Kompilace a spustenie

```bash
g++ -o task1 task1.cpp
./task1
```

### Bonus: Experimentujte

Čo sa stane, ak odstránite `wait()`? Pozrite si proces s `ps aux` - bude zombie?

---

## Úkol 2 – Lifecycle a stavy procesov

### Cieľ
Praktické overenie **stavov procesu** (NEW → READY → RUNNING → WAITING → TERMINATED) z prednášky.

### Zadanie

Napíšte program `task2.cpp`, ktorý:

1. Vytvorí potomka pomocou `fork()`
2. **Child proces:**
   - Vypíše: `"[CHILD] START: pid=<pid>, parent_pid=<ppid>"`
   - Uspí sa na 2 sekundy (`sleep(2)`)
   - Vypíše: `"[CHILD] END: pid=<pid>"`
3. **Parent proces:**
   - Vypíše: `"[PARENT] Child started: pid=<child_pid>"`
   - Počka na child (`wait()`)
   - Vypíše: `"[PARENT] Child finished"`

### Očakávaný výstup

```
[CHILD] START: pid=1234, parent_pid=1233
[PARENT] Child started: pid=1234
[PARENT] Čaká...
[CHILD] END: pid=1234
[PARENT] Child finished
```

### Pokyny

- Použite `sleep(2)` - umiestní proces do stavu **WAITING**
- Počas `sleep(2)` spustite v inom termináli: `ps aux | grep task2`
- Vidíte child proces v stave **S** (INTERRUPTIBLE_SLEEP)?
- **Koncept z hodín :** Vidíte zmeny stavov: READY → RUNNING → WAITING → TERMINATED

### Kompilace a spustenie

```bash
g++ -o task2 task2.cpp
./task2

# V inom termináli počas behu:
ps aux | grep task2
```

---

## Úkol 3 – Zombie proces

### Cieľ
Praktické pochopenie **zombie procesov** a problému, keď parent NEZAVOLÁ `wait()`.

### Zadanie

Napíšte program `task3.cpp`, ktorý:

1. Vytvorí potomka pomocou `fork()`
2. **Child proces:**
   - Vypíše: `"[CHILD] Doing work..."`
   - Pracuje 1 sekundu (`sleep(1)`)
   - Vypíše: `"[CHILD] Done. Exiting."`
   - Skončí (`exit(0)`)
3. **Parent proces:**
   - Vypíše: `"[PARENT] Child created: pid=<child_pid>"`
   - **NEZAVOLÁ `wait()`!** (to je chyba!)
   - Spí 5 sekúnd (`sleep(5)`)
   - Vypíše: `"[PARENT] Exiting."`

### Očakávaný výstup

```
[PARENT] Child created: pid=1234
[CHILD] Doing work...
[CHILD] Done. Exiting.
[PARENT] Exiting.
```

### Pokyny

- Spustite program: `./task3`
- Počas behu (v inom termináli) spustite: `ps aux | grep task3`
- **Vidíte zombie proces?** Hľadajte riadok s **Z** alebo `<defunct>`
- Príkaz: `ps aux | grep defunct`
- **Koncept z hodín :** Zombie proces - child skončil, ale záznam zostáva v tabuľke

### Kompilace a spustenie

```bash
g++ -o task3 task3.cpp
./task3 &

# Počas behu v inom termináli:
ps aux | grep task3
ps aux | grep defunct
```

### Otázka k premýšľaniu

Ako by ste problém vyriešili? (Odpoveď: pridaním `wait()` v parent procese)

---

## Úkol 4 – Orphan proces

### Cieľ
Praktické pochopenie **orphan procesov** - čo sa stane, keď parent zomrie skôr ako child.

### Zadanie

Napíšte program `task4.cpp`, ktorý:

1. Vytvorí potomka pomocou `fork()`
2. **Child proces:**
   - Vypíše: `"[CHILD] START - parent_pid=<ppid>"`
   - Spí 3 sekundy (`sleep(3)`)
   - Vypíše: `"[CHILD] MIDDLE - parent_pid=<ppid>"` (všimnite si zmenu!)
   - Spí ďalších 2 sekúnd
   - Vypíše: `"[CHILD] END - parent_pid=<ppid>"`
3. **Parent proces:**
   - Vypíše: `"[PARENT] Child created: pid=<child_pid>"`
   - Spí len 1 sekundu (`sleep(1)`)
   - Vypíše: `"[PARENT] Parent exiting!"`
   - Skončí (bez `wait()`)

### Očakávaný výstup

```
[PARENT] Child created: pid=1234
[PARENT] Parent exiting!
[CHILD] START - parent_pid=1233
[CHILD] MIDDLE - parent_pid=1      <--- PPID sa zmenilo!
[CHILD] END - parent_pid=1
```

### Pokyny

- **Kľúčové pozorovanie:** PPID sa zmení z `1233` (original parent) na `1` (PID 1 = init/systemd)
- PID 1 adoptuje osirelého potomka
- **Koncept z hodín :** "Child zostane bez parenta. PID 1 ho adoptuje."

### Kompilace a spustenie

```bash
g++ -o task4 task4.cpp
./task4

# Pozorujte zmenu PPID!
```

---

## Úkol 5 – Preemption a Scheduler

### Cieľ
Praktické pochopenie **Preemption** - OS vám odoberie CPU, aj keď ešte neskončil.

### Zadanie

Napíšte program `task5.cpp`, ktorý:

1. Vytvorí 3 potomkov pomocou `fork()` v cykle
2. **Všetci potomkovia:**
   - Vypíšu: `"[CHILD-<N>] START"`
   - Počítajú od 0 do 1 000 000 000 a vypíšu výsledok
   - Vypíšu: `"[CHILD-<N>] END"`
3. **Parent proces:**
   - Čaká na všetkých potomkov (`wait()`)
   - Vypíše: `"[PARENT] All children finished"`

### Očakávaný výstup

```
[CHILD-1] START
[CHILD-2] START
[CHILD-3] START
[CHILD-1] END
[CHILD-2] END
[CHILD-3] END
[PARENT] All children finished
```

### Pokyny

- Všimnite si, že procesy sa **prepínajú** - nie všetci bežia naraz
- Počas behu spustite: `top` alebo `watch -n 1 'ps aux | grep task5'`
- **Vidíte, ako sa procesy striedajú?**
- **Koncept z prednášky:** Preemption - OS prepína medzi procesmi

### Kompilace a spustenie

```bash
g++ -o task5 task5.cpp -lm
./task5

# V inom termináli:
top
# Pozorujte, ako sa procesy striedajú na CPU
```

---

## Úkol 6 – Copy-on-Write optimalizácia

### Cieľ
Pochopenie **Copy-on-Write (COW)** optimalizácie - fork() neskopíruje hneď pamäť, len keď sa zmení.

### Zadanie

Napíšte program `task6.cpp`, ktorý:

1. Vytvorí veľký vector (1 000 000 prvkov) a naplní ho hodnotami
2. Vytvorí potomka pomocou `fork()`
3. **Child proces:**
   - Vytlačí: `"[CHILD] START - value[0]=<value>"`
   - Zmení prvý prvok: `arr[0] = 999`
   - Vypíše: `"[CHILD] MODIFIED - value[0]=<value>"`
4. **Parent proces:**
   - Vypíše: `"[PARENT] START - value[0]=<value>"`
   - Spí 2 sekundy
   - Vypíše: `"[PARENT] END - value[0]=<value>"` (bude stále 10!)

### Očakávaný výstup

```
[PARENT] START - value[0]=10
[CHILD] START - value[0]=10
[CHILD] MODIFIED - value[0]=999
[PARENT] END - value[0]=10    <--- nezmenilo sa!
```

### Pokyny

- **Dôležité:** Zmena v child procese neovplyvní parent
- Toto je dôkaz **Copy-on-Write** - pri zápise sa vytvorí kópia len tej časti
- **Koncept z hodín :** "Po forku procesy zdieľajú pamäť (read-only). Pri zápise sa vytvorí kópia len tej časti."

### Kompilace a spustenie

```bash
g++ -o task6 task6.cpp
./task6
```

---

## Bonus: Úkol 7 – Strom procesov

### Cieľ
Praktické pochopenie **hierarchie procesov** (parent-child strom).

### Zadanie

Napíšte program `task7.cpp`, ktorý:

1. Vytvorí 2 potomkov (Level 1)
2. Každý z nich vytvorí 2 potomkov (Level 2)
3. Všetci vypíšu svoju hierarchiu: `"[LEVEL-<L>] PID=<pid>, PPID=<ppid>"`
4. Parent počka na všetkých (`wait()`)

### Očakávaný výstup

```
[LEVEL-1] PID=1234, PPID=1000
[LEVEL-1] PID=1235, PPID=1000
[LEVEL-2] PID=1236, PPID=1234
[LEVEL-2] PID=1237, PPID=1234
[LEVEL-2] PID=1238, PPID=1235
[LEVEL-2] PID=1239, PPID=1235
```

### Pokyny

- Spustite: `pstree -p` - vidíte celý strom?
- **Koncept z hodín :** "PID 1 je koreň všetkých procesov"

### Kompilace a spustenie

```bash
g++ -o task7 task7.cpp
./task7

# V inom termináli počas behu:
pstree -p | grep task7
```

---

## Pokyny pre odevzdanie

### Štruktúra projektu

```
PRO_Homework_1_6/
├── task1.cpp
├── task2.cpp
├── task3.cpp
├── task4.cpp
├── task5.cpp
├── task6.cpp
├── task7.cpp (bonus)
├── Makefile
└── README.md
```

### Kompilacia a testovanie

```bash
# Jednotlivá kompilacia
g++ -o task1 task1.cpp
g++ -o task2 task2.cpp
# ... atď

# Alebo cez Makefile:
make all
```

### Príklad Makefile

```makefile
CC = g++
CFLAGS = -Wall -g -std=c++11
TARGETS = task1 task2 task3 task4 task5 task6 task7

all: $(TARGETS)

task1: task1.cpp
	$(CC) $(CFLAGS) -o task1 task1.cpp

task2: task2.cpp
	$(CC) $(CFLAGS) -o task2 task2.cpp

task3: task3.cpp
	$(CC) $(CFLAGS) -o task3 task3.cpp

task4: task4.cpp
	$(CC) $(CFLAGS) -o task4 task4.cpp

task5: task5.cpp
	$(CC) $(CFLAGS) -o task5 task5.cpp

task6: task6.cpp
	$(CC) $(CFLAGS) -o task6 task6.cpp

task7: task7.cpp
	$(CC) $(CFLAGS) -o task7 task7.cpp

clean:
	rm -f $(TARGETS) *.o

.PHONY: all clean
```

### README.md - Čo napísať

```markdown
# PRO domáca úloha: Procesy a správa úloh

Autor: [Vaše meno]
Dátum: [Dátum odevzdania]

## Úlohy

### Task 1: Jednoduchý potomek
- Testovanie: ./task1
- Pozorovaní: [Čo ste pozorovali]

### Task 2: Lifecycle a stavy procesov
- Testovanie: ./task2 & ps aux | grep task2
- Pozorovaní: [Čo ste pozorovali]

... atď pre všetky úkoly

## Záver
[Čo ste sa naučili z jednotlivých úloh]
```

---

## Bezpečnostný a kvalitný checklist

- Všetky `fork()` majú error handling (`if (pid < 0)`)
- Všetci potomkovia sú čistení cez `wait()` (bez zombie)
- Programy sú preložiteľné bez warningov
- Kód je čitateľný a okomentovaný
- Výstupy sú jasné a ľahko overiteľné
- Testované s `ps aux` počas behu

### Príklad error handlingu v C++

```cpp
#include <iostream>
#include <unistd.h>
#include <sys/wait.h>

using namespace std;

int main() {
    pid_t pid = fork();
    
    if (pid < 0) {
        cerr << "fork failed" << endl;
        return 1;
    }
    
    if (pid == 0) {
        // Child
        cout << "Child: PID=" << getpid() << endl;
    } else {
        // Parent
        cout << "Parent: Child PID=" << pid << endl;
        wait(nullptr);  // Očisti zombie!
    }
    
    return 0;
}
```

---

## Debugging tipy

```bash
# Ak vidíte zombie procesy:
ps aux | grep defunct

# Sledovanie procesov v reálnom čase:
watch -n 1 'ps aux | grep task'

# Analýza memory leakov:
valgrind --leak-check=full ./task1

# Debugging s GDB:
gdb ./task1
(gdb) run
(gdb) break main
(gdb) continue
```

---

Držím palce pri vypracovaní domácej úlohy.

S pozdravom a prianím pekného dňa,
Tomáš
