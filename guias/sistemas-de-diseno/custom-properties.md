---
description: Teoriza de forma practica la definición de variables para sistemas de diseño
---

# Custom properties

> Recomendación personal como [autor de Atomico\(@uppercod\)](https://twitter.com/uppercod), siéntase libre de seguirla o enseñarme mejores practicas.

### Custom properties de thema

Son las variables externas a nuestro sistema de diseño y pertenecen al sitio o aplicación que implementa nuestro sistema de diseño.

```css
:root{
    --theme-primary: black;
    --theme-font-display: "font-title";
    --theme-font-content: "font-content";
}
```

#### Sintaxis

```css
:root{
    --theme-<utility>: value;
}
```

Donde: 

1. utility: Toda utilidad que se asocia al tema, ejemplo tamaño de letra, márgenes, espacios, color, fondo y estado.

El prefijo no es estricto, ya que estas son heredadas directamente del sitio o aplicación.

### Custom properties del sistema de diseño

**Contexto global**: todas las variables compartidas por nuestro sistema de diseño, estas solo se importan una sola para todos los componentes.

**Sintaxis**: 

```css
:root{
    --<prefix>-<utility>: <value>;
}
```

**Ejemplo**

{% tabs %}
{% tab title="css" %}
```css
:root{
    --ds-primary: var(--theme-primary);
}
```
{% endtab %}

{% tab title="importación" %}
```markup
<link rel="stylesheet" href="my-ds.css">
```
{% endtab %}
{% endtabs %}

Del ejemplo de `importación` quiero que infiera que todas las custom properties globales del sistema de diseño se encuentran solo en el archivo my-ds.css, el beneficio de esto es la importación desde el documento principal, permitiéndonos:

1.  Evitar el bloqueo de la importación tipográfica. 
2. Estilos antes de la carga, podremos anteponernos a la definición de carga de nuestros componente con estilos bases para mejorar los [**web vitals**](https://web.dev/vitals/) ****o simplemente ocultar nuestro componente para evitar una visualización antes de su carga, ejemplo en tab `Ejemplo de estilos ante de la carga`.
3. Las variables globales podrán ser referenciadas por el componente sin una importación por parte del componente, ejemplo en tab `ejemplo de uso de variables globales`.

{% tabs %}
{% tab title="Ejemplo de estilos ante de la carga" %}
```css
/**
Nuestro componente solo mostrará uno
una vez que se haya registrado.
**/
my-component:not(:defined){
    visibility: hidden;
}
```
{% endtab %}

{% tab title="ejemplo de uso de variables globales" %}
```javascript
// Esto no evita que el componente posea 
// propiedades únicas o compartidas entre 
// un grupo de componentes.
button.styles = css`
  :host {
    background: var(--ds-primary);
  }
  :host[warning] {
    background: var(--ds-warning);
  }
  :host[success] {
    background: var(--ds-success);
  }
`;
```
{% endtab %}
{% endtabs %}

**Contexto local**

```javascript
button.styles = css`
  :host {
    background: var(--ds-button-background);
  }
`;
```

Pero como recomendación evite atomizar lar custom properties, es mas practico generalizar, ya que reduce la complejidad de edición del mismo sistema de diseño, pero esto dependerá directamente del diseño de la UI. Supongamos que hemos formalizado el espacio de acción para todo componente cliqueable, ejemplo: 

```css
:root{
    --ds-action-space: padding: .5rem 1rem;
}
```

la custom property expuesta podrá ser heredada entre componentes tipo input, button, link, tags y mas.  

