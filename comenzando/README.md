---
description: >-
  Gracias por estar aquí e iniciarte con Atomico en esta guía conocerás lo
  esencial para comenzar a desarrollar webcomponents con Atomico
---

# 🚀 Comenzando con Webcomponents

 Atomico es simple y puedes  comenzar a practicar con el desde un fichero HTML añadiendo el siguiente código:

```markup
<script type="module">
  import { html } from "https://unpkg.com/atomico";
</script>
```

Del código anterior destacaré lo siguiente:

1. Estamos consumiendo Atomico desde el **CDN Unpkg**, puedes usar cualquier otro que soporte ESM.
2. Estamos desestructurado la función `html` del módulo,  esta nos permitirá construir la plantilla HTML de nuestro webcomponent.

Ahora a crear nuestro primer componente declarando nuestra función que llamaremos `component`:

```markup
<script type="module">
  import { html } from "https://unpkg.com/atomico";

  function component() {
    return html`<host>
      <h1>hola mundo</h1>
    </host>`;
  }
</script>
```

Quiero que notes el retorno de la función `component` esto es realmente importante ya que es una regla en Atomico **"Todo componente creado con Atomico debe retornar siempre el tag host".** El tag `<host>` representa la instancia del customElement y a través este tag podrás asociar eventos, propiedades, atributos y métodos a tu componente.

Ahora solo falta ver el resultado en el navegador, para ello deberás importar de Atomico la función `c` del módulo Atomico, esta transformará nuestra función `component` en un customElement estándar para ser registrado:

```markup
<script type="module">
  import { c, html } from "https://cdn.skypack.dev/atomico";

  function component() {
    return html`<host>
      <h1>hola mundo</h1>
    </host>`;
  }

  customElements.define("mi-componente", c(component));
</script>
```

Con nuestro componente ya registrado podrás hacer uso`<mi-componente>` en tu HTML para instanciarlo:

{% embed url="https://codepen.io/uppchile/pen/PojWpbb" %}

Listo, hemos creado un pequeño webcomponent con Atomico que te muestra los principios básicos para seguir avanzando con los siguientes tutoriales:

1. ¿Cómo asociar propiedades y Atributos a nuestro webcomponent?
2. Mejorar la apariencia usando el ShadowDOM.
3. Bienvenido a los hooks y di hola a useProp.
4. Ciclo de vida con useEffect.
5. Emitir eventos con useEvent.

