---
description: >-
  By default, Storybook does not support Atomico's JSX/TSX. With @atomico/vite,
  you will be able to use Atomico's syntax in your stories for Storybook.
---

# 📕 Use the JSX/TSX syntax of Atomico when using Storybook.

## Support Atomico + Vite + Storybook

Take advantage of automatic Storybook support in React, to cover the use of TSX/JSX. This allows both React and Atomic to Coexist in the same environment within the TSX/JSX Storybook.

### Config

```javascript
import atomico from "@atomico/vite";

export default {
  plugins: atomico({
    // Atomico components using Storybook with TSX/JSX
    storybook: ["components/**/*"],
  }),
};
```
