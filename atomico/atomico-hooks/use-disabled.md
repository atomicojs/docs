---
description: Sincroniza el estado de la prop disabled con el tag fieldset
---

# use-disabled

Heredar el estado deshabilitado de una etiqueta de conjunto de campos, bajo ciertas reglas:

1. La etiqueta debe estar en el lightDOM.
2. El componente que usa este gancho debe declarar la propiedad deshabilitada.

### Import

```javascript
import { useDisabled } from "@atomico/hooks/use-disabled";
```

### Sintaxis 

```typescript
const disabled:boolean = useDisabled();
```

### Parámetros

1. `matches`: string, permite cambiar la búsqueda del padre `fieldset` por otro tag o selector. 

### Ejemplo

```jsx
import { c, css } from "atomico";

function component(){
    const disabled = useDisabled();
    return <host>
        <button disabled={disabled}><slot/></button>
    </host>;
}

component.props = { disabled: Boolean };

component.styles = css`
    :host([disabled]){
        pointer-events: none;
    }
`;

customElements.define("my-component", c(component));
```



