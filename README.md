# Šifry

Vibecodovaná webová aplikace (https://prokocku.github.io/CipherSolver/) pro řešení běžných šifer jako morse, semafor, Braille, binárka, trojkovka, polský kříž, svátky a šifrovací mřížka, s možností volného kreslení do čtvrečkované sítě s manipulací (otočení, překlopení, přesun) objektů stejné barvy. Na iOS je možné ji v Safari, pomocí nabídky sdílet, uložit na plochu a tím z ní udělat plnohodnotnou aplikaci s ikonou, která bude fungovat offline, viz https://support.apple.com/cs-cz/guide/iphone/iphea86e5236/26/ios/26. Inspirace šifrovací pomůcky Absolutno https://github.com/vasekp/sifry

---

## Přehled funkcí

### 🔴 Morseova abeceda

Interaktivní zadávání morseovy abecedy pomocí tlačítek tečka (·) a čárka (-). Po krátkém čase bez vstupu se sekvence automaticky potvrdí jako písmeno. Podporuje celou českou abecedu včetně **Ch** (----). Zobrazuje aktuální sekvenci symbolů a rozpoznané písmeno v reálném čase.

Pole **Zakóduj** umožňuje zadat libovolné písmeno a zobrazit jeho morse kód - sekvence se načte do zadávacího pole a lze ji ihned přidat do výstupu.

---

### 🟣 Semafor

Vizuální zobrazení semaforové abecedy pomocí interaktivního terče se dvěma páry paží. Každé klepnutí nastaví polohu levé a poté pravé paže (8 poloh × 8 poloh). Aplikace v reálném čase zobrazuje odpovídající písmeno.

Pole **Zakóduj** automaticky nastaví polohu paží pro zadané písmeno.

---

### 🟡 Braille

Šestibodová mřížka braillova písma (body 1–6). Klepnutím na jednotlivé body se označují aktivní body znaku. Aplikace zobrazuje rozpoznané písmeno nebo speciální znak (mezera, číslo, velké písmeno). Podporuje celou českou abecedu.

Pole **Zakóduj** okamžitě označí správnou kombinaci bodů pro zadané písmeno.

---

### 🔵 Binární kód

Pětibitové binární kódování abecedy (A = 00001, Z = 11010). Zobrazuje binární zápis, desetinnou hodnotu a odpovídající písmeno. Klepnutím se přepínají jednotlivé bity.

Pole **Zakóduj** nastaví bity pro zadané písmeno.

---

### 🔴 Trojková soustava

Kódování abecedy v číselné soustavě o základu 3 (A = 001₃, Z = 222₃). Zadávání pomocí mřížky 3 × 3 - každý sloupec odpovídá jedné cifře (hodnoty 0, 1, 2). Zobrazuje trojkový zápis, desetinnou hodnotu a písmeno.

Pole **Zakóduj** nastaví správnou trojici číslic pro zadané písmeno.

---

### 🟢 Sedmisegmentový displej

Interaktivní zobrazení číslic a písmen na sedmisegmentovém displeji. Klepnutím se označují aktivní segmenty. Rozpoznává písmena i číslice, u nejednoznačných kombinací (S/5, Z/2) zobrazí obě varianty.

Pole **Zakóduj** aktivuje segmenty odpovídající zadanému písmenu nebo číslici.

---

### 🔴 Polský kříž

Klepnutím se aktivují hrany (nahoře, vpravo, dole, vlevo) a tečky (1–3). Klepnutím do rohu se aktivují přilehlé hrany. Aplikace rozpoznává znak a zobrazuje ho v reálném čase. 

Dva režimy přepínatelné tlačítkem:
- **Bez CH** - 25 písmen české abecedy bez Ch
- **S CH** - 26 znaků včetně Ch jako samostatného znaku

Pole **Zakóduj** automaticky nastaví hrany a tečky pro zadané písmeno. Detekuje zadání kombinace **CH** a při aktivním režimu S CH vykreslí správný znak.

---

### 📅 Svátky

Pomocná funkce pro hledání jmenin a svátků v českém kalendáři.

- **Jméno → svátek**: zadáním jména (s automatickým doplňováním) zobrazí datum svátku
- **Datum → jméno**: výběrem dne a měsíce pomocí bubnových roletek zobrazí jméno slavící svátek

---

### 🔲 Mřížková šifra (Grille)

Implementace otočné mřížkové šifry. Čtvercová mřížka o velikosti 4×4 až 8×8. Klepnutím se označují otvory - aplikace automaticky hlídá platnost (každý otvor musí být jedinečný ve všech čtyřech otočeních).

Dva režimy podle pořadí zadávání:

**Šifrování** (otvory → text): nejprve se označí otvory mřížky, poté se píše zpráva. Znaky se automaticky rozmísťují do otvorů v pořadí pro každé otočení (0° → 90° → 180° → 270°). Panel výsledků zobrazuje přečtený text pro každé otočení.

**Dešifrování** (text → otvory): nejprve se vepíše šifrovaný text (limit = počet políček mřížky), poté se označují otvory. Písmena zůstávají na lineárních pozicích, otvory ukazují která jsou viditelná v každém otočení.

---

### 🎨 Kresli

Mřížkový kreslicí nástroj pro tvorbu vzorů, šifer a symbolů.

**Mřížka**: 3×3 až 20×20 políček, velikost se přizpůsobuje obrazovce.

**Paleta barev**: 11 barev + bílá + prázdná (guma).

**Ovládání**:
- 1. klepnutí na prázdné pole → obarví barvou z palety
- 2. klepnutí na pole stejné barvy → označí celý **spojený tvar** (BFS po hranách)
- 3. klepnutí + podržení na označeném tvaru → aktivuje přesun tažením

**Operace s označeným tvarem**:
- **↻ 90°** - otočení o 90° po směru hodinových ručiček
- **⇄ Flip** - horizontální překlopení (zrcadlení)
- **Přesun tažením** - přetažení na libovolnou volnou pozici

Při otočení nebo překlopení, které by způsobilo překryv s objektem jiné barvy, se tvar automaticky posune na nejbližší volnou pozici (spirálové prohledávání od původní polohy).

---

## Společné ovládání

Všechny šifrovací funkce (Morse, Semafor, Braille, Binár, Trojkovka, Segment, Polský kříž) sdílejí stejnou lištu tlačítek:

| Tlačítko | Akce |
|----------|------|
| ⌫ Zpět | Smaže poslední přidaný znak |
| ✓ Písmeno | Přidá aktuálně zobrazený znak do výstupu |
| ␣ Mezera | Přidá mezeru do výstupu |
| ✕ Vše | Smaže celý výstup |

Výstupní pole nahoře zobrazuje sestavený text. Znaky jsou zobrazeny bez mezer, mezera je vizuálně odlišena znakem ·.

---

## Technické informace

- **Typ**: Single-page PWA (Progressive Web App)
- **Závislosti**: žádné - čistý HTML/CSS/JavaScript, bez frameworků
- **Offline podpora**: ano, po přidání na plochu funguje bez připojení
- **Kompatibilita**: iOS Safari 15+, Android Chrome 90+, moderní desktopové prohlížeče

## Instalace

Otevřete aplikaci (https://prokocku.github.io/CipherSolver/) v mobilním prohlížeči a vyberte **Přidat na plochu** (iOS: Sdílet → Přidat na plochu, Android: menu → Přidat na plochu). Po instalaci funguje jako nativní aplikace bez adresního řádku.
