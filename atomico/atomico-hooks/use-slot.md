---
description: Escucha el evento slotchange para obtener los assignedNodes del slot.
---

# use-slot

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useSlot } from "@atomico/hooks/use-slot";
```

### Sintaxis

```jsx
const slots:Node[] = useSlot(ref);
```

### Ejemplo

```jsx
const ref = useSlot();
const slots = useSlot(ref);

return (
  <host shadowDom>
    <slot ref={ref}></slot>
  </host>
);
```

