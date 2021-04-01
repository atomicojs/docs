---
description: >-
  Captura todos los nodos no creados por el render del webcomponent, ideal para
  aplicar polyfill de slot en LightDOM.
---

# use-child-nodes

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useChildNodes } from "@atomico/hooks/use-child-nodes";
```

### Sintaxis

```javascript
const [childNodes, update] = useChildNodes();
```

Donde :

1. `childNodes` : Lista de nodos que no pertenecen al render del webcomponent.
2. `update`: Callback que fuerza una nueva exploración de `childNodes`.

### Ejemplo

```jsx
function component() {
  const [childNodes] = useChildNodes();
  return (
    <host>
      {childNodes
        .filter((node) => node.localName == "h1")
        .map((Title) => (
          <Title onclick={() => console.log("click h1!")} />
        ))}
    </host>
  );
}
```

Del ejemplo podemos destacar que el webcomponent usara todos los childrens no creados por el del tipo "h1" y asociara a estos el handler onclick.

