---
description: >-
  Trata de un repositorio que posee un componentes versionados a nivel de
  sistema de diseño.
---

# Monorepositorio versionado a nivel de sistema de diseño

Trata de un repositorio que posee un componentes versionados a nivel de sistema de diseño esto quiere decir que cualquier cambio a nivel de componente se publicara como una nueva versión del sistema de diseño.

### Ventajas

1. Mayor agilidad al crear nuevos componentes, ya que no deberemos crear un nuevo package para un nuevo componente.
2. Facil centralización de todo el sistema de diseño, bastara con un fichero `components` para definir que se exporta a nivel de sistema de diseño.

### Desventajas

1. No podremos individualizar las dependencias por componente, ya que estas estarán atadas al package de todo el sistema de diseño.

### Ejemplo de estructura:&#x20;

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

### Ejemplo de importación por componente

```javascript
import { Button } from "@ds/components/button";
```

### Ejemplo de importación por sistema de componentes

```javascript
import { Button } from "@ds/components";
```
