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


