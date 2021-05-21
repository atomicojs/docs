# ✨ Sistemas de diseño

Uno de los objetivos de Atomico es facilitar el uso de webcomponents mediante un Api funcional, pero el resultado siempre es un webcomponent Estándar y Optimizado útil para representar sistemas de diseño.

Con Atomico podrás lograr los siguientes objetivos:

1. **Interfaces escalable y reutilizable**: con Atomico el código es más simple y podrás aplicar practicas que faciliten la reutilización de tu código.
2. **Comunicación abierta**: su webcomponent podrá comunicar su estado sea por eventos, propiedades o métodos.
3. **Agnóstico**: su webcomponent servirá en cualquier librería compatible con la web, ejemplo React, Vue o Svelte.
4. **Performance**: Atomico posee un performance comparativo a niveles de Svelte, ganando la tercera posición en performance según [**webcomponents.dev**](https://twitter.com/atomicojs/status/1391775734641745929)  en una comparativa de 55 librerías entre las cuales esta React, Vue, Stencil y Lit.

Quiero enseñarte el como se comporta Atomico al momento de ser usado para la creacion de DS\(Sistema de diseño\), comenzando con un botón.

```jsx
import { c, css } from "Atomico";

// Lógica y plantilla
function myButton() {
  return (
    <host shadowDom>
      <slot>button</slot>
    </host>
  );
}

// Propiedades y atributos
myButton.props = { small: { type: Boolean, reflect: true } };

// Estilos estáticos
myButton.styles = css`
  :host {
    font-size: var(--button-fontSize, 1rem);
    padding: var(--button-padding, 0.5rem 1rem);
    background: var(--button-background, #000);
    color: var(--button-color, #fff);
  }
`;

// CustomElement
export const MyButton = c(myButton);
```

Del ejemplo destacaremos  las siguientes practicas:

1. `myButton.styles`: nos permite asociar estilos de forma estática, esto es altamente eficiente, porque los estilos  procesan solo una vez y pueden ser heredados. 
2. Usamos customProperties\(variables de css\) para referenciar propiedades del css que queremos mantener  variables.
3. El contenido de button es referenciado mediante el uso del tag `slot`. 
4. `MyButton` es un webcomponent, por lo que puede ser instanciado o extendido.

Ahora supongamos que `MyButton` botón es parte de nuestro sistema de diseño y debemos modificar ante la llegada de un nuevo proyecto pero sin rescribirlo por completo.

## ¿Cómo modificar la apariencia de mi webcomponent creado con Atomico?

Las técnicas que puedes aplicar con Atomico son:

1. Custom properties\(Variables de css\)
2. Herencia de clase
3. Selector part

### Custom properties\(Variables de css\)

Estas nos permiten modificar aspectos ya referenciados mediante la declaraciones de custom properties. El mayor potencial de estas es la herencia descendente, ejemplo:

```markup
<style>
  .theme {
    --theme-primary: black;
    --button-background: var(--primary);
    --button-padding: 0.5rem 1rem;
  }

  .theme-dark {
    --theme-primary: #fff;
  }

  my-button[small] {
    --button-padding: 0.25rem 0.5rem;
    --button-fontSize: 0.75rem;
  }
</style>
<body class="theme">
  <my-button>content</my-button>
  <my-button small>content</my-button>
</body>
```

Del ejemplo destacaremos lo siguiente:

1. El selector `.theme` declara custom properties visibles solo para el selector, **esto posee un efecto positivo vs `:root` porque reduce el conflicto de nombre de las custom properties y limita su uso solo al contenedor asociado**
2. El selector `my-button[small]` activa las custom properties solo si declaramos la propiedad `small` en la instancia del webcomponent.

### Herencia fuera de Atomico

El webcomponent creado por atomico posee la propiedad `static get styles`, que ante una herencia permite modificar completamente la apariencia de su componente, ejemplo:

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

Del ejemplo destacaremos lo siguiente:

1. `MyNewButton` heredara todo del componente anterior; propiedades y estilos.
2. El css creado asocia la custom propertie `--button-background: teal`, creando una variación en el componente principal.

**Esta herencia también es valida entre componentes de Atomico**, pero esta rescribirá el render, considérela si su busca referenciar variables de css o props\(Propiedades\).

### **Selector ::part**

Nos permite modificar la apariencia de los elementos dentro del shadowDOM que hagan uso del atributo `part="<identificador>"`,  ejemplo:

```jsx
import { c } from "atomico";

function card() {
  return (
    <host shadowDom>
      <header part="header">
        <slot name="header" />
      </header>
    </host>
  );
}

customElements.define("my-card", c(card));
```

Gracias al uso del atributo `part`, podremos modificar toda la apariencia del Elemento que referencie el atributo, ejemplo:

```css
my-card::part(header){
    padding: 1rem;
    font-size: 50px;
}

```

Es probable de que su componente posea apariencias variables, ejemplo un modo dark y el problema es que `part` limita su efecto a solo a  [**pseudoclase**](https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-classes), por lo que \`::part\(header\).dark\` no funcionara, para escapar de esto solo aplique props su componente, ejemplo

```jsx
function card() {
  return (
    <host shadowDom>
      <header>
        <slot name="header" />
      </header>
    </host>
  );
}

card.props = {
  dark: {type: Boolean, reflect: true},
};

```

```css
my-card[dark]::part("header"){
    background: black;
    color: white;
}
```

Atomico busca facilitar la creación de webcomponents útiles para sistemas de diseño en la siguiente guía conocerás como estructurar y documentar Sistemas de diseño



