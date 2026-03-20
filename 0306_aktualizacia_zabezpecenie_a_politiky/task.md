# Cvičenie 6: Aktualizácia, zabezpečenie OS Windows a systémové politiky

## Úloha 1: Windows Update

### 1.1 Pojmy

1. Čo je Windows Update a na čo slúži?

slúži na sťahovanie a inštaláciu aktualizácií systému, bezpečnostných opráv, ovládačov a nových funkcií.

2. Čo znamená označenie KB (napr. KB5034441)?

KB znamená Knowledge Base. Je to identifikačné číslo konkrétnej aktualizácie a

3. Vysvetlite rozdiel medzi aktualizáciou kvality (Quality) a aktualizáciou funkcií (Feature):

Quality update – menšie aktualizácie, ktoré opravujú chyby a bezpečnostné problémy.

Feature update – veľké aktualizácie, ktoré pridávajú nové funkcie alebo menia verziu systému Windows.

4. Prečo je nebezpečné neaktualizovať systém? Uveďte reálny príklad:

Neaktualizovaný systém môže obsahovať bezpečnostné chyby, ktoré môžu hackeri zneužiť.
ransomware útok WannaCry z roku 2017

### 1.2 Praktická časť


| Otázka | Odpoveď |
|--------|---------|
| Je systém aktuálny? (Áno/Nie) |Nie |
| Koľko aktualizácií čaká na inštaláciu? |4 |
| Dátum poslednej nainštalovanej aktualizácie |13.3. 2026 |
| KB číslo poslednej aktualizácie |KB507195 |



| Otázka | Odpoveď |
|--------|---------|
| Koľko aktualizácií vidíte vo výpise? |21 |
| HotFixID poslednej aktualizácie | KB5071982 |



| Otázka | Odpoveď |
|--------|---------|
| Stav služby (Spustená/Zastavená) |Spustená |
| Typ spustenia (Automaticky/Ručne/Zakázané) |ručne |

5. Čo by sa stalo, keby ste typ spustenia služby Windows Update zmenili na "Zakázané"?

vypne sa

## Úloha 2: Zabezpečenie Windows

### 2.1 Pojmy

1. Čo je Windows Defender?

 je antivírusový program zabudovaný v systéme Windows, ktorý chráni počítač pred vírusmi, malwarem a inými hrozbami.

2. Aký je rozdiel medzi rýchlym a úplným skenovaním?

Rýchle skenovanie kontroluje najdôležitejšie miesta systému.

Úplné skenovanie kontroluje všetky súbory a disky v počítači.

3. Čo je firewall a na čo slúži? Vysvetlite vlastnými slovami:

Firewall je bezpečnostný systém, ktorý kontroluje sieťovú komunikáciu a blokuje nebezpečné alebo neautorizované pripojenia k počítaču.

5. Windows firewall má 3 profily – vymenujte ich a napíšte, kedy sa ktorý aktivuje:

-Doménový: aktivuje sa, keď je počítač pripojený do firemnej domény.
-Súkromný: používa sa v dôveryhodných sieťach, napríklad doma.
-Verejný: používa sa v nedôveryhodných sieťach, napríklad na verejnej Wi-Fi.

6. Čo znamená príkaz `wf.msc` a čo `firewall.cpl`? Aký je medzi nimi rozdiel?

 wf.msc otvorí pokročilé nastavenia Windows Firewallu.
 firewall.cpl otvorí základné nastavenia firewallu v Ovládacom paneli.

### 2.2 Praktická časť

**Otvorte** Zabezpečenie systému Windows a zapíšte stav:

| Komponent | Stav (OK / Varovanie / Chyba) |
|-----------|-------------------------------|
| Ochrana pred vírusmi a hrozbami | OK |
| Firewall a ochrana siete | OK |

**Spustite v CMD:** `netsh advfirewall show allprofiles state`

| Profil | Stav (ON/OFF) |
|--------|---------------|
| Doménový | ON |
| Súkromný | ON |
| Verejný | ON |

6. Prečo by ste nemali firewall vypínať, aj keď vám niečo nefunguje? Čo by ste mali urobiť namiesto toho?

 Firewall chráni počítač pred nebezpečnými pripojeniami z internetu.
Namiesto jeho vypnutia by ste mali vytvoriť výnimku alebo pravidlo pre konkrétnu aplikáciu.

------------------------

## Úloha 3: Lokálne politiky – gpedit.msc

### 3.1 Pojmy

1. Čo je gpedit.msc a na čo slúži?

