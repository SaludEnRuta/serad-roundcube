<div align="center">

<img src="images/logo.png" alt="Logo de Salud en Ruta" height="140" />

# Salud en Ruta Mail — Roundcube Skin

**Skin de Salud en Ruta para Roundcube Webmail.**
Modo oscuro nativo, paleta de marca y logos propios, listo para producción.

[![License: CC BY-SA 3.0](https://img.shields.io/badge/License-CC%20BY--SA%203.0-0a7c95?style=flat-square)](http://creativecommons.org/licenses/by-sa/3.0/)
[![Roundcube](https://img.shields.io/badge/Roundcube-1.7.5-06576a?style=flat-square)](https://roundcube.net/)
[![Based on Elastic](https://img.shields.io/badge/Based%20on-Elastic%20Skin-63cce3?style=flat-square)](https://github.com/roundcube/roundcubemail/tree/master/skins/elastic)
![Visitas](https://visitor-badge.laobi.icu/badge?page_id=SaludEnRuta.serad-roundcube&left_text=visitas&right_color=%230a7c95)

</div>

---

## Capturas de pantalla

| Modo claro | Modo oscuro |
|---|---|
| ![Login, modo claro](docs/capturas/login-light.png) | ![Login, modo oscuro](docs/capturas/login-dark.png) |
| ![Bandeja de entrada, modo claro](docs/capturas/bandeja-light.png) | ![Bandeja de entrada, modo oscuro](docs/capturas/bandeja-dark.png) |
| ![Redactar, modo claro](docs/capturas/redactar-light.png) | ![Redactar, modo oscuro](docs/capturas/redactar-dark.png) |
| ![Configuración, modo claro](docs/capturas/ajustes-light.png) | ![Configuración, modo oscuro](docs/capturas/ajustes-dark.png) |

Hechas con Roundcube 1.7.5 en Docker y correos de ejemplo.

---

## Características

- **Paleta de Salud en Ruta**: turquesa profundo `#0a7c95` (la variante AA del `#0B8FAC` de marca), aguamarina `#63cce3` del pulso del logo y menú lateral en petróleo `#0f3d4c`.
- **Modo oscuro nativo** (`dark_mode_support: true`): fondos `#0a1519` / `#132429` de la intranet de Salud en Ruta.
- **Logos por modo**: logo completo claro/oscuro para el login y versión reducida para el menú lateral.
- **Sin gradientes**: diseño plano y limpio.
- **Scrollbars, foco y selección** con los colores de la marca en ambos modos.
- **Responsive**: escritorio, tableta y móvil (widescreen).
- **Hereda de Elastic** (`extends: elastic`), el skin oficial de Roundcube, a partir del tema de [NextAura](https://github.com/TheIsmael12/nextaura-roundcube). Plantillas y JavaScript siempre al día con tu Roundcube.

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

## Roundcube 1.7.5: hereda de Elastic

Desde esta versión el skin **hereda de Elastic** (`"extends": "elastic"` en `meta.json`), como recomienda la [guía de skins de Roundcube](https://github.com/roundcube/roundcubemail/wiki/Skins), en lugar de ser una copia completa.

- Las **plantillas, el JavaScript, las fuentes y los iconos** son los de Elastic de tu instalación, así que el skin recibe sus correcciones al actualizar Roundcube.
- El skin solo aporta la **paleta** (`styles/colors.less`), los **ajustes de marca** (`styles/_styles.less` y `styles/_dark.less`), los **logos** (con `skin_logo` en `meta.json`, sin tocar plantillas), el favicon, la marca de agua y `templates/includes/layout.html`, la única plantilla propia, que carga la hoja de estilos de la marca.
- Los estilos se compilan con los LESS de **Elastic 1.7.5**, y la CI comprueba que el CSS publicado está al día.
- Compatible con el plugin [Mail Scheduler](https://github.com/TheIsmael12/roundcube-mail-scheduler) (envíos programados y respuestas automáticas), que incluye estilos para este skin.

> Para Roundcube 1.6 usa la versión anterior del skin (commit `02137bc`).

---

## Estructura

```
serad-roundcube/
├── meta.json                 # "extends": "elastic", logos (skin_logo) y modo oscuro
├── images/                   # Logos por modo y favicon
├── styles/
│   ├── colors.less           # ★ Paleta: solo lo que cambia respecto a Elastic
│   ├── _styles.less          # ★ Ajustes de marca (variables @br-*)
│   ├── _dark.less            # Ajustes del modo oscuro
│   ├── styles.less           # Entrada: Elastic + paleta + ajustes
│   ├── embed.less            # Contenido embebido (editor y mensajes)
│   └── *.min.css             # CSS compilado
├── templates/includes/
│   └── layout.html           # Carga styles.css de la marca (copia de la de Elastic 1.7.5)
├── bin/build.mjs             # Compilación de estilos
├── watermark.html            # Marca de agua del panel vacío
├── thumbnail.png
└── docs/capturas/
```

---

## Instalación

### 1. Copiar el skin

```bash
git clone https://github.com/TheIsmael12/serad-roundcube.git /var/www/roundcube/skins/saludenruta
```

O con Composer:

```bash
composer require theismael12/saludenruta
```

El skin necesita `skins/elastic`, que viene siempre con Roundcube.

### 2. Activar en Roundcube

```php
// config/config.inc.php
$config['skin'] = 'saludenruta';
```

---

## Compilar estilos

Tras tocar `colors.less`, `_styles.less` o `_dark.less`, o al actualizar Roundcube:

```bash
cd /var/www/roundcube/skins/saludenruta
npm install
npm run build        # usa ../elastic de la instalación
```

Fuera de una instalación de Roundcube:

```bash
ELASTIC_DIR=/ruta/a/roundcube/skins/elastic npm run build
npm run build -- --download   # descarga Elastic 1.7.5 de la release oficial
```

`npm run check -- --download` comprueba que el CSS publicado coincide con el que se generaría (es lo que ejecuta la CI).

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
