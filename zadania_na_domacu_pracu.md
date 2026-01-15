# Docker - Cvičebné úlohy

## Úloha 1: Prvý kontajner - Spustíme Nginx!

**Čo sa naučíš:** Ako stiahnuť Docker image a spustiť prvý kontajner

### Teória - Čo je to image a container?

- **Image** = "recept" alebo "šablóna" - napríklad inštalačka programu
- **Container** = "bežiaca aplikácia" vytvorená z image - napríklad spustený program

**Analógia:** Image je ako .exe inštalátor, Container je ako nainštalovaný a spustený program.

---

### Krok za krokom

#### Krok 1: Stiahni Nginx image

```bash
docker pull nginx
```

**Čo sa stalo?** Docker stiahol image zo servera (Docker Hub). Trvá to pár sekúnd.

**Vysvetlenie výstupu:**
```
Using default tag: latest  ← používame najnovšiu verziu
latest: Pulling from library/nginx  ← sťahuje sa oficiálny nginx
Digest: sha256:...  ← unikátny identifikátor
Status: Downloaded newer image for nginx:latest
```

---

#### Krok 2: Skontroluj, že máš image

```bash
docker images
```

Mal by si vidieť niečo ako:
```
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
nginx        latest    abc123...      2 days ago     142MB
```

**Čo to znamená?**
- `REPOSITORY` = názov image (nginx)
- `TAG` = verzia (latest = najnovšia)
- `SIZE` = veľkosť na disku

---

#### Krok 3: Spusti kontajner z image

```bash
docker run --name moj-nginx -p 8080:80 -d nginx
```

**Rozober si príkaz po častiach:**
- `docker run` = "spusti nový kontajner"
- `--name moj-nginx` = daj kontajneru meno "moj-nginx" (aby sme ho ľahko našli)
- `-p 8080:80` = **PORT MAPPING**: 
  - Port 8080 na TVOJOM počítači → Port 80 V KONTAJNERI
  - Keď otvoríš `localhost:8080`, spojíš sa s portom 80 v kontajneri
- `-d` = detached mode = beží na pozadí (nedržíš terminál)
- `nginx` = názov image, ktorý použijeme

**Výstup:** Dlhé číslo (napr. `a1b2c3d4...`) = ID kontajnera (kontajner je spustený!)

---

#### Krok 4: Over, že kontajner beží

```bash
docker ps
```

Mal by si vidieť:
```
CONTAINER ID   IMAGE    COMMAND                  PORTS                  NAMES
a1b2c3d4...    nginx    "/docker-entrypoint.…"   0.0.0.0:8080->80/tcp   moj-nginx
```

**Vysvetlenie stĺpcov:**
- `CONTAINER ID` = krátke ID kontajnera
- `IMAGE` = z akého image vznikol
- `PORTS` = `8080->80` znamená "port 8080 na PC je prepojený s portom 80 v kontajneri"
- `NAMES` = meno, ktoré sme dali kontajneru

---

#### Krok 5: Otvor v prehliadači! 

Otvor: `http://localhost:8080`

**Mali by si vidieť:** Uvítaciu stránku Nginx s nápisom "Welcome to nginx!"

**Gratulujem!** Práve si spustil svoju prvú aplikáciu v Dockeri! 

---

#### Krok 6: Pozri si logy kontajnera

```bash
docker logs moj-nginx
```

Uvidíš, čo sa deje vnútri kontajnera - napríklad:
```
/docker-entrypoint.sh: Configuration complete; ready for start up
```

**Refresh stránku v prehliadači** a znova pozri logy - uvidíš nový záznam o HTTP requeste!

---

#### Krok 7: Zastav kontajner

```bash
docker stop moj-nginx
```

**Čo sa stalo?** Kontajner sa pekne zastavil (nie zmazal!). Stránka na `localhost:8080` už nebude fungovať.

**Skontroluj:**
```bash
docker ps
```
Nič tam nie je - žiadne bežiace kontajnery.

**Ale pozor!** Kontajner stále existuje, len je zastavený:
```bash
docker ps -a
```

Teraz uvidíš aj zastavené kontajnery:
```
CONTAINER ID   IMAGE    STATUS                      NAMES
a1b2c3d4...    nginx    Exited (0) 10 seconds ago   moj-nginx
```

`STATUS: Exited` = zastavený, ale stále existuje

---

#### Krok 8: Zmaž kontajner

```bash
docker rm moj-nginx
```

**Teraz je kontajner úplne preč!** Over si:
```bash
docker ps -a
```
Prázdny zoznam = žiadne kontajnery.

**Ale pozor!** Image `nginx` stále máš:
```bash
docker images
```
Stále tam je! Môžeš z neho kedykoľvek vytvoriť nový kontajner.

---

