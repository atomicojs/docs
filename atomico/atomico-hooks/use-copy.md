---
description: Copia el contenido en formato de texto de una referencia.
---

# use-copy

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useCopy } from "@atomico/hooks/use-copy";
```

### Sintaxis

```javascript
const copy:()=>void = useCopy(ref);
```

Donde :

1. `ref` : Referencia del nodo a copiar
2. `copy`: Callback, copia el contenido a la papelera del cliente.

### Ejemplo

```jsx
function component() {
  const ref = useRef();
  const copy = useCopy(ref);
  return (
    <host>  
      <textarea ref={ref}></textarea>
      <button onclick={copy}>Copy!</button>
    </host>
  );
}
```



