# Instrucciones para crear Favicons

Instrucciones para crear favicons para los sitios web. Basado en este excelente [artículo](https://evilmartians.com/chronicles/how-to-favicon-in-2021-six-files-that-fit-most-needs): 

Estos son los elementos que van en el `<head>` del html:

```html
<link rel="icon" href="/favicon.ico" sizes="any"><!-- 500x500 -->
<link rel="icon" href="/favicon.svg" type="image/svg+xml"><!-- 36x36 -->
<link rel="apple-touch-icon" href="/apple-touch-icon.png"><!-- 180×180 -->
<link rel="manifest" href="/sitio.webmanifest">
```

El archivo `sitio.webmanifest` se escribe en formato de JSON así:

```json
{
  "name": "Laboratorio EnFlujo",
  "short_name": "EnFlujo",
  "icons": [
    { "src": "/icono_192.png", "sizes": "192x192", "type": "image/png" },
    { "src": "/icono_512.png", "sizes": "512x512", "type": "image/png" }
  ]
}

```

## Pasos para crear los iconos

La imagen desde donde se crean el resto de versiones debe ser un SVG de 512x512