### Čo si sa naučil?

 `docker pull` = stiahni image  
 `docker images` = zobraz stiahnuté images  
 `docker run` = vytvor a spusti kontajner z image  
 `-p` = mapovanie portov (PC:Kontajner)  
 `-d` = spusti na pozadí  
 `--name` = daj kontajneru meno  
 `docker ps` = zobraz bežiace kontajnery  
 `docker ps -a` = zobraz všetky kontajnery (aj zastavené)  
 `docker stop` = zastav kontajner  
 `docker rm` = zmaž kontajner  
 `docker logs` = zobraz logy kontajnera  

---

### Extra: Čo je rozdiel medzi stop a rm?

| Príkaz | Čo sa stane | Analógia |
|--------|------------|----------|
| `docker stop` | Kontajner sa zastaví, ale ešte existuje | Vypol si PC, ale PC stále existuje |
| `docker rm` | Kontajner sa úplne zmaže | Vyhodil si PC do koša |

**Prečo to?** Niekedy chceš kontajner len zastaviť a neskôr ho znova spustiť (`docker start moj-nginx`)!

---

## Úloha 2: Interaktívna práca - Vstúp do kontajnera!

**Čo sa naučíš:** Ako pracovať s kontajnerom "zvnútra" ako s počítačom

### Teória - Čo je interaktívny režim?

Kontajner môžeš spustiť ako "počítač v počítači". Môžeš vstúpiť dovnútra, inštalovať programy, vytvárať súbory - ako keby si mal druhý počítač!

**Analógia:** Je to ako SSH pripojenie na server, ale miesto servera máš kontajner.

---

### Krok za krokom

#### Krok 1: Spusti Ubuntu kontajner interaktívne

```bash
docker run -it ubuntu bash
```

**Čo sa stalo?** Otvorí sa ti terminál VNÚTRI kontajnera! Všimni si, že prompt sa zmenil:
```
root@a1b2c3d4:/#
```

**Rozober si príkaz:**
- `docker run` = spusti kontajner
- `-it` = interaktívny terminál (skratka z `-i -t`)
  - `-i` = interactive (interaktívny)
  - `-t` = tty (terminál)
- `ubuntu` = použijeme Ubuntu image (automaticky sa stiahne, ak ho nemáš)
- `bash` = spusť bash shell

**Si VNÚTRI kontajnera!** To znamená, že všetky príkazy sa teraz vykonávajú v kontajneri, nie na tvojom PC!

---

#### Krok 2: Orientuj sa v kontajneri

Vyskúšaj základné príkazy:

```bash
# Zisti, kde si
pwd
# Výstup: /

# Zobraz súbory
ls
# Uvidíš: bin  boot  dev  etc  home  lib  ...

# Zisti verziu Ubuntu
cat /etc/os-release
# Uvidíš: Ubuntu 22.04 (alebo podobné)
```

**Zaujímavosť:** Hoci si na Windowse/Mac, vnútri kontajnera máš Linux! 

---

#### Krok 3: Aktualizuj package manager

```bash
apt update
```

**Čo sa deje?** Ubuntu sťahuje zoznam dostupných balíčkov. Trvá to pár sekúnd.

**Vysvetlenie:**
- `apt` = Advanced Package Tool = inštalátor programov pre Ubuntu/Debian
- `update` = obnov zoznam dostupných programov

---

#### Krok 4: Nainštaluj programy

```bash
apt install -y curl vim
```

**Čo sme nainštalovali:**
- `curl` = nástroj na sťahovanie súborov z internetu
- `vim` = textový editor
- `-y` = automaticky potvrď inštaláciu (bez pýtania "yes/no")

**Potrvá to pár sekúnd...**

Po dokončení vyskúšaj:
```bash
curl --version
# Mal by si vidieť verziu curl
```

---

#### Krok 5: Vytvor súbor v kontajneri

```bash
echo "Docker je super!" > /tmp/test.txt
```

**Čo sa stalo?** Vytvoril sa súbor `/tmp/test.txt` s textom "Docker je super!"

**Over, že súbor existuje:**
```bash
cat /tmp/test.txt
# Výstup: Docker je super!
```

**Skús aj vim:**
```bash
vim /tmp/test.txt
```
- Stlač `i` pre vstup do režimu úprav
- Pridaj nejaký text
- Stlač `ESC` a napíš `:wq` a `ENTER` pre uloženie a ukončenie

---

#### Krok 6: Opusti kontajner (zastaví sa!)

```bash
exit
```

**Čo sa stalo?**
- Vrátil si sa späť na SVOJ počítač (pozri si prompt - už nie je `root@...`)
- Kontajner sa **zastavil** (lebo bash proces skončil)

**Over si to:**
```bash
docker ps
```
Nič tam nie je - kontajner nebeží.

```bash
docker ps -a
```
Teraz uvidíš zastavený kontajner:
```
CONTAINER ID   IMAGE    STATUS                     
a1b2c3d4...    ubuntu   Exited (0) 5 seconds ago
```

---

#### Krok 7: Spusti kontajner znova a PRIPOJ SA k nemu

Tu je trik! Kontajner existuje, len je zastavený. Môžeš ho znova spustiť:

