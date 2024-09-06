---
layout: post
title: "Liquid"
categories: [minimal,jekyll]
---

<div align="center">
  <p><em><strong>Descargo de responsabilidad:</strong> La información aquí puede variar dependiendo de la versión que estés usando.<br/>
  Por favor, consulta el archivo <code>README.md</code> incluido en el tema para obtener información específica de tu versión o dirígete
  a la etiqueta Git correspondiente a tu versión. Ejemplo: https://github.com/jekyll/minima/blob/v2.5.0/README.md.<br/>
  Ejecutar <code>bundle show minima</code> te proporcionará la ruta local a la versión actual de tu tema.</em></p>
  <img src="/readme_banner.svg"/>
  <p>Es el tema predeterminado (y el primero) de Jekyll. Es lo que obtienes cuando ejecutas <code>jekyll new</code>.</p>
  <p><a href="https://jekyll.github.io/minima/">Vista previa del tema</a></p>
  <p><img src="/screenshot.png"/></p>
</div>

## Instalación

Añade esta línea al archivo Gemfile de tu sitio Jekyll:

```ruby
gem "minima"
```

Y luego ejecuta:

    $ bundle

## Contenido a Primer Vista

Minima ha sido generado por el comando `jekyll new-theme` y por lo tanto tiene todos los archivos y directorios necesarios para tener un nuevo sitio Jekyll en funcionamiento con cero configuración.

### Layouts (Diseños)

