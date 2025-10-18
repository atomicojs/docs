---
description: >-
  A micro library inspired by React Hooks, designed and optimized for the
  creation of webcomponents.
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

Atomico simplifies learning, workflow and maintenance when creating webcomponents and achieves it with:

1. **Scalable and reusable interfaces**: with Atomico the code is simpler and you can apply practices that facilitate the reuse of your code.
2. **Open communication**: with Atomico you can communicate states by events, properties or methods.
3. **Agnostic**: your custom Element will work in any web-compatible library, eg React, Vue, Svelte or Angular.
4. **Performance**: Atomico has a comparative performance at Svelte levels, winning the third position in performance according to [**webcomponents.dev**](https://twitter.com/atomicojs/status/1391775734641745929) in a comparison of 55 libraries among which is React, Vue, Stencil and Lit.

### API

{% content-ref url="api/props/" %}
[props](api/props/)
{% endcontent-ref %}

{% content-ref url="api/virtualdom/" %}
[virtualdom](api/virtualdom/)
{% endcontent-ref %}

{% content-ref url="api/hooks/" %}
[hooks](api/hooks/)
{% endcontent-ref %}

{% content-ref url="api/testing/" %}
[testing](api/testing/)
{% endcontent-ref %}
