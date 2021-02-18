---
description: >-
  Permite forzar la renderización del webcomponent sin la necesidad de estar
  ligado a un estado o propiedad
---

# useForceRender

### Instalación

```bash
npm install @atomico/kit
```

### Modulo

```javascript
import { useForceRender } from "@atomico/kit/use-force-render";
```

### Sintaxis

```javascript
 const forceRender = useForceRender();
```

Donde: 

1. `forceRender`: Callback para forzar la renderización del webcomponent.

### Ejemplo

En ocasiones la renderización del webcomponent no depende de un estado o propiedad de este, para reflejar dichos cambios  puede usar `useForceRender` para regenerar el DOM, ejemplo:

```jsx
function component() {
  const ref = useRef();
  const forceRender = useForceRender();

  return (
    <host>
      {ref.current.anyProp}
      <my-component ref={ref} onclick={forceRender}></my-component>
    </host>
  );
}
```

