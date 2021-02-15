---
description: >-
  Una microlibrería inspirada en React Hooks, diseñada y optimizada para la
  creación de webcomponentes.
---

# 👋 Atomico

```jsx
import { c } from "atomico"; // 2.5kB

function component({ name }) {
  return <host shadowDom>Hello, {name}</host>;
}

component.props = {
  name: String,
};

customElements.define("my-component", c(component));
```

Atomico simplifica el aprendizaje, flujo de trabajo y el mantenimiento al crear webcomponents y lo  logra con :

1. Comportamiento funcional: Olvídese del uso de clases, declaración de propiedades setter/getter y complicados métodos de ciclo de vida. Atomico logra todo lo que necesitaras desde una simple función. 
2. Logica basada en hooks:  Atomico implementa el API de hooks de React,  consiguiendo así una composición funcional eficiente y altamente reutilizable.
3. VirtualDOM diseñado para webcomponents.

### Api

{% page-ref page="guias/props.md" %}

{% page-ref page="guias/hooks/" %}

{% page-ref page="guias/testing/" %}

{% page-ref page="guias/virtualdom.md" %}



