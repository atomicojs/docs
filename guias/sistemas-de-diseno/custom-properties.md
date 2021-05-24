---
description: Teoriza de forma practica la definición de variables para sistemas de diseño
---

# Custom properties

> Recomendación personal como autor de Atomico\(@uppercod\), siéntase libre de seguirla o enseñarme mejores practicas.

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

El prefijo no es estricto ya que el contexto puede ser heredado de la plantilla.

### Custom properties del sistema de diseño

**Contexto global**: todas las variables compartidas por nuestro sistema de diseño, estas solo se importan una sola para todos los componentes.

**Sintaxis**: 

```css
:root{
    --<prefix>-<utility>: <value>;
}
```

**Ejemplo**

```css
:root{
    --ds-primary: var(--theme-primary);
}
```

Al ser una agrupación de variables globales podrán ser referenciadas por el componente sin una importación por parte del componente, ejemplo:

```javascript
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

Esto no evita que el componente posea propiedades únicas o compartidas entre un grupo de componentes, ejemplo:

**Contexto local**

```javascript
button.styles = css`
  :host {
    background: var(--ds-button-background);
  }
`;
```

Pero como recomendación evite atomizar lar custom properties, es mas practico generalizar, ya que reduce la complejidad de edición, ejemplo:

```javascript
input.styles = css`
  :host {
    background: var(--ds-primary);
    padding: var(--ds-input-padding);
  }
`;

button.styles = css`
  :host {
    background: var(--ds-primary);
    padding: var(--ds-input-padding);
  }
`;
```

Esto dependerá directamente del diseño UI

