---
description: Simplify sharing webcomponents in NPM
---

# @atomico/exports

Simplifica la generación de build, tipos y exports al distribuir webcomponents en NPM, con `@atomico/exports` tu  podrás:

1. Exportación de múltiples archivos usando expresiones ejemplo : `exports src/components/*.{js,jsx}`.
2. asociar automáticamente package.json\#exports. flag `--exports`
3. asociar automáticamente los tipos para typescript y asociarlos al package.json\#typesVersions. flag `--types`
4. Optimizar la distribución de la build gracias a ESbuild.
5. Importar los assets mediante el uso de import.meta.url.
6. Añadir soporte a módulos CSS.
7. Crear wrapper para usar los webcomponents en react. flag `--react-wrapper`
8. Minificar el código. flag `--minify`.
9. Centralizar workspace en un solo package de instalacion. flag `--workspace <spaces>`.

## Flags

### --exports

Añadirá los archivos de la build a la propiedad exports  dentro del package.json.

