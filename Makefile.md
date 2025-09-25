# Makefile Guide - Základy a Príklady

## Čo je Makefile?

Makefile je súbor obsahujúci inštrukcie pre nástroj `make`, ktorý automatizuje proces kompilácie a buildu projektov. Umožňuje definovať závislosti medzi súbormi a pravidlá pre ich vytvorenie.

## Základné komponenty Makefile

### 1. Pravidlá (Rules)
Základná štruktúra pravidla:
```makefile
target: dependencies
	command
```

**Dôležité:**
- **target** - súbor, ktorý chceme vytvoriť
- **dependencies** - súbory potrebné na vytvorenie target-u
- **command** - príkaz na vytvorenie target-u (MUSÍ začínať TAB-om, nie medzerami!)

### 2. Premenné (Variables)
```makefile
CC = g++                    # Kompilátor
CFLAGS = -Wall -std=c++17   # Flagy kompilátora
TARGET = program            # Názov výsledného programu
SOURCES = main.cpp          # Zdrojové súbory
```

### 3. Komentáre
```makefile
# Toto je komentár v Makefile
```

## Primitívny Makefile pre main.cpp

### Najjednoduchší Makefile
```makefile
# Základný Makefile pre main.cpp
program: main.cpp
	g++ -o program main.cpp
```

**Použitie:**
```bash
make program    # Skompiluje main.cpp do programu "program"
make           # Spustí prvé pravidlo (program)
```

### Rozšírený Makefile s premennými
```makefile
# Definícia premenných
CC = g++
CFLAGS = -Wall -Wextra -std=c++17
TARGET = program
SOURCE = main.cpp

# Hlavné pravidlo
$(TARGET): $(SOURCE)
	$(CC) $(CFLAGS) -o $(TARGET) $(SOURCE)

# Pravidlo na vyčistenie
clean:
	rm -f $(TARGET)

# Označenie, že clean nie je súbor
.PHONY: clean
```

**Použitie:**
```bash
make           # Skompiluje program
make clean     # Vymaže program
```

## Komplexnejší Makefile pre viac súborov

### Štruktúra projektu:
```
project/
├── main.cpp
├── functions.cpp
├── functions.h
└── Makefile
```

### Pokročilý Makefile:
```makefile
# Kompilátor a flagy
CC = g++
CFLAGS = -Wall -Wextra -std=c++17 -g
LDFLAGS = 

# Názvy
TARGET = program
SOURCES = main.cpp functions.cpp
OBJECTS = $(SOURCES:.cpp=.o)
HEADERS = functions.h

# Hlavné pravidlo
all: $(TARGET)

$(TARGET): $(OBJECTS)
	$(CC) $(OBJECTS) -o $(TARGET) $(LDFLAGS)

# Pravidlo pre objektové súbory
%.o: %.cpp $(HEADERS)
	$(CC) $(CFLAGS) -c $< -o $@

# Vyčistenie
clean:
	rm -f $(OBJECTS) $(TARGET)

# Reinstall
rebuild: clean all

# Spustenie programu
run: $(TARGET)
	./$(TARGET)

# Debug verzia
debug: CFLAGS += -DDEBUG
debug: $(TARGET)

.PHONY: all clean rebuild run debug
```

## Užitočné Makefile funkcie

### 1. Automatické premenné
```makefile
$@    # Názov target-u
$<    # Prvá závislosť
$^    # Všetky závislosti
$?    # Závislosti novšie ako target
```

### 2. Pattern rules
```makefile
%.o: %.cpp
	$(CC) $(CFLAGS) -c $< -o $@
```

### 3. Podmienené kompilovanie
```makefile
# Debug/Release mód
ifeq ($(DEBUG),1)
    CFLAGS += -g -DDEBUG
else
    CFLAGS += -O2 -DNDEBUG
endif
```

## Príklad Makefile-u pre C++ projekt

