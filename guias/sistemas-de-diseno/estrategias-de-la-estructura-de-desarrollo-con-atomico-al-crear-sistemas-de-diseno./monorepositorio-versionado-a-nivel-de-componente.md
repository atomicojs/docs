---
description: >-
  Trata de un repositorio que posee componentes versionados como paquetes
  individuales.
---

# Monorepositorio versionado a nivel de componente



### Ejemplo

```
packages
├─ components
│  ├─ my-button
│  │  └─ package.json
│  ├─ my-input
│  │  └─ package.json
│  └─ my-card
│     └─ package.json
└─ storybook
   └─ package.json
```

la idea de este monorepositorio es individualizar cada componente como  package, esto con los siguientes objetivos:

1. **Versionamiento**: Trata de cada package estará versionado, ejemplo `@ds/button@1.0.0`, esto permite que podamos agregar mejoras o corregir problemas apuntando solo a la versión del componente afectado.
2.  **Mantenimiento**: Al ser un package, podemos individualizar sus dependencias, es ideal que definamos correctamente:

    1. [dependencies](https://docs.npmjs.com/cli/v9/configuring-npm/package-json#dependencies): dependencias requeridas, es natural que los componentes dependerán entre si, una definición incorrecta  puede generar duplicación de packages en node\_modules, procure identificar bien entre dependencies y peerDependecies.
    2. [peerDependencies](https://docs.npmjs.com/cli/v9/configuring-npm/package-json#peerdependencies): dependencias requeridas pero en función del entorno y otras dependencias.
    3. [devDependencies](https://docs.npmjs.com/cli/v9/configuring-npm/package-json#devdependencies): dependencias solo para el desarrollo sea empaquetado o testing.


3. **Abstracción**: Es ideal que nuestro package distribuya el componente en si y los slots de composición(Subcomponentes que únicamente dependen del componente principal, ejemplo el tag options del tag select) y alguna otra utilidad especifica del componente.
