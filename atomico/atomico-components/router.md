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

```markup
<script type="module">
import { 
    RouterCase, RouterSwitch, RouterRedirect
} from "@atomico/components/router";

customElements.define("router-redirect", RouterRedirect);
customElements.define("router-switch", RouterSwitch);
customElements.define("router-case", RouterCase);
</script>
<router-redirect>
    <a href="/">home</a>
    <router-switch>
        <router-case path="/" src="./component.js"></router-case>
        <router-case path="/[...notFound]" for="notFound"></router-case>
        <h1 slot="notFound">Not Found</h1>
    </router-switch>
</router-redirect>
```

