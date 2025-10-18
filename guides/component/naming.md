---
description: Simple but useful
---

# Naming

If you are a React user, it is common for you to make component declarations like these:

```tsx
export function MyComponent(){
    return <>My component in react</>
}
```

Thanks to the previous code in React we can:

1. Instantiate your component through its function, example `<MyComponent>`
2. Friendly export component as module

In Atomico there are some small differences [👇](https://emojipedia.org/emoji/%F0%9F%91%87/)

## we recommend in Atomico

Export the return of the c function, since it is instantiable at the JSX level or when using the new operator, example:



{% tabs %}
{% tab title="my-component.tsx" %}
```tsx
export const MyComponent = c(() => <host>My component in Atomico</host>);

export const MyComponent = c(myComponent);

customElements.define("my-component", MyComponent);
```
{% endtab %}

{% tab title="Instance in JSX" %}
```tsx
import { MyComponent } from "./my-component";

function app(){
    return <host>    
        <MyComponent/>
    </host>
}
```
{% endtab %}

{% tab title="Instance in JS" %}
**Instance with operator new**: The new operator allows the instance to associate at the TS level the types declared using Atomico

```javascript
import { MyComponent } from "./my-component";

const component = new MyComponen; 
```

**Instance with document.createElement**&#x20;

<pre class="language-javascript"><code class="lang-javascript"><strong>import "./my-component";
</strong>
const component = document.createElement("my-component");
</code></pre>
{% endtab %}

{% tab title="Instance in HTML" %}
```markup
<my-component></my-component>
```
{% endtab %}
{% endtabs %}

Gracias a lo anterior podemos:

1. Instantiate your component with TS-level type validation either by using JSX or the new operator with, **but remember that to get this type of instances you must first have registered your customElement in the same file or another.**
2. Export the useful component to instantiate.

{% hint style="warning" %}
Prefer this export format because tools like @atomico/exports take advantage of this format to automatically create wrappers for React, Preact, and Vue.
{% endhint %}



