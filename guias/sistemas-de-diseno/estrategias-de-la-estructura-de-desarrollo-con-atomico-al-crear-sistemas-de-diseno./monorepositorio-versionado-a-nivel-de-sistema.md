---
description: Trata de un repositorio que posee componentes versionados a nivel de sistema.
---

# Monorepositorio versionado a nivel de sistema



### Ejemplo:

```
packages
├─ components
│  ├─ src 
│  │  ├─ my-button
│  │  ├─ my-input
│  │  ├─ my-card
│  │  └─ components.{ts,js,tsx,jsx}
│  └─ package.json
└─ storybook
   └─ package.json
```

Le invito a notar que la estructura de mono repositorio sigue estando presente, ya que es la forma más conveniente de gestionar un sistema de diseño, ya que de esta forma podemos aislar el Storybook y otras necesidades que giren entorno a nuestro sistema de diseño.

una de las mayores ventajas del repositorio single packages es la agilidad al crear componentes, ya que no deberemos crear un nuevo package, bastara con crear la carpeta y los archivos correspondientes,&#x20;
