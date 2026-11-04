<div align="center">

<img src="images/logo.png" alt="Logo de Salud en Ruta" height="140" />

# Salud en Ruta Mail — Roundcube Skin

**Skin de Salud en Ruta para Roundcube Webmail.**
Modo oscuro nativo, paleta de marca y logos propios, listo para producción.

[![License: CC BY-SA 3.0](https://img.shields.io/badge/License-CC%20BY--SA%203.0-0a7c95?style=flat-square)](http://creativecommons.org/licenses/by-sa/3.0/)
[![Roundcube](https://img.shields.io/badge/Roundcube-1.6%2B-06576a?style=flat-square)](https://roundcube.net/)
[![Based on Elastic](https://img.shields.io/badge/Based%20on-Elastic%20Skin-63cce3?style=flat-square)](https://github.com/roundcube/roundcubemail/tree/master/skins/elastic)

</div>

---

## Características

- **Paleta de Salud en Ruta**: turquesa profundo `#0a7c95` (la variante AA del `#0B8FAC` de marca), aguamarina `#63cce3` del pulso del logo y menú lateral en petróleo `#0f3d4c`.
- **Modo oscuro nativo** (`dark_mode_support: true`): fondos `#0a1519` / `#132429` de la intranet de Salud en Ruta.
- **Logos por modo**: logo completo claro/oscuro para el login y versión reducida para el menú lateral.
- **Sin gradientes**: diseño plano y limpio.
- **Scrollbars, foco y selección** con los colores de la marca en ambos modos.
- **Responsive**: escritorio, tableta y móvil (widescreen).
- **Construido sobre Elastic**, el skin oficial de Roundcube, a partir del tema de [NextAura](https://github.com/TheIsmael12/nextaura-roundcube).

---

## Identidad de marca

| Rol                              | Color     | Vista |
|----------------------------------|-----------|-------|
| Primario (turquesa profundo, AA) | `#0a7c95` | ![](https://placehold.co/14x14/0a7c95/0a7c95.png) |
| Turquesa de marca                | `#0b8fac` | ![](https://placehold.co/14x14/0b8fac/0b8fac.png) |
| Primario active                  | `#06576a` | ![](https://placehold.co/14x14/06576a/06576a.png) |
| Azul Salud en Ruta               | `#24badb` | ![](https://placehold.co/14x14/24badb/24badb.png) |
| Aguamarina del pulso (acento)    | `#63cce3` | ![](https://placehold.co/14x14/63cce3/63cce3.png) |
| Acento suave                     | `#e0f6fb` | ![](https://placehold.co/14x14/e0f6fb/e0f6fb.png) |
| Menú lateral (petróleo)          | `#0f3d4c` | ![](https://placehold.co/14x14/0f3d4c/0f3d4c.png) |
| Fondo oscuro                     | `#0a1519` | ![](https://placehold.co/14x14/0a1519/0a1519.png) |

Toda la marca está en las variables `@br-*` al principio de `styles/_styles.less` y en las `@color-*` de `styles/colors.less`.

---

## Estructura

```
serad-roundcube/
├── images/               # Logos y assets gráficos
│   ├── logo.png          # Logo principal (login, modo claro)
│   ├── logo-dark.png     # Logo para modo oscuro y menú lateral
│   ├── logo-small.png    # Logo reducido (modo claro)
│   ├── logo-small-dark.png
│   └── favicon.ico
├── styles/
│   ├── _styles.less      # ★ Overrides de marca (variables @br-*)
│   ├── _variables.less   # Variables del tema base
│   ├── colors.less       # Paleta de colores de Elastic
│   ├── styles.less       # Punto de entrada principal
│   └── styles.min.css    # CSS compilado y minificado
├── templates/            # Plantillas HTML de Roundcube
├── fonts/                # Roboto + FontAwesome 5
├── deps/                 # Bootstrap 4 bundle
└── meta.json             # Metadatos del skin
```

Logos: Generados a partir de los logos de `landing-serad/public/images` (la versión oscura pasa el texto negro a blanco y conserva el pulso) y del icono de `intranet-serad`.

---

## Instalación

### 1. Copiar el skin

```bash
git clone https://github.com/TheIsmael12/serad-roundcube.git /var/www/roundcube/skins/saludenruta
```

### 2. Activar en Roundcube

```php
// config/config.inc.php
$config['skin'] = 'saludenruta';
```

### 3. Limpiar caché de assets (opcional)

```bash
cd /var/www/roundcube
bin/updatecss.sh --dir skins/saludenruta
```

---

## Compilar estilos

Los estilos están en **LESS**. Tras tocar `_styles.less`, `_variables.less` o `colors.less`:

```bash
npm install -g less clean-css-cli
lessc styles/styles.less | cleancss -O1 -o styles/styles.min.css
lessc styles/print.less  | cleancss -O1 -o styles/print.min.css
lessc styles/embed.less  | cleancss -O1 -o styles/embed.min.css
```

> `less-plugin-clean-css` falla con las versiones actuales de Node (`util.isRegExp is not a function`); por eso se minifica aparte con `clean-css-cli`.

---

## Créditos

Construido sobre el tema **Elastic** del equipo de Roundcube.

- Tema base: [Elastic Skin](https://github.com/roundcube/roundcubemail/tree/master/skins/elastic) — Aleksander Machniak
- Personalización de marca: [NextAura](https://nextaura.es) para [Salud en Ruta](https://saludenruta.es)

| Librería         | Licencia   |
|------------------|------------|
| Bootstrap 4      | MIT        |
| FontAwesome 5    | CC BY 4.0  |
| Roboto (Google)  | Apache 2.0 |

---

## Licencia

**Creative Commons Attribution-ShareAlike 3.0**, heredada del skin Elastic.
Puedes copiar, distribuir, modificar y adaptar este trabajo siempre que mantengas los créditos al autor original (**Aleksander Machniak**) en este `README.md`.

[Ver licencia completa](http://creativecommons.org/licenses/by-sa/3.0/)