```bash
# Najprv zisti ID alebo meno kontajnera
docker ps -a

# Spusti ho (nahraď CONTAINER_ID skutočným ID)
docker start a1b2c3d4

# Pripoj sa k bežiacemu kontajneru
docker exec -it a1b2c3d4 bash
```

**Rozdiely:**
- `docker start` = spusti zastavený kontajner
- `docker exec` = vykonaj príkaz v BEŽIACOM kontajneri
- `-it bash` = interaktívne, spusti bash

---

#### Krok 8: Over, že súbor stále existuje!

```bash
cat /tmp/test.txt
```

**TÁÁÁÁDA!**  Súbor je stále tam! Dáta v kontajneri prežili zastavenie!

**Ale POZOR:** Ak kontajner ZMAŽEŠ (`docker rm`), všetky dáta sa stratia! (To napravíme v Úlohe 3 s volumes)

---

#### Krok 9: Upratanie

Opusti kontajner:
```bash
exit
```

Zastav a zmaž kontajner:
```bash
# Zisti ID kontajnera
docker ps -a

# Zastav (ak beží)
docker stop a1b2c3d4

# Zmaž
docker rm a1b2c3d4
```

---

### Čo si sa naučil?

 `-it` = interaktívny terminál (môžeš vstúpiť do kontajnera)  
 `bash` = spusti bash shell v kontajneri  
 `exit` = opusti kontajner (zastaví ho)  
 `docker start` = spusti zastavený kontajner  
 `docker exec -it <id> bash` = pripoj sa k bežiacemu kontajneru  
 Dáta v kontajneri prežijú zastavenie, ale NIE zmazanie!  
 V kontajneri môžeš inštalovať programy a meniť súbory  

---

### Rozdiel medzi run a exec

| Príkaz | Kedy použiť | Čo robí |
|--------|------------|---------|
| `docker run -it ubuntu bash` | Vytvoriť NOVÝ kontajner | Vytvorí nový kontajner a vstúpi doň |
| `docker exec -it <id> bash` | Pripojiť sa k BEŽIACEMU | Pripojí sa k už spustenému kontajneru |

**Analógia:**
- `run` = zapni nový počítač a prihlás sa
- `exec` = prihlás sa k už zapnutému počítaču

---

### Bonus: Pomenovanie kontajnera

Namiesto ID môžeš použiť meno:

```bash
docker run -it --name moj-ubuntu ubuntu bash
# Teraz môžeš použiť:
docker start moj-ubuntu
docker exec -it moj-ubuntu bash
```

Oveľa jednoduchšie, však? 

---

## Úloha 3: Práca s volumes - Uchováme si dáta!

**Čo sa naučíš:** Ako uchovať dáta aj po zmazaní kontajnera pomocou Docker volumes

### Teória - Prečo potrebujeme volumes?

Keď zmažeš Docker kontajner, všetky dáta v ňom sa stratia. To je problém! Predstav si, že máš databázu - nechceš, aby sa dáta stratili pri reštarte kontajnera.

**Riešenie:** Docker volumes - špeciálne úložisko mimo kontajnera, ktoré prežije aj jeho zmazanie.

---

### Krok za krokom

#### Krok 1: Vytvor volume (úložisko)
```bash
docker volume create moje-data
```

**Čo sa stalo?** Docker vytvoril špeciálny priestor na disku, kde môžeš uchovávať súbory.

**Skontroluj, že sa vytvoril:**
```bash
docker volume ls
```
Mal by si vidieť `moje-data` v zozname.

---

#### Krok 2: Spusti nginx kontajner s volume

```bash
docker run -d \
  --name moj-nginx \
  -p 8081:80 \
  -v moje-data:/usr/share/nginx/html \
  nginx:alpine
```

**Rozober si príkaz:**
- `-d` = detached mode (beží na pozadí)
- `--name moj-nginx` = dáme kontajneru meno
- `-p 8081:80` = port 8081 na tvojom PC → port 80 v kontajneri
- `-v moje-data:/usr/share/nginx/html` = **DÔLEŽITÉ!** Pripoj volume `moje-data` do priečinka `/usr/share/nginx/html` v kontajneri
- `nginx:alpine` = použijeme malý nginx image

---

#### Krok 3: Vytvor vlastnú HTML stránku vo volume

Teraz pridáme vlastný súbor do volume:

```bash
docker exec moj-nginx sh -c 'echo "<h1>Ahoj z Docker volume!</h1><p>Tento súbor prežije zmazanie kontajnera </p>" > /usr/share/nginx/html/index.html'
```

**Čo sa stalo?**
- `docker exec` = spusti príkaz v bežiacom kontajneri
- `sh -c '...'` = spusti shell príkaz
- `echo "..." > file.html` = vytvor súbor s týmto obsahom

---

#### Krok 4: Over v prehliadači

Otvor: `http://localhost:8081`

Mal by si vidieť tvoju vlastnú stránku! 

