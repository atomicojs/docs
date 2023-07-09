---
description: >-
  This package is used by @atomico/react and @atomico/vue to retrieve the
  tagName of the customElement registered through customElements.define
---

# @atomico/wrapper

Additionally, this package offers other utilities.

### @atomico/wrapper/allow-deduple&#x20;

This is an optional import module that allows coexistence of multiple versions of web components in JSX-based environments (Atomico, React, or Preact) and Vue, specifically when using @atomico/vue. For example:&#x20;

1. Component `A` depends on `B@1`.&#x20;
2. Component `C` depends on `B@2`.&#x20;

Normally, this would result in conflicts during registration at the browser level due to attempting to register the same tagName for component `B@*`. However, by importing the `allow-deduple` module, this works only if we use **JSX** or **Vue** for instantiations.

#### Instantiate via JSX

```tsx
<MyComponent/>
```

