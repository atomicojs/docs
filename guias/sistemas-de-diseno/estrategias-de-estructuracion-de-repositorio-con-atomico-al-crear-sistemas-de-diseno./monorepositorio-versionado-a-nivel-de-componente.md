---
description: >-
  Trata de un repositorio que posee un sistema de diseño versionados por
  componentes
---

# Monorepositorio versionado a nivel de componente

Es la estrategia más habitual al momento de crear sistemas de diseño, ya que permite individualizar los cambios a nivel de componente:

### Ventajas&#x20;

Gracias a que cada componente posee su package.json se lograra:

* **Versionamiento**: Cada package estará versionado, ejemplo `@ds/button@1.0.0`, esto permite que podamos agregar mejoras o corregir problemas apuntando solo a la versión del componente afectado.
* **Mantenimiento**: Al ser un package, podemos individualizar sus dependencias y pruebas, lo que facilita el mantenimiento.
* **Abstracción**: Trata de que cada componente aislara en su package los slots de composición(Subcomponentes que únicamente dependen del componente principal, ejemplo el tag option depende del tag select) y alguna otra utilidad especifica del componente.

### Desventajas

Las siguientes desventajas son prácticas:

1. Mayor lentitud al crear nuevos componentes, ya que cada componente requerirá ser un nuevo package.
2. Mayor dificultad de centralización de componentes en un solo package, ya que cada cambio requerirá actualizar el package principal y adjuntar la nueva exportación.

{% hint style="info" %}
Las desventajas prácticas pueden ser reparadas mediante herramientas de CLI que automatizan la generación de archivos y centralización de packages
{% endhint %}

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

### Ejemplo de importación por componente

```javascript
import { Button } from "@ds/my-button";
```

### Ejemplo de importación por sistema de componentes

```javascript
import { Button } from "@ds/components";
```

