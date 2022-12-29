---
description: >-
  Facilita la gestión de tokens como variables de css para sistemas de diseños o
  aplicaciones.
---

# @atomico/postcss-tokens

## Sintaxis

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

## Ejemplo de transformacion

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
Fichero de entrada con importación

```css
@tokens "./tokens.yaml" (root: ":root");
```

Fichero de salida&#x20;

```css
:root{
    --myprefix--color-primary-text: white;
    --myprefix--color-primary-background: tomato;
}
```
{% endtab %}

{% tab title="tokens.css (:host)" %}
Fichero de entrada con importacion

```css
@tokens "./tokens.yaml";
```

Fichero de salida&#x20;

```css
:host{
    --color-primary-text: var(--myprefix--color-primary-text);
    --color-primary-background: var(--myprefix--color-primary-background);
}
```
{% endtab %}
{% endtabs %}

## Configuracion



