# STU FEI — Beginner Track

Tri laby · spolu ~70 minút · Predchádzajúca skúsenosť s Bobom nie je potrebná

---

## Prehľad tracku

| # | Lab | Čas | Cieľ |
|---|---|---|---|
| B1 | **Preskúmajte režimy a vytvorte uvítaciu aplikáciu STU FEI** | 25 min | Spoznajte tri režimy Boba vytvorením uvítacej stránky s konfetami |
| B2 | **Pripojte a rozšírte Galaxium Travels: lety s prestupmi** | 25 min | Pridajte skutočnú funkciu do full-stack aplikácie postupom Ask → Plan → Agent |
| B3 | **Výber dátumu, zoradenie podľa ceny a rezervačný agent** | 20 min | Tri rýchle vylepšenia, v ktorých Bob rieši UI, logiku a simulovanú AI |

!!! tip "Ako používať túto príručku"
    Každý lab nadväzuje na predchádzajúce. Absolvujte ich v poradí. Každý blok s promptom si môžete skopírovať — kliknite na ikonu kopírovania v pravom hornom rohu ľubovoľného bloku kódu.

---

## Požiadavky

- [ ] Nainštalovaný a prihlásený **IBM Bob IDE** — stiahnite si ho z [bob.ibm.com/download](https://bob.ibm.com/download) (samostatná aplikácia, nie rozšírenie pre VS Code), alebo **Bob Shell**, ak preferujete terminál (`curl -fsSL https://bob.ibm.com/download/bobshell.sh | bash`) — podrobnosti nájdete v časti [Príprava](../setup.md)
- [ ] Nainštalovaný Node.js 20 LTS
- [ ] Nainštalovaný Git
- [ ] Repozitár Galaxium Travels dostupný v `galaxium-travels/` (je súčasťou repozitára workshopu — samostatné klonovanie nie je potrebné)

---

## Lab B1 — Preskúmajte režimy a vytvorte uvítaciu aplikáciu STU FEI

**25 minút** · Skúsenosť s programovaním nie je potrebná

### Čo sa naučíte

Tri režimy Boba — **Ask**, **Plan** a **Agent** — majú každý svoju osobitnú úlohu. Tento lab rozdiel zhmotní tým, že všetky tri použijete na vytvorenie jednej malej aplikácie.

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'primaryColor': '#1a56db', 'primaryTextColor': '#ffffff', 'primaryBorderColor': '#1a56db', 'lineColor': '#6b7280', 'mainBkg': '#1a56db', 'nodeBorder': '#1a56db', 'clusterBkg': '#1e3a5f', 'titleColor': '#ffffff', 'edgeLabelBackground': 'transparent'}}}%%
flowchart LR
    A["🔍 Režim Ask\nPoznajte režimy"] --> P["📋 Režim Plan\nNavrhnite aplikáciu"] --> G["⚙️ Režim Agent\nVytvorte ju"]
    classDef node fill:#1a56db,color:#fff,stroke:#1a56db
    class A,P,G node
