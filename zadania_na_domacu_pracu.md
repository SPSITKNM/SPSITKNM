# Úlohy na precvičenie OOP v C++

Teóriu k týmto úlohám nájdeš v [poznámkach k OOP](https://spsitknm.github.io/citacka.html?s=oop&doc=oop-opakovanie): kapitoly *Enkapsulácia*, *Dedičnosť*, *Abstrakcia* a *Polymorfizmus*.

## ZÁKLADY

### 1. Triedy, atribúty a metódy

**Úloha: Knižnica**
- Vytvor triedu `Kniha` s atribútmi: `nazov`, `autor`, `rokVydania`, `pocetStran`
- Pridaj konštruktor, ktorý nastaví všetky atribúty
- Vytvor metódu `vypisInfo()`, ktorá vypíše všetky informácie o knihe
- Vytvor metódu `jeStara()`, ktorá vráti `true` ak je kniha staršia ako 50 rokov (aktuálny rok zisti z hodín počítača, nepíš ho natvrdo)
- Vytvor 3 rôzne objekty knihy a zavolaj ich metódy

**Kroková príručka:**
```cpp
#include <iostream>
#include <string>
#include <ctime>                // pre zistenie aktuálneho roka
using namespace std;

class Kniha {
private:
    // 1. KROK: Definuj atribúty tu
    string nazov;
    // ... doplň ostatné
    
public:
    // 2. KROK: Vytvor konštruktor
    Kniha(string n, string a, int rok, int strany) {
        nazov = n;
        // ... doplň ostatné
    }
    
    // 3. KROK: Vytvor metódu vypisInfo()
    void vypisInfo() {
        cout << "Názov: " << nazov << endl;
        // ... doplň ostatné výpisy
    }
    
    // 4. KROK: Vytvor metódu jeStara()
    bool jeStara() {
        time_t cas = time(nullptr);                         // aktuálny čas z hodín počítača
        int aktualnyRok = localtime(&cas)->tm_year + 1900;  // rok = počet rokov od 1900
        return (aktualnyRok - rokVydania) > 50;
    }
};

int main() {
    // 5. KROK: Vytvor objekty a otestuj
    Kniha k1("1984", "George Orwell", 1949, 328);
    k1.vypisInfo();
    
    if(k1.jeStara()) {
        cout << "Táto kniha je stará!" << endl;
    }
    
    return 0;
}
```

---

## ENKAPSULÁCIA

### 2. Enkapsulácia (zapuzdrenie)

**Úloha: Bankový účet**
- Vytvor triedu `BankovyUcet` s privátnym atribútom `zostatok` (začne na 0)
- Pridaj metódu `vlozit(double suma)` - pridá peniaze (iba ak je suma > 0)
- Pridaj metódu `vybrat(double suma)` - odoberie peniaze (iba ak je dostatok)
- Pridaj metódu `getZostatok()` - vráti aktuálny zostatok
- Skús pristúpiť k `zostatok` priamo z `main()` - čo sa stane?

**Riešenie s vysvetlením:**
```cpp
#include <iostream>
using namespace std;

class BankovyUcet {
private:
    double zostatok;  // PRIVATE - nedostupný z vonku!
    
public:
    // Konštruktor
    BankovyUcet() {
        zostatok = 0;
    }
    
    void vlozit(double suma) {
        if(suma > 0) {
            zostatok += suma;
            cout << "Vložené: " << suma << " EUR" << endl;
        } else {
            cout << "Chyba: Suma musí byť kladná!" << endl;
        }
    }
    
    void vybrat(double suma) {
        if(suma > zostatok) {
            cout << "Chyba: Nedostatok peňazí!" << endl;
        } else if(suma <= 0) {
            cout << "Chyba: Suma musí byť kladná!" << endl;
        } else {
            zostatok -= suma;
            cout << "Vybraté: " << suma << " EUR" << endl;
        }
    }
    
    double getZostatok() {
        return zostatok;
    }
};

int main() {
    BankovyUcet ucet;
    ucet.vlozit(1000);
    ucet.vybrat(300);
    cout << "Zostatok: " << ucet.getZostatok() << " EUR" << endl;
    
    // ucet.zostatok = 999999;  // CHYBA! zostatok je private
    
    return 0;
}
```

### Enkapsulácia s gettermi a settermi

**Úloha: Študent s validáciou**
- Vytvor triedu `Student` s privátnym atribútom `vek`
- Vytvor getter `getVek()` a setter `setVek(int v)`
- V settri validuj, že vek musí byť 15-25 rokov
- Vytvor privátny atribút `priemer` (0.0 - 5.0)
- Vytvor setter s validáciou a getter

```cpp
class Student {
private:
    string meno;
    int vek;
    double priemer;
    
public:
    Student(string m) {
        meno = m;
        vek = 18;
        priemer = 0.0;
    }
    
    // GETTERY
    int getVek() { return vek; }
    double getPriemer() { return priemer; }
    string getMeno() { return meno; }
    
    // SETTERY s validáciou
    void setVek(int v) {
        if(v >= 15 && v <= 25) {
            vek = v;
        } else {
            cout << "Chyba: Vek musí byť 15-25!" << endl;
        }
    }
    
    void setPriemer(double p) {
        if(p >= 0.0 && p <= 5.0) {
            priemer = p;
        } else {
            cout << "Chyba: Priemer musí byť 0.0-5.0!" << endl;
        }
    }
    
    void vypisInfo() {
        cout << "Študent: " << meno << ", Vek: " << vek 
             << ", Priemer: " << priemer << endl;
    }
};
```

---

## DEDIČNOSŤ

### 3. Dedičnosť (inheritance)

**Úloha: Zvieratá**
- Vytvor rodičovskú triedu `Zviera` s atribútmi: `meno`, `vek`
- Pridaj metódu `zvuk()`, ktorá vypíše "Zviera robí zvuk"
- Vytvor triedu `Pes`, ktorá dedí od `Zviera`
  - Prepiš (override) metódu `zvuk()` - "Haf haf!"
  - Pridaj novú metódu `aportuj()`
- Vytvor triedu `Macka`, ktorá dedí od `Zviera`
  - Prepiš metódu `zvuk()` - "Mňau!"
  - Pridaj novú metódu `pradaj()`

**Kompletné riešenie:**
```cpp
#include <iostream>
#include <string>
using namespace std;

// RODIČOVSKÁ TRIEDA
class Zviera {
protected:  // protected = dostupné v potomkoch
    string meno;
    int vek;
    
public:
    Zviera(string m, int v) {
        meno = m;
        vek = v;
    }
    
    void zvuk() {
        cout << "Zviera robí zvuk" << endl;
    }
    
    void vypisInfo() {
        cout << "Meno: " << meno << ", Vek: " << vek << " rokov" << endl;
    }
};

// POTOMOK 1
class Pes : public Zviera {
public:
    // Konštruktor potomka volá konštruktor rodiča
    Pes(string m, int v) : Zviera(m, v) {
    }
    
    // OVERRIDE - prepísanie metódy
    void zvuk() {
        cout << meno << " hovorí: Haf haf!" << endl;
    }
    
    void aportuj() {
        cout << meno << " aportuje loptu!" << endl;
    }
};

// POTOMOK 2
class Macka : public Zviera {
public:
    Macka(string m, int v) : Zviera(m, v) {
    }
    
    void zvuk() {
        cout << meno << " hovorí: Mňau!" << endl;
    }
    
    void pradaj() {
        cout << meno << " priadne priadne..." << endl;
    }
};

int main() {
    Pes dunco("Dunčo", 3);
    dunco.vypisInfo();
    dunco.zvuk();
    dunco.aportuj();
    
    cout << endl;
    
    Macka micka("Mička", 2);
    micka.vypisInfo();
    micka.zvuk();
    micka.pradaj();
    
    return 0;
}
```

---

## POLYMORFIZMUS

### 4. Polymorfizmus

**Úloha: Geometrické tvary**
- Vytvor rodičovskú triedu `Tvar` s **virtuálnou** metódou `vypocitajObsah()`
- Vytvor triedy `Stvorec`, `Kruh`, `Obdlznik`, ktoré dedia od `Tvar`
- V každej triede prepíš metódu `vypocitajObsah()`
- Vytvor pole ukazateľov na `Tvar` a ulož tam rôzne tvary
- V cykle zavolaj pre každý `vypocitajObsah()` - POLYMORFIZMUS!

**Dôležité:**
- Metóda v rodičovi musí byť `virtual`
- Pracujeme s **ukazateľmi** (pointers)
- Deštruktor musí byť tiež `virtual`

```cpp
#include <iostream>
#include <cmath>
using namespace std;

// RODIČOVSKÁ TRIEDA
class Tvar {
public:
    // VIRTUAL = umožňuje polymorfizmus
    virtual double vypocitajObsah() {
        return 0;
    }
    
    // Virtual deštruktor je dôležitý!
    virtual ~Tvar() {}
};

class Stvorec : public Tvar {
private:
    double strana;
    
public:
    Stvorec(double s) : strana(s) {}
    
    double vypocitajObsah() override {
        return strana * strana;
    }
};

class Kruh : public Tvar {
private:
    double polomer;
    
public:
    Kruh(double r) : polomer(r) {}
    
    double vypocitajObsah() override {
        return 3.14159 * polomer * polomer;
    }
};

class Obdlznik : public Tvar {
private:
    double sirka, vyska;
    
public:
    Obdlznik(double s, double v) : sirka(s), vyska(v) {}
    
    double vypocitajObsah() override {
        return sirka * vyska;
    }
};

int main() {
    // Pole UKAZATEĽOV na rodičovskú triedu
    Tvar* tvary[3];
    
    tvary[0] = new Stvorec(5);
    tvary[1] = new Kruh(3);
    tvary[2] = new Obdlznik(4, 6);
    
    // POLYMORFIZMUS v akcii!
    for(int i = 0; i < 3; i++) {
        cout << "Obsah tvaru " << i+1 << ": " 
             << tvary[i]->vypocitajObsah() << endl;
    }
    
    // Nezabudnite uvoľniť pamäť!
    for(int i = 0; i < 3; i++) {
        delete tvary[i];
    }
    
    return 0;
}
```

**Vysvetlenie polymorfizmu:**
```
Bez virtual:
- tvary[0]->vypocitajObsah() by volalo Tvar::vypocitajObsah() (vždy 0)

S virtual:
- tvary[0]->vypocitajObsah() volá Stvorec::vypocitajObsah()
- tvary[1]->vypocitajObsah() volá Kruh::vypocitajObsah()
- atď.

To je POLYMORFIZMUS - jeden interface, rôzne správanie!
```

---

## ABSTRAKCIA (POKROČILÉ)

### 5. Abstraktné triedy

**Úloha: Platobné metódy**
- Vytvor abstraktnú triedu `PlatobnaMetoda` s čisto virtuálnou metódou `zaplat(double suma)`
- Vytvor triedy `KreditnaKarta` a `Hotovost`, ktoré implementujú `zaplat()`
- Skús vytvoriť objekt z abstraktnej triedy - čo sa stane?

```cpp
#include <iostream>
using namespace std;

// ABSTRAKTNÁ TRIEDA
class PlatobnaMetoda {
public:
    // Čisto virtuálna metóda = 0 (abstraktná)
    virtual void zaplat(double suma) = 0;
    
    virtual ~PlatobnaMetoda() {}
};

class KreditnaKarta : public PlatobnaMetoda {
private:
    string cisloKarty;
    
public:
    KreditnaKarta(string cislo) : cisloKarty(cislo) {}
    
    // MUSÍME implementovať abstraktnú metódu
    void zaplat(double suma) override {
        cout << "Platba " << suma << " EUR kartou " 
             << cisloKarty << endl;
    }
};

class Hotovost : public PlatobnaMetoda {
public:
    void zaplat(double suma) override {
        cout << "Platba " << suma << " EUR v hotovosti" << endl;
    }
};

class Bitcoin : public PlatobnaMetoda {
private:
    string wallet;
    
public:
    Bitcoin(string w) : wallet(w) {}
    
    void zaplat(double suma) override {
        cout << "Platba " << suma << " EUR v BTC na " 
             << wallet << endl;
    }
};

int main() {
    // PlatobnaMetoda pm;  // CHYBA! Nemôžeme vytvoriť objekt z abstraktnej triedy
    
    PlatobnaMetoda* platby[3];
    
    platby[0] = new KreditnaKarta("1234-5678-9012");
    platby[1] = new Hotovost();
    platby[2] = new Bitcoin("1A2B3C4D");
    
    for(int i = 0; i < 3; i++) {
        platby[i]->zaplat(100.50);
    }
    
    for(int i = 0; i < 3; i++) {
        delete platby[i];
    }
    
    return 0;
}
```

---

## KOMPLEXNÁ ÚLOHA

### 6. Systém zamestnancov (všetky koncepty)

**Rozdelené na kroky:**

**KROK 1: Abstraktná rodičovská trieda**

Na začiatok súboru daj `#include <iostream>`, `#include <string>` a `using namespace std;`. Kroky 1 až 4 potom spolu tvoria jeden program (triedy idú pred `main()`).
```cpp
class Zamestnanec {
protected:
    string meno;
    string priezvisko;
    double plat;  // protected, nie private
    
public:
    Zamestnanec(string m, string p, double pl) {
        meno = m;
        priezvisko = p;
        setPlat(pl);  // validácia cez setter
    }
    
    // Abstraktná metóda
    virtual double vypocitajBonus() = 0;
    
    // Gettery a settery
    double getPlat() { return plat; }
    
    void setPlat(double pl) {
        if(pl > 0) {
            plat = pl;
        } else {
            cout << "Chyba: Plat musí byť kladný!" << endl;
            plat = 1000;
        }
    }
    
    string celeMeno() {
        return meno + " " + priezvisko;
    }
    
    virtual ~Zamestnanec() {}
};
```

**KROK 2: Potomok Programator**
```cpp
class Programator : public Zamestnanec {
private:
    string programovaciJazyk;
    
public:
    Programator(string m, string p, double pl, string jazyk) 
        : Zamestnanec(m, p, pl) {
        programovaciJazyk = jazyk;
    }
    
    double vypocitajBonus() override {
        return plat * 0.20;  // 20% bonus
    }
    
    void vypisInfo() {
        cout << "Programátor: " << celeMeno() 
             << ", Jazyk: " << programovaciJazyk
             << ", Plat: " << plat << " EUR"
             << ", Bonus: " << vypocitajBonus() << " EUR" << endl;
    }
};
```

**KROK 3: Potomok Manager**
```cpp
class Manager : public Zamestnanec {
private:
    int pocetPodriadených;
    
public:
    Manager(string m, string p, double pl, int pocet) 
        : Zamestnanec(m, p, pl) {
        pocetPodriadených = pocet;
    }
    
    double vypocitajBonus() override {
        return plat * 0.15 + pocetPodriadených * 100;
    }
    
    void vypisInfo() {
        cout << "Manažér: " << celeMeno() 
             << ", Podriadeních: " << pocetPodriadených
             << ", Plat: " << plat << " EUR"
             << ", Bonus: " << vypocitajBonus() << " EUR" << endl;
    }
};
```

**KROK 4: Použitie v main()**
```cpp
int main() {
    Programator prog1("Ján", "Novák", 2000, "C++");
    Programator prog2("Mária", "Horváthová", 2500, "Python");
    Manager man1("Peter", "Kovács", 3000, 5);
    
    cout << "=== ZAMESTNANCI FIRMY ===" << endl << endl;
    
    prog1.vypisInfo();
    prog2.vypisInfo();
    man1.vypisInfo();
    
    cout << endl << "=== POLYMORFIZMUS ===" << endl << endl;
    
    // Polymorfizmus s ukazateľmi
    Zamestnanec* zamestnanci[3];
    zamestnanci[0] = &prog1;
    zamestnanci[1] = &prog2;
    zamestnanci[2] = &man1;
    
    for(int i = 0; i < 3; i++) {
        cout << zamestnanci[i]->celeMeno() 
             << " - Bonus: " << zamestnanci[i]->vypocitajBonus() 
             << " EUR" << endl;
    }
    
    return 0;
}
```

---

## BONUSOVÉ ÚLOHY

### 7. Viacnásobná dedičnosť

**Úloha: Elektrické auto**
- Vytvor triedu `Auto` s atribútmi: `znacka`, `rychlost`
- Vytvor triedu `ElektrickeZariadenie` s atribútmi: `kapacitaBaterie`
- Vytvor triedu `ElektrickeAuto`, ktorá dedí od OBOCH tried
- Implementuj metódy oboch rodičov

```cpp
#include <iostream>
#include <string>
using namespace std;

class Auto {
protected:
    string znacka;
    int rychlost;
    
public:
    Auto(string z, int r) : znacka(z), rychlost(r) {}
    
    void jazdi() {
        cout << znacka << " jazdí rýchlosťou " << rychlost << " km/h" << endl;
    }
};

class ElektrickeZariadenie {
protected:
    int kapacitaBaterie;  // v kWh
    
public:
    ElektrickeZariadenie(int kap) : kapacitaBaterie(kap) {}
    
    void nabij() {
        cout << "Nabíjam batériu " << kapacitaBaterie << " kWh" << endl;
    }
};

// VIACNÁSOBNÁ DEDIČNOSŤ
class ElektrickeAuto : public Auto, public ElektrickeZariadenie {
private:
    int dojazd;  // v km
    
public:
    ElektrickeAuto(string z, int r, int kap, int d) 
        : Auto(z, r), ElektrickeZariadenie(kap), dojazd(d) {
    }
    
    void vypisInfo() {
        cout << "Elektrické auto: " << znacka << endl;
        cout << "Kapacita: " << kapacitaBaterie << " kWh" << endl;
        cout << "Dojazd: " << dojazd << " km" << endl;
    }
};

int main() {
    ElektrickeAuto tesla("Tesla Model 3", 200, 75, 500);
    
    tesla.vypisInfo();
    tesla.jazdi();
    tesla.nabij();
    
    return 0;
}
```

---

## TIPY A TRIKY

### Rozdiel medzi private, protected, public:

```cpp
class Rodic {
private:
    int a;      // Nedostupné v potomkoch ANI z vonku
protected:
    int b;      // Dostupné v potomkoch, ale NIE z vonku
public:
    int c;      // Dostupné všade
};

class Potomok : public Rodic {
    void test() {
        // a = 10;  // CHYBA - private
        b = 20;     // OK - protected
        c = 30;     // OK - public
    }
};

int main() {
    Potomok p;
    // p.a = 10;  // CHYBA - private
    // p.b = 20;  // CHYBA - protected
    p.c = 30;     // OK - public
}
```

### Kedy použiť virtual:

```cpp
// BEZ virtual
class Rodic {
    void metoda() { cout << "Rodič"; }
};

// S virtual (polymorfizmus)
class Rodic {
    virtual void metoda() { cout << "Rodič"; }
};
```

### Pamäťový cheat sheet:

```cpp
// Objekt na stacku
Student s1("Ján");

// Objekt na heape (dynamicky)
Student* s2 = new Student("Mária");
delete s2;  // MUSÍME uvoľniť!

// Pole objektov
Student* studenti[3];
studenti[0] = new Student("A");
// ... nezabudnite delete!
```

---

**Info čo sa zijde**
- Ako kompilovať: `g++ main.cpp -o program`
- Ako spustiť: `./program`
- Ako debugovať základné chyby (chýbajúci `;`, `{}`, atď.)

---

# Usmernenia

## Dôležité informácie

### Riešenia
- Riešenia žiadam odovzdávať do otvorenej úlohy na EduPage.

### Plagiát
- Plagiát štýlu 1:1 od kolegu je hodnotený automaticky známkou 5.
- Využitie zdrojov je voľné, vrátane AI je povolené.
- Prístup štýlu CTRL + C a CTRL + V do AI neodporúčam, úlohy sú nastavené tak aby riešenie cez AI trvalo rovnako ako dĺžka Vami implementovanej logiky... 

### Termíny
- Každý deň po deadline znamená o stupeň horšiu známku!

## Veľa šťastia,
**TM**

