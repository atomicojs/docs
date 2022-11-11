# Frequent questions

### How to render a webcomponent in Storybook with React

The following error is the most common when using Atomico in Storybook with React.

```bash
localhost/:1 Uncaught DOMException: Failed to execute 'define' on 'CustomElementRegistry': this constructor has already been used with this registry
```

We recommend using [@atomico/react](../packages/atomico-react.md), this package creates a friendly wrapper for React.

{% hint style="info" %}
Using [@atomico/react](../packages/atomico-react.md) requires the following script to be imported into the .storybook/preview.js file
{% endhint %}

```javascript
import "@atomico/react/proxy";
```

