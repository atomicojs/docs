# 📖 Atomico and Storybook

## Status

* [x] **Decorator,** Atomico's decorator extends atomico's rendering capabilities to storybook.
* [x] **Monorepo,** We invite you to use the recipe through the CLI `npm init atomico`, you can also find this [configuration on Github](https://github.com/atomicojs/base/tree/storybook-monorepo)
* [ ] **MDX**, in progress investigation...

## Frequent questions

### How to render a webcomponent in Storybook with React

we recommend using [@atomico/react](../packages/atomico-react.md), this package creates a friendly wrapper for React.

{% hint style="info" %}
Using [@atomico/react](../packages/atomico-react.md) requires the following script to be imported into the .storybook/preview.js file
{% endhint %}

```javascript
import "@atomico/react/proxy";
```