```makefile
# ===========================================
# Makefile pre C++ projekt
# ===========================================

# Kompilátor a nástroje
CXX = g++
RM = rm -f

# Flagy kompilátora
CXXFLAGS = -Wall -Wextra -std=c++17
LDFLAGS = 
LDLIBS = 

# Debug/Release konfigurácia
DEBUG ?= 0
ifeq ($(DEBUG), 1)
    CXXFLAGS += -g -O0 -DDEBUG
    TARGET_SUFFIX = _debug
else
    CXXFLAGS += -O2 -DNDEBUG
    TARGET_SUFFIX = 
endif

# Názvy a cesty
TARGET = program$(TARGET_SUFFIX)
SRCDIR = src
OBJDIR = obj
SOURCES = $(wildcard $(SRCDIR)/*.cpp)
OBJECTS = $(SOURCES:$(SRCDIR)/%.cpp=$(OBJDIR)/%.o)

# Vytvorenie objektového adresára
$(shell mkdir -p $(OBJDIR))

# ===========================================
# PRAVIDLÁ
# ===========================================

# Hlavné pravidlo
all: $(TARGET)

# Linkovanie
$(TARGET): $(OBJECTS)
	$(CXX) $(OBJECTS) -o $@ $(LDFLAGS) $(LDLIBS)
	@echo "Build completed: $(TARGET)"

# Kompilovanie objektových súborov
$(OBJDIR)/%.o: $(SRCDIR)/%.cpp
	$(CXX) $(CXXFLAGS) -c $< -o $@

# Vyčistenie
clean:
	$(RM) $(OBJECTS) $(TARGET)
	@echo "Cleaned up"

# Úplné prebudovanie
rebuild: clean all

# Spustenie
run: $(TARGET)
	./$(TARGET)

# Inštalácia (voliteľné)
install: $(TARGET)
	cp $(TARGET) /usr/local/bin/

# Debug build
debug:
	$(MAKE) DEBUG=1

# Zobrazenie informácií
info:
	@echo "Target: $(TARGET)"
	@echo "Sources: $(SOURCES)"
	@echo "Objects: $(OBJECTS)"
	@echo "CXX Flags: $(CXXFLAGS)"

# Označenie non-file targets
.PHONY: all clean rebuild run install debug info

# ===========================================
# POMOCNÉ PRAVIDLÁ
# ===========================================

# Kontrola syntaxe bez linkovania
check:
	$(CXX) $(CXXFLAGS) -fsyntax-only $(SOURCES)

# Generovanie závislostí
depend: $(SOURCES)
	$(CXX) -MM $(SOURCES) > dependencies.mk

-include dependencies.mk
```

## Praktické tipy

### 1. Testovanie Makefile
```bash
make -n        # Dry run - ukáže čo by sa vykonalo
make -j4       # Paralelná kompilácia (4 procesy)
make DEBUG=1   # Kompilovanie s debug flagmi
```

### 2. Bežné chyby
- **Použitie medzier namiesto TAB-ov** - najčastejšia chyba!
- **Nesprávne názvy premenných** - rozlišuje sa veľkosť písmen
- **Chýbajúce závislosti** - súbory sa nekompilujú keď sa zmení header

### 3. Štruktúra pre začiatočníkov
```makefile
# 1. Definovať premenné
CC = g++
TARGET = program
SOURCES = main.cpp

# 2. Hlavné pravidlo
$(TARGET): $(SOURCES)
	$(CC) -o $(TARGET) $(SOURCES)

# 3. Vyčistenie
clean:
	rm -f $(TARGET)

.PHONY: clean
```

## Najčastejšie používané pravidlá

```makefile
all:        # Hlavné pravidlo - kompiluje všetko
clean:      # Vymaže vygenerované súbory
install:    # Inštaluje program do systému
uninstall:  # Odinštaluje program
test:       # Spustí testy
run:        # Spustí program
debug:      # Kompiluje debug verziu
release:    # Kompiluje release verziu
help:       # Zobrazí nápovedu
```

## Príklad spustenia

```bash
# Kompilovanie
make

# Debug verzia
make debug

# Spustenie
make run

# Vyčistenie
make clean

# Zobrazenie informácií
make info
```

---

**Pamätajte:** 
1. Príkazy v Makefile MUSIA začínať TAB-om, nie medzerami!
2. Make porovnáva časové pečiatky súborov - kompiluje len to, čo sa zmenilo
3. Používajte `.PHONY` pre pravidlá, ktoré nevytvárajú súbory
4. Testujte Makefile pomocou `make -n` pred skutočným spustením