---

#### Krok 5: Teraz príde kúzlo - zmaž kontajner!

```bash
docker stop moj-nginx
docker rm moj-nginx
```

Kontajner je preč! Ale čo dáta? 

---

#### Krok 6: Vytvor NOVÝ kontajner s tým ISTÝM volume

```bash
docker run -d \
  --name novy-nginx \
  -p 8082:80 \
  -v moje-data:/usr/share/nginx/html \
  nginx:alpine
```

Všimni si:
- Nový názov kontajnera: `novy-nginx`
- Nový port: `8082`
- Ale TEN ISTÝ volume: `moje-data` 

---

#### Krok 7: Over v prehliadači znova!

Otvor: `http://localhost:8082`

**TÁÁÁDÁÁÁ!**  Tvoja stránka je stále tam! Volume uchoval dáta aj keď sa kontajner zmazal!

---

### Upratanie

```bash
# Zastav a zmaž kontajner
docker stop novy-nginx
docker rm novy-nginx

# Zmaž volume (len ak už naozaj nechceš dáta)
docker volume rm moje-data
```

---

### Čo si sa naučil?

 Volume je úložisko mimo kontajnera  
 Dáta vo volume prežijú zmazanie kontajnera  
 Viacero kontajnerov môže používať ten istý volume  
 Volumes sú ideálne pre databázy, upload súborov, konfiguračné súbory  

---

### Bonus: Dva typy volumes

1. **Named volumes** (používali sme):
   ```bash
   docker run -v moje-data:/path ...
   ```
   Docker ich spravuje, ukladajú sa do špeciálneho priečinka

2. **Bind mounts** (priamy priečinok z PC):
   ```bash
   docker run -v /cesta/na/pc:/path ...
   ```
   Môžeš editovať súbory priamo na PC a vidia sa v kontajneri!

---

## Úloha 4: Vytvorenie vlastného Docker Image - Tvoja prvá "recepta"!

**Čo sa naučíš:** Ako vytvoriť vlastný Docker image pomocou Dockerfile

### Teória - Čo je Dockerfile?

**Dockerfile** = textový súbor s návodom, ako vytvoriť Docker image.

Je to ako **recept na varenie**:
- Základný image (FROM) = základná surovina (napr. múka)
- Inštrukcie (RUN, COPY) = kroky receptu (pridaj, zamiešaj, peč)
- Výsledok (CMD) = hotové jedlo 

---

### Krok za krokom

#### Krok 1: Vytvor adresár pre projekt

```bash
mkdir moja-webova-stranka
cd moja-webova-stranka
```

---

#### Krok 2: Vytvor HTML súbor

Vytvor súbor `index.html` s týmto obsahom:

```html
<!DOCTYPE html>
<html lang="sk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Moja Docker Stránka</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            background: white;
            padding: 50px;
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            text-align: center;
        }
        h1 {
            color: #667eea;
            margin: 0 0 20px 0;
        }
        .emoji {
            font-size: 80px;
            margin: 20px 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="emoji"></div>
        <h1>Ahoj z môjho Docker kontajnera!</h1>
        <p>Toto je moja prvá vlastná Docker aplikácia </p>
        <p><strong>Vytvoril:</strong> [Tvoje meno]</p>
    </div>
</body>
</html>
```

**Tip:** Zmeň `[Tvoje meno]` na svoje meno!

---

#### Krok 3: Vytvor Dockerfile

V tom istom priečinku vytvor súbor s názvom presne `Dockerfile` (bez prípony!):

```dockerfile
# KROK 1: Začni s nginx obrazom (malá Alpine verzia)
FROM nginx:alpine

# KROK 2: Skopíruj náš HTML súbor do nginx priečinka
COPY index.html /usr/share/nginx/html/index.html

# KROK 3: Povedz Dockeru, že tento kontajner používa port 80
EXPOSE 80

# KROK 4: Príkaz na spustenie (nginx sa spustí automaticky)
# Tento krok je voliteľný, nginx:alpine už má definovaný CMD
```

**Vysvetlenie po riadkoch:**

```dockerfile
FROM nginx:alpine
```
- `FROM` = začni s týmto základným image
- `nginx:alpine` = nginx webserver v malej Alpine Linux verzii (~23 MB!)
- Tento image už má nainštalovaný a nakonfigurovaný nginx

```dockerfile
COPY index.html /usr/share/nginx/html/index.html
```
- `COPY` = skopíruj súbor z počítača do kontajnera
- `index.html` = náš súbor (zdroj)
- `/usr/share/nginx/html/index.html` = kam ho v kontajneri uložiť (cieľ)
- Nginx automaticky zobrazuje súbory z `/usr/share/nginx/html/`

```dockerfile
EXPOSE 80
```
- `EXPOSE` = dokumentácia - tento kontajner používa port 80
- Neznamená to automatický port mapping! Je to len informácia.

---

#### Krok 4: Zbuilduj Docker image

Teraz "uvaríme recept" - vytvoríme image!

