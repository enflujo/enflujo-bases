# Bases de buenas prácticas en sitios web EnFlujo 💅🏽
----

## 1. Fuentes suplentes o _font fallbacks_


En el espcacio en blanco (__________), va el nombre de la tipografía escogida, que será nuestra primera opción. Cuando esa fuente se demore o no se pueda cargar por alguna razón, el navegador debería usar las que están a la derecha.

El nombre `--fuente` corresponde al nombre de variable que le estamos dando a cada una de las fuentes.

Estos textos normalmente los ponemos en `estilos`:
```css

root {
// Monoespaciadas
--fuenteMonoespaciada: '______________', 'Courier New', monospace;

// Serif
--fuenteSerifada: '______________', 'Garamond', 'Georgia', 'Times', serif;

// Sans-serif
--fuenteSinSerifas: '______________',  'Helvetica', 'Roboto', 'Arial', 'Tahoma', 'Verdana', sans-serif;

}
```

Para cada tipo de fuente se debería poner algo así (el nombre de la variable puede cambiar):




----


## 2. Instrucciones para crear Favicons

Basado en este excelente [artículo](https://evilmartians.com/chronicles/how-to-favicon-in-2021-six-files-that-fit-most-needs): 

Estos son los elementos que van en el `<head>` del HTML:

```html
<link rel="icon" href="/favicon.ico" sizes="32x32">
<link rel="icon" href="/favicon.svg" type="image/svg+xml">
<link rel="apple-touch-icon" href="/apple-touch-icon.png">
<link rel="manifest" href="/sitio.webmanifest">
```
--

El archivo `sitio.webmanifest` se escribe en formato de JSON así:

```json
{
  "name": "Laboratorio EnFlujo", // Nombre del sitio web
  "short_name": "EnFlujo", // Nombre corto del sitio web
  "icons": [
    { "src": "/icono_192.png", "sizes": "192x192", "type": "image/png" },
    { "src": "/icono_512.png", "sizes": "512x512", "type": "image/png" }
  ]
}

```

Normalmente ese archivo se guarda así `recursos/sitio.webmanifest` o `estaticos/sitio.webmanifest`, dependiendo como llamemos la carpeta donde guardamos los archivos (íconos, imágenes, etc) que no necesitamos que Astro o Vite, o el _framework_ que estemos usando, procese.

--

### Pasos para crear los íconos

La imagen desde donde se crean el resto de versiones debe ser un SVG de 512x512. 
Esa imagen se guarda en `.recursos/icono_512.png`

Squoosh es una herramienta genial para imágenes rasterizadas:

1. Abre tu imagen icono-512.png en [Squoosh](https://squoosh.app/).
2. Cambia los ajustes de compresión a `OxiPNG``.
3. Habilita "Reducir paleta" o “Reduce palette”.
4. Selecciona 64 colores.
5. Compara el antes y el después moviendo la perilla. SI ves alguna diferencia, aumenta el número de colores.
6. Guarda el archivo.
7. Repite estos pasos para tu icono-192.png y apple-touch-icon.png.

También se hace una de 192x192 y se guarda en `.recursos/icono_192.png` o `estaticos/icono_192.png`, dependiendo de cómo llamemos la carpeta.

----

## 3. Instrucciones para [SEO](https://es.wikipedia.org/wiki/Posicionamiento_en_buscadores) (posicionamemiento en buscadores)

En el `<head>`del HTML vamos a ubicar las siguientes líneas y a reemplazar lo que haga falta para cada proyecto en particular:


```html
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="icon" href="/favicon.ico" sizes="any" />
    <link rel="icon" href="/favicon.svg" type="image/svg+xml" />
    <link rel="apple-touch-icon" href="/apple-touch-icon.png" />
    <link rel="manifest" href="/sitio.webmanifest" />
    <!-- <link rel="canonical" href="https://enflujo.com" /> -->

    <title>..:: EnFlujo ::..</title>
    <!-- <meta name="description" content="Descripción del sitio...." /> -->

    <!-- OpenGraph -->
    <meta property="og:locale" content="es_CO" />
    <!-- <meta property="og:site_name" content="EnFlujo" /> -->
    <meta property="og:type" content="website" />
    <!-- <meta property="og:url" content="https://enflujo.com" /> -->
    <!-- <meta property="og:title" content="Titulo ..." /> -->
    <!-- <meta property="og:description" content="Descripción ..." /> -->
    <!-- <meta property="og:image" content="https://xxxxxx.jpg" /> -->
    <!-- <meta property="og:image:alt" content="Texto que describe la imagen" /> -->
    <!-- <meta property="og:image:width" content="1200" /> -->
    <!-- <meta property="og:image:height" content="630" /> -->

    <!-- Twitter -->
    <!-- <meta name="twitter:card" content="summary_large_image" /> -->
    <!-- <meta name="twitter:site" content="@labenflujo" /> -->
    <!-- <meta name="twitter:creator" content="@labenflujo" /> -->
    <!-- <meta name="twitter:url" content="https://enflujo.com" /> -->
    <!-- <meta name="twitter:title" content="Titulo ..." /> -->
    <!-- <meta name="twitter:description" content="Descripción ..." /> -->
    <!-- <meta name="twitter:image" content="https://xxxxxx.jpg" /> -->
    <!-- <meta name="twitter:image:alt" content="Texto que describe la imagen" /> -->
  </head>
</html>

```

Aquí hay un ejemplo con un proyecto que ya se hizo:

```html

<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="icon" href="/favicon.ico" sizes="any" />
    <link rel="icon" href="/favicon.svg" type="image/svg+xml" />
    <link rel="apple-touch-icon" href="/apple-touch-icon.png" />
    <link rel="manifest" href="/sitio.webmanifest" />
    <link rel="canonical" href="https://cerosetenta.uniandes.edu.co/especiales/lam/" />

    <title>Lazos de Poder Mariano | 070-Manifiesta-EnFlujo</title>
    <meta
      name="description"
      content="Grupo religioso que en Colombia ha buscado imponer en la agenda pública restricciones al aborto tras el fallo de la Corte Constitucional que lo despenaliza hasta la semana 24."
    />

    <!-- OpenGraph -->
    <meta property="og:locale" content="es_CO" />
    <meta property="og:site_name" content="Cerosetenta" />
    <meta property="og:type" content="website" />
    <meta property="og:url" content="https://cerosetenta.uniandes.edu.co/especiales/lam/" />
    <meta property="og:title" content="Lazos de Poder Mariano | 070-Manifiesta-EnFlujo" />
    <meta
      property="og:description"
      content="Grupo religioso que en Colombia ha buscado imponer en la agenda pública restricciones al aborto tras el fallo de la Corte Constitucional que lo despenaliza hasta la semana 24."
    />
    <meta property="og:image" content="https://cerosetenta.uniandes.edu.co/especiales/lam/imgs/img-redes.jpg" />
    <meta property="og:image:alt" content="Lazos de Poder Mariano" />
    <meta property="og:image:width" content="1200" />
    <meta property="og:image:height" content="630" />

    <!-- Twitter -->
    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:site" content="@cerosetenta" />
    <meta name="twitter:creator" content="@cerosetenta" />
    <meta name="twitter:url" content="https://cerosetenta.uniandes.edu.co/especiales/lam/" />
    <meta name="twitter:title" content="Lazos de Poder Mariano | 070-Manifiesta-EnFlujo" />
    <meta
      name="twitter:description"
      content="Grupo religioso que en Colombia ha buscado imponer en la agenda pública restricciones al aborto tras el fallo de la Corte Constitucional que lo despenaliza hasta la semana 24."
    />
    <meta name="twitter:image" content="https://cerosetenta.uniandes.edu.co/especiales/lam/imgs/img-redes.jpg" />
    <meta name="twitter:image:alt" content="Lazos de Poder Mariano" />

    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Grenze+Gotisch:wght@700&family=Roboto+Mono:wght@400;600&display=swap"
      rel="stylesheet"
    />
    <script
      async
      src="https://analitica.enflujo.com/script.js"
      data-website-id="569a36fc-18d4-4ee4-a40c-7c7a9a35b3a1"
    ></script>
  </head>
  </html>

``````
----
## 4. Compresión extrema de archivos SVG

Ya teniendo el SVG, vamos a [Squoosh](https://squoosh.app/) y realizamos estos pasos:

1. Abre tu imagen en [Squoosh](https://squoosh.app/).
2. Cambia los ajustes de compresión a `OxiPNG``.
3. Habilita "Reducir paleta" o “Reduce palette”.
4. Selecciona 64 colores.
5. Compara el antes y el después moviendo la perilla. SI ves alguna diferencia, aumenta el número de colores.
6. Guarda el archivo.

7. Una vez tengas ese archivo, abrimos el SVG con `Vscode` .
8. Quitamos la información de las capas que es información que no vamos a necesitar

```svg

<svg id="Capa_2" data-name="Capa 2"></svg>
<g id="Capa_1-2" data-name="Capa 1"></g>

``````
9. Buscamos la extensión SVGO. Con ella vamos a los archivos y le decimos en cada uno, c9.lic derecho, `Minify current SVG`. Con ese comando, el SVG pasa a ocupar menos líneas y por ende a bajar un poco el peso. 

10. Le damos guardar y tenemos nuestro SVG comprimido.
