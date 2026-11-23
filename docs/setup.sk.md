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
    Stiahnite si inštalátor pre váš operačný systém z **[bob.ibm.com/download](https://bob.ibm.com/download)**:

    | OS | Inštalátor |
    |---|---|
    | macOS (Apple Silicon) | `.pkg` — mac-ARM |
    | macOS (Intel) | `.pkg` — mac-intel |
    | Windows | `.exe` |
    | Linux (Debian/Ubuntu) | `.deb` |
    | Linux (Red Hat/Fedora) | `.rpm` |

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

- Nainštalovaný **[Node.js](https://nodejs.org) 20 LTS** a **[Python](https://www.python.org/downloads/) 3.11+**
- Nakonfigurovaný **[Git](https://git-scm.com/downloads)** (`user.name` a `user.email`)

---

## Kontrolný zoznam

- [ ] IBMid vytvorené, IBM Bob nainštalovaný a prihlásený
- [ ] `node`, `python3` a `git` fungujú v termináli
- [ ] Git `user.name` a `user.email` nastavené

---

## Užitočné odkazy

| | Odkaz |
|---|---|
| **IBM Bob** | [bob.ibm.com](https://bob.ibm.com) |
| **Dokumentácia** | [ibm.biz/bob-doc](https://ibm.biz/bob-doc) |
| **Blog** | [bob.ibm.com/blog/getting-the-most-out-of-bob](https://bob.ibm.com/blog/getting-the-most-out-of-bob) |
| **Registrácia IBMid** | [ibm.com/account/reg](https://www.ibm.com/account/reg/us-en/signup?formid=urx-19776) |
