# Algoritmická expedícia: Záchrana Kódlandu, záskok za Muchu.

## Úvod do sveta Kódlandu

### Nezabudnite si prehrať demo v jazyku Python, ktoré je priložené k tejto domácej úlohe na Edupage, aby ste sa pripravili na riešenie úloh ;)

Vitajte v Kódlande, fascinujúcom digitálnom svete, kde sa stretávajú logika, matematika a algoritmické myslenie. Tento kedysi pokojný svet však čelí vážnemu nebezpečenstvu. Legendárny strážca Kódlandu, Mucha, musel nečakane odletieť do Ostravy, aby si vydobil slobodu, čím nechal Gotham a Kódland blízko KNM nechránené. O Gotham sa síce postaral Batman ako záskok, ale o zvyšok Kódlandu sa nemá kto posratať.

Túto situáciu okamžite využila temná entita známa ako "Bugzilla", ktorá začala korumpovať základnú štruktúru Kódlandu a narúšať jeho kľúčové systémy.

Ako skúsený programátor ste boli povolaný na pomoc. Vaša misia je jednoduchá, no náročná: vyriešiť sériu algoritmických problémov, ktoré pomôžu obnoviť poškodené časti Kódlandu a zastaviť šírenie Bugzilly.

Každý problém predstavuje jeden narušený systém. S každým vyriešeným problémom sa približujete k záchrane Kódlandu a obnoveniu jeho pôvodnej harmónie.

## Všeobecné pokyny

- Všetky riešenia implementujte v jednotno jazyku Vami zvolenom : Pascal, Assembly, Nim, Pony, Idris, Haskell, Erlang 
- Dbajte na efektívnosť algoritmov a pamäťovú náročnosť
- Každé riešenie by malo obsahovať komentáre vysvetľujúce hlavné časti kódu
- Odovzdávajte riešenia vo forme zdrojových súborov (.<zvolený jazyk>), nie .docx !pptx
- Optional : Ku každému riešeniu pripojte krátky dokument popisujúci váš postup a časovú/pamäťovú zložitosť vášho algoritmu

## Úloha 1: Energetické krištáľy

### Príbeh
Energetické krištáľy sú základným zdrojom energie v Kódlande. Bugzilla však premenila mnoho z nich na falošné krištále, ktoré namiesto dodávania energie systém vyčerpávajú. Vašou úlohou je identifikovať pravé krištále.

### Problém
Máte zoznam čísel, kde každé číslo predstavuje energetickú signatúru krištáľu. Pravé krištále majú unikátnu vlastnosť: keď zoradíte cifry ich signatúr vzostupne, rozdiel medzi výsledným číslom a pôvodnou signatúrou je deliteľný magickým číslom K.

### Vstup
- Prvý riadok obsahuje dve celé čísla N a K, kde N je počet krištáľov a K je magické číslo
- Nasledujúcich N riadkov obsahuje celé čísla Si - signatúry krištáľov

### Výstup
- Vypíšte celkový počet pravých krištáľov
- Následne vypíšte súčet signatúr všetkých pravých krištáľov

### Príklad
**Vstup:**
```
5 7
123
321
547
789
1024
```

**Výstup:**
```
2
1345
```

**Vysvetlenie:**
- 123 zoradené je 123, rozdiel 123-123=0, 0 je deliteľné 7 -> pravý krištáľ
- 321 zoradené je 123, rozdiel 123-321=-198, -198 nie je deliteľné 7 -> falošný krištáľ
- 547 zoradené je 457, rozdiel 457-547=-90, -90 nie je deliteľné 7 -> falošný krištáľ
- 789 zoradené je 789, rozdiel 789-789=0, 0 je deliteľné 7 -> pravý krištáľ
- 1024 zoradené je 0124, rozdiel 124-1024=-900, -900 nie je deliteľné 7 -> falošný krištáľ
- Počet pravých krištáľov: 2
- Súčet signatúr pravých krištáľov: 123+789=1345

## Úloha 2: Kvantové tunely

### Príbeh
Hlavný transportný systém Kódlandu tvoria kvantové tunely, ktoré spájajú rôzne oblasti. Bugzilla poškodila mnoho z týchto tunelov a narušila optimálne trasy. Musíte nájsť najkratšiu cestu naprieč sieťou tunelov.

