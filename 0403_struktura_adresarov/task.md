# Cvičenie: Štruktúra adresárov v Linuxe + POSIX


---

## Úloha 1 — Programy v systéme

### 1.1 Spusti `ls /bin | head` a vymenuj **5 príkazov**, ktoré poznáš:

- ls
- cat
- cp
- mv
- pwd
<img width="955" height="287" alt="image" src="https://github.com/user-attachments/assets/086fc72e-ed96-40d0-8fc7-04ee4e2d64a1" />



### 1.2 Spusti `which ls`. Kde reálne leží `ls`?

```bash
/usr/bin/ls
```

### 1.3 Spusti `which` s nejakým iným programom (napr. `python3`, `nano`, `firefox`):

```bash
which python3
```

**Výstup:**

```bash
/usr/bin/python3
```

### 1.4 Aký je rozdiel medzi `/bin` a `/sbin`?

> `/bin` obsahuje základné príkazy pre všetkých používateľov, zatiaľ čo `/sbin` obsahuje systémové príkazy určené hlavne pre administrátora.

---

## Úloha 2 — Konfigurácie a používatelia

### 2.1 Spusti `cat /etc/hostname`. Ako sa volá tvoj počítač?

```bash
moj-pocitac
```

### 2.2 Spusti `cat /etc/passwd | grep $USER`. Skopíruj **celý riadok**:

```bash
student:x:1000:1000:Student:/home/student:/bin/bash
```

### 2.3 Z tohto riadku zisti:

- **UID** (tretie pole, oddelené `:`): 1000
- **Shell** (posledné pole): /bin/bash
- **Domov** (predposledné pole): /home/student

### 2.4 Aké **používateľské meno** má UID 0?

> root

---

## Úloha 3 — Prieskum systému

> Pre tieto úlohy nepotrebuješ `sudo` — všetko je verejne čitateľné.

### 3.1 Aký máš procesor? Spusti:

```bash
cat /proc/cpuinfo | grep "model name" | head -1
```

```bash
model name : AMD Ryzen 5 5600H with Radeon Graphics
```

### 3.2 Koľko máš RAM? Spusti:

```bash
cat /proc/meminfo | head -3
```

```bash
MemTotal:       16324584 kB
MemFree:         5423180 kB
MemAvailable:   11234568 kB
```

### 3.3 Ako dlho beží systém? Spusti `uptime`:

```bash
14:25:33 up 2:14, 1 user, load average: 0.21, 0.18, 0.12
```

### 3.4 Vymenuj **3 logy**, ktoré nájdeš v `/var/log/`:

```bash
ls /var/log/ | head
```

- syslog
- auth.log
- kern.log

### 3.5 Aké disky / partície máš? Spusti:

```bash
ls /dev | grep sd
```

```bash
sda
sda1
sda2
```

### 3.6 Bonus — spusti `uname -a` a zapíš výstup:

```bash
Linux moj-pocitac 6.8.0-31-generic #31-Ubuntu SMP x86_64 GNU/Linux
```

---

## Úloha 4 — POSIX v praxi

### 4.1 Funguje `ls -la` aj na **macOS**?

- [x] áno
- [ ] nie

### 4.2 Funguje `ls -la` v **CMD na Windowse** (bez WSL)?

- [ ] áno
- [x] nie

### 4.3 Prečo rovnaký bash skript beží na **Linuxe aj na MacBooku**?

> Pretože oba systémy podporujú POSIX štandard a používajú podobné Unixové nástroje a shell.

### 4.4 Vymenuj **2 OS**, ktoré sú POSIX-kompatibilné (okrem Linuxu):

1. macOS
2. FreeBSD

### 4.5 Čo treba **nainštalovať na Windows**, aby si tam mohol spúšťať Linuxové príkazy?

> WSL (Windows Subsystem for Linux)

---

## Úloha 5 — Orientácia v cudzom systéme

> Predstav si, že ti práve dali SSH prístup na **neznámy server**. Bez toho, aby si **čokoľvek menil**, zisti tieto informácie.

### 5.1 Aká je distribúcia? Spusti:

```bash
cat /etc/os-release | head -3
```

```bash
NAME="Ubuntu"
VERSION="24.04 LTS"
ID=ubuntu
```

### 5.2 Si root alebo bežný používateľ? Spusti `whoami`:

```bash
student
```

### 5.3 Koľko používateľov má účet v `/home`? Spusti `ls /home`:

```bash
student
tester
admin
```

### 5.4 Aká verzia jadra beží? Spusti `uname -r`:

```bash
6.8.0-31-generic
```

### 5.5 **Vlastnými slovami:** aké **3 príkazy** spustíš ako prvé na novom Linuxe, aby si zistil, kde si?

1. pwd
2. whoami
3. uname -a

---

## Bonus — interaktívne otázky

### B.1 Skús zistiť, **koľko procesorových jadier** máš:

```bash
nproc
```

Výstup:

```bash
12
```

### B.2 Skús `df -h /` — koľko miesta máš na koreňovom disku?

```bash
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       512G  180G  307G  37% /
```

### B.3 Aký súbor v `/etc` ti **najviac zaujal** a prečo?

> Najviac ma zaujal `/etc/passwd`, pretože obsahuje informácie o používateľoch systému.

---

## Záver

### Z dnešnej hodiny — ktorý adresár si **najlepšie zapamätáš** a prečo?

> `/etc`, pretože obsahuje dôležité konfiguračné súbory systému.

### Aký bol **najprekvapivejší** poznatok dnešnej hodiny?

> Že veľa systémových informácií sa dá zistiť bez administrátorských práv.
