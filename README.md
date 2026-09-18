# Tugas Rutin 4 — Konversi CSS ke SCSS

Konversi `style.css` (Tugas Pertemuan 2 - Dashboard/Portofolio) ke SCSS dengan
struktur modular **7-1 pattern**.

## Struktur Folder

```
scss/
├── abstracts/
│   ├── _variables.scss   # semua token: colors, spacing scale, breakpoints, radius
│   └── _mixins.scss      # 4 mixin reusable: respond-to, flex, card-base, hover-lift
├── base/
│   ├── _reset.scss       # reset dasar + body
│   └── _root.scss        # generate :root custom properties (loop @each & @for)
├── layout/
│   ├── _container.scss
│   ├── _header.scss
│   ├── _nav.scss
│   ├── _main.scss
│   └── _footer.scss
├── components/
│   ├── _card.scss
│   ├── _buttons.scss
│   └── _form.scss
├── pages/
│   ├── _about.scss       # Tentang Saya
│   ├── _pendidikan.scss
│   ├── _hobby.scss       # loop @each untuk warna aksen tiap kartu hobi
│   ├── _aside.scss
│   └── _kontak.scss
├── themes/
│   └── _dark.scss        # override dark mode via loop @each
└── main.scss              # entry point, meng-@use semua partial
```

## Requirements yang dipenuhi

1. **Konversi CSS existing ke SCSS** — seluruh isi `style.css` asli dipecah ke partial di atas.
2. **Variables untuk colors & spacing** — `abstracts/_variables.scss` (map `$colors`, `$colors-dark`, skala spasi 4px).
3. **Nesting maksimal 3 level** — mis. `.about > figure > img`, `aside > ul > li`.
4. **Struktur 7-1 pattern (partials)** — lihat folder di atas (folder `vendors/` tidak dipakai karena tidak ada library CSS pihak ketiga).
5. **Memakai `@use`** di seluruh file, tidak ada `@import`.
6. **Minimal 3 mixin reusable** — ada 4: `respond-to`, `flex`, `card-base`, `hover-lift`.
7. **Minimal 1 `@each`/`@for`** — dipakai 2 kali:
   - `@for` di `base/_root.scss` membangkitkan skala spasi `--spacing-1`…`--spacing-12`.
   - `@each` di `base/_root.scss` (map warna), `pages/_hobby.scss` (warna aksen tiap kartu), dan `themes/_dark.scss` (override dark mode).

## Cara compile

```bash
npm install
npm run build       # sass scss/main.scss -> style.css
npm run watch        # mode watch saat development
```

Bisa juga dengan Dart Sass langsung tanpa npm script:

```bash
npx sass scss/main.scss style.css --no-source-map --style=expanded
```

Atau lewat Vite (opsional) dengan menambahkan `sass` sebagai devDependency —
Vite otomatis meng-compile file `.scss` yang di-import di entry JS/HTML-nya.

## File hasil compile

`style.css` di root folder ini adalah hasil compile dari `scss/main.scss`
dan yang di-link oleh `index.html`.
