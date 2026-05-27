# Cvičenie: Súborové systémy + monitorovanie procesov


---

## Úloha 1 — Pripojené disky

### 1.1 Spusti `mount | grep "^/dev"`. Vymenuj **disky, ktoré sú pripojené**:

```bash
mount | grep "^/dev"
```

**Výstup:**

```
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sda2 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
```

### 1.2 Spusti `df -T /`. Aký **súborový systém** má tvoj koreňový disk?

```bash
df -T /
```

**Odpoveď (názov FS):** ext4

### 1.3 Spusti `cat /etc/fstab`. Koľko **trvalých pripojení** je tam definovaných (riadky, ktoré nezačínajú `#`)?

```bash
cat /etc/fstab | grep -v "^#" | grep -v "^$" | wc -l
```

**Počet:** 3

### 1.4 Aký je rozdiel medzi `/mnt` a `/media`?

> `/mnt` je určený na dočasné ručné pripojenie diskov administrátorom, zatiaľ čo `/media` slúži na automatické pripojenie vymeniteľných médií (USB kľúče, CD) systémom.

---

## Úloha 2 — Stav diskov

### 2.1 Spusti `df -h`. Aká je **celková veľkosť** tvojho koreňového disku (`/`)?

```bash
df -h
```

**Výstup pre `/`:**

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        25G  6.2G   18G  27% /
```

### 2.2 Z toho istého výstupu — koľko **% je obsadené** na `/`?

**Use%:** 27%

### 2.3 Spusti `du -sh ~`. Koľko zaberá tvoj **domov**?

```bash
du -sh ~
```

**Veľkosť:** 148

### 2.4 Spusti `du -sh ~/* 2>/dev/null`. Ktorý priečinok v home zaberá **najviac**?

```bash
du -sh ~/* 2>/dev/null
```

**Najväčší priečinok:** Downloads 
---

## Úloha 3 — Tvoje procesy

### 3.1 Spusti `ps aux | wc -l`. Koľko procesov **celkom beží** v systéme?

```bash
ps aux | wc -l
```

**Počet procesov:** 142


### 3.2 Spusti `ps aux | grep bash`. Nájdi **svoj `bash`** — aké je jeho **PID**?

```bash
ps aux | grep bash
```

**Tvoje PID `bash`:** 2847


### 3.3 Spusti `ps -p 1`. Aký **proces má PID 1**?

```bash
ps -p 1
```

**Odpoveď:** systemd

### 3.4 Spusti `ps aux --sort=-%mem | head -3`. Ktoré **3 procesy** žerú najviac RAM?

```bash
ps aux --sort=-%mem | head -3
```

1. Xorg
2. cinnamon
3. Web Content (firefox)

---

## Úloha 4 — Live monitoring s `top`

> Spusti `top` a **30 sekúnd sleduj**, ako sa hodnoty menia. Potom ukončenie klávesou **`q`**.

### 4.1 Aké je **`load average`** (prvé číslo — priemer za 1 minútu)?


**Load average (1 min):** 0.42

### 4.2 Stlač **`M`** (veľké M) v `top` na zoradenie podľa pamäte. Aký **proces je na vrchu**?

**Najväčší žrút RAM:** Xorg

### 4.3 Z hlavičky `top` — koľko procesov **celkom beží** (`Tasks: ___ total`)?

**Tasks total:** 141

### 4.4 Z hlavičky `top` — aký je **uptime** systému?

> *(Hľadaj `up X:YY` alebo `up X days`.)*

**Uptime:** up 1:23

---

## Úloha 5 — Zabitie procesu

### 5.1 Spusti **bezpečný** dlho-bežiaci proces na pozadí:

```bash
sleep 600 &
```

**Výstup terminálu** (zapíš PID, ktoré sa vypíše v `[1] _____`):

```
[1] 3142
```

### 5.2 Nájdi proces v `ps aux`:

```bash
ps aux | grep sleep
```

**Tvoje PID procesu `sleep`:** 3142

### 5.3 Zabi proces obyčajným `kill`:

```bash
kill 3142
```

> *(Nahraď `<PID>` číslom z 5.2.)*

### 5.4 Skontroluj, že proces zmizol:

```bash
ps aux | grep sleep
```

**Vidíš ešte riadok so `sleep 600`?**

- [x] nie (proces je preč) ✅

### 5.5 Aký je **rozdiel** medzi `kill <PID>` a `kill -9 <PID>`?

> `kill <PID>` pošle procesu signál SIGTERM, čo mu dá šancu sa slušne ukončiť (uložiť dáta, zatvoriť súbory). `kill -9 <PID>` pošle SIGKILL, ktorý proces okamžite zabije bez možnosti akejkoľvek reakcie — používa sa ak proces nereaguje na bežný kill.

---
