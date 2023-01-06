---
description: >-
  Es grato saber que hoy te enfrentas al desafío de implementar un sistema de
  diseño con Atomico, espero que esta guía te ayude a abordar:
---

# ✨ Sistemas de diseño con Atomico

1. Flujo de desarrollo con Atomico al crear sistemas de diseño.
   1. seleccionar la estrategia del repositorio y publicación como package, sea:
      1. monorepo multi package
      2. repositorio single package
2. Recomendación en la creacion de Tokens (Custom properties) para tus webcomponents.
3. Abstracción de componentes.
4. Composición. (Slots)
5. Distribución.
6. Documentación.

### Estructura recomendada

```bash
src/
	# Importara, exporta y declara todos nuestros componentes
	components.js 
  # Agrupa todos los tokens de nuestro sistema
	tokens.js
	# Ejemplo de estructura para nuestro componente
	/button
		button.{js,jsx,ts,tsx}
		button.md
		button.test.js
```

A continuación analizaremos los archivos expuesto.

### **src/components.js**

Archivo que importa, exporta y declara todo los componentes de nuestro sistema de diseño, ejemplo:

```javascript
import { Button } from "./button/button";
export { Button } from "./button/button";

customElements.define("my-button", Button);
```

Los beneficios de centralizar todo en components.js son:

1. Claridad de la definición del customElements en un solo archivo para todo nuestro sistema
2. Exportación de todos los customElements para ser extendido o redefinido.

### src/tokens.js

Archivo que centraliza las custom-properties de nuestro sistema de diseño, ejemplo:

```javascript
import { css } from "atomico";

export const tokensInput = css`
  :host {
    --background: var(--my-ds-input--background, #fff);
    --border-width: var(--my-ds-input--border-width, 1px);
    --border-color: var(--my-ds-input--border-color, black);
    --radius: var(--my-ds-input--radius, 0.5rem);
    --min-height: var(--my-ds-input--min-height, 40px);
  }
  .input-box {
    background: var(--background);
    min-height: var(--min-height);
  }
  .input-box--use-border {
    border: var(--border-width) solid var(--border-color);
  }
`;

export const tokenColors = css`
  :host {
    --primary: var(--my-ds--primary);
    --secondary: var(--my-ds--secondary);
    --success: var(--my-ds--warning);
    --warning: var(--my-ds--warning);
    --danger: var(--my-ds--warning);
    --info: var(--my-ds--warning);
  }
`;
```

Del ejemplo anterior destaco:

#### 1. Clases de utilidades en en tokensInput

#### 2. Patrón de declaración de las custom properties

```css
:host {
    --background: var(--my-ds-input--background, #fff);
}
```

`--background` será un token que se puede modificar a nivel de instancia y este hereda un token global de nuestro sistema llamado `--my-ds-input--background`, quiero que notes que el nombre global de nuestra custom property posee un patron, ejemplo:

```css
---my-ds-input--background
---<prefix>-<namespace>--<property>
```

Donde:

1. Prefix : Prefijo de nuestro sistema de diseño a nivel global
2. namespace: grupo independiente dentro de nuestro sistema de diseño
3. property: propiedad asociada al sistema, sea color, tamaño u otro valor.

**¿Por que usar el patrón recomendado?**, para individualizar la configuración a nivel de grupos y separar de esta la definición de la propiedad gracias al uso de doble guion(--), internamente todo se simplifica ya que los tokens solo capturan la configuración global global para reflejarla a una variable mas simple accesible solo desde desde el nivel de instancia del componente.

#### Nivel de instancia

Es la instancia del componente sea en el HTML o JS, ejemplo:

{% tabs %}
{% tab title="HTML" %}
```markup
<my-component style="--background: red;"></my-component>;
```
{% endtab %}

{% tab title="JS" %}
```javascript
const component = document.createElement("my-component");

component.style = "--background: red";
```
{% endtab %}
{% endtabs %}

### src/button.js

{% tabs %}
{% tab title="JS" %}
```javascript
import { c, html, css } from "atomico";
import { tokensColor, tokensInput } from "../tokens";

function button(props) {

  return html`<host shadowDom>
    <button ...${props} class="input-box input-box--use-border">
      <slot name="icon"></slot>
      <slot></slot>
    </button>
  </host>`;
}

button.props = {
  name: String,
  value: String,
  disabled: Boolean,
};

button.styles = [
  tokensColor,
  tokensInput,
  css`
    .input-box {
      display: flex;
      gap: 1rem;
    }
  `,
];
```
{% endtab %}

{% tab title="JSX" %}
```jsx
import { c, css } from "atomico";
import { tokensColor, tokensInput } from "../tokens";

function button(props) {
  return (
    <host shadowDom>
      <button {...props} class="input-box input-box--use-border">
        <slot name="icon"></slot>
        <slot></slot>
      </button>
    </host>
  );
}

button.props = {
  name: String,
  value: String,
  disabled: Boolean,
};

button.styles = [
  tokensColor,
  tokensInput,
  css`
    .input-box {
      display: flex;
      gap: 1rem;
    }
  `,
];

export const Button = c(button);
```
{% endtab %}
{% endtabs %}

Del código anterior destaco:

1. **importación de "../tokens"** y la desestructuración del modulo que declarar el uso de `tokensColor` y `tokensInput`.
2. \*\*Clases de utilidades: \*\*Nuestro componente hace uso de las clases de utilidades del `tokensColor`.
3. \*\*button.styles: \*\*Atomico permite asociar múltiples estilos mediante el uso de un array.
4. **Exportación de Button.**
