---
description: >-
  Makes it easy to manage tokens as CSS custom properties for design system
  development
---

# @atomico/postcss-tokens

## Syntax

{% tabs %}
{% tab title="Yaml" %}
```yaml
color:
  primary:
    text: white
    background: tomato
```
{% endtab %}

{% tab title="Json" %}
```json
{
  "color": {
    "primary": {
      "text": "white",
      "background": "tomato"
    }
  }
}
```
{% endtab %}

{% tab title="Style dictionary" %}
```json
{
  "color": {
    "primary": {
      "text": { "value": "white" },
      "background": { "value": "tomato" }
    }
  }
}
```
{% endtab %}
{% endtabs %}

### atRule @tokens

This atRule allows importing yaml or json files to be used as custom properties, example:



{% tabs %}
{% tab title="tokens.yaml" %}
```yaml
color:
  primary:
    text: white
    background: tomato
```
{% endtab %}

{% tab title="tokens.css (:root)" %}
**Importing the tokens.yaml file**

```css
@tokens "./tokens.yaml" (root: ":root");
```

**Output**

```css
:root{
    --myprefix--color-primary-text: white;
    --myprefix--color-primary-background: tomato;
}
```
{% endtab %}

{% tab title="tokens.css (:host)" %}
**Importing the tokens.yaml file**

```css
@tokens "./tokens.yaml";
```

**Output**

```css
:host{
    --color-primary-text: var(--myprefix--color-primary-text);
    --color-primary-background: var(--myprefix--color-primary-background);
}
```
{% endtab %}
{% endtabs %}

### root: string

Defines the type of root that will use the tokens, by default `":host"`, example:

```
@tokens "./tokens.yaml" (root: ":root");
```

Consider the following behaviors:

1. root puede ser cualquier tipo de selector
2. if root is equal to `":root"`, the build rules will work at the `:root/lightDOM` level.
3. if root is equal to `":host"`, the generation rules will work at the `:host/shadowDOM` level.

### filter: string

It will only take the tokens assigned in the filter to create the custom properties, example:&#x20;

{% tabs %}
{% tab title="Input CSS" %}
```css
export const GenericStateTokens = css`
    @tokens "./tokens.yaml" (filter: color);
`;
```
{% endtab %}

{% tab title="Output CSS" %}
```css
:host{
    --color-primary: var(--myprefix--color-primary);
    --color-secondary: var(--myprefix--color-secondary);
}
```
{% endtab %}

{% tab title="Tokens" %}
```yaml
size: 
    small: 1rem
    normal: 2rem
color: 
    primary: red
    secondary: gold
```
{% endtab %}
{% endtabs %}

From the previous example `@atomic/postcss-tokens` will only take the tokens from the color property.

### import: string

It behaves similarly to filter, but with the big difference that **filter** preserves the scope structure vs **import** that shortens it, example:&#x20;

{% tabs %}
{% tab title="Input CSS" %}
```css
export const GenericStateTokens = css`
    @tokens "./tokens.yaml" (import: color);
`;
```
{% endtab %}

{% tab title="Output CSS" %}
```css
:host{
    --primary: var(--myprefix--color-primary);
    --secondary: var(--myprefix--color-secondary);
}
```
{% endtab %}

{% tab title="Tokens" %}
```yaml
size: 
    small: 1rem
    normal: 2rem
color: 
    primary: red
    secondary: gold
```
{% endtab %}
{% endtabs %}

## Configuration in postcss

### prefix: string

Define el prefijo para las custom properties

### defaultValue : boolean

Define que las customProperties que trabaje a nivel de shadowDom poseeran un valor por defecto si no se declara el tokens en :root, ejemplo:

```css
:host{
    --color-primary: var(--my-ds--color-primary, red);
}
```