### Problém
Máte mapu kvantových tunelov reprezentovanú ako neorientovaný graf. Každý tunel má špecifickú dĺžku. Potrebujete nájsť najkratšiu cestu zo štartovacieho bodu do cieľového bodu tak, aby ste navštívili všetky povinné kontrolné body.

### Vstup
- Prvý riadok obsahuje štyri celé čísla N, M, S, D, kde:
  - N je počet uzlov (oblastí Kódlandu)
  - M je počet hrán (kvantových tunelov)
  - S je štartovací uzol
  - D je cieľový uzol
- Druhý riadok obsahuje celé číslo K a potom K celých čísel, ktoré predstavujú povinné kontrolné body
- Nasledujúcich M riadkov obsahuje trojice celých čísel A, B, L, kde:
  - A a B sú uzly spojené tunelom
  - L je dĺžka tunelu

### Výstup
- Vypíšte najkratšiu celkovú dĺžku cesty zo S do D, ktorá prechádza cez všetky kontrolné body
- Na druhý riadok vypíšte postupnosť uzlov tvoriacich túto cestu

### Príklad
**Vstup:**
```
6 8 1 6
2 3 5
1 2 5
1 3 2
2 3 1
2 4 3
3 4 2
3 5 4
4 6 6
5 6 3
```

**Výstup:**
```
11
1 3 5 6
```

## Úloha 3: Binárny déšť

### Príbeh
Údolie kódu je ohrozené zvláštnym binárnym dažďom, ktorý padá na digitálnu krajinu. Každá kvapka dažďa obsahuje sekvenciu núl a jednotiek. Vašou úlohou je analyzovať vzory v daždi, aby ste mohli predpovedať jeho správanie a ochrániť kritické oblasti.

### Problém
Máte záznamy o binárnom daždi – dlhé sekvencie núl a jednotiek. Nájdite najdlhšiu podsekvenciu, ktorá sa opakuje aspoň K-krát (môže sa prekrývať).

### Vstup
- Prvý riadok obsahuje dve celé čísla N a K, kde N je dĺžka sekvencie a K je minimálny počet opakovaní
- Druhý riadok obsahuje sekvenciu núl a jednotiek dĺžky N

### Výstup
- Vypíšte dĺžku najdlhšej opakujúcej sa podsekvencie
- Na druhý riadok vypíšte nájdenú podsekvenciu
- Ak existuje viac podsekvenčií s rovnakou maximálnou dĺžkou, vypíšte tú, ktorá sa začína na najnižšej pozícii

### Príklad
**Vstup:**
```
20 3
10110110110110110110
```

**Výstup:**
```
6
101101
```

**Vysvetlenie:**
Podsekvenicia "101101" sa opakuje 3-krát (na pozíciách 0, 6 a 12)

## Úloha 4: Data Fragmenty

### Príbeh
Hlavná databáza Kódlandu bola fragmentovaná Bugzillou. Zhromaždite a spojte roztratené fragmenty dát, aby ste obnovili dôležité informácie.

### Problém
Každý fragment dát je reprezentovaný reťazcom. Vašou úlohou je nájsť najkratší superreťazec, ktorý obsahuje všetky zadané fragmenty ako súvislé podreťazce, pričom môžete využiť prekrývanie fragmentov.

### Vstup
- Prvý riadok obsahuje celé číslo N, počet fragmentov
- Nasledujúcich N riadkov obsahuje reťazce Si - jednotlivé fragmenty

### Výstup
- Vypíšte jeden reťazec - najkratší možný superreťazec obsahujúci všetky fragmenty

### Príklad
**Vstup:**
```
4
ABCD
CDFE
FEGI
GHIJ
```

**Výstup:**
```
ABCDFEGIHJ
```

**Vysvetlenie:**
Fragmenty sa môžu prekrývať: ABCD + CDFE = ABCDFE (prekrytie "CD"), ABCDFE + FEGI = ABCDFEGI (prekrytie "FE"), ABCDFEGI + GHIJ = ABCDFEGIHJ (prekrytie "G")

