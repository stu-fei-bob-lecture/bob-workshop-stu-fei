# Príprava — pred prednáškou

Pripravte si svoj počítač podľa nasledujúcich krokov.

---

## 1 — Získajte IBMid

IBM Bob vyžaduje IBMid. **IBMid je bezplatné** — vytvorte si ho na [ibm.com/account/reg](https://www.ibm.com/account/reg/us-en/signup?formid=urx-19776) (trvá to ~2 minúty). Ak už IBMid máte, tento krok preskočte.

## 2 — Aktivujte bezplatnú skúšobnú verziu

Zaregistrujte sa na skúšobnú verziu IBM Bob (**50 Bobcoinov na 30 dní**) pomocou **rovnakého IBMid**, ktoré ste vytvorili v kroku 1: [bob.ibm.com/trial](https://bob.ibm.com/trial)

## 3 — Nainštalujte IBM Bob

IBM Bob je **samostatné IDE** — nie rozšírenie pre VS Code. Stiahnite si ho z [bob.ibm.com/download](https://bob.ibm.com/download) a pri prvom spustení sa prihláste pomocou svojho IBMid.

=== "IBM Bob IDE (odporúčané)"
    Stiahnite si inštalátor pre váš operačný systém z **[bob.ibm.com/download](https://bob.ibm.com/download)**.

    Spustite inštalátor, postupujte podľa sprievodcu a pri prvom spustení sa prihláste pomocou **IBMid**.

=== "Bob Shell (terminál)"
    Preferujete prácu v termináli? Nainštalujte si Bob Shell:

    **macOS / Linux**
    ```bash
    curl -fsSL https://bob.ibm.com/download/bobshell.sh | bash
    ```
    **Windows (PowerShell)**
    ```powershell
    powershell -ep Bypass 'irm -Uri "https://bob.ibm.com/download/bobshell.ps1" | iex'
    ```
    Po výzve sa autentifikujte na `bob.ibm.com/login`.

## 4 — Ďalšie požiadavky

- Nainštalovaný **[Node.js](https://nodejs.org) 20 LTS** (alebo novší LTS), **[Python](https://www.python.org/downloads/) 3.11+** a **[Git](https://git-scm.com/downloads)** (ak ich ešte nemáte, pozrite nižšie)
- Naklonovaný repozitár z GitHubu spolu s projektom Galaxium Travels (pozrite posledný krok nižšie)

### Ako otvoriť terminál

=== "Windows"
    Stlačte kláves `Win`, napíšte **PowerShell** a stlačte `Enter`. (Alebo kliknite pravým tlačidlom na tlačidlo Štart a vyberte **Terminal** / **Windows PowerShell**.)

=== "macOS"
    Stlačte `Cmd` + `Space`, napíšte **Terminal** a stlačte `Enter`. (Alebo otvorte **Finder → Applications → Utilities → Terminal**.)

=== "Linux"
    Stlačte `Ctrl` + `Alt` + `T` (funguje vo väčšine distribúcií) alebo vyhľadajte **Terminal** v ponuke aplikácií.

Môžete použiť aj terminál priamo v IBM Bob: stlačte `` Ctrl+` `` (alebo v menu vyberte **Terminal → New Terminal**).

### Inštalácia Node.js, Pythonu a Gitu (preskočte, čo už máte)

Najprv skontrolujte, čo už máte nainštalované — v termináli spustite:

```bash
node --version    # potrebná verzia v20 alebo novšia
python3 --version # potrebná verzia 3.11 alebo novšia (vo Windows: python --version)
git --version
```

Ak príkaz nebol nájdený alebo je verzia príliš stará, nainštalujte ho:

=== "Windows"
    Otvorte **PowerShell** a použite `winget` (súčasť Windows 10/11):

    ```powershell
    winget install --id Git.Git -e
    winget install --id OpenJS.NodeJS.LTS -e
    winget install --id Python.Python.3.12 -e
    ```

    Potom **zatvorte a znovu otvorte terminál**, aby sa načítala nová premenná `PATH`. Vo Windows sa Python spúšťa príkazom `python` (alebo `py`), nie `python3`.

    Nemáte `winget`? Stiahnite si inštalátory z [nodejs.org](https://nodejs.org/en/download), [python.org](https://www.python.org/downloads/windows/) (zaškrtnite **Add python.exe to PATH**) a [git-scm.com](https://git-scm.com/downloads/win).

=== "macOS"
    Ak nemáte [Homebrew](https://brew.sh), nainštalujte ho a potom spustite:

    ```bash
    brew install git node python@3.12
    ```

    Alternatívne si stiahnite inštalátory z [nodejs.org](https://nodejs.org/en/download), [python.org](https://www.python.org/downloads/) a [git-scm.com](https://git-scm.com/downloads).

=== "Linux (Debian / Ubuntu)"
    ```bash
    sudo apt update
    sudo apt install -y git python3 python3-pip python3-venv curl
    ```

    Node.js v predvolených repozitároch `apt` býva príliš starý, preto ho nainštalujte cez [nvm](https://github.com/nvm-sh/nvm):

    ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
    ```

    Reštartujte terminál a potom spustite:

    ```bash
    nvm install --lts
    ```

    Ak je `python3 --version` staršia ako 3.11, nainštalujte novšiu (napr. `sudo apt install python3.12 python3.12-venv`) alebo postupujte podľa dokumentácie vašej distribúcie.

### Overenie inštalácie

Po inštalácii **zatvorte terminál a otvorte nový**, potom znova skontrolujte, že je všetko nainštalované:

```bash
node --version    # v20 alebo novšia
python3 --version # 3.11 alebo novšia (vo Windows: python --version)
git --version
```

Každý príkaz by mal vypísať číslo verzie. Ak sa zobrazí „command not found“ alebo „is not recognized“, inštalácia sa nedokončila alebo ste terminál nereštartovali — zopakujte inštaláciu príslušného nástroja.

### Naklonovanie repozitára

Naklonujte repozitár do priečinka **Documents**:

=== "Windows"
    V PowerShelli:

    ```powershell
    cd $HOME\Documents
    git clone --recurse-submodules https://github.com/stu-fei-bob-lecture/bob-workshop-stu-fei.git
    ```

    Projekt bude v `C:\Users\<vaše-meno>\Documents\bob-workshop-stu-fei`.

=== "macOS"
    ```bash
    cd ~/Documents
    git clone --recurse-submodules https://github.com/stu-fei-bob-lecture/bob-workshop-stu-fei.git
    ```

    Projekt bude v `/Users/<vaše-meno>/Documents/bob-workshop-stu-fei`.

=== "Linux"
    ```bash
    cd ~/Documents
    git clone --recurse-submodules https://github.com/stu-fei-bob-lecture/bob-workshop-stu-fei.git
    ```

    Projekt bude v `/home/<vaše-meno>/Documents/bob-workshop-stu-fei`. Ak priečinok `Documents` nemáte, najprv ho vytvorte príkazom `mkdir -p ~/Documents`.

---

## Kontrolný zoznam pred prednáškou

Zaškrtni všetky kroky, ktoré už máš úspešne hotové.

- [ ] **1. Zaregistrovaný IBMid účet**<br>
  <small>Máš vytvorený študentský/osobný IBM účet.</small>
- [ ] **2. Aktivované bezplatné kredity (50 Bobcoinov)**<br>
  <small>Na adrese [bob.ibm.com/trial](https://bob.ibm.com/trial) máš aktivovaný bezplatný skúšobný balík.</small>
- [ ] **3. Nainštalované prostredie IBM Bob IDE**<br>
  <small>Aplikácia IBM Bob je nainštalovaná a prihlásená k tvojmu účtu.</small>
- [ ] **4. Overené: Node.js v20+ funguje**<br>
  <small>Príkaz `node --version` vypisuje verziu v20 alebo novšiu.</small>
- [ ] **5. Overené: Python 3.11+ funguje**<br>
  <small>Príkaz `python3 --version` (vo Windows `python --version`) vypisuje verziu 3.11 alebo novšiu.</small>
- [ ] **6. Overené: Git funguje**<br>
  <small>Príkaz `git --version` vypisuje číslo verzie Gitu.</small>
- [ ] **7. Projekt naklonovaný a pripravený**<br>
  <small>Repozitár je naklonovaný v priečinku Documents.</small>

---

## Užitočné odkazy

| | Odkaz |
|---|---|
| **IBM Bob** | [bob.ibm.com](https://bob.ibm.com) |
| **Dokumentácia** | [ibm.biz/bob-doc](https://ibm.biz/bob-doc) |
| **Blog** | [bob.ibm.com/blog/getting-the-most-out-of-bob](https://bob.ibm.com/blog/getting-the-most-out-of-bob) |
| **Registrácia IBMid** | [ibm.com/account/reg](https://www.ibm.com/account/reg/us-en/signup?formid=urx-19776) |
