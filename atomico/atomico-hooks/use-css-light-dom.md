---
description: use CSS en el lightDOM localmente en el webcomponent.
---

# use-css-light-dom

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useCssLightDom } from "@atomico/hooks/use-css-light-dom";
```

### Sintaxis

```jsx
const css = useCssLightDom();

return (
  <host
    class={css`
      width: 100px;
      height: 100px;
      :hover {
        background: red;
      }
    `}
  >
    <slot ref={ref}></slot>
  </host>
);
```