gpedit.msc je nástroj na správu lokálnych skupinových politík vo Windows.
Umožňuje správcovi nastavovať bezpečnostné pravidlá a obmedzenia systému.

3. Aký je rozdiel medzi lokálnou politikou a doménovou politikou?

Lokálna politika platí iba pre jeden počítač.
Doménová politika sa nastavuje na serveri a platí pre všetky počítače v doméne.

5. Čo robí príkaz `gpupdate /force`? Kedy ho musíte spustiť?

Tento príkaz okamžite aktualizuje a aplikuje všetky skupinové politiky. Spúšťa sa po zmene politík.

6. Čo robí príkaz `gpresult /r`?

Zobrazí zoznam aktívnych skupinových politík, ktoré sú aplikované na počítač alebo používateľa.

7. Vysvetlite, čo je politika uzamknutia účtu a proti akému typu útoku chráni:

Politika uzamknutia účtu zablokuje účet po určitom počte
nesprávnych pokusov o prihlásenie. Chráni proti brute force útokom.

3.2 Praktická časť – politiky hesiel

### 3.2 Praktická časť – politiky hesiel

**Otvorte** `gpedit.msc` → Konfigurácia počítača → Nastavenia systému Windows → Nastavenia zabezpečenia → Politiky účtov → Politika hesiel

Zapíšte aktuálne hodnoty:

| Politika | Aktuálna hodnota |
|----------|-------------------|
| Minimálna dĺžka hesla | 8 znakov |
| Maximálny vek hesla | 42 dní |
| Heslo musí spĺňať požiadavky na zložitosť | Zapnuté |
| Vynútiť históriu hesiel | 24 hesiel |

6. Prečo je dôležité vynútiť históriu hesiel? Čo by sa stalo bez nej?

Zabraňuje používateľovi opakovane používať staré heslá. Bez tejto politiky by
mohol používateľ stále meniť heslo napríklad medzi dvoma rovnakými heslami.

### 3.3 Praktická časť – uzamknutie účtu a CMD

**Nastavte politiku uzamknutia účtu:**

1. Prah uzamknutia → **5 pokusov**
2. Potvrďte dobu uzamknutia **30 minút**
3. Spustite `gpupdate /force`
 - [ ]  Hotovo

**Vyskúšajte zakázať CMD:**

Cesta: Konfigurácia používateľa → Šablóny pre správu → Systém → Zabrániť prístupu k príkazovému riadku

1. Zapnite politiku → spustite `gpupdate /force` → skúste otvoriť CMD

| Otázka | Odpoveď |
|--------|---------|
| Čo sa stalo po pokuse otvoriť CMD? | Zobrazila sa správa, že prístup k príkazovému riadku je zablokovaný správcom. |
| Funguje PowerShell naďalej? (Áno/Nie) | Áno |

2. **DÔLEŽITÉ:** Vráťte politiku späť na **Nekonfigurované** a spustite `gpupdate /force`!

- [ ] Vrátené

-----------------------

## Bonusové scenáre (nepovinné)

### Scenár 1: Ransomware útok

*Kolega zavolá, že na obrazovke sa objavila správa: "Vaše súbory boli zašifrované."*

1. Čo mal mať zapnuté, aby sa tomu predišlo? (2 veci)

Antivírus (Windows Defender) a pravidelné aktualizácie Windows Update.

2. Aký typ skenovania by ste spustili na ostatných PC?

Úplné skenovanie systému.

### Scenár 2: Nový zamestnanec

*Šéf chce: žiadny CMD, žiadne registre, heslo aspoň 10 znakov.*

1. Aký nástroj použijete? (_____.msc)

gpedit.msc

2. Napíšte celú cestu v gpedit.msc k politike minimálnej dĺžky hesla:

 Konfigurácia počítača → Nastavenia systému Windows → Nastavenia zabezpečenia → Politiky účtov → Politika hesiel → Minimálna dĺžka hesla

3. Napíšte celú cestu k politike zakázania CMD:

 Konfigurácia používateľa → Šablóny pre správu → Systém → Zabrániť prístupu k príkazovému riadku

4. Aký príkaz spustíte po zmene politík?

 gpupdate /force

### Scenár 3: Podozrivá aktivita

*V logoch je 50 neúspešných prihlásení na jeden účet za 10 minút.*

1. O aký typ útoku ide?

 Brute force útok.

2. Aká politika by tomu zabránila a aké hodnoty by ste nastavili?

 Politika uzamknutia účtu – napríklad uzamknutie po 5 neúspešných pokusoch na 30 minút.
