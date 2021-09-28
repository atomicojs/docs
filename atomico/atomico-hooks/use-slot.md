---
description: Recupera los nodos asignados a un slot.
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

```javascript
const childNodes = useSlot(ref);
```

### Ejemplo

```jsx
import { useRef } from "atomico";
import { useSlot } from "@atomico/hooks/use-slot";

function component(){
    const ref = useRef();
    const childNodes = useSlot();
    return  <host shadowDom>
        <slot ref={ref}/>
        <h1>slot length {childNodes.length}</h1>
    </host>
}
```

