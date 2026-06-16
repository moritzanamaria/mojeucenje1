# 📘 Frontend Developer — Mali vodič

---

## 🕒 Verzioniranje izvornog koda (Version Control)

### Što je i zašto?

Sustav koji prati povijest promjena u datotekama — kao "Time Machine" za programere.

- Nema straha od grešaka — lako vraćanje na stariju verziju
- Nema duplanja mapa (projekt_v1, projekt_FINAL, projekt_FINAL2...)
- Praćenje tko je, kada i što promijenio
- Osnova timskog rada na kodu

### Vrste sustava

**Centralizirani (CVS, Subversion/SVN):**
- Jedan repozitorij na poslužitelju
- Svaki korisnik radi s radnom kopijom

**Distribuirani (Git, Mercurial):**
- Svaki korisnik ima **cijeli repozitorij** lokalno
- Može raditi offline, sinkronizira se s poslužiteljem

### 📅 Kratka povijest

| Godina | Sustav |
|---|---|
| 1986 | CVS (centralizirani) |
| 2000 | Apache Subversion / SVN (centralizirani) |
| 2005 | **Git** + Mercurial (distribuirani) |
| 2005 | GitHub Desktop, SourceTree, SmartGit... |

### 🐙 Git & GitHub Pojmovi

| Pojam | Značenje |
|---|---|
| **Git** | Alat na računalu — distribuirani VCS, open source, GPL2 |
| **GitHub** | Web platforma za hosting Git repozitorija |
| **GitHub Desktop** | GUI klijent za Git (bez terminala) |
| **Repository** | Mapa projekta s cijelom poviješću promjena |
| **Radna kopija** | Lokalna kopija koda na računalu |

### 🛠️ Osnovne Git naredbe

```bash
git clone <url>        # Kopira repozitorij s interneta na računalo
git add .              # Priprema sve promijenjene datoteke za commit
git commit -m "poruka" # Snimka stanja — sprema promjene lokalno
git push               # Šalje commite na GitHub
git pull               # Preuzima promjene s GitHuba na računalo
```

### 💻 Pokretanje alata (Windows)

- **File Explorer:** `Windows + E`
- **Command Prompt:** `Windows + R` → upiši `cmd` → Enter


## 🌐 HTML — HyperText Markup Language

HTML je **označiteljski jezik** koji definira značenje i strukturu sadržaja mrežnih stranica. Sastoji se od oznaka (tagova) kojima se označavaju tekst, slike i drugi sadržaji.

### 🏗️ Anatomija HTML dokumenta

```html
<!DOCTYPE html>          <!-- Oznaka tipa dokumenta (HTML5) -->
<html lang="hr">         <!-- Korijen dokumenta (ima samo head i body) -->
  <head>                 <!-- Nevidljivi dio: metapodaci -->
    <meta charset="UTF-8">
    <title>Naslov</title>
  </head>
  <body>                 <!-- Vidljivi dio stranice -->

  </body>
</html>
```

- HTML dokument se sprema kao `.html` datoteka u **UTF-8** kodnoj stranici
- `index.html` je datoteka koju poslužitelj dostavlja ako je naveden samo naziv direktorija
- **Preporučeni editor:** Microsoft Visual Studio Code

### 🧩 Anatomija HTML elementa

```html
<element atribut="vrijednost">
  Sadržaj elementa
</element>

<!-- Element bez djece (self-closing) -->
<drugelement />

<!-- Primjer 1 -->
<p title="Osijek, 07. prosinca">Osjećam se odlično.</p>

<!-- Primjer 2 — ugniježđeni elementi -->
<div class="popis">
  <ul id="lista">
    <li>Stavka 1</li>
  </ul>
</div>
```

- Oznake su sastavljene od `<`, naziva elementa i `>`
- Zatvaranje: `</element>`
- Atributi idu unutar otvarajuće oznake: `naziv="vrijednost"` (dvostruki navodnici)

### 📋 Atributi HTML elemenata

**Globalni atributi** (rade na svim elementima): `id`, `class`, `style`, `title`, `lang`, `hidden`, `data-*`, `tabindex`...

**Atributi događaja**: `onclick`, `onmouseover`, `onkeypress`, `onsubmit`...

