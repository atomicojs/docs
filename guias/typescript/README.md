---
description: Mejora la experiencia de desarrollo de Atomico al usar JSDOC o Typescript.
---

# 📜 Typescript & JSDOC

## Componente

### Props\<typeof component.props>

Permite recuperar los tipos del objeto `props` asociado a la función.

{% tabs %}
{% tab title="Typescript" %}
```typescript
import { Props, c } from "atomico";

function component(props: Props<typeof component.props>) {
  return <host shadowDom>
    Atomico + Typescript
  </host>
}

component.props = {
    propString: String,
    propObject: {
        type: Object,
        value: (): { prop?: number } => ({}),
    },
};

customElements.define("my-component", c(component));import { Props, c } from "atomico";
```
{% endtab %}

{% tab title="JSDOC" %}
```jsx
import { c } from "atomico";
/**
 * @param {import("atomico").Props<component.props>} props
 */
function component(props) {
  return <host shadowDom>
    Atomico + Typescript
  </host>
}

component.props = {
    propString: String,
    propObject: {
        type: Object,
        value: (): { prop?: number } => ({}),
    },
};

customElements.define("my-component", c(component));
```
{% endtab %}
{% endtabs %}

### Component

{% tabs %}
{% tab title="Typescript" %}
```typescript
import { c, Component } from "atomico";

const component: Component<{ value: string }> = (props) => {
  return <host shadowDom></host>;
};

component.props = {
  value: String,
}
```
{% endtab %}

{% tab title="JSDOC" %}
```jsx
import { c } from "atomico";
/**
 * @type {import("atomico").Component<{ value: string }>}
 */
const component = (props) => {
  return <host shadowDom></host>;
};

component.props = {
  value: String,
};
```
{% endtab %}
{% endtabs %}

## Hooks

La mayoría de los hooks infieren los tipos automática mente al usar Typescript, pero otros requieren una declaración para mejorar la experiencia de tipado, ejemplo:

### useProp

{% tabs %}
{% tab title="Typescript" %}
```typescript
const [value, setValue] = useProp<number>("value");
```
{% endtab %}

{% tab title="JSDOC" %}
```javascript
/** @type {import("atomico").UseProp<number>} */
const [value, setValue] = useProp("value");
```
{% endtab %}
{% endtabs %}

Fuerza el tipo `number`para `value` y `setValue`, según el ejemplo `value` solo puede ser del tipo `number`.

### useState

**useState infiere el tipo en la mayoría de los casos,** pero el no usar un estado inicial impide un tipado estricto, pude corregir esto de la siguiente manera:

{% tabs %}
{% tab title="Typescript" %}
```typescript
const [value, setValue] = useState<number>();
```
{% endtab %}

{% tab title="JSDOC" %}
```javascript
/** @type {import("atomico").UseState<number>}
const [value, setValue] = useState();
```
{% endtab %}
{% endtabs %}

Fuerza el tipo `number` para `value` y `setValue`, segun el ejemplo `value` solo puede ser del tipo `number`.

### useRef

{% tabs %}
{% tab title="Typescript" %}
```typescript
const ref = useRef<HTMLInputElement>();
```
{% endtab %}

{% tab title="JSDOC" %}
```javascript
/** @type{import("atomico").UseRef<HTMLInputElement>} */
const ref = useRef();
```
{% endtab %}
{% endtabs %}

Fuerza que **ref.current** se `HTMLInputElement`.
