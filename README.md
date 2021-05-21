---
description: >-
  Una microlibrería inspirada en React Hooks, diseñada y optimizada para la
  creación de webcomponentes.
---

# 👋 Atomico



{% tabs %}
{% tab title="JSX" %}
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
{% endtab %}

{% tab title="TSX" %}
```jsx
import { Props, c } from "atomico"; // 2.5kB

function component({ name }:Props<typeof component.props>) {
  return <host shadowDom>Hello, {name}</host>;
}

component.props = {
  name: String,
};

customElements.define("my-component", c(component));
```
{% endtab %}

{% tab title="JS" %}
```javascript
import { c, html } from "atomico"; // 3.0kB


function component({ name }) {
  return html`<host shadowDom>Hello, ${name}</host>`;
}

component.props = {
  name: String,
};

customElements.define("my-component", c(component));
```
{% endtab %}
{% endtabs %}

Atomico simplifica el aprendizaje, flujo de trabajo y el mantenimiento al crear webcomponents y lo  logra con :

1. **Interfaces escalable y reutilizable**: con Atomico el código es más simple y podrás aplicar practicas que faciliten la reutilización de tu código.
2. **Comunicación abierta**: su webcomponent podrá comunicar su estado sea por eventos, propiedades o métodos.
3. **Agnóstico**: su webcomponent servirá en cualquier librería compatible con la web, ejemplo React, Vue o Svelte.
4. **Performance**: Atomico posee un performance comparativo a niveles de Svelte, ganando la tercera posición en performance según [**webcomponents.dev**](https://twitter.com/atomicojs/status/1391775734641745929)  en una comparativa de 55 librerías entre las cuales esta React, Vue, Stencil y Lit.

### Api

{% page-ref page="api/props.md" %}

{% page-ref page="api/hooks/" %}

{% page-ref page="api/testing/" %}

{% page-ref page="api/virtualdom.md" %}

{% page-ref page="guias/sistemas-de-diseno.md" %}



