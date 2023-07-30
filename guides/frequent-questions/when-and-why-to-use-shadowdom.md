# When and why to use shadowDom?

## When to use the shadow Dom?



## Why use shadowDOM?

To protect our component at the DOM manipulation level and take advantage of some of the benefits of the shadowDOM such as:

1. Slot management
2. CSS appearance of web component.

### Slot management

Slots allow us to reflect existing nodes in the lightDOM into the shadowDOM, example:

<figure><img src="../../.gitbook/assets/web_1366_7.png" alt=""><figcaption></figcaption></figure>

This is really useful, since we can group slots according to their name in a specific place of the webcomponent.

We invite you to learn more about slots through the following guide:

{% content-ref url="../atomico-design-patterns/slot.md" %}
[slot.md](../atomico-design-patterns/slot.md)
{% endcontent-ref %}

### CSS appearance of web component.

The shadowDOM allows you to do something fantastic, protect your CSS from global styles, this has 2 great advantages:

1. The appearance of our component will not be affected by global CSS declarations.
2. Customization protected by CSS custom Properties

We invite you to learn more about handling styles in atomic through the following guide:

