---
description: Wrapper to use webcomponents in React
---

# @atomico/react

{% embed url="https://github.com/atomicojs/react" %}

### ¿What is @atomico/react?

It is a Wrapper to eliminate React's own problems when rendering webcomponents, with @atomico/react you can:

1. Using your webcomponent's type declarations in React/Preact
2. Synchronize the events of your webcomponents with React
3. Composition from React using children and slots
4. Use SSR of your webcomponents in React/Preact based environments for example Next.js

### When to use @atomico/react?

We recommend using Atomico/react when looking to support React or Preact from your webcomponents built with Atomico.

{% hint style="success" %}
We also support vue with @atomico/vue
{% endhint %}

### @atomico/react vs other solutions?

With Atomico/react it's really easy to use, example:&#x20;

{% tabs %}
{% tab title="@atomico/react" %}
```tsx
import { auto } from "@atomico/react";
import { MyComponent as _MyComponent } from "./my-component.js";

export const MyComponent = auto( _MyComponent );
```
{% endtab %}

{% tab title="@lit-labs/react" %}
```tsx
import * as React from 'react';
import { createComponent } from '@lit-labs/react';
import { MyComponent as _MyComponent } from './my-component.js';

export const MyComponent = createComponent({
  tagName: 'my-component', //⚠️ requires the tagName
  elementClass: _MyComponent, 
  react: React, //⚠️ requires react module
  events: { //⚠️ requires events
    onactivate: 'activate',
    onchange: 'change',
  },
});
```
{% endtab %}
{% endtabs %}

### Example

```jsx
import { auto } from "@atomico/react";
import { HTMLMyComponent } from "./my-component.js";

export const MyComponent = auto( HTMLMyComponent );
```

{% embed url="https://codesandbox.io/s/atomico-react-example-cizcy" %}

### @atomico/exports

We invite you to meet [@atomico/exports](atomico-react.md#atomico-exports) to automate the generation of wrappers for your webcomponents

{% content-ref url="introduction/" %}
[introduction](introduction/)
{% endcontent-ref %}
