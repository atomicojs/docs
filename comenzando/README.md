---
description: >-
  Esta guía conocerás lo esencial para comenzar a desarrollar webcomponents con
  Atomico
---

# 🚀 Comenzando con Webcomponents

Gracias por estar aquí e iniciarte con Atomico. Hablemos un poco de lo que hoy ofrece atomico:

1. **Agilidad de desarrollo**, el enfoque funcional de Atomico simplifica el código en todas las etapas de desarrollo.
2. **Ligero por dentro y por fuera**, Atomico te permite crear un componente con menos código y con un bajo impacto de dependencias 3kb Aproximadamente.
3. **Realmente rapido**, Atomico posee un buen performance en el browser y una experiencia de desarrollo ágil.

Ahora fuera de todo el marketing entendamos el como luce un webcomponent creado con Atomico:

```javascript
// IMPORTACIÓN
import { c, html, css } from "atomico";

// WEBCOMPONENT
function component({ message }) {
  return html`<host shadowDom>${message}</host>`;
}

// PROPIEDADES Y ATRIBUTOS DEL WEBCOMPONENTE
components.props = {
  message: String,
};

// APARIENCIA DEL WEBCOMPONENTE
component.styles = css`
  :host {
    font-size: 30px;
  }
`;

// DEFINICION DEL WEBCOMPONENT COMO ETIQUETA
customElements.define("my-component", c(component));
```

Analicemos el código por partes...

### Importación

```javascript
import { c, html, css } from "atomico";
```

¿Qué hemos importado?

1. `c`: Función que transforma el componente funcional en un customElement estándar. 
2. `html`: Función que declarar la plantilla de nuestro componente, también puedes usar JSX.
3. `css`: Función que permite crear el CSSStyleSheet\(CSS\) para nuestro componente siempre y cuando este declare el shadowDom.

### Webcomponent

```javascript
function component({ message }) {
  return html`<host shadowDom>${message}</host>`;
}
```

Nuestra función `component` recibe todas las props\(Propiedades y Atributos\) declaradas en `component.props`, la función `component` declarar toda la lógica y plantilla del webcomponent.  Una regla importante dentro de Atomico es "**todo componente creado con Atomico debe siempre retornar el tag `<host>`**".

### Propiedades y atributos del webcomponent

Atomico detecta las prop del componente gracias a la asociación del objeto props, este mediante el uso de índice y valor te permite definir:

1. **índice**: Nombre del la propiedad y atributo.
2. **Valor**: tipo del la prop.

```javascript
components.props = {
  message: String,
};
```

Del ejemplo podemos inferir que Atomico creará en nuestro componente una propiedad y atributo llamada mensaje y esta solo puede ser del tipo String.

### Apariencia del webcomponent.

Atomico detecta los estilos estáticos de tu componente gracias a la asociación del la propiedad styles:

```javascript
component.styles = css`
  :host {
    font-size: 30px;
  }
`;
```

`styles` acepta valores CSSStyleSheet\(CSS\)  individual o en lista, el retorno de la función `css` es un CSSStyleSheet estándar, por lo que puede ser compartido fuera de Atomico.

### Definición de tu webcomponent

```javascript
customElements.define("my-component", c(component));
```

Todo componente creado con Atomico antes de ser definido o extendido debe ser entregado antes a la función `c` del modulo Atomico, esta transforma tu función en un customElement estándar.



1. ¿Cómo asociar propiedades y Atributos a nuestro webcomponent?
2. Mejorar la apariencia usando el ShadowDOM.
3. Bienvenido a los hooks y di hola a useProp.
4. Ciclo de vida con useEffect.
5. Emitir eventos con useEvent.

