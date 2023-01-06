---
description: >-
  Conozcamos 2 estrategias de estructuración de tu proyecto recomendadas por
  UpperCod para el desarrollo de sistemas de diseño.
---

# Estrategias de la estructura de desarrollo con Atomico al crear sistemas de diseño.

Puede ser confuso abordar a el desarrollo de un sistema de diseño sin saber como estructurar nuestro proyecto, la estructura de nuestro repositorio definirá en gran medida la publicación de nuestro package sea:

1. Monorepositorio multi package
2. Repositorio single package

### Monorepositorio multi package

Trata de un repositorio que posee componentes aislados como paquetes, ejemplo:

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

    1. dependecies: dependencias requeridas, es natural que los componentes dependerán entre si, una definición incorrecta  puede generar duplicación de packages en node\_modules, procure identificar bien entre dependencies y peerDependecies.
    2. peerDependecies: dependencias requeridas pero en función del entorno y otras dependencias.
    3. devDependecies: dependencias solo para el desarrollo sea empaquetado o testing.


3.  **Abstracción**: Es ideal que nuestro package distribuya el componente en si y los slots de composición y alguna otra utilidad especifica del componente.