## Úloha 5: Kvantové šifrovanie

### Príbeh
Bugzilla zašifrovala kľúčové protokoly Kódlandu pomocou sofistikovaného kvantového šifrovania. Vašou úlohou je dešifrovať tieto protokoly, aby ste obnovili kontrolu nad systémami.

### Problém
Máte zašifrovanú správu a zoznam transformácií. Každá transformácia má vzor a náhradu. Vašou úlohou je aplikovať transformácie na zašifrovanú správu, aby ste ju dešifrovali.

Transformácie musia byť aplikované efektívne:
1. V každom kroku nájdite všetky výskyty aktuálneho vzoru v správe
2. Nahraďte súčasne všetky tieto výskyty príslušnou náhradou
3. Pokračujte ďalšou transformáciou

### Vstup
- Prvý riadok obsahuje zašifrovanú správu S
- Druhý riadok obsahuje celé číslo N, počet transformácií
- Nasledujúcich N riadkov obsahuje dvojice reťazcov Pi, Ri - vzor a náhrada pre i-tu transformáciu

### Výstup
- Vypíšte dešifrovanú správu po aplikovaní všetkých transformácií

### Príklad
**Vstup:**
```
ABABABABABA
2
ABA XYZ
XYZ 123
```

**Výstup:**
```
123B123B1
```

**Vysvetlenie:**
1. Správa: ABABABABABA
2. Po aplikovaní 1. transformácie (ABA -> XYZ): XYZB XYZB XYZ 
   (kde pre prehľadnosť sú medzery, reálne tam nie sú)
3. Po aplikovaní 2. transformácie (XYZ -> 123): 123B123B1

Poznámka: Transformácie sa aplikujú postupne, nie súčasne.

## Hodnotenie

Za každú úlohu môžete získať maximálne 20 bodov:
- Správnosť riešenia: 12 bodov
- Efektívnosť algoritmu: 5 bodov
- Kvalita kódu a komentáre: 3 body

## Termín odovzdania

Riešenia odovzdajte do dvoch týždňov od zadania úloh.

## Bonusová úloha: Obrana pred Bugzillou

### Príbeh
Konečne ste lokalizovali centrálu Bugzilly! Aby ste ju porazili, musíte naprogramovať optimálnu obrannú stratégiu. Avšak Bugzilla je chránená komplexným systémom adaptívnych firewallov.

### Problém
Firewall je reprezentovaný maticou N×M, kde každá bunka obsahuje číslo reprezentujúce silu ochrany. Každých K sekúnd sa konfigurácia firewallu zmení podľa nasledujúcich pravidiel:
1. Každá bunka počíta súčet hodnôt svojich 8 susedov (vodorovne, zvisle a diagonálne)
2. Ak je súčet väčší ako dvojnásobok hodnoty bunky, hodnota bunky sa zvýši o 1
3. Ak je súčet menší ako polovica hodnoty bunky, hodnota bunky sa zníži o 1
4. Inak zostáva hodnota nezmenená

Vašou úlohou je určiť stav firewallu po T sekundách a identifikovať najslabšie miesto (bunku s najnižšou hodnotou).

### Vstup
- Prvý riadok obsahuje štyri celé čísla N, M, K, T
- Nasledujúcich N riadkov obsahuje po M číslach - inicializačná konfigurácia firewallu

### Výstup
- Vypíšte N riadkov po M číslach - stav firewallu po T sekundách
- Na posledný riadok vypíšte súradnice najslabšieho miesta (riadok a stĺpec, číslovanie od 0)

### Príklad
(Príklad nie je uvedený kvôli väčšej komplexnosti úlohy - je to bonusová úloha určená pre skutočných hrdinov Kódlandu!)

## Záver

Mucha ďakuje za vašu pomoc pri záchrane Kódlandu! S každou vyriešenou úlohou sa svet algoritmov a dátových štruktúr stáva opäť bezpečnejším miestom. Nech vás sprevádza logika a efektívnosť!

S pozdravom,
Mucha Tomáš. 

---

*"V Kódlande nie je problém prekážkou, ale príležitosťou ukázať silu algoritmického myslenia!"*
