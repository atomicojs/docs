---
description: Asocia un evento a una referencia
---

# use-listener

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useListener } from "@atomico/hooks/use-listener";
```

### Sintaxis 

```jsx
useListener(
    ref: Ref<Element>, 
    name: string, 
    handler: (event)=>void, 
    option?: boolean | AddEventListenerOptions 
);
```

### Ejemplo

```jsx
import { useRef } from "atomico";
import { useListener } from "@atomico/hooks/use-listener";

function component(){
    const ref = useRef();
    
    useListener(ref,"input", console.log);
    
    return <host>
        <input ref={ref}/>
    </host>
}
```

