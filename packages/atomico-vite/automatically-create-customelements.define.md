---
description: >-
  With @atomico/vite you can automate the declaration of customElements.define,
  @atomico/vite will transform the export of your customElement into a record
  for customElements.define.
---

# 🤖 Automatically create customElements.define

<figure><img src="../../.gitbook/assets/Group 260.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Atomico will transform the export name of your web component to **kebab case**. For example, `MyComponent` will be transformed to `my-component`. **Additionally, you can configure the plugin to add a prefix.**
{% endhint %}

### Config

```javascript
import atomico from "@atomico/vite";

export default {
  plugins: atomico({
    customElements: {
      // Optional, prefix for your customElements
      prefix: "a",
      // component folders to associate the customElement
      define: ["components/src/**/*"],
    },
  }),
};
```
