---
description: Recupere un nodo superior al webcomponent actual.
---

# use-parent

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useResponsiveState } from "@atomico/hooks/use-responsive-state";
```

### Sintaxis

```jsx
const selector = "form";
const parent = useParent(selector);
```

Donde:

* `selector`: string,  Selector a ser usado por `Element.matches`al buscar el padre.
* `parent`: Element, resultado de búsqueda ascendente  según selector.