```

### Prečo používať tri režimy namiesto jedného?

Rozdelenie práce medzi režimy je **osvedčený vývojársky postup**, nie len zvláštnosť Boba. Každý režim má zámerne iné oprávnenia na nástroje:

- **Ask** môže čítať súbory, ale nemôže zapisovať ani spúšťať príkazy — bezpečný na skúmanie a otázky
- **Plan** môže čítať súbory a zapisovať dokumentáciu (napr. súbory plánu `.md`), ale nemôže spúšťať príkazy shellu — ideálny na návrh bez vedľajších účinkov
- **Agent** môže čítať, zapisovať aj spúšťať príkazy — plná sila autonómneho programátorského agenta

Použitie správneho režimu pre každú fázu robí kroky Boba **predvídateľnými, kontrolovateľnými a vratnými**. Keď prototypujete v režime Ask, nič sa nepokazí. Keď finalizujete v režime Agent, každá akcia je zámerná.

### Krok 1 — Režim Ask: pochopte režimy

1. Vytvorte na svojom počítači nový prázdny priečinok (napr. `stu-fei-welcome`)
2. Spustite **IBM Bob** a otvorte tento priečinok ako svoj projekt (**File → Open Folder…**, vyberte priečinok)
3. Vyberte režim **Ask**
4. Odošlite tento prompt:

```
Aké sú tri vstavané režimy Boba, aké nástroje každý z nich povoľuje
a kedy mám ktorý použiť?
```

**Pozorujte:** Bob poskytne jasnú odpoveď, ale nemôže vytvárať súbory ani spúšťať príkazy.
Režim Ask je zámerne len na čítanie — ideálny na otázky a skúmanie.

!!! info "Ask = len na čítanie"
    Režim Ask nemá skupiny nástrojov `edit` ani `command`. Bob vidí váš kód, ale nemôže ho meniť. Je to najbezpečnejší režim, keď chcete odpovede bez rizika neúmyselných zmien.

### Krok 2 — Režim Plan: navrhnite aplikáciu

1. V bočnom paneli prepnite na režim **Plan**
2. Odošlite tento prompt:

```
Naplánuj aplikáciu v React + Vite s názvom "STU FEI Welcome".
Mala by zobrazovať celoobrazovkovú uvítaciu stránku s:
- Pozadím v modrej farbe IBM Bob (#0f62fe)
- Bielym textom: "Welcome to STU FEI"
- Podnadpisom: "Powered by IBM Bob"
- Výbuchom konfiet po načítaní stránky

Konfety musia používať iba CSS keyframe animácie a čistý JS (vanilla JS) — žiadne npm balíky.
Priprav zoznam komponentov, prístup k CSS animáciám a štruktúru súborov.
```

**Pozorujte:** Bob vytvorí podrobný plán — názvy komponentov, stratégiu CSS, strom súborov. Režim Plan vie navrhovať, ale nie implementovať.

!!! info "Plan = návrh bez vedľajších účinkov"
    Režim Plan môže čítať súbory a zapisovať dokumentáciu (napr. poznámky k plánu alebo súbory `.md`), ale nemôže spúšťať príkazy shellu ani meniť zdrojový kód. Použite ho na spoločný návrh s Bobom ešte pred samotnou implementáciou. Dobrý prompt na plánovanie vás ušetrí nákladných zmien smeru uprostred práce.

!!! tip "Prečo plánovať pred vytváraním?"
    Ak Bobovi najprv zadáte plánovanie, získate možnosť posúdiť a upresniť postup. Ak plán nevyzerá dobre, opravíte ho tu — nie potom, čo Bob napíše 15 súborov. Je to rovnaká disciplína ako písanie návrhového dokumentu pred otvorením editora.

### Krok 3 — Režim Agent: implementácia

1. Prepnite na režim **Agent**
2. Odošlite tento prompt:

```
Implementuj plán, ktorý si práve navrhol.
Vytvor kostru aplikácie Vite + React, vytvor komponent WelcomeScreen,
použi modrú farebnú schému IBM Bob a implementuj konfety
pomocou CSS keyframe animácií na náhodne umiestnených elementoch <span>,
ktoré vytvorí malá pomocná funkcia vo vanilla JS (žiadne npm balíky).
```

**Pozorujte:**

- Bob spustí `npm create vite` a nainštaluje závislosti
- Vytvorí `src/WelcomeScreen.tsx` s uvítacím rozložením
- Vytvorí `src/confetti.ts` — generuje ~40 elementov `<span>` s náhodnými farbami, pozíciami, rotáciou a postupne oneskorenými CSS animáciami
- Pridá CSS konfiet do `src/index.css`

!!! tip "Skontrolujte volania nástrojov Boba pred schválením"
    Bob si pred spustením príkazov ako `npm create vite` vyžiada povolenie. **Prečítajte si navrhovaný príkaz skôr, než kliknete na Approve.** Je to najbezpečnejší návyk: rozumieť tomu, čo Bob v každom kroku robí. Navrhovaný príkaz môžete pred schválením aj upraviť.

### Krok 4 — Spustite ju

```bash
npm run dev
```

Otvorte `http://localhost:5173` — po načítaní by mali vybuchnúť konfety.

!!! tip "Konfety sa neobjavili?"
    Požiadajte Boba v režime Agent: `"Konfety sa nezobrazujú — skontroluj confetti.ts a či sa zhodujú názvy CSS animácií."`

    **Toto je bežný iteratívny vývoj.** Prvé spustenia málokedy fungujú dokonale. Bob prečíta chybu, diagnostikuje ju a opraví — často jednou správou. Postup je: spustiť → pozorovať → vrátiť chybu Bobovi → opakovať.

### Krok 5 — Reflexia: začnite novú úlohu

Prepnite späť na režim **Ask**, kliknutím na **+ New task** začnite novú konverzáciu a odošlite:

```
Čo by sa stalo, keby som sa pokúsil spustiť npm install
v režime Ask alebo Plan?
```

!!! info "Prečo začať novú úlohu?"
    Bob má **kontextové okno s veľkosťou 270 000 tokenov** — veľký, ale konečný rozpočet. Každé prečítanie súboru, volanie nástroja a odpoveď spotrebúvajú tokeny. Začatie novej úlohy tlačidlom **+ New task** vám dá čistý štart pre novú tému. Stará konverzácia zostane v histórii, ale už nespotrebúva váš rozpočet.

    **Odporúčaný postup:** Začnite novú úlohu, keď meníte tému, dokončíte fázu vytvárania alebo spozorujete, že Bob začína strácať niť či si protirečí. Úlohy držte zamerané a krátke.

---

## Lab B2 — Pripojte a rozšírte Galaxium Travels: lety s prestupmi

**25 minút** · Vyžaduje dokončený Lab B1

### Čo sa naučíte

Galaxium Travels je oficiálna demo aplikácia IBM Bob — full-stack rezervačný systém pre medziplanetárne lety. Spustíte `/init`, aby Bob získal hlboký kontext, a potom naplánujete a implementujete skutočnú funkciu naprieč celým stackom.

### Prečo je `/init` dôležitý

Veľké jazykové modely sú **bezstavové** — každá nová konverzácia začína s nulovou pamäťou o kódovej základni. Bez explicitného kontextu musí Bob pri každej úlohe znova objavovať každý súbor od nuly, čo plytvá tokenmi a vedie k nekonzistentným výsledkom.

`/init` to rieši tak, že prehľadá projekt a zapíše štruktúrovaný súhrn `AGENTS.md`, ktorý Bob automaticky číta na začiatku každej konverzácie. Je to ekvivalent úvodnej dokumentácie pre Boba — napísaná raz, použitá všade.

### Požiadavky

- [ ] Dokončený Lab B1 (režimy sú pochopené)
- [ ] Nainštalovaný Python 3.8+
- [ ] Nainštalovaný a nakonfigurovaný Git — pozrite si [Príprava](../setup.md#4-dalsie-poziadavky)

### Krok 1 — Otvorte projekt a spustite aplikáciu

1. Naklonujte repozitár workshopu (preskočte, ak ho už máte): [github.com/stu-fei-bob-lecture/bob-workshop-stu-fei](https://github.com/stu-fei-bob-lecture/bob-workshop-stu-fei)

    ```bash
    git clone --recurse-submodules https://github.com/stu-fei-bob-lecture/bob-workshop-stu-fei.git
    ```

    `galaxium-travels/` je git submodul, preto je `--recurse-submodules` povinné — bez neho bude priečinok prázdny. Ak ste už naklonovali bez neho, spustite v repozitári `git submodule update --init`.

2. V **IBM Bob** otvorte priečinok `galaxium-travels/` z naklonovaného repozitára (`bob-workshop-stu-fei/galaxium-travels`) ako svoj projekt (**File → Open Folder…**)
3. Otvorte vstavaný terminál (**Terminal → New Terminal**) — spustí sa v priečinku `galaxium-travels/`
4. Spustite:

```bash
./start.sh
```

Tento terminál nechajte otvorený — beží v ňom server. Na ostatné veci použite druhý terminál.

Otvorte `http://localhost:5173` — mali by ste vidieť rozhranie rezervácie letov Galaxium.

!!! note "Start.sh trvá ~2 minúty"
    Nainštaluje závislosti Pythonu a Node a spustí oba servery. Frontend beží na `:5173`, backend na `:8001`.

### Krok 2 — Spustite `/init`

1. Uistite sa, že priečinok `bob-workshop-stu-fei/galaxium-travels` je stále otvorený v **IBM Bob** (z kroku 1)
2. Prepnite na režim **Agent**
3. Napíšte `/init` a odošlite

**Čo sa stane:** Bob prečíta celú kódovú základňu a potom zapíše:

- `AGENTS.md` v koreni repozitára — prehľad projektu, kľúčové obmedzenia, mapu súborov
- `.bob/rules-agent/AGENTS-agent.md` — kontext pre režim Agent (štruktúra súborov, konvencie pomenovania)
- `.bob/rules-plan/AGENTS-plan.md` — kontext pre režim Plan (architektúra, obmedzenia)
- `.bob/rules-ask/AGENTS-ask.md` — kontext pre režim Ask (prehľad projektu, slovník pojmov)

Ak `AGENTS.md` už existuje (napr. z predchádzajúceho spustenia `/init`), Bob ho **prepíše** novým prehľadaním. Všetky ručné doplnky, ktoré chcete zachovať, presuňte pred opätovným spustením do samostatného súboru pravidiel v `.bob/rules/`.

**Prečítajte si `AGENTS.md` spoločne.** Bob zistil:

- Tri služby (frontend / backend / hold service)
- Vlastné tokeny Tailwindu (`space-dark`, `space-blue`, `cosmic-purple`, …)
- Integráciu FastMCP na `/mcp`
- Kľúčové obmedzenie: **každý nový backendový endpoint potrebuje REST handler A zodpovedajúci MCP nástroj**

!!! info "AGENTS.md — pamäť Boba medzi reláciami"
    Bob automaticky vkladá `AGENTS.md` do každej novej konverzácie. To znamená:

    - Noví členovia tímu získajú kontext projektu okamžite po `git clone` a otvorení Boba
    - Nikdy nemusíte opakovať ten istý prompt „takto tento projekt funguje“
    - Pravidlá a obmedzenia objavené v jednej relácii sa prenášajú do ďalšej

    **Spustite `/init` znova vždy, keď pridáte nové moduly, zmeníte štruktúru adresárov alebo zaúčate nových členov tímu.**

!!! tip "AGENTS.md môžete upravovať ručne"
    Automatické prehľadanie je len východisko. Pridajte vlastné riadky: konvencie nasadenia, obchodné pravidlá, veci, ktoré sa z prehľadania nedajú odvodiť. Chápte ho ako živý úvodný dokument vášho tímu.

### Krok 3 — Naplánujte funkciu prestupov

Prepnite na režim **Plan** a odošlite:

```
Naplánuj funkciu "lety s prestupmi" pre Galaxium Travels.

Prestup je zastávka medzi východiskovým a cieľovým miestom,
s názvom planéty a dĺžkou prestupu v minútach.

Funkcia vyžaduje:
1. Typ LayoverStop pridaný do typov TypeScriptu a modelov v Pythone
2. FlightRoute upravený tak, aby obsahoval zoznam prestupových zastávok (môže byť prázdny)
3. Výpočet ceny, ktorý pridá 10 % za každú prestupovú zastávku
4. Upravenú kartu trasy v UI, ktorá zobrazuje prestupové zastávky priamo v karte

Dodržiavaj existujúce konvencie z AGENTS.md.
```

**Pozorujte:** Bob vytvorí plán naprieč všetkými tromi vrstvami bez zapísania jediného súboru.

!!! tip "V promptoch pre Plan vždy odkazujte na konvencie z AGENTS.md"
    Pokyn Bobovi „follow the existing AGENTS.md conventions“ je silná skratka. Keďže AGENTS.md popisuje vzory vášho projektu, Bob ich použije automaticky — konvencie pomenovania, umiestnenie súborov, povinné MCP nástroje popri REST endpointoch — bez toho, aby ste museli všetko opakovať.

### Krok 4 — Implementujte

Začnite **+ New task** a pred odoslaním tohto promptu prepnite na režim **Agent**. Implementačný kontext tak zostane čistý a oddelený od diskusie o plánovaní:

```
Implementuj plán prestupov. Dodržiavaj konvencie z AGENTS.md:
- Pre každú novú backendovú trasu pridaj REST endpoint A zodpovedajúci MCP nástroj
- V Pythone používaj snake_case, pre typy v TypeScripte PascalCase
- Pre všetky nové prvky UI použi existujúce Tailwind tokeny space
```

**Sledujte, ako Bob pracuje naprieč:**

- `booking_system_backend/models.py` — model `LayoverStop`
- `booking_system_backend/server.py` — aktualizovaná schéma trasy
- `booking_system_frontend/src/types/` — TypeScript typ `LayoverStop`
- `booking_system_frontend/src/pages/Flights.tsx` — aktualizovaná karta trasy
- Nový komponent `LayoverBadge`

!!! info "FastMCP a registrácia MCP nástrojov"
    Galaxium Travels používa `FastMCP`, ktorý **automaticky sprístupňuje všetky trasy FastAPI ako MCP nástroje** — nemusíte ich registrovať ručne. Obmedzenie „REST + MCP nástroj“ v AGENTS.md odráža tento vzor: pridanie REST endpointu stačí a MCP nástroj sa objaví automaticky. Bob môže napriek tomu vygenerovať explicitný dekorátor `mcp.tool()`; funguje oboje a explicitná forma neskôr uľahčuje prispôsobenie schémy nástroja.

**Reštartujte backend a obnovte prehliadač** — teraz sa zobrazujú trasy s viacerými zastávkami.

!!! info "Prečo začať novú úlohu pre implementáciu?"
    Začatie novej úlohy pred implementáciou v režime Agent drží diskusiu o plánovaní mimo implementačného kontextu. Model sa tak nesnaží zosúladiť rozpracované plány so skutočnými súbormi, ktoré píše — častá príčina odchýlok. Čistý kontext → sústredené výsledky.

### Krok 5 — Overte

V režime **Ask**:

```
Dodržiava nová implementácia prestupov obmedzenie z AGENTS.md,
že každá backendová trasa má REST handler aj MCP nástroj?
```

Toto je **dôveruj, ale preveruj** — zdravý návyk pri každom agentickom nástroji. Režim Ask dokáže auditovať kódovú základňu bez rizika náhodnej zmeny.

---

## Lab B3 — Výber dátumu, zoradenie podľa ceny a rezervačný agent

**20 minút** · Vyžaduje dokončený Lab B2 · Aplikácia musí bežať

### Čo sa naučíte

Tri rýchle vylepšenia ukazujúce, ako Bob zvláda vstup z UI, logiku zoradenia a vzor simulovaného AI agenta — všetko bez opustenia kódovej základne Galaxium. Každé vylepšenie ukazuje inú techniku promptovania.

### Vylepšenie 1 — Výber dátumu (režim Agent)

```
Pridaj výber dátumu odletu do vyhľadávacieho formulára letov Galaxium.
Použi natívny HTML <input type="date">.
Po výbere dátumu filtruj výsledky vyhľadávania na strane klienta
tak, aby sa zobrazili iba lety dostupné v daný deň.
Žiadna externá knižnica na prácu s dátumami.
```

**Prečo tento prompt funguje:** Je **konkrétny** (natívny `<input type="date">`), uvádza **obmedzenie** (žiadna knižnica) a popisuje **očakávané správanie** (filtrovanie po výbere). Vágne prompty ako „add a date thing“ dávajú nekonzistentné výsledky. Buďte presní ako vstupné pole dobre navrhnutého formulára.

Overte, že sa vstup pre dátum zobrazuje a zoznam výsledkov sa po výbere aktualizuje.

### Vylepšenie 2 — Prepínač zoradenia podľa ceny (režim Agent)

```
Pridaj tlačidlo na prepínanie zoradenia do výsledkov vyhľadávania letov Galaxium.
Kliknutím sa prepína medzi "Price: Low to High" a "Price: High to Low".
Zoradenie implementuj celé v stave komponentu — žiadna externá knižnica na zoradenie.
```

Overte, že kliknutie na tlačidlo zmení poradie výsledkov.

!!! tip "Použite `@/path/to/file` na poskytnutie presného kontextu Bobovi"
    Ak Bob potrebuje kontext z konkrétneho súboru, použite vo svojom prompte `@/booking_system_frontend/src/pages/Flights.tsx` namiesto popisovania súboru. Bob si ho prečíta priamo. Je to rýchlejšie než vkladanie kódu a vyhnete sa chybám pri kopírovaní.

### Vylepšenie 3 — Medziplanetárny rezervačný agent (Plan → Agent)

Toto vylepšenie zámerne sleduje vzor **Plan → nová úloha → Agent** — je zložitejšie a profituje z predchádzajúceho návrhu.

Najprv prepnite na režim **Plan**:

```
Navrhni komponent simulovaného AI rezervačného agenta s názvom BookingAgent.
Prijíma textový vstup v prirodzenom jazyku (napr. "cheapest route to Europa")
a vráti 3 najlepšie zodpovedajúce trasy z existujúcich dát o letoch
pomocou porovnávania kľúčových slov a rozpoznania zámeru podľa ceny/rýchlosti.
Žiadne skutočné volanie LLM — čistá logika v JavaScripte na strane klienta.
```

Potom kliknite na **+ New task** a prepnite na režim **Agent**:

```
Implementuj komponent BookingAgent, ktorý si práve naplánoval.
- Textové pole + tlačidlo na odoslanie
- Z textu vyparsuj kľúčové slová cieľa a zámer "cheapest"/"fastest"
- Podľa toho filtruj a zoraď pole letov
- Zobraz 3 najlepšie zodpovedajúce trasy ako karty
```

**Vyskúšajte:** napíšte `"cheapest route to Europa"` — mali by sa zobraziť 3 najlacnejšie lety na Europu.

!!! tip "Požiadajte Boba, aby to vysvetlil"
    Prepnite do režimu Ask: `"Ako BookingAgent rozhoduje, ktoré lety zodpovedajú zámeru 'cheapest'? Preveď ma logikou krok za krokom."`

    **Je to výborný návyk.** Použitie režimu Ask na kontrolu výstupu režimu Agent vám pomáha pochopiť kód, ktorý Bob napísal — aby ste ho vlastnili, nielen spúšťali.

---

## Kľúčové vzory z tohto tracku

| Vzor | Prečo na ňom záleží |
|---|---|
| **Ask → Plan → Agent** | Každá fáza má správne oprávnenia. Navrhujte bez vedľajších účinkov, potom implementujte s istotou. |
| **Medzi fázami začnite + New task** | Čistý kontext = sústredené výsledky. Zabráni tomu, aby odchýlky z plánovania kontaminovali implementáciu. |
| **Na novom projekte vždy najprv spustite `/init`** | Dáva Bobovi trvalý kontext bez opätovného čítania súborov v každej relácii. |
| **Po veľkých zmenách spustite `/init` znova** | Udržiava AGENTS.md aktuálny, ako projekt rastie. |
| **Skontrolujte pred schválením** | Prečítajte si každý navrhovaný príkaz pred kliknutím na Approve. Bob vie príkazy aj upraviť. |
| **Buďte v promptoch konkrétni** | Pomenujte súbor, funkciu, obmedzenie. Vágne prompty dávajú vágny kód. |
| **Používajte odkazy `@/file/path`** | Dajte Bobovi presný súbor, ktorý potrebuje, namiesto jeho popisovania. |

---

## Čo ďalej?

| Ak chcete ísť hlbšie… | Vyskúšajte |
|---|---|
| Tímové štandardy a automatizácia SDLC | [Intermediate Track](intermediate.md) |
| Vlastné režimy, MCP a pokročilá konfigurácia Boba | [Expert Track](expert.md) |
