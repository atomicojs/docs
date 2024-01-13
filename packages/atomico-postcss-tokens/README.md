---
description: >-
  Makes it easy to manage tokens as CSS custom properties for design system
  development
---

# @atomico/postcss-tokens

`@atomico/postcss-tokens` works through yaml or json files that declare tokens to be later imported from CSS files using the [@tokens](./#atrule-tokens) atRule. Through @tokens you can define if the resource to be generated should be global in scope **(:root)** or at the webcomponent level **(:host)**

## Token syntax

Tokens are declared using YAML to JSON files, token declarations can be:

1. simple: object declaring only token property and value
2. variations by attributes: object that declares the tokens according to the assignment of an attribute at the webcomponent level

### Example of simple tokens

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

### Example of variations by attributes

This type of declaration allows assigning tokens according to the attribute of a webcomponent

{% tabs %}
{% tab title="Yaml" %}
```yaml
space:
  around: 1rem
  between: 1rem
  safe: .5rem
  (size=small):
    around: .8rem
    between: .8rem
    safe: .4rem
```
{% endtab %}
{% endtabs %}

Thanks to this type of declaration you will be able to manage the variations directly from the token file.

## AtRule @tokens

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
@tokens "./tokens.yaml" scope(:root);
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
@tokens "./tokens.yaml" scope(:root);
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
    @tokens "./tokens.yaml" filter(color);
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

### use: string

It behaves similarly to filter, but with the big difference that **filter** preserves the scope structure vs **use** that shortens it, example:&#x20;

{% tabs %}
{% tab title="Input CSS" %}
```css
export const GenericStateTokens = css`
    @tokens "./tokens.yaml" use(color);
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