Se refiere a los archivos dentro del directorio `_layouts`, que definen el marcado para tu tema.

  - `base.html` — El diseño base que sienta las bases para los diseños posteriores. Los diseños derivados inyectan su
    contenido en este archivo en la línea que dice `{{ content }}` y están vinculados a este archivo a través de
    la declaración [FrontMatter](https://jekyllrb.com/docs/frontmatter/) `layout: base`.
  - `home.html` — El diseño para tu página de inicio / página principal / página índice. [[Más información.](#home-layout)]
  - `page.html` — El diseño para tus documentos que contienen FrontMatter, pero no son publicaciones.
  - `post.html` — El diseño para tus publicaciones.

#### Diseño Base

Desde Minima v3 en adelante, el diseño base se llama **`base.html`** en lugar de `default.html` para evitar confundir a los nuevos usuarios al asumir que ese nombre tiene un estatus especial.

Se aconseja a los usuarios que migran desde versiones anteriores con `_layouts/default.html` personalizado que cambien el nombre de su copia a `_layouts/base.html`. Los usuarios en migración con diseños personalizados adicionales pueden actualizar las referencias en FrontMatter al diseño anterior `default.html` o crear un nuevo diseño `default.html` que haga referencia al actual `base.html`, según sea el camino más fácil:

```
---
# nuevo `_layouts/default.html` para compatibilidad hacia atrás cuando se han personalizado múltiples
# diseños.

layout: base
---

{{ content }}
```

#### Diseño de Inicio

`home.html` es un diseño HTML flexible para la página de inicio / página principal / página índice. <br/>

##### *Encabezado Principal y Inyección de Contenido*

Desde Minima v2.2 en adelante, el *diseño* de inicio inyectará todo el contenido de tu `index.md` / `index.html` **antes** del encabezado **`Posts`**. Esto te permitirá incluir contenido no relacionado con publicaciones que se publique en la página de inicio bajo un encabezado dedicado. *Recomendamos que titules esta sección con un Encabezado2 (`##`)*.

Usualmente, el `site.title` en sí mismo sería suficiente como el 'título principal' implícito para una página de inicio. Pero, si tu página de inicio desea que se muestre un encabezado explícitamente, simplemente define una variable `title` en el Front Matter del documento y se renderizará con una etiqueta `<h1>`.

##### *Listado de Publicaciones*

Esta sección es opcional desde Minima v2.2 en adelante.<br/>
Se incluirá automáticamente solo cuando tu sitio contenga una o más publicaciones o borradores válidos (si el sitio está configurado para `show_drafts`).

El título para esta sección es `Posts` por defecto y se renderiza con una etiqueta `<h2>`. Puedes personalizar este encabezado definiendo una variable `list_title` en el Front Matter del documento.

### Includes (Incluir)

Se refiere a fragmentos de código dentro del directorio `_includes` que se pueden insertar en múltiples diseños (y otro archivo de inclusión también) dentro del mismo tema.

  - `disqus_comments.html` — Código para marcar el cuadro de comentarios de Disqus.
  - `footer.html` — Define la sección de pie de página del sitio.
  - `google-analytics.html` — Inserta el módulo de Google Analytics (activo solo en el entorno de producción).
  - `head.html` — Bloque de código que define el `<head></head>` en el diseño *predeterminado*.
  - `custom-head.html` — Marcador de posición para permitir a los usuarios agregar más metadatos a `<head />`.
  - `header.html` — Define la sección de encabezado principal del sitio. Por defecto, las páginas con un atributo `title` definido tendrán enlaces mostrados aquí.
  - `social.html` — Renderiza íconos de redes sociales basados en los datos `minima:social_links` en el archivo de configuración.
  - `social-item.html` — Plantilla para renderizar un ítem de lista individual que contiene un enlace gráfico al perfil social configurado.
  - `social-links/*.svg` — Componentes de marcado SVG de íconos sociales compatibles.

### Sass

Se refiere a archivos `.scss` dentro del directorio `_sass` que definen los estilos del tema.

  - `minima/skins/classic.scss` — El "skin" clásico del tema. *Usado por defecto.*
  - `minima/initialize.scss` — Un componente que define los valores predeterminados de variables y partes de Sass que no están relacionadas con la piel del tema.
    Importa los siguientes componentes (en el siguiente orden):
    - `minima/custom-variables.scss` — Un gancho que permite sobrescribir los valores predeterminados de variables y mixins. (*Nota: No se pueden sobrescribir estilos*)
    - `minima/_base.scss` — Parte de Sass para reinicios y define estilos base para varios elementos HTML.
    - `minima/_layout.scss` — Parte de Sass que define el estilo visual para varios diseños.
    - `minima/custom-styles.scss` — Un gancho que permite sobrescribir los estilos definidos arriba. (*Nota: No se pueden sobrescribir variables*)

Consulta la sección [skins](#skins) para más detalles.

### Assets (Recursos)

Se refiere a varios archivos de recursos dentro del directorio `assets`.

  - `assets/css/style.scss` — Importa archivos sass desde el directorio `_sass` y se procesa en la hoja de estilos del tema: `assets/css/styles.css`.
  - `assets/minima-social-icons.html` — Importa el gráfico del ícono social habilitado y se procesa en un archivo SVG compuesto.
    Consulta la [sección sobre redes sociales](#social-networks) para su uso.

### Plugins

Minima viene con el plugin [`jekyll-seo-tag`](https://github.com/jekyll/jekyll-seo-tag) preinstalado para asegurar que tu sitio web obtenga las metaetiquetas más útiles. Consulta [uso](https://github.com/jekyll/jekyll-seo-tag#usage) para saber cómo configurarlo.

## Uso

Asegúrate de tener la siguiente línea en tu archivo de configuración:

```yaml
theme: minima
```

### Personalización de Plantillas

Para sobrescribir la estructura y el estilo predeterminados de minima, simplemente crea el directorio correspondiente en la raíz de tu sitio, copia el archivo que deseas personalizar a ese directorio y luego edita el archivo.
Por ejemplo, para sobrescribir el archivo [`_includes/head.html `](_includes/head.html) para especificar una ruta de estilo personalizada, crea un directorio `_includes`, copia `_includes/head.html` desde la carpeta del tema minima a `<yoursite>/_includes` y comienza a editar ese archivo.

La CSS predeterminada del sitio ahora se ha movido a un nuevo lugar dentro del mismo tema, [`assets/css/style.scss`](assets/css/style.scss).

En Minima 3.0, si solo necesitas personalizar los colores del tema, consulta la sección siguiente sobre skins. Para tener tus
*CSS overrides* en sincronía con los cambios futuros en versiones posteriores, puedes recopilar todas tus sobrescrituras para las variables de Sass y mixins dentro de un archivo sass colocado en `_sass/minima/custom-variables.scss` y todas las demás sobrescrituras dentro de un archivo sass ubicado en `_sass/minima/custom-styles.scss`.

No necesitas mantener partes completas en la fuente del sitio solo para sobrescribir algunos estilos. Sin embargo, la fuente principal de tu hoja de estilos (`assets/css/style.scss`) debe contener lo siguiente:

  - Guiones de Front Matter al principio (pueden estar vacíos).
  - Directiva para importar un skin.
  - Directiva para importar los estilos base (carga automáticamente las sobrescrituras cuando están disponibles).

Por lo tanto, tu `assets/css/style.scss` debe contener lo siguiente como mínimo:

```sass
---
---

@import
  "minima/skins/{{ site.minima.skin | default: 'classic' }}",
 

 "minima/initialize",
  "minima/custom-variables",
  "minima/_base",
  "minima/_layout",
  "minima/custom-styles"
```

### Skins

Para cambiar el aspecto de tu sitio sin tener que sobrescribir la hoja de estilos, puedes seleccionar una piel diferente. Minima incluye varias pieles prediseñadas para su uso.

#### Instalación de Nuevas Pieles

Para instalar pieles adicionales desde el repositorio `jekyll/minima`, sigue los siguientes pasos:

1. Crea un archivo `_sass/minima/skins/custom.scss` en tu proyecto y copia el código del archivo `.scss` de la piel deseada al nuevo archivo `custom.scss`.
2. Modifica el archivo `custom.scss` según sea necesario para personalizarlo.
3. Establece la variable `minima: skin` en tu archivo `_config.yml` para que coincida con el nombre del archivo de la piel `custom.scss`.

    ```yaml
    minima:
      skin: custom
    ```

Para habilitar una piel en lugar de `custom`, sigue el formato predeterminado en el archivo `_config.yml`:

```yaml
minima:
  skin: classic
```

> Nota: Es posible que las pieles prediseñadas y nuevas pieles no sean completamente compatibles entre versiones del tema. Consulta los archivos `_sass/minima/skins` para la configuración disponible.

### Redes Sociales

Puedes configurar iconos de redes sociales en el encabezado de tu sitio web a través de la configuración de tu sitio `_config.yml`. Aquí está el formato para agregar un enlace de red social:

```yaml
minima:
  social_links:
    - icon: "twitter"
      url: "https://twitter.com/minima"
    - icon: "github"
      url: "https://github.com/jekyll/minima"
```

Por defecto, Minima usa íconos de `font-awesome`. Si prefieres usar otro conjunto de íconos, consulta el archivo [`_includes/social.html`](https://github.com/jekyll/minima/blob/master/_includes/social.html).

## Actualizaciones

Cada vez que actualices el tema minima, puede haber cambios en las variables de Sass y en las hojas de estilo. Revisa el archivo [`README.md`](https://github.com/jekyll/minima/blob/master/README.md) para las notas de la versión. Asegúrate de revisar los cambios y migrar tus sobrescrituras si es necesario.

---
