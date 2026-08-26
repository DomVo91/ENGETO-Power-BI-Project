# Analýza turnajů a hráčů ATP Tour (2005–2025)
Cílem projektu je interaktivní analýza mužského tenisového okruhu ATP Tour v letech 2005–2025 — vývoje turnajů, jejich obsazenosti a povrchu, úspěšnosti jednotlivých hráčů a jejich zemí, a dotací (prize money) u čtyř grandslamových turnajů. Report je zpracován ve čtyřech propojených stránkách s interaktivním filtrováním a navigací.

Zdrojová data pocházejí z výsledků mužského okruhu ATP Tour za období 2005–2025 (výsledky finále jednotlivých turnajů) (zdroj: veřejně dostupný dataset ATP zápasů (2005–2025), stažený z Kaggle.com) , doplněná o referenční přehled počtu turnajů v jednotlivých letech (zdroj: tenisportal.cz/kalendar/atp) a ručně sestavenou tabulku zemí. Do modelu byly načteny čtyři samostatné zdrojové tabulky:

## Příprava a čištění dat
Před načtením do datového modelu proběhly v Power Query a v samotném Power BI následující úpravy:
1. Odstranění duplicitních řádků ve zdrojové tabulce turnajů (stejný turnaj/datum/vítěz zapsaný vícekrát).
2. Rozdělení jedné široké tabulky na samostatnou faktovou tabulku Turnaje a dimenzní tabulku Players — duplikací dotazu v Power Query, ponecháním pouze sloupců vztahujících se k hráči (jméno, ruka, ID) a odstraněním duplicit podle ID hráče.
3. Sjednocení typu klíčových sloupců (winner_id jako celé číslo) na obou stranách vazeb, aby šlo vytvořit korektní relace.
4. Ruční sestavení referenční tabulky Countries (48 zemí) s přiřazením kontinentu ke každému IOC kódu, pro potřeby mapy a hierarchie.
5. Vytvoření samostatné tabulky Grandslam Winners s dotacemi vítězů grandslamů, propojené na hráče přes winner_id (spolehlivější než párování podle jména).