```bash
docker build -t moja-stranka:v1 .
```

**Rozober si príkaz:**
- `docker build` = vytvor nový image podľa Dockerfile
- `-t moja-stranka:v1` = TAG (pomenovanie):
  - `moja-stranka` = názov image
  - `v1` = verzia (tag)
- `.` = POZOR! Bodka = "použi Dockerfile v AKTUÁLNOM priečinku"

**Výstup:**
```
[+] Building 2.5s (7/7) FINISHED
 => [1/2] FROM nginx:alpine
 => [2/2] COPY index.html /usr/share/nginx/html/index.html
 => exporting to image
 => => naming to moja-stranka:v1
```

**Čo sa stalo?**
1. Docker stiahol `nginx:alpine` (ak ho ešte nemáš)
2. Vytvoril nový "layer" so skopírovaným súborom
3. Uložil výsledný image s menom `moja-stranka:v1`

---

#### Krok 5: Skontroluj, že image existuje

```bash
docker images
```

Mali by si vidieť:
```
REPOSITORY      TAG       IMAGE ID       SIZE
moja-stranka    v1        xyz123...      23.5MB
nginx           alpine    abc456...      23.4MB
```

**Všimni si:** Tvoj image má len o 0.1 MB viac ako základný nginx! To je kvôli tvojmu HTML súboru.

---

#### Krok 6: Spusti kontajner z tvojho image!

```bash
docker run -d --name moja-web-app -p 8090:80 moja-stranka:v1
```

**Vysvetlenie:**
- `-d` = detached (na pozadí)
- `--name moja-web-app` = meno kontajnera
- `-p 8090:80` = port 8090 na PC → port 80 v kontajneri
- `moja-stranka:v1` = použiť TVOJ image!

---

#### Krok 7: Otvor v prehliadači!

Otvor: `http://localhost:8090`

**Mali by si vidieť:** Tvoju krásnu stránku s veľkým veľrybím emoji! 

**GRATULUJEM!** Práve si vytvoril vlastný Docker image a spustil z neho kontajner!

---

#### Krok 8: Upratanie

```bash
# Zastav kontajner
docker stop moja-web-app

# Zmaž kontajner
docker rm moja-web-app

# (Voliteľne) Zmaž image
docker rmi moja-stranka:v1
```

---

### Čo si sa naučil?

 **Dockerfile** = recept na vytvorenie image  
 `FROM` = základ (base image)  
 `COPY` = skopíruj súbory do image  
 `EXPOSE` = dokumentuj, ktorý port sa používa  
 `docker build -t nazov:tag .` = vytvor image  
 Tvoj vlastný image je znovupoužiteľný!  

---

### Štruktúra projektu

```
moja-webova-stranka/
 Dockerfile         ← Recept na image
 index.html         ← Tvoja webová stránka
```

Po zbuildovaní máš:
- **Image**: `moja-stranka:v1` (šablóna)
- Môžeš z neho vytvoriť koľkokoľvek kontajnerov!

---

### Bonus: Verzie imagov

Môžeš vytvoriť viacero verzií:

```bash
# Verzia 1
docker build -t moja-stranka:v1 .

# Zmeň index.html...

# Verzia 2
docker build -t moja-stranka:v2 .

# "Latest" verzia (štandardný tag)
docker build -t moja-stranka:latest .
# alebo jednoducho:
docker build -t moja-stranka .
```

**Tip:** Verziovanie je dôležité! Vždy vieš vrátiť späť na staršiu verziu.

---

### Rozdiel: Image vs Container

| Image | Container |
|-------|-----------|
| Šablóna/Recept | Spustená aplikácia |
| Statický | Dynamický (beží, mení sa) |
| Môžeš mať 1 image | Z 1 image môžeš mať 10+ containerov |
| `docker build` | `docker run` |
| `docker images` | `docker ps` |

**Analógia:** Image je ako .exe inštalátor, Container je ako spustený program.

---

## Úloha 5: Node.js aplikácia s Dockerfile

**Cieľ:** Vytvoriť a kontajnerizovať jednoduchú Node.js aplikáciu

### Zadanie:
1. Vytvor jednoduchú Node.js aplikáciu:
   - `package.json` s express závislosťou
   - `server.js` - Express server na porte 3000 s jednou route `/`
2. Vytvor `Dockerfile`, ktorý:
   - Použije `node:18-alpine` ako base image
   - Nastaví pracovný adresár `/app`
   - Skopíruje `package*.json` a spustí `npm install`
   - Skopíruje zvyšok aplikácie
   - Exponuje port 3000
   - Spustí aplikáciu pomocou `CMD`
3. Zbuilduj image
4. Spusti kontajner a over funkčnosť

### Starter kód `server.js`:
```javascript
const express = require('express');
const app = express;
const PORT = 3000;

app.get('/', (req, res) => {
  res.send('<h1>Ahoj z Dockeru!</h1>');
});

app.listen(PORT, '0.0.0.0', => {
  console.log(`Server beží na porte ${PORT}`);
});
```

