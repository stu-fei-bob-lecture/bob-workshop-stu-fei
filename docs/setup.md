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

- **[Node.js](https://nodejs.org) 20 LTS** and **[Python](https://www.python.org/downloads/) 3.11+** installed
- **[Git](https://git-scm.com/downloads)** configured with `user.name` and `user.email`
- The GitHub repository cloned together with the Galaxium Travels project (included as a submodule):

    ```bash
    git clone --recurse-submodules https://github.com/stu-fei-bob-lecture/bob-workshop-stu-fei.git
    ```

---

## Setup checklist

- [ ] IBMid created, IBM Bob installed and signed in
- [ ] `node`, `python3` and `git` work in the terminal
- [ ] Git `user.name` and `user.email` configured
- [ ] Repository cloned, `galaxium-travels/` folder is not empty

---

## Resources

| | Link |
|---|---|
| **IBM Bob** | [bob.ibm.com](https://bob.ibm.com) |
| **Documentation** | [ibm.biz/bob-doc](https://ibm.biz/bob-doc) |
| **Blog** | [bob.ibm.com/blog/getting-the-most-out-of-bob](https://bob.ibm.com/blog/getting-the-most-out-of-bob) |
| **IBMid sign-up** | [ibm.com/account/reg](https://www.ibm.com/account/reg/us-en/signup?formid=urx-19776) |
