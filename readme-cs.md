# md2web

**md2web** je mini CMS systém, který z jednoho Markdown souboru vytvoří krásně navržený a plně funkční web s pokročilými funkcemi. Napište obsah do jednoho souboru `.md` a md2web se postará o vše ostatní — víceúrovňová struktura stránek, navigace, sidebar, barevné motivy a další.

---

## Obsah

- [Funkce](#funkce)
- [Začínáme](#začínáme)
- [Psaní obsahu](#psaní-obsahu)
  - [Více stránek ze sekcí](#více-stránek-ze-sekcí)
  - [Dvouúrovňová navigace](#dvouúrovňová-navigace)
  - [Sidebar](#sidebar)
  - [Interní odkazy](#interní-odkazy)
  - [Critic Markup — sledování revizí](#critic-markup--sledování-revizí)
- [Pokročilá konfigurace](#pokročilá-konfigurace)
- [Vícejazyčná podpora](#vícejazyčná-podpora)
- [Barevné motivy](#barevné-motivy)
- [Licence](#licence)

---

## Funkce

| Funkce | Popis |
|---|---|
| 📄 **Jeden Markdown soubor** | Celý web žije v jediném souboru `.md` |
| 📑 **Více stránek** | Nadpisy první úrovně `#` se automaticky stávají samostatnými stránkami |
| 🗂️ **Dvouúrovňová navigace** | Nadpisy první a druhé úrovně tvoří dvouúrovňové navigační menu |
| 🗃️ **Sidebar** | Volitelný postranní panel automaticky generovaný z obsahu |
| 🔗 **Interní odkazy** | Propojení sekcí a stránek pomocí standardní Markdown syntaxe |
| ✏️ **Critic Markup** | Vizuální sledování revizí — přidání, smazání a komentáře přímo v textu |
| ⚙️ **Pokročilá konfigurace** | Podrobné nastavení názvu webu, rozvržení, metadat a dalšího |
| 🌍 **Vícejazyčnost** | Vestavěná podpora i18n s možností přidávání vlastních překladů |
| 🎨 **Barevné motivy** | Více vestavěných barevných schémat; snadno přepínejte nebo vytvářejte vlastní |

---

## Začínáme

### Požadavky

- Webový server (Apache, Nginx nebo jakýkoliv hostitel statických souborů) **nebo** jednoduše otevřete soubor lokálně v prohlížeči
- Žádný build krok, žádný Node.js, žádné závislosti k instalaci

### Instalace

1. Naklonujte nebo stáhněte tento repozitář:

   ```bash
   git clone https://github.com/michalradacz/md2web.git
   cd md2web
   ```

2. Umístěte svůj Markdown soubor s obsahem (např. `content.md`) do kořenového adresáře projektu.

3. Otevřete `index.html` v prohlížeči nebo nasaďte složku na jakýkoliv webový hosting.

---

## Psaní obsahu

Vše, co potřebujete k vytvoření kompletního webu, píšete do **jednoho Markdown souboru**. md2web tento soubor přečte a automaticky ho transformuje na víceúrovňový web s navigací.

### Více stránek ze sekcí

Každý **nadpis první úrovně** (`# Nadpis`) v Markdown souboru se stane **samostatnou stránkou** na webu. Návštěvníci mohou mezi stránkami přecházet pomocí automaticky vygenerovaného navigačního menu.

```markdown
# Domů

Vítejte na mém webu!

# O nás

Dozvězte se o nás více.

# Kontakt

Kontaktujte nás.
```

Tento příklad vytvoří tři stránky: *Domů*, *O nás* a *Kontakt*.

### Dvouúrovňová navigace

md2web automaticky vytvoří **dvouúrovňové navigační menu**:

- **Úroveň 1** — nadpisy první úrovně (`#`) tvoří hlavní položky navigace (stránky)
- **Úroveň 2** — nadpisy druhé úrovně (`##`) v rámci každé stránky tvoří položky podnavigace (sekce uvnitř stránky)

```markdown
# Produkty

## Software

Naše softwarová nabídka.

## Hardware

Naše hardwarová nabídka.

# Podpora

## Časté dotazy

Nejčastěji kladené otázky.

## Kontakt

Jak nás kontaktovat.
```

Navigace zobrazí *Produkty* a *Podpora* jako položky první úrovně, každou s vlastním rozbalovacím menu.

### Sidebar

Můžete zapnout **volitelný postranní panel (sidebar)**, který se automaticky naplní obsahem z vašeho Markdown souboru. Sidebar je konfigurovatelný — můžete řídit, které sekce se v něm zobrazí a co zobrazuje (např. obsah stránky, rychlé odkazy nebo doplňkové informace).

Pro přidání obsahu sidebaru použijte k tomu určenou sekci nebo možnost konfigurace (viz [Pokročilá konfigurace](#pokročilá-konfigurace)).

### Interní odkazy

Můžete odkazovat na **libovolný nadpis** na jakékoli stránce pomocí standardní Markdown syntaxe s kotvou. md2web tyto odkazy automaticky vyřeší tak, aby ukazovaly na správnou stránku a správnou pozici pro posouvání, i po rozdělení dokumentu na více stránek.

```markdown
Více podrobností najdete v [našich FAQ](#faq) nebo na [stránce kontaktů](#kontakt).
```

Interní odkazy fungují napříč stránkami — md2web zajistí směrování tak, aby se čtenář dostal na správnou stránku.

### Critic Markup — sledování revizí

md2web podporuje **[Critic Markup](http://criticmarkup.com/)**, odlehčenou syntaxi pro sledování revizí přímo v Markdownu. Umožňuje zobrazit přidané části, smazané části, náhrady, zvýraznění a komentáře přímo v textu vykresleného webu.

| Syntaxe | Význam |
|---|---|
| `{++ vložený text ++}` | Přidání |
| `{-- smazaný text --}` | Smazání |
| `{~~ starý ~> nový ~~}` | Náhrada |
| `{== zvýrazněný text ==}` | Zvýraznění |
| `{>> komentář <<}` | Komentář / poznámka |

**Příklad:**

```markdown
Cena je {--100 Kč--}{++80 Kč++} za kus.
Prosím {==zkontrolujte tuto sekci==}{>>potřebuje ověření faktů<<}.
```

Vykreslený výstup zobrazí revizi vizuálně, takže je snadné přehledně sledovat změny v dokumentaci nebo návrzích obsahu přímo na webu.

---

## Pokročilá konfigurace

md2web podporuje blok **YAML front matter** na začátku Markdown souboru pro celowebovou a stránkovou konfiguraci.

```yaml
---
title: Můj skvělý web
description: Web vytvořený pomocí md2web
language: cs
theme: ocean
sidebar: true
author: Jana Nováková
---
```

### Možnosti konfigurace

| Klíč | Typ | Výchozí | Popis |
|---|---|---|---|
| `title` | řetězec | Název souboru | Název webu zobrazený v záložce prohlížeče a záhlaví |
| `description` | řetězec | — | Meta popis použitý pro SEO |
| `language` | řetězec | `en` | Kód jazyka rozhraní (viz [Vícejazyčná podpora](#vícejazyčná-podpora)) |
| `theme` | řetězec | `default` | Název barevného motivu (viz [Barevné motivy](#barevné-motivy)) |
| `sidebar` | boolean | `false` | Zapnutí nebo vypnutí sidebaru |
| `author` | řetězec | — | Jméno autora zobrazené v patičce stránky |
| `nav_depth` | celé číslo | `2` | Počet úrovní nadpisů zahrnutých do navigace (1 nebo 2) |
| `toc` | boolean | `true` | Zobrazení nebo skrytí obsahu v sidebaru |
| `date_format` | řetězec | `YYYY-MM-DD` | Formát data používaný na celém webu |

### Konfigurace pro konkrétní stránku

Konfiguraci lze nastavit také pro jednotlivé stránky umístěním YAML bloku bezprostředně za nadpis `#` dané stránky:

```markdown
# Poznámky k vydání

---
sidebar: false
toc: false
---

Obsah stránky s poznámkami k vydání…
```

---

## Vícejazyčná podpora

md2web je dodáváno s vestavěnými překlady rozhraní webu (popisky navigace, tlačítek, metadat apod.). Jazyk se nastavuje pomocí klíče `language` v front matter.

### Vestavěné jazyky

| Kód | Jazyk |
|---|---|
| `en` | Angličtina |
| `cs` | Čeština |
| `de` | Němčina |
| `fr` | Francouzština |
| `sk` | Slovenština |

### Vlastní překlady

Chcete-li přidat vlastní jazyk nebo přepsat libovolný existující překlad, vytvořte soubor s překladem v adresáři `lang/`:

```
lang/
├── en.json
├── cs.json
└── muj-jazyk.json   ← váš vlastní jazyk
```

**Formát souboru s překladem** (`lang/muj-jazyk.json`) — hodnoty jsou v cílovém jazyce:

```json
{
  "nav.home": "Domů",
  "nav.top": "Nahoru",
  "search.placeholder": "Hledat…",
  "toc.title": "Obsah",
  "footer.generated": "Generováno pomocí md2web",
  "revision.added": "Přidáno",
  "revision.removed": "Odstraněno",
  "revision.comment": "Komentář"
}
```

Potom uveďte svůj jazyk v front matter:

```yaml
---
language: muj-jazyk
---
```

---

## Barevné motivy

md2web je dodáváno s několika vestavěnými barevnými motivy. Aktivní motiv nastavte v front matter pomocí klíče `theme`.

### Vestavěné motivy

| Název motivu | Popis |
|---|---|
| `default` | Čistý světlý motiv s neutrálními šedými tóny |
| `ocean` | Modrozelená paleta inspirovaná mořem |
| `forest` | Tmavé zelené a zemité tóny |
| `sunset` | Teplé oranžové a červené barvy |
| `night` | Tmavý mód s hlubokým tmavě modrým pozadím |
| `minimal` | Čistě bílé s minimálním stylováním |
| `paper` | Béžové/sépiové tóny připomínající tištěný papír |

### Vlastní motivy

Chcete-li vytvořit vlastní motiv, přidejte CSS soubor do adresáře `themes/`:

```
themes/
├── default.css
├── ocean.css
└── muj-motiv.css   ← váš vlastní motiv
```

Soubor s motivem přepisuje CSS vlastní vlastnosti (CSS custom properties):

```css
/* themes/muj-motiv.css */
:root {
  --color-bg: #fdf6e3;
  --color-text: #333;
  --color-primary: #268bd2;
  --color-secondary: #2aa198;
  --color-accent: #cb4b16;
  --color-nav-bg: #eee8d5;
  --color-nav-text: #657b83;
  --color-sidebar-bg: #fdf6e3;
  --color-code-bg: #eee8d5;
}
```

Potom ho uveďte v front matter:

```yaml
---
theme: muj-motiv
---
```

---

## Licence

Tento projekt je licencován pod [GNU General Public License v3.0](LICENSE).

---

*Vytvořeno s ❤️ pomocí md2web — jednoduchého Markdown CMS.*