---

## Úloha 6: Multi-stage build

**Cieľ:** Optimalizovať veľkosť Docker image

### Zadanie:
1. Uprav Dockerfile z predchádzajúcej úlohy na multi-stage build:
   - Stage 1 (build): nainštaluj všetky dependencies
   - Stage 2 (production): skopíruj len potrebné súbory a production dependencies
2. Porovnaj veľkosť pôvodného a optimalizovaného image (`docker images`)

### Pomôcka:
```dockerfile
FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install

FROM node:18-alpine
WORKDIR /app
COPY --from=build /app/node_modules ./node_modules
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]
```

---

## Úloha 7: Docker Compose - základy

**Cieľ:** Naučiť sa používať docker-compose

### Zadanie:
1. Vytvor `docker-compose.yml` s dvoma službami:
   - **web**: nginx kontajner s tvojím vlastným HTML
   - **api**: tvoja Node.js aplikácia z predchádzajúcej úlohy
2. Nastav:
   - Port mapping pre obe služby
   - Volumes pre web službu
   - Reštart policy
3. Spusti služby pomocou `docker-compose up`
4. Over, že obe služby bežia
5. Zobraz logy jednej služby
6. Zastav všetky služby

### Pomôcka:
```yaml
version: '3.8'
services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
  api:
    build: ./api
    ports:
      - "3000:3000"
    restart: always
```

---

## Úloha 8: Prepojenie služieb - Frontend volá Backend

**Čo sa naučíš:** Ako spolu komunikujú kontajnery pomocou Docker networking

### Teória - Docker networking

Keď spustíš viacero kontajnerov cez Docker Compose, automaticky sa vytvára **sieť** (network). Kontajnery sa môžu navzájom volať pomocou **názvu služby** namiesto IP adresy!

**Príklad:** Ak máš službu `backend`, frontend ju môže volať na adrese `http://backend:4000`

---

### Krok za krokom

#### Krok 1: Vytvor štruktúru priečinkov

```bash
mkdir docker-app
cd docker-app
mkdir frontend backend
```

Tvoja štruktúra:
```
docker-app/
 docker-compose.yml
 frontend/
    Dockerfile
    package.json
    server.js
 backend/
     Dockerfile
     package.json
     server.js
```

---

#### Krok 2: Backend - API server

**Vytvor `backend/package.json`:**
```json
{
  "name": "backend",
  "version": "1.0.0",
  "dependencies": {
    "express": "^4.18.0",
    "cors": "^2.8.5"
  }
}
```

**Vytvor `backend/server.js`:**
```javascript
const express = require('express');
const cors = require('cors');
const app = express;
const PORT = 4000;

// Povoľ CORS (aby frontend mohol volať backend)
app.use(cors);

// Náš API endpoint
app.get('/api/message', (req, res) => {
  console.log('Backend dostal request!');
  res.json({ 
    message: 'Ahoj z backendu! ',
    timestamp: new Date.toLocaleString('sk-SK')
  });
});

// Ďalší endpoint - náhodné číslo
app.get('/api/random', (req, res) => {
  const randomNum = Math.floor(Math.random * 100);
  res.json({ number: randomNum });
});

app.listen(PORT, '0.0.0.0', => {
  console.log(` Backend beží na porte ${PORT}`);
});
```

**Vytvor `backend/Dockerfile`:**
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package.json ./
RUN npm install
COPY server.js ./
EXPOSE 4000
CMD ["node", "server.js"]
```

---

#### Krok 3: Frontend - Webová stránka

**Vytvor `frontend/package.json`:**
```json
{
  "name": "frontend",
  "version": "1.0.0",
  "dependencies": {
    "express": "^4.18.0"
  }
}
```

**Vytvor `frontend/server.js`:**
```javascript
const express = require('express');
const app = express;
const PORT = 3000;

