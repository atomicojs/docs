---
description: Mejora la interacción con los formularios y accesibilidad de tus componentes.
---

# Formularios y ShadowDOM

Es normal que usemos la técnica de  despachar eventos desde el componente para comunicar estados y más, pero al usar formularios esto cambia ya que los eventos dentro del shadowDOM no interactúan con el formulario fuera de este, ejemplo:

```markup
<form>
    <my-input>
        #shador-root
            <input/>
    </my-input>
</form>
```

para resolver esto deberemos anidar un tag input en el lightDOM de nuestro componente, para así reflejar la lógica de de este al formulario. Atomico facilita esta interacción hibrida entre lightDOM y shadowDOM con el hook [**@atomico/hooks/use-render**](../atomico/atomico-hooks/use-render.md) que permite ejecutar un segundo render que trabaje desde el lightDOM, ejemplo:

```jsx
import { useRender } from "@atomico/hooks/use-render";

function myInput(){
    // render LightDOM
    useRender(()=><input/>);
    
    // render ShadowDOM
    return <host shadowDom>
        <slot/>
    </host>
}
```

Con esto has ganado control total sobre el tag input existente en el lightDOM, permitiéndote aplicar estilos usando el selector `::slotted`, ejemplo:

```javascript
myInput.styles = css`
    :slotted(input){
        border: 1px solid black;
        height: 40px;
    }
`;
```

hemos creado un tag input que permite interactuar directamente con el formulario, esta técnica es aplicable con todos los tags que interactúan con el tag `<form>`, ejemplo `<button>`, `<textarea>` y `<input>`.

