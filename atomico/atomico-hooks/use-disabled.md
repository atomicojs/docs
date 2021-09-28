---
description: Sincroniza el estado de la prop disabled con el tag fieldset
---

# use-disabled

Heredar el estado  `disabled` de una etiqueta padre tipo `fieldset` , bajo ciertas reglas:

1. La etiqueta debe estar en el lightDOM.
2. El componente que usa este hook debe declarar la prop \`{ disabled: Boolean}\`.

### Import

```javascript
import { useDisabled } from "@atomico/hooks/use-disabled";
```

### Sintaxis 

```typescript
const disabled:boolean = useDisabled(matches?: string = "fieldset");
```

### Parámetros

1. `matches`: string opcional, permite cambiar la búsqueda del tag padre `fieldset` por otro tag o selector compatible con `Element.matches` .

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



