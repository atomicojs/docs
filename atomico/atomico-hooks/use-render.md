---
description: >-
  Ejecuta un segundo render antes del render del webcomponent, ideal para
  trabajo colaborativo entre shadowDOM y lightDOM
---

# use-render

### Sintaxis

```jsx
useRender(()=><input type="text"/>,optionalArguments);
```

### Ejemplo

En ocasiones se trabaja con shadowDOM inputs, el shadowDOM evita la comunicación de eventos con un formulario superior al shadowDOM, \`useRender\`, permite crear inputs en el lightDOM y así mantener los efectos deseados. 

```jsx
import { useProp } from "atomico";
import { useRender } from "@atomico/hooks/use-render";

function myInput({name}) {
  const [checked, setChecked] = useProp("checked");
  const toggle = () => setChecked(!checked);
  // El estado del webcomponent se podra reflejar 
  // en el formulario ejemplo usando formData
  useRender(() => <input type="checkbox" name={name} checked={checked} />);
  return (
    <host shadowDom>
      <button onclick={toggle}>{checked ? "✔️" : "❌"}</button>
    </host>
  );
}

myInput.props = {
  name:  String,
  checked: Boolean,
};
```

