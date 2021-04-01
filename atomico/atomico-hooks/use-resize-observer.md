---
description: Observa el cambio de tamaño de una referencia
---

# use-resize-observer

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useResizeObserver, useResizeObserverState } from "@atomico/hooks/use-resize-observer";
```

### Sintaxis

#### useResizeObserver

```javascript
useResizeObserver(
  ref,
  (rect) => void
);
```

Donde:

* `ref`: Ref, referencia a observar el redimensionamiento.
* `rect`: object,  el retorno de `DOMRectReadOnly.toJSON()`, documentación de [DOMRect](%20https://developer.mozilla.org/en-US/docs/Web/API/DOMRectReadOnly)
  * width
  * height
  * x
  * y
  * top
  * right
  * bottom
  * left

#### useResizeObserverState

```javascript
const rect = useResizeObserverState(ref);
```

Donde:

* `ref`: Ref, referencia a observar el redimensionamiento.
* `rect`: object,  el retorno de `DOMRectReadOnly.toJSON()`, documentación de [DOMRect](%20https://developer.mozilla.org/en-US/docs/Web/API/DOMRectReadOnly)
  * width
  * height
  * x
  * y
  * top
  * right
  * bottom
  * left

