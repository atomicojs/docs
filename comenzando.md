---
description: >-
  Esta guía conocerás lo esencial para comenzar a desarrollar webcomponents con
  Atomico
---

# 🚀 Comenzando con Webcomponents

Gracias por estar aquí e iniciarte con Atomico. Hablemos un poco de lo que hoy ofrece atomico:

1. **Agilidad de desarrollo**, el enfoque funcional de Atomico simplifica el código en todas las etapas de desarrollo.
2. **Ligero por dentro y por fuera**, Atomico te permite crear un componente con menos código y con un bajo impacto de dependencias 3kb Aproximadamente.
3. **Realmente rapido**, Atomico posee un [buen performance](https://twitter.com/atomicojs/status/1391775734641745929) en el browser y una experiencia de desarrollo ágil.

Entendamos el como luce un webcomponent creado con Atomico:

{% code title="MyComponent.jsx" lineNumbers="true" %}
```tsx
// Importaciones 
import { c, css } from "atomico";

// Creando nuestro webcomponents: Definiendo el customElement
export const MyComponent = c(
  // Definiendo el renderizado del componente
  ({ message }) => {
    return <host shadowDom>{message}</host>;
  },
  {
    // Definiendo propiedades(props) y atributos
    props: {
      message: String,
    },
    // Definiendo estilo css encapsulado 
    styles: css`
      :host {
        font-size: 30px;
      }
    `,
  }
);

// Registro del custom tag del Web Component
customElements.define("my-component", c(component));
```
{% endcode %}

Analicemos el código por partes...

### 1.0 Importaciónes

```tsx
import { c, css } from "atomico";
```

¿Qué hemos importado?

1. `c`: Función que transforma el componente funcional en un customElement estándar.
2. `css`: Función que permite crear el CSSStyleSheet(CSS) para nuestro componente siempre y cuando este declare el shadowDom.

### 2.0 Creando nuestro webcomponents: Definiendo el customElement

#### 2.1. Definiendo el renderizado del componente

{% code title="MyComponent.tsx - Linea: 7 a 9" %}
```tsx
// Definiendo el renderizado del componente
({ message }) => {
    return <host shadowDom>{message}</host>;
}
```
{% endcode %}

Nuestra función recibe todas las props(Propiedades y Atributos) declaradas en `props`(linea 12) la función declara toda la lógica y plantilla del webcomponent. Una regla importante dentro de Atomico es "**todo componente creado con Atomico debe siempre retornar el tag `<host>`**".

#### 2.2 Definiendo propiedades(props) y atributos

Atomico detecta las prop(Propiedades y Atributos) del componente gracias a la asociación del objeto props, esto mediante el uso de índices y valores te permite definir:

1. **índice**: Nombre de la propiedad y atributo.
2. **Valor**: tipo de la prop.

{% code title="MyComponent.tsx - Lina: 12 a 14" %}
```tsx
// Defining Component Properties(props) and Attributes
props: {
  message: String,
},
```
{% endcode %}

Del ejemplo podemos inferir que Atomico creará en nuestro webcomponente una propiedad y atributo llamada mensaje y esta solo puede recibir valores del tipo String.

#### 2.3 Definiendo estilo css encapsulado

Atomico detecta los estilos estáticos de tu componente gracias a la asociación de la propiedad `styles`:

{% code title="MyComponent.tsx - Linea: 16 a 19" %}
```tsx
styles: css`
  :host {
    font-size: 30px;
  }
`,
```
{% endcode %}

`styles` acepta valores CSSStyleSheet(CSS) de forma individual o en lista, el retorno de la función `css` es un CSSStyleSheet estándar, por lo que puede ser compartido fuera de Atomico.

### 3.0 Registro del custom tag del Web Component

{% code title="MyComponent.tsx - Linea: 25" %}
```tsx
// Web Component Registration and Definition
customElements.define("my-component", MyComponent);
```
{% endcode %}

Para crear nuestro customElement estándar deberemos entregar nuestro componente funcional a la función `c` del módulo de Atomico, la función `c` generará como retorno un customElement que puede ser definido o extendido.

### Ejemplo

{% embed url="https://webcomponents.dev/edit/collection/wuKH7azM3kT3jqKv9ZV9/7dNVyEXrCpmpKF9NXAAY/src/index.jsx" %}
