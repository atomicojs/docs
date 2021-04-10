---
description: Gestione rutas para aplicaciones de forma simple y declarativa
---

# router

### Modulo

```javascript
import {
    getPath, // ()=>string
    redirect, // (path:string)=>void
    RouterCase, // HTMLElement
    RouterSwitch, // HTMLElement
    RouterRedirect // HTMLElement
} from "@atomico/components/router";
```

### Ejemplo

{% tabs %}
{% tab title="HTML" %}
```markup
<router-redirect>
    <a href="/">home</a>
    <router-switch>
        <router-case path="/" load="./component.js"></router-case>
        <router-case path="/[...notFound]" for="notFound"></router-case>
        <h1 slot="notFound">Not Found</h1>
    </router-switch>
</router-redirect>
```
{% endtab %}

{% tab title="IMPORT" %}
```javascript
import { 
    RouterCase, RouterSwitch, RouterRedirect
} from "@atomico/components/router";

customElements.define("router-redirect", RouterRedirect);
customElements.define("router-switch", RouterSwitch);
customElements.define("router-case", RouterCase);
```
{% endtab %}
{% endtabs %}

### router-redirect

Redirige todo evento `onclick` que declare la propiedad `href` en su target, ejemplo tag &lt;a&gt;.

| Props | Tipo | Descripción |
| :--- | :--- | :--- |
| path | String | Define un `path` a concatenar a los `path` anidados, sea por redireccion o router-switch. |

### router-switch

Controla la ruta a mostrar o montar según la expresión del path

| Props | Tipo | Descripción |
| :--- | :--- | :--- |
| path | String | Define un `path` a concatenar a los `path` anidados, sea por redireccion o router-switch. |

### router-case

| Props | Tipo | Descripción |
| :--- | :--- | :--- |
| path | `String` | Define el `path` en el que se debe mostrar el contenido. |
| load | `String | ()=>Promise<any>`  | Contenido a importar al momento del match por `path`. |
| for | String | Contenido a mostrar al momento del match por `path`, `for` debe apuntar a un slot dentro del padre. |



