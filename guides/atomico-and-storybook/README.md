# 📖 Atomico and Storybook

## Status

* [x] **Decorator,** Atomico's decorator extends atomico's rendering capabilities to storybook.
* [x] **Monorepo,** We invite you to use the recipe through the CLI `npm init atomico`, you can also find this [configuration on Github](https://github.com/atomicojs/base/tree/storybook-monorepo)
* [x] Decorator for Storybook, Easily render webcomponents created with Atomico inside storytbook stories.&#x20;
* [x] storybook 7 and storybook + Vite
* [x] **MDX.**&#x20;

## @Atomico/storybook

{% content-ref url="../../packages/atomico-storybook.md" %}
[atomico-storybook.md](../../packages/atomico-storybook.md)
{% endcontent-ref %}

### decorador

Easily render webcomponents created with Atomico inside storytbook stories.&#x20;

**.storybook/preview.js**

```typescript
import { decorator } from "@atomico/storybook";

export const decorators = [decorator];
```

### define

It facilitates the creation of stories, analyzing the components created with Atomico to automatically define the `argTypes` and `args`.

```tsx
import { define } from "@atomico/storybook";
import { ColorPicker } from "./color-picker";

export default {
  title: "components/brand",
  ...define(ColorPicker)
};

export const Default = (props: any) => <ColorPicker {...props}></ColorPicker>;
```

define also improves the declaration of stories by improving the autocompletion of these.



## @atomico/vite

`@atomico/vite` has exclusive storybook utilities, with these it seeks to facilitate the use of Atomico's JSX /TSX and live reload.

### Config storybook 7

{% tabs %}
{% tab title=".storybook/main.mjs" %}
```javascript
import { mergeConfig } from "vite";

export default {
    stories: [
        // 📌 remember to define the path according to your configuration
        "../../components/**/*.stories.mdx",
        "../../components/**/*.stories.@(js|jsx|ts|tsx)",
        "../../components/*.stories.mdx",
        "../../components/*.stories.@(js|jsx|ts|tsx)",
    ],
    addons: ["@storybook/addon-links", "@storybook/addon-essentials"],
    framework: {
        name: "@storybook/web-components-vite",
        options: {},
    },
    async viteFinal(config, { configType }) {
        // 📌 return the customized config
        return mergeConfig(config, {
            plugins: [
                ...(await import("@atomico/vite")).default({
                    // 📌 needed to define files that use JSX/TSX
                    storybook: ["components/**/*"],
                }),
            ],
        });
    },
};
v
```
{% endtab %}

{% tab title="package.json" %}
```json
{
  "type": "module",
  "scripts": {
    "storybook": "storybook dev -p 6006",
    "build-storybook": "storybook build"
  },
  "dependencies": {
    "atomico": "^1.68.0"
  },
  "devDependencies": {
    "@atomico/storybook": "^1.5.0",
    "@atomico/tsconfig": "^1.1.2",
    "@atomico/vite": "^2.3.2",
    "@storybook/addon-actions": "^7.0.0-alpha.47",
    "@storybook/addon-essentials": "^7.0.0-alpha.47",
    "@storybook/addon-links": "^7.0.0-alpha.47",
    "@storybook/web-components": "^7.0.0-alpha.47",
    "@storybook/web-components-vite": "^7.0.0-alpha.47",
    "lit-html": "^2.4.0",
    "storybook": "^7.0.0-alpha.47",
    "vite": "^3.2.2"
  }
}
```
{% endtab %}
{% endtabs %}

{% content-ref url="frequent-questions.md" %}
[frequent-questions.md](frequent-questions.md)
{% endcontent-ref %}





