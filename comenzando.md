---
description: >-
  Gracias por estar aquí e iniciarte con Atomico en esta guía conocerás lo
  esencial para comenzar a desarrollar con Atomico
---

# 🚀 Comenzando

 Atomico es simple y te lo demostrare comenzando desde CodePen usando solo un tag script en nuestro HTML. Comenzaremos creando dentro de nuestro HTML el siguiente contenido:

```markup
<script type="module"></script>
```

Como notaras hemos añadido un tag `script[type=module]`, esto nos permitirá usar ESM\(módulos nativos\) y asociar  la siguiente importación:

```markup
<script type="module">
  import { html } from "https://unpkg.com/atomico";
</script>
```

Del código anterior destacare lo siguiente:

1. Estoy consumiendo Atomico desde el **CDN Unpkg**, puedes usar cualquier otro que soporte ESM.
2. he desestructurado la función `html` del modulo, esta nos permitirá construir el HTML de nuestro webcomponent.

Ahora a crear nuestro primer componente solo declarando una simple función:

```markup
<script type="module">
  import { html } from "https://unpkg.com/atomico";

  function component() {
    return html`<host></host>`;
  }
</script>
```

Quiero que notes el retorno de la función `component` esto es realmente importante ya que es una regla en Atomico **"Todo componente creado con Atomico debe retornar el tag host"**. El tag `<host>` representa el customElement y a través este tag podrás asociar eventos, propiedades, atributos y métodos a tu componente. 

Aun no hemos  añadido nada dentro del componente, que tal si añadimos un `<h1>hola mundo</h1>`:

```markup
<script type="module">
  import { html } from "https://cdn.skypack.dev/atomico";

  function component() {
    return html`<host>
      <h1>hola mundo</h1>
    </host>`;
  }
</script>
```

Listo, solo falta ver el resultado en el navegador, para ello deberás importar de Atomico la función `c` que transforma nuestra función `component` en un customElement estándar para ser registrado:

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

Con nuestro componente registrado, ya puedes hacer uso este a través de la etiqueta  `<mi-componente>` en nuestro HTML:

{% embed url="https://codepen.io/uppchile/pen/PojWpbb" %}

Hemos creado un pequeño webcomponent con Atomico que te muestra los principios básicos para seguir avanzar con los siguientes tutoriales:

1. Añadir nuestras primeras propiedades y Atributos
2. Mejorar la apariencia usando el ShadowDOM.
3. bienvenido a los hooks y di hola a useProp.
4. ciclo de vida con useEffect.
5. Emitir eventos con useEvent.

