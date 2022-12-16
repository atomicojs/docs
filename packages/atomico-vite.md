---
description: Improves the webcomponent development experience in vite and its ecosystem.
---

# @atomico/vite

`@atomico/vite` improve the development experience by solving the following objectives:

1. Allow the use of postcss in Atomico's CSS Template Literals.
2. Automatically create customElements.define
3. Support Atomico + Vite + Storybook
4. Support Atomico + Vite + Vitest
5. Facilitate the export of JS and TS code in library format

## Allow the use of postcss in Atomico's CSS Template Literals.

With `@atomico/vite` you can compile your css template string through postcss. Thanks to this feature you can use sass, autoprefixer, tailwind or minify the css of your template string

<figure><img src="../.gitbook/assets/Group 259.png" alt=""><figcaption></figcaption></figure>

### setting

<pre class="language-javascript"><code class="lang-javascript"><strong>import atomico from "@atomico/vite";
</strong>
export default {
  plugins: atomico({
    cssLiterals: { postcss: true },
  }),
};
</code></pre>

## Automatically create customElements.define

With `@atomico/vite` you can automate the declaration of customElements.define, `@atomico/vite` will transform the export of your customElement into a record for customElements.define.

<figure><img src="../.gitbook/assets/Group 260.png" alt=""><figcaption></figcaption></figure>

```javascript
import atomico from "@atomico/vite";

export default {
  plugins: atomico({
    customElements: {
      // prefix for your customElements
      prefix: "a",
      // component folders to associate the customElement
      define: ["components/src/**/*"],
    },
  }),
};
```
