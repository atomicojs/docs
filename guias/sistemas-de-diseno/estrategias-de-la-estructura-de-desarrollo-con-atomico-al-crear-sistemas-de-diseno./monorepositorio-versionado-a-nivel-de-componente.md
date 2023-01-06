---
description: >-
  Trata de un repositorio que posee componentes versionados a nivel del
  componente, esto quiere decir que cualquier cambio a nivel de componente
  generara una nueva versión del componente.
---

# Monorepositorio versionado a nivel de componente

Esta es la estrategia más habitual al momento de crear sistemas de diseño, ya que permite individualizar los cambios a nivel de componente, gracias a que cada componente posee su package.json con los siguientes objetivos:

* **Versionamiento**: Trata de cada package estará versionado, ejemplo `@ds/button@1.0.0`, esto permite que podamos agregar mejoras o corregir problemas apuntando solo a la versión del componente afectado.
* **Mantenimiento**: Al ser un package, podemos individualizar sus dependencias y pruebas, lo que facilita el mantenimiento.
*   **Abstracción**: Trata de que cada componente aislara en su package los slots de composición(Subcomponentes que únicamente dependen del componente principal, ejemplo el tag option depende del tag select) y alguna otra utilidad especifica del componente.



### Ejemplo de estructura

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

### Ejemplo de importacion individual

```javascript
import { Button } from "@ds/my-button";
```

### Ejemplo de importación a nivel de sistema

```javascript
import { Button } from "@ds/components";
```
