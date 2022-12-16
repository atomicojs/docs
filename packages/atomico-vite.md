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

### Config

<pre class="language-javascript"><code class="lang-javascript"><strong>import atomico from "@atomico/vite";
</strong>
export default {
  plugins: atomico({
    cssLiterals: { 
      postcss: true,
      // Optional, minify the css code
      minify: true
    },
  }),
};
</code></pre>

## Automatically create customElements.define

With `@atomico/vite` you can automate the declaration of customElements.define, `@atomico/vite` will transform the export of your customElement into a record for customElements.define.

<figure><img src="../.gitbook/assets/Group 260.png" alt=""><figcaption></figcaption></figure>

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

## Support Atomico + Vite + Vitest

Improve the experience of the atomico fixture function in vitest.

```javascript
import atomico from "@atomico/vite";

export default {
  plugins: atomico({
    vitest: true,
  }),
};
```

## Facilitate the export of JS and TS code in library format

Configure the output of vite in library format for 1 or more Javascript or Typescript files:

```bash
npx library src/**/*
```

the above script will send all files found in the `src` folder to vite, example output:

```bash
# Input                        # Output
/src                            /lib
  /my-component-1.tsx             /my-component-1.js
  /my-component-2.tsx             /my-component-2.tsx
  /my-component-3.tsx             /my-component-3.tsx
```

{% hint style="success" %}
This script can be combined with [@atomico/exports](introduction/) to improve the generation of your package.json
{% endhint %}
