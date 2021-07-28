---
description: >-
  Atomico posee un comportamiento funcional inspirado en React Hooks que no
  limita el uso de clases internas o externas a Atomico.
---

# Herencia de clases

### Clases externas a Atomico

```javascript
import { c, html } from "atomico";

function component() {
  return html`<host shadowDom> ...my content </host>`;
}

class VanillaElement extends HTMLElement {
  constructor() {
    super();
    console.log("create");
  }
  connectedCallback() {
    console.log("mount");
  }
  disconnectedCallback() {
    console.log("mount");
  }
  attributeChangedCallback() {
    console.log("my-attr update");
  }
  static get observedAttributes() {
    return ["my-attr"];
  }
  // ⚠️ not native but valid within Atomico.
  // this is just an example the ideal is to 
  // have a shared reference of the CSSStyleSheet
  static get styles(){
    const sheet= new CSSStyleSheet();
    sheet.replace('a { color: blue; }');
    return sheet;
  }
}


const Component = c( component,  VanillaElement );
```

`component`: función que declara el webcomponent para Atomico.

`VanillaElement`: es la clase que será extendida por Atomico para crear `Component`, Atomico no romperá el ciclo de vida del componente, permitiendo que estos interactúen libremente.

### Clases internas a Atomico

estas clases son las producidas por la función `c` de Atomico, estas pueden ser extendidas entre componentes, ejemplo:

```javascript
import { c, html, css } from "atomico";

function component1({ prop1 }) {
  return html`<host shadowDom> ...my content, ${prop1} </host>`;
}

component1.props = {
  prop1: String,
};

component1.styles = css`
  :host {
    font-size: 100px;
  }
`;

function component2({ prop1, prop2 }) {
  return html`<host shadowDom> ...my content, ${prop1} and ${prop2} </host>`;
}

component2.props = {
  prop2: String,
};

const Component1 = c(component1);

const Component2 = c(component2, Component1);

customElements.define("component-2", Component2);

```

Considere los siguientes efectos al usar este modelo de herencia:

1. El render será rescrito.
2. las props se hereda, Atomico reutilizara las props previamente declaradas.
3. los styles se heredan. Atomico fusionará las hojas de estilo. 

### Herencia fuera de Atomico

La función `c` de Atomico crea un customElement estándar optimizado, el que puede ser extendido para modificar su comportamiento, sea: 

1. Añadiendo métodos.
2. Creando o remplazando las hojas de estilo. 
3. Creando nuevas propiedades.

Supongamos de que poseemos un `MyButton` producto de la función `c`, nosotros podremos extender este componente para modificar su apariencia sin la necesidad de rescribirlo por completo, ejemplo:

```javascript
import { css } from "atomico";
import { MyButton } from "./src/my-button/my-button.js";

class MyNewButton extends MyButton {
  static styles = [
    /**
     * super.styles permite cargar los estilos anteriores
     * esta propiedad estática es creada internamente por atomico
     */
    ...super.styles,
    /**
     * De la siguiente manera estamos asociados a un nuevo
     * styleSheet a nuestro webcomponent
     */
    css`
      :host {
        --button-background: teal;
      }
    `,
  ];
}
```

El beneficio de esta herencia es simplificar la modificación de la apariencia de un componente creado con Atomico, ya que evita la rescritura del mismo. 