// HTML stránka s tlačidlami
app.get('/', (req, res) => {
  res.send(`
    <!DOCTYPE html>
    <html>
    <head>
      <title>Frontend App</title>
      <style>
        body {
          font-family: Arial, sans-serif;
          max-width: 600px;
          margin: 50px auto;
          padding: 20px;
          background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
          color: white;
        }
        .container {
          background: rgba(255, 255, 255, 0.1);
          padding: 30px;
          border-radius: 10px;
          backdrop-filter: blur(10px);
        }
        button {
          background: #4CAF50;
          color: white;
          border: none;
          padding: 15px 30px;
          font-size: 16px;
          border-radius: 5px;
          cursor: pointer;
          margin: 10px 5px;
          transition: all 0.3s;
        }
        button:hover {
          background: #45a049;
          transform: scale(1.05);
        }
        #result {
          margin-top: 20px;
          padding: 15px;
          background: rgba(255, 255, 255, 0.2);
          border-radius: 5px;
          min-height: 50px;
          font-size: 18px;
        }
        h1 { margin-top: 0; }
      </style>
    </head>
    <body>
      <div class="container">
        <h1> Docker Komunikácia</h1>
        <p>Frontend kontajner volá Backend kontajner!</p>
        
        <button onclick="getMessage"> Získaj správu</button>
        <button onclick="getRandomNumber"> Náhodné číslo</button>
        
        <div id="result">Klikni na tlačidlo...</div>
      </div>

      <script>
        // Volanie backendu - endpoint /api/message
        async function getMessage {
          document.getElementById('result').innerHTML = '⏳ Načítavam...';
          
          try {
            // DÔLEŽITÉ: Voláme cez náš proxy endpoint
            const response = await fetch('/api/message');
            const data = await response.json;
            
            document.getElementById('result').innerHTML = 
              ' ' + data.message + '<br><small>Čas: ' + data.timestamp + '</small>';
          } catch (error) {
            document.getElementById('result').innerHTML = 
              ' Chyba: ' + error.message;
          }
        }

        // Volanie backendu - endpoint /api/random
        async function getRandomNumber {
          document.getElementById('result').innerHTML = '⏳ Generujem...';
          
          try {
            const response = await fetch('/api/random');
            const data = await response.json;
            
            document.getElementById('result').innerHTML = 
              ' Tvoje náhodné číslo je: <strong>' + data.number + '</strong>';
          } catch (error) {
            document.getElementById('result').innerHTML = 
              ' Chyba: ' + error.message;
          }
        }
      </script>
    </body>
    </html>
  `);
});

// PROXY endpointy - preposielajú requesty na backend
// Toto je dôležité! Frontend kontajner sa pripája na backend kontajner

app.get('/api/message', async (req, res) => {
  try {
    // Dynamický import pre node-fetch
    const fetch = (await import('node-fetch')).default;
    
    // POZOR: používame názov služby 'backend' a port 4000
    const response = await fetch('http://backend:4000/api/message');
    const data = await response.json;
    
    console.log(' Frontend dostal dáta z backendu:', data);
    res.json(data);
  } catch (error) {
    console.error(' Chyba pri volaní backendu:', error);
    res.status(500).json({ error: 'Backend nedostupný' });
  }
});

app.get('/api/random', async (req, res) => {
  try {
    const fetch = (await import('node-fetch')).default;
    const response = await fetch('http://backend:4000/api/random');
    const data = await response.json;
    res.json(data);
  } catch (error) {
    res.status(500).json({ error: 'Backend nedostupný' });
  }
});

app.listen(PORT, '0.0.0.0', => {
  console.log(` Frontend beží na porte ${PORT}`);
});
```

**Vytvor `frontend/Dockerfile`:**
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package.json ./
RUN npm install
RUN npm install node-fetch
COPY server.js ./
EXPOSE 3000
CMD ["node", "server.js"]
```

---

#### Krok 4: Docker Compose - spojíme to dokopy!

**Vytvor `docker-compose.yml` v hlavnom priečinku `docker-app/`:**
```yaml
version: '3.8'

services:
  # Backend služba
  backend:
    build: ./backend
    container_name: moj-backend
    ports:
      - "4000:4000"
    networks:
      - app-network

  # Frontend služba
  frontend:
    build: ./frontend
    container_name: moj-frontend
    ports:
      - "8080:3000"
    depends_on:
      - backend
    networks:
      - app-network

# Vytvoríme vlastnú sieť
networks:
  app-network:
    driver: bridge
```

**Vysvetlenie:**
- `build: ./backend` - zbuilduj Dockerfile z priečinka backend
- `ports: "8080:3000"` - port 8080 na PC → port 3000 v kontajneri
- `depends_on: backend` - najprv spusti backend, potom frontend
- `networks: app-network` - obe služby sú v tej istej sieti = môžu sa volať!

---

#### Krok 5: Spustenie!

V priečinku `docker-app/` spusti:

```bash
docker-compose up --build
```

**Čo sa deje:**
1. Docker zbuilduje oba images (frontend a backend)
2. Vytvorí sieť `app-network`
3. Spustí backend kontajner
4. Spustí frontend kontajner
5. Prepojí ich do siete

Uvidíš logy z oboch kontajnerov:
```
 Backend beží na porte 4000
 Frontend beží na porte 3000
```

---

#### Krok 6: Testovanie!

1. Otvor prehliadač: `http://localhost:8080`
2. Klikni na " Získaj správu" - mala by sa zobraziť správa z backendu!
3. Klikni na " Náhodné číslo" - mal by sa zobraziť náhodné číslo!

**Čo sa stalo?**
- Klikol si na tlačidlo vo frontende
- Frontend zavolal svoj endpoint `/api/message`
- Frontend proxy zavolal backend na `http://backend:4000/api/message`
- Backend odpovedal s JSON dátami
- Frontend zobrazil odpoveď!

---

#### Krok 7: Sleduj logy

V novom terminály:
```bash
docker-compose logs -f frontend
```

