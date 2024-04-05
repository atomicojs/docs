---
description: Improves the generation of stories in Storybook.
---

# @atomico/storybook

This package has 2 main objectives:

1. Render as stories webcomponents created with Atomico using JSX/TSX within Storybook
2. Facilitate and automate the generation of stories.



## Render as stories webcomponents created with Atomico using JSX/TSX within Storybook.

`@atomico/storybook` has a decorator that allows Storybook to render the JSX/TSX of webcomponents created with Atomico.

### **Config**

The following configuration can be added per story or in the `.storybook/preview.js` file:

```javascript
import { decorator } from "@atomico/storybook";

export const decorators = [decorator()];
```

## Facilitate and automate the generation of stories.

`@atomico/storybook` has the define function to infer from its webcomponent created with Atomico the configuration of the `argTypes` and `args` for Storybook, example:

{% tabs %}
{% tab title="my-component.stories.tsx" %}
```typescript
import { define } from "@atomico/storybook";
import { MyComponent } from "./my-component";

export default {
    title: "Components/Card",
    ...define(MyComponent),
};

export const Default = (props)=><MyComponent {...props}/>
```
{% endtab %}

{% tab title="my-component.tsx" %}
```javascript
import { c } from "atomico";

function myComponent() {
  return <host></host>;
}

myComponent.props = {
  checked: Boolean,
  message: String,
};

export const MyComponent = c(myComponent);

customElements.define("my-component", MyComponent);
```
{% endtab %}
{% endtabs %}

`@atomico/storybook` transforms its component's props into argTypes valid for Storybook.

You can also rewrite all or part of the configuration created by `@atomico/storybook` by giving the function `define` a second argument, example:

```typescript
export default {
  title: "Components/Card",
  ...define(MyComponent, {
    argTypes: {
      message: {
        // Opcional, define la categoria para la tabla.
        category: "Internals",
        description: "Define un mensaje para el componente",
      },
      checked: {
        control: "radio",
        options: ["Show", "Hide"],
      },
    },
  }),
};

```

{% hint style="danger" %}
You can use the spread operator according to the storybook configuration.&#x20;

* **Storybook 6.\* webpack 4 + Vite**, does not support the spread operator in the default export of your story.&#x20;
* **Storybook 7.\* + Vite**, if it supports the spread operator in its story.
* **Storybook 8.\* + Vite**, if it supports the spread operator in its story.
{% endhint %}

