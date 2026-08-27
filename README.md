# Analýza turnajů a hráčů ATP Tour (2005–2025)
Cílem projektu je interaktivní analýza mužského tenisového okruhu ATP Tour v letech 2005–2025 — vývoje turnajů, jejich povrchu, úspěšnosti jednotlivých hráčů a jejich zemí, a dotací (prize money) u čtyř grandslamových turnajů. Report je zpracován ve čtyřech propojených stránkách s interaktivním filtrováním a navigací.

Zdrojová data pocházejí z výsledků mužského okruhu ATP Tour za období 2005–2025 (výsledky finále jednotlivých turnajů) (zdroj: veřejně dostupný dataset ATP zápasů (2005–2025), stažený z Kaggle.com), doplněný o referenční přehled počtu turnajů v jednotlivých letech (zdroj: tenisportal.cz/kalendar/atp) a ručně sestavenou tabulku zemí. Do modelu byly načteny čtyři samostatné zdrojové tabulky:

# Příprava a čištění dat
Před načtením do datového modelu proběhly v Power Query a v samotném Power BI následující úpravy:
1. Odstranění duplicitních řádků ve zdrojové tabulce turnajů (stejný turnaj/datum/vítěz zapsaný vícekrát).
2. Rozdělení jedné široké tabulky na samostatnou faktovou tabulku Turnaje a dimenzní tabulku Players — duplikací dotazu v Power Query, ponecháním pouze sloupců vztahujících se k hráči (jméno, ruka, ID) a odstraněním duplicit podle ID hráče.
3. Sjednocení typu klíčových sloupců (winner_id jako celé číslo) na obou stranách vazeb, aby šlo vytvořit korektní relace.
4. Ruční sestavení referenční tabulky Countries (48 zemí) s přiřazením kontinentu ke každému IOC kódu, pro potřeby mapy a hierarchie.
5. Vytvoření samostatné tabulky Grandslam Winners s dotacemi vítězů grandslamů, propojené na hráče přes winner_id (spolehlivější než párování podle jména).

Datový rozsah pokrývá roky 2005–2025, celkem 1 364 odehraných finále na čtyřech typech povrchu (Hard 755, Clay 454, Grass 137, Carpet 18).

# Struktura reportu
## Stránka 1 — Úvodní stránka
Titulní stránka s názvem projektu, logem ATP Tour a čtyřmi navigačními tlačítky (Úvodní stránka, Přehled, Hráči, Grandslamy) pro přechod na jednotlivé stránky reportu.
## Stránka 2 — Přehled
KPI karty (celkem titulů, unikátní vítězové, průměrný věk výherce), přehled počtu titulů podle zemí, donut graf rozdělení titulů podle povrchu (Hard/Clay/Grass/Carpet) a mapa vyhraných turnajů podle zemí. Stránka obsahuje slicer a dvě záložky (bookmarks) — Přehled a Mapa — pro přepínání mezi standardním pohledem a zvětšenou mapou.
## Stránka 3 — Hráči
Průměrné pořadí v žebříčku a průměrný věk hráčů jako KPI karty, mapa/dlaždice kontinentů, žebříček top hráčů podle počtu titulů (pruhový graf), donut graf podle dominantní ruky (pravák/levák) a graf vývoje průměrného, minimálního a maximálního věku vítěze v čase (2005–2025). Obsahuje slicer pro filtrování.
## Stránka 4 — Grandslamy
Karty s průměrnou dotací podle kategorie grandslamu (Australian Open, French Open, US Open, Wimbledon), donut graf podílu titulů podle hráče a maticová tabulka s vývojem dotací jednotlivých grandslamů podle roku (2005–2025) včetně součtových řádků. Obsahuje slicery pro filtrování.
