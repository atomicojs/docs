---
description: >-
  Genera un cuello de botella a la definición de un estado, limita la
  concurrencia.
---

# use-debounce-state

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useDebounceState } from "@atomico/hooks/use-debounce-state";
```

### Sintaxis

Este hook es similar a useState, pero con el objetivo de generar un cuello de botella al momento de actualizar el estado.

```javascript
const [state, setState] = useDebounceState(delay:number, initialState: any);
```

### Ejemplo

```jsx
function component() {
  const [state, setState] = useDebounceState(200);
  return (
    <host>  
        <input oninput={event=>setState(event.target.value)}/>
        {state} despues de 200ms
    </host>
  );
}
```



