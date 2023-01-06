---
description: >-
  Le invito a conocer 2 estrategias de estructuración de tu repositorio para tu
  proyecto como sistemas de diseño.
---

# Estrategias de estructuración de repositorio con Atomico al crear sistemas de diseño.

Puede ser confuso abordar a el desarrollo de un sistema de diseño sin saber como estructurar nuestro proyecto, la estructura de nuestro repositorio definirá en gran medida el formato de publicación de nuestro sistema de diseño sea:

1. [monorepositorio-versionado-a-nivel-de-componente.md](monorepositorio-versionado-a-nivel-de-componente.md "mention")
2. [monorepositorio-versionado-a-nivel-de-sistema-de-diseno.md](monorepositorio-versionado-a-nivel-de-sistema-de-diseno.md "mention")

## ¿Por qué monorepositorio para sistemas de  diseño?

Es la forma más eficiente de asilar las herramientas que gira  entorno a nuestro sistema de diseño.

### Recomendaciones para su monorepositorio

#### 1. Aislé su Storybook como package.

Esto mantendrá limpio el workspaces.

#### 2. Adjunte las historias para Storybook en a nivel de componente.

Storybook puede consumir las historias fuera de su repositorio

```bash
packages
├─ components
│  └─ my-button
│     └─ src
│        └─ define.stories.tsx
│
└─ storybook 
```



