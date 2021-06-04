---
description: Facilita la distribución de webcomponents
---

# @atomico/exports

![](../.gitbook/assets/grupo-2.png)

Simplifica la generación de build, tipos y exports al distribuir webcomponents en NPM, con `@atomico/exports` tu  podrás:

1. Exportación de múltiples archivos usando expresiones ejemplo : `exports src/components/*.{js,jsx}`.
2. asociar automáticamente package.json\#exports. flag `--exports`
3. asociar automáticamente los tipos para typescript y asociarlos al package.json\#typesVersions. flag `--types`
4. Optimizar la distribución de la build gracias a ESbuild.
5. Importar los assets mediante el uso de import.meta.url.
6. Añadir soporte a módulos CSS genérico a base de Atomico. 
7. Crear automáticamente wrapper para usar los webcomponents en react
8. Minifica el código. flag `--minify`.
9. Centralizar workspace en un solo package de instalación. flag `--workspace <spaces>`.
10. Crear automáticamente los ficheros de visibilidad de CSS para los customElements encontrados en la exportación, ejemplo `my-component:not(:defined){ visibility: hidden }`

## Instalación

{% tabs %}
{% tab title="NPM" %}
```bash
npm install -D @atomico/exports
```
{% endtab %}

{% tab title="package.json\#scripts" %}
```javascript
{
    /**
     * ⚠️ El flag --types requiere la instalación de @typescript
     */
    "scripts": "exports src/components/*/*.js --exports --types"
}
```
{% endtab %}
{% endtabs %}

## Flags

### --exports

Añadirá los archivos de la build a la propiedad exports  dentro del package.json.

### --types

Requiere la instalación de Typescript, creara los tipos y añadirá los archivos a la propiedad typesVersion dentro de package.json

### --workspace

Buscara los subpackages que declaren dependencias y las añadirá en la propiedad dependencias del package.json

### --ignore-build

Evita el uso de esbuild, ideal si se posee código js estándar que se quiere distribuir sin compilación 

### --meta-url &lt;tipo de archivo&gt;

Añade soporte adicional a archivos que no se encuentren por defecto en la exportación de meta-url.

### --main &lt;nombre&gt;

De todos los archivos exportados asociara el que censida con el nombre del archivo como principal para la exportación del package.json

### --dest &lt;destino&gt;

Modifica el directorio de destino para la build

### --watch

Asocia el uso de watch a esbuild, ignorando los análisis de tipo y exports. 

### --minify

Habilita el minificar código de esbuild.