**Obavezni atributi** na određenim elementima:
```html
<img src="slike/logo.png" alt="Logo" />
<a href="stranica.html">Stranica</a>
```

HTML ima **127 elemenata** — puni popis: [developer.mozilla.org/en-US/docs/Web/HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)

### ✅ Validacija HTML-a

Provjera ispravnosti: [https://validator.w3.org](https://validator.w3.org)

---

## 🎨 CSS — Cascading Style Sheets

CSS je jezik kojim opisujemo **vizualni izgled** HTML elemenata (boje, fontovi, razmaci, raspored...).

### 📝 Sintaksa CSS-a

```css
selektor {
  svojstvo: vrijednost;
  svojstvo2: vrijednost2;
}

/* Lista selektora */
h1, h2 {
  color: navy;
}

/* Potomak > direktno dijete */
#podrucje > .unos {
  float: left;
}
```

> Na kraju zadnjeg svojstva tehnički ne treba `;`, ali preporučuje se pisati uvijek.

### 🎯 Vrste CSS selektora

| Vrsta | Primjer | Opis |
|---|---|---|
| Univerzalni | `* { color: green; }` | Svi elementi |
| Element | `ul { list-style: none; }` | Svi `<ul>` elementi |
| ID | `#podrucje { width: 960px; }` | Element s tim ID-om (jedinstven) |
| Klasa | `.unos { padding: 20px; }` | Svi elementi s tom klasom |
| Potomak | `#podrucje .unos { }` | `.unos` unutar `#podrucje` (bilo gdje duboko) |
| Dijete | `#podrucje > .unos { }` | `.unos` koji je **direktno** dijete `#podrucje` |
| Rođak | `h2 ~ p { }` | Svi `<p>` nakon `<h2>` na istoj razini |
| Susjedni rođak | `h2 + p { }` | Samo prvi `<p>` odmah nakon `<h2>` |
| Atribut | `input[type="text"] { }` | `<input>` s tim atributom |
| Pseudo klasa | `a:hover { color: red; }` | Stanje elementa |
| Pseudo element | `.dodaj:before { content: "+"; }` | Generirani sadržaj |

### 💧 Kaskadnost (The Cascade)

**Cascading** = kaskadno, vodopadno — primjenjuje se **zadnje dodijeljeno** svojstvo.

Redoslijed prioriteta (od najnižeg prema najvišem):

```
Vanjska CSS datoteka  →  HTML <style> element  →  Inline style atribut (JavaScript)
```

Svojstva se **ne mijenjaju** u originalnoj datoteci — redefiniraju se kaskadno.

### 📐 Načini pisanja CSS-a

**1. Vanjska CSS datoteka** (preporučeno):
```html
<head>
  <link rel="stylesheet" href="stil.css">
</head>
```

**2. HTML `<style>` element** (u `<head>`):
```html
<style>
  body { color: purple; }
</style>
```

**3. Inline CSS** (direktno na elementu):
```html
<p style="color: purple; padding-left: 11em;">Lorem ipsum</p>
```

**4. JavaScript:**
```js
document.getElementById('tekst').style.color = 'tomato';
```

### 📏 CSS jedinice mjera

**Apsolutne:**

| Jedinica | Naziv | Ekvivalent |
|---|---|---|
| `px` | Pikseli | 1px = 1/96 incha |
| `pt` | Točke | 1pt = 1/72 incha |
| `cm` | Centimetri | 1cm = 96px/2.54 |
| `mm` | Milimetri | 1mm = 1/10 cm |
| `in` | Inchi | 1in = 2.54cm = 96px |

**Relativne:**

| Jedinica | Relativno prema... |
|---|---|
| `em` | Veličina fonta roditeljskog elementa |
| `rem` | Veličina fonta korijenskog elementa |
| `%` | Roditeljski element |
| `vw` | 1% širine viewporta |
| `vh` | 1% visine viewporta |
| `vmin` | 1% manjeg viewporta (širina ili visina) |
| `vmax` | 1% većeg viewporta |

### ✅ Validacija CSS-a

Provjera ispravnosti: [https://jigsaw.w3.org/css-validator/](https://jigsaw.w3.org/css-validator/)

