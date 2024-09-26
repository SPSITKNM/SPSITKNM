# Program na počítanie histogramu čísel - PRO - 27.9.2024

Program bude počítať histogram čísel. Histogram bude mať 9 košov a bude zaznamenávať četnosť jednotlivých hodnôt, ktoré budú v rozsahu zadanom na vstupe programu.

## Požiadavky na program

### 1. Voľba vykreslenia
Načítate zo vstupu znak, ktorý bude udávať, či sa má vykresliť horizontálny (pokiaľ bol na vstupe znak `h`) alebo vertikálny (pokiaľ bol na vstupe znak `v`) histogram.

- Ak bude zadaný iný znak ako `v` alebo `h`, vypíšte riadok **"Neplatný mód vykreslenia"** na štandardný výstup a ukončite program s chybovým kódom `1`.

### 2. Načítanie vstupných hodnôt
Načítate zo vstupu dve nezáporné čísla `n` a `m`.

- `n` udáva, koľko čísel program načíta, z ktorých bude počítať histogram.
- `m` udáva rozsah čísel, pre ktoré máte počítať histogram. Tento rozsah bude daný intervalom \[`m`, `m + 8`\].

Napríklad, ak bude `m = 5`, histogram bude počítať výskyty čísel od 5 až po 13 vrátane.

### 3. Výpočet histogramu
Načítate od používateľa `n` celých čísel oddelených medzerou a vypočítate pre ne histogram.

- Ak bude číslo na vstupe mimo intervalu \[`m`, `m + 8`\], považujte také číslo za neplatné. Počet neplatných čísel si v programe pamätajte.
- Histogram počíta, koľkokrát sa jednotlivé hodnoty z intervalu `m` až `m + 8` vyskytli vo vstupe.
- Histogram reprezentujte poľom.
- Ideálne riešenie na výpočet histogramu by nemalo obsahovať 9x `if-else` vetvy. Zamyslite sa, ako histogram spočítať bez podmienok, dá sa to vykonať jedným riadkom.

### 4. Výstup - Horizontálny histogram
Ak bol na vstupe znak `h`, vykreslite horizontálny histogram na výstup:

- Vypíšte pod seba čísla od `m` až po `m + 8`, každé číslo na jednom riadku.
- Zarovnajte čísla doprava tak, aby počty výskytov pre jednotlivé čísla začínali vždy v tom istom stĺpci. Napríklad, ak bude `m = 98`, tak `m + 8` bude 106, a toto číslo má viac číslic ako 98. Preto musíte pred výpisom pred 98 a 99 vypísať jednu medzeru, inak by čísla pod sebou nesedeli správne.
- Tu je znak `_`, ktorý reprezentuje medzeru.

```cpp
_98: **
_99: **
100: *
101: 
102: *
103: 
104: 
105: *
106: *
Počet neplatných čísel: 0
```
