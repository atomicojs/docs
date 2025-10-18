---
description: >-
  Una microlibrería inspirada en React Hooks, diseñada y optimizada para la
  creación de webcomponentes.
---

# 👋 Atomico

![](.gitbook/assets/header-2.svg)

{% tabs %}
{% tab title="JSX" %}
```jsx
import { c } from "atomico"; // 2.5kB

const MyComponent = c(
  ({name})=><host shadowDom>Hello, {name}</host>,
  {
    props: { name: String }
  }
);

customElements.define("my-component", c(component));
```
{% endtab %}

{% tab title="TSX" %}
```jsx
import { c } from "atomico"; // 2.5kB

const MyComponent = c(
  ({name})=><host shadowDom>Hello, {name}</host>,
  {
    props: { name: String }
  }
);

customElements.define("my-component", c(component));
```
{% endtab %}
{% endtabs %}

Atomico simplifica el aprendizaje, flujo de trabajo y el mantenimiento al crear webcomponents y lo logra con :

1. **Interfaces escalable y reutilizable**: con Atomico el código es más simple y podrás aplicar practicas que faciliten la reutilización de tu código.
2. **Comunicación abierta**: su webcomponent podrá comunicar su estado sea por eventos, propiedades o métodos.
3. **Agnóstico**: su webcomponent servirá en cualquier librería compatible con la web, ejemplo React, Vue o Svelte.
4. **Performance**: Atomico posee un performance comparativo a niveles de Svelte, ganando la tercera posición en performance según [**webcomponents.dev**](https://twitter.com/atomicojs/status/1391775734641745929) en una comparativa de 55 librerías entre las cuales esta React, Vue, Stencil y Lit.

### Api

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="guias/sistemas-de-diseno/" %}
[sistemas-de-diseno](guias/sistemas-de-diseno/)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}