Alebo len backend:
```bash
docker-compose logs -f backend
```

Uvidíš, ako sa služby navzájom volajú! 

---

#### Krok 8: Zastavenie

```bash
docker-compose down
```

---

### Čo si sa naučil?

 Služby v Docker Compose sa volajú pomocou **názvu služby**  
 `depends_on` zabezpečí správne poradie spustenia  
 Všetky služby v compose súbore sú automaticky v rovnakej sieti  
 Frontend môže volať `http://backend:4000` namiesto IP adresy  
 Port mapping: externý port (8080) vs. interný port (3000)  

---

### Debug tipy

**Problém:** Frontend nedokáže zavolať backend

**Riešenie:**
1. Over, že obe služby bežia: `docker-compose ps`
2. Skontroluj logy: `docker-compose logs backend`
3. Over názov služby v `docker-compose.yml` - musí sa zhodovať s URL v kóde
4. Skontroluj, či je CORS povolený v backende

**Testovanie backendu priamo:**
```bash
curl http://localhost:4000/api/message
```

Mali by si dostať JSON odpoveď!

---

## Úloha 9: Databáza v Docker Compose

**Cieľ:** Pridať databázu do aplikácie

### Zadanie:
1. Rozšír predchádzajúcu aplikáciu o MongoDB
2. Backend:
   - Pripoj sa na MongoDB
   - Vytvor endpoint `/api/visits` na počítanie návštev
   - Pri každom volaní zvýš počítadlo v databáze a vráť aktuálny počet
3. Frontend:
   - Zobraz počet návštev stránky
4. V `docker-compose.yml`:
   - Pridaj službu `mongodb`
   - Nastav environment premenné pre pripojenie
   - Vytvor volume pre perzistenciu dát
   - Definuj `depends_on` pre backend službu

### Pomôcka pre docker-compose.yml:
```yaml
services:
  mongodb:
    image: mongo:7
    volumes:
      - mongo-data:/data/db
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: heslo123

  backend:
    build: ./backend
    depends_on:
      - mongodb
    environment:
      MONGO_URL: mongodb://admin:heslo123@mongodb:27017/

volumes:
  mongo-data:
```

---

## Úloha 10: Full-stack aplikácia s reverse proxy

**Cieľ:** Vytvoriť kompletnú aplikáciu s nginx ako reverse proxy

### Zadanie:
Vytvor todo aplikáciu s týmto stackom:
1. **Frontend**: React/Vue/vanilla JS stránka
2. **Backend**: Node.js REST API (CRUD operácie pre todos)
3. **Database**: MongoDB pre uloženie todos
4. **Nginx**: Reverse proxy, ktorý:
   - Smeruje `/` na frontend
   - Smeruje `/api/*` na backend
   - Má len jeden exponovaný port (80)

### Štruktúra:
```
projekt/
 docker-compose.yml
 nginx/
    nginx.conf
 frontend/
    Dockerfile
    (HTML/JS súbory)
 backend/
    Dockerfile
    package.json
    server.js
```

### Nginx konfigurácia príklad:
```nginx
server {
    listen 80;
    
    location / {
        proxy_pass http://frontend:3000;
    }
    
    location /api/ {
        proxy_pass http://backend:4000;
    }
}
```

### Požiadavky:
- Všetky služby musia mať vlastný Dockerfile
- Použiť Docker networks
- Databázové dáta musia byť perzistentné
- Aplikácia musí byť dostupná len cez nginx na porte 80

---

## Bonusová úloha: Health checks a restart policies

**Cieľ:** Zabezpečiť robustnosť aplikácie

### Zadanie:
Rozšír úlohu 10 o:
1. Health check endpoints v backend API
2. HEALTHCHECK direktívu v Dockerfile
3. Správne restart policies v docker-compose
4. Limits na CPU a RAM pre každú službu
5. Logging driver konfiguráciu

### Pomôcka:
```dockerfile
HEALTHCHECK --interval=30s --timeout=3s \
  CMD node healthcheck.js || exit 1
```

```yaml
services:
  backend:
    deploy:
      resources:
        limits:
          cpus: '0.5'
          memory: 512M
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:4000/health"]
      interval: 30s
      timeout: 10s
      retries: 3
```

---

## Užitočné príkazy na kontrolu

```bash
# Zobrazenie všetkých images
docker images

# Zobrazenie bežiacich kontajnerov
docker ps

# Zobrazenie všetkých kontajnerov
docker ps -a

# Zobrazenie logov kontajnera
docker logs <container_name>

# Zobrazenie využitia zdrojov
docker stats

# Vyčistenie nepoužívaných images/volumes
docker system prune

# Docker Compose príkazy
docker-compose up -d        # Spustenie v pozadí
docker-compose down         # Zastavenie a odstránenie
docker-compose logs -f      # Sledovanie logov
docker-compose ps           # Stav služieb
docker-compose restart      # Reštart služieb
```

---

## Developed by Tom. Muc. 
