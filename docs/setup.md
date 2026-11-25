# Setup — before the lecture

Please prepare your machine using the steps below.

---

## 1 — Get an IBMid

IBM Bob requires an IBMid. **IBMid is free** — create one at [ibm.com/account/reg](https://www.ibm.com/account/reg/us-en/signup?formid=urx-19776) (takes ~2 minutes). If you already have one, skip this step.

## 2 — Start your free trial

Register for the IBM Bob trial (**50 Bobcoins for 30 days**) using the **same IBMid** you created in step 1: [bob.ibm.com/trial](https://bob.ibm.com/trial)

## 3 — Install IBM Bob

IBM Bob is a **standalone IDE** — not a VS Code extension. Download from [bob.ibm.com/download](https://bob.ibm.com/download) and sign in with your IBMid.

=== "IBM Bob IDE (recommended)"
    Download the installer for your OS from **[bob.ibm.com/download](https://bob.ibm.com/download)**.

    Run the installer, follow the wizard, then sign in with your **IBMid** on first launch.

=== "Bob Shell (terminal)"
    Prefer the terminal? Install Bob Shell instead:

    **macOS / Linux**
    ```bash
    curl -fsSL https://bob.ibm.com/download/bobshell.sh | bash
    ```
    **Windows (PowerShell)**
    ```powershell
    powershell -ep Bypass 'irm -Uri "https://bob.ibm.com/download/bobshell.ps1" | iex'
    ```
    Authenticate at `bob.ibm.com/login` when prompted.

## 4 — Other prerequisites

- **[Node.js](https://nodejs.org) 20 LTS** (or a newer LTS), **[Python](https://www.python.org/downloads/) 3.11+** and **[Git](https://git-scm.com/downloads)** installed (see below if you do not have them yet)
- The GitHub repository cloned (see the last step below)

### How to open a terminal

=== "Windows"
    Press the `Win` key, type **PowerShell** and press `Enter`. (Or right-click the Start button and choose **Terminal** / **Windows PowerShell**.)

=== "macOS"
    Press `Cmd` + `Space`, type **Terminal** and press `Enter`. (Or open **Finder → Applications → Utilities → Terminal**.)

=== "Linux"
    Press `Ctrl` + `Alt` + `T` (works in most distributions), or search for **Terminal** in the applications menu.

You can also use the terminal built into IBM Bob: press `` Ctrl+` `` (or choose **Terminal → New Terminal** from the menu).

### Install Node.js, Python and Git (skip what you already have)

First check what is already installed — run in the terminal:

=== "Windows"
    ```powershell
    node --version    # needs v20 or newer
    python --version  # needs 3.11 or newer
    git --version
    ```

=== "macOS / Linux"
    ```bash
    node --version    # needs v20 or newer
    python3 --version # needs 3.11 or newer
    git --version
    ```

**How to read the terminal output:**

| Tool | Required | 🟢 OK | 🔴 Error |
|---|---|---|---|
| **Node.js** | v20+ | Prints e.g. `v20.18.0` | Message *"is not recognized…"* (macOS/Linux: *"command not found"*) |
| **Python** | v3.11+ | Prints e.g. `Python 3.12.4` | Message *"is not recognized…"* or the Microsoft Store opens — installation needed |
| **Git** | version 2.x | Prints e.g. `git version 2.45…` | Message *"is not recognized…"* (macOS/Linux: *"command not found"*) |

If a command is not found or the version is too old, install it:

=== "Windows"
    Open **PowerShell** and use `winget` (included in Windows 10/11):

    ```powershell
    winget install --id Git.Git -e
    winget install --id OpenJS.NodeJS.LTS -e
    winget install --id Python.Python.3.12 -e
    ```

    Then **close and reopen the terminal** so the new `PATH` is picked up.

    `winget` does not work? Download the installers from [nodejs.org](https://nodejs.org/en/download), [python.org](https://www.python.org/downloads/windows/) (tick **Add python.exe to PATH**) and [git-scm.com](https://git-scm.com/downloads/win).

=== "macOS"
    Install [Homebrew](https://brew.sh) first if you do not have it, then:

    ```bash
    brew install git node python@3.12
    ```

    Alternatively, download the installers from [nodejs.org](https://nodejs.org/en/download), [python.org](https://www.python.org/downloads/) and [git-scm.com](https://git-scm.com/downloads).

=== "Linux (Debian / Ubuntu)"
    ```bash
    sudo apt update
    sudo apt install -y git python3 python3-pip python3-venv curl
    ```

    The Node.js in the default `apt` repositories is usually too old, so install it with [nvm](https://github.com/nvm-sh/nvm):

    ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
    ```

    Restart the terminal, then:

    ```bash
    nvm install --lts
    ```

    If `python3 --version` is older than 3.11, install a newer one (for example `sudo apt install python3.12 python3.12-venv`) or use your distribution's documentation.

### Verify the installation

After installing, **close the terminal and open a new one**, then check again that everything is installed:

=== "Windows"
    ```powershell
    node --version    # v20 or newer
    python --version  # 3.11 or newer
    git --version
    ```

=== "macOS / Linux"
    ```bash
    node --version    # v20 or newer
    python3 --version # 3.11 or newer
    git --version
    ```

Each command should print a version number. If you see "command not found" or "is not recognized", the installation did not finish or the terminal was not restarted — repeat the install step for that tool.

??? warning "If the `python` command keeps opening the Microsoft Store (Windows)"
    Windows contains preset "aliases" that block the real Python installation. Turn them off:

    1. Press the `Win` key and type **Manage app execution aliases**.
    2. In the list find **App Installer (python.exe)** and **python3.exe**.
    3. Switch both toggles to **Off**.
    4. In PowerShell, reinstall Python:

        ```powershell
        winget install --force Python.Python.3.12
        ```

    Then close the terminal, open a new one and run `python --version` again.

### Clone the repository

Clone the repository into your **Documents** folder:

=== "Windows"
    In PowerShell:

    ```powershell
    cd $HOME\Documents
    git clone --recurse-submodules https://github.com/stu-fei-bob-lecture/bob-workshop-stu-fei.git
    ```

    The project will be in `C:\Users\<your-name>\Documents\bob-workshop-stu-fei`.

=== "macOS"
    ```bash
    cd ~/Documents
    git clone --recurse-submodules https://github.com/stu-fei-bob-lecture/bob-workshop-stu-fei.git
    ```

    The project will be in `/Users/<your-name>/Documents/bob-workshop-stu-fei`.

=== "Linux"
    ```bash
    cd ~/Documents
    git clone --recurse-submodules https://github.com/stu-fei-bob-lecture/bob-workshop-stu-fei.git
    ```

    The project will be in `/home/<your-name>/Documents/bob-workshop-stu-fei`. If you have no `Documents` folder, create it first with `mkdir -p ~/Documents`.

---

## Checklist before the lecture

Tick every step you have completed successfully.

- [ ] **1. IBMid account registered**<br>
  <small>You have created a student/personal IBM account.</small>
- [ ] **2. Free trial activated (50 Bobcoins)**<br>
  <small>You have activated the free trial at [bob.ibm.com/trial](https://bob.ibm.com/trial).</small>
- [ ] **3. IBM Bob IDE installed**<br>
  <small>The IBM Bob app is installed and signed in to your account.</small>
- [ ] **4. Verified: Node.js v20+ works**<br>
  <small>`node --version` prints v20 or newer.</small>
- [ ] **5. Verified: Python 3.11+ works**<br>
  <small>`python3 --version` (on Windows `python --version`) prints 3.11 or newer.</small>
- [ ] **6. Verified: Git works**<br>
  <small>`git --version` prints a Git version number.</small>
- [ ] **7. Project cloned and ready**<br>
  <small>The repository is cloned into your Documents folder.</small>

---

## Resources

| | Link |
|---|---|
| **IBM Bob** | [bob.ibm.com](https://bob.ibm.com) |
| **Documentation** | [ibm.biz/bob-doc](https://ibm.biz/bob-doc) |
| **Blog** | [bob.ibm.com/blog/getting-the-most-out-of-bob](https://bob.ibm.com/blog/getting-the-most-out-of-bob) |
| **IBMid sign-up** | [ibm.com/account/reg](https://www.ibm.com/account/reg/us-en/signup?formid=urx-19776) |
