---
description: >-
  Accelerates the implementation of design tokens in web components in a
  sustainable and scalable way
---

# @atomico/design-tokens

{% embed url="https://github.com/atomicojs/design-tokens" %}

With `@atomico/design-tokens` you can:

1. [Resolve scalability and maintenance issues with your design tokens.](./#resolve-scalability-and-maintenance-issues-with-your-design-tokens.)
2. [Create utility classes from design tokens.](./#create-utility-classes-to-be-used-internally-by-your-component-system.)

### Resolve scalability and maintenance issues with your design tokens.

Design systems are complex to develop, due to the number of configurations that are shared between all our components, with `@atomico/design-tokens` we will solve:

1. Naming problems of the custom properties of your design tokens.
2. Legibility of your CSS.

#### How does @atomico/design-tokens solve the scalability of your design tokens?

For this example we will use Atomico, by the way you can use `@atomico/design-tokens` with any library.

```javascript
import { css } from "atomico";
import { compose, tokens } from "@atomico/design-tokens";

const designTokens = compose(
  tokens(
    {
      size: {
        xl: "40px",
        l: "32px",
        m: "28px",
        s: "20px",
      },
    },
    "ds"
  )
);

export const tokens = designTokens(css``);
```

The result of the CSS will be the following:

```css
:host {
  --size-xl: var(--ds--size-xl, 40px);
  --size-l: var(--ds--size-l, 32px);
  --size-m: var(--ds--size-m, 28px);
  --size-s: var(--ds--size-s, 20px);
}
```

This is a technique that I have created to improve the scalability of design tokens, with it you can:

1. edit token globally using custom properties:

```css
:root {
  --my-ds-size-xl: 50px;
}
```

> This is also applicable within a selector.

1. Simplify maintenance, since your components will use the custom properties without a prefix:

```jsx
import { c, css } from "atomico";
import tokens from "./tokens";
function button() {
  return (
    <host shadowDom>
      <slot />
    </host>
  );
}

button.styles = [
  tokens,
  css`
    :host {
      height: var(--size-xl);
      background: var(--color-primary-60);
      padding: var(--size-xxs) var(--size-xs);
    }
  `,
];
```

### Create utility classes to be used internally by your component system.

I am personally a fan of custom properties, but their use would become repetitive, to avoid this and improve maintenance @atomico/design-tokens introduces `classes`, a generator of utility classes based on the proposed design tokens, example:

```javascript
import { css } from "atomico";
import { compose, tokens, classes } from "@atomico/design-tokens";

const designTokens = compose(
  classes({
    size: {
      xl: "40px",
      l: "32px",
      m: "28px",
      s: "20px",
    },
  })
);

export const tokensSize = designTokens(
  css`
    .gap.--size {
      gap: var(--size);
    }
  `
);
```

The `classes` middleware will parse the CSSStyleSheet to relate the custom propeprtiy `--size` as a class of `.gap`, internally the `css` will be as follows:

```css
.gap\.xl {
  gap: var(--size-xl);
}

.gap\.l {
  gap: var(--size-l);
}

.gap\.m {
  gap: var(--size-m);
}

.gap\.s {
  gap: var(--size-s);
}
```

This makes it really simple to reuse the tokens, example:

```jsx
import { c } from "atomico";
import { tokensSize } from "./tokens";

function button() {
  return (
    <host shadowDom>
      <button class="gap.xl">
        <slot />
      </button>
    </host>
  );
}

button.styles = tokensSize;

customElements.define("my-button", c(button));
```

{% content-ref url="atomico-design-tokens-api.md" %}
[atomico-design-tokens-api.md](atomico-design-tokens-api.md)
{% endcontent-ref %}
