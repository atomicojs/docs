---
description: >-
  With @atomico/vite, you will be able to use the `atomico/test-dom` module
  without any issues.
---

# ☑ Support for Vitest for Atomico.

```javascript
import atomico from "@atomico/vite";

export default {
  plugins: atomico({
    vitest: true,
  }),
};
```
