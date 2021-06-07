---
description: Facilita el testing del DOM asociado a un árbol de componentes.
---

# atomico/test-dom

### fixture

Esta función crea un render persistente para cada ejecución de la función `it` de su entorno de test, que implemente las funciones globales `beforeEach` y `afterEach`

```javascript
import { fixture } from "atomico/test-dom";
import { Component } from "./component.js";

describe("my test", () => {
  it("my-component", async () => {
    const component = fixture(html`<${Component}>
        <span>content...</span>
    </${Component}>`);

    await component.updated;

    /** logica del test */
  });
});
```

esto permite que cada ejecución de fixture dentro de `it` se relacione con el contenedor usado para el test, permitiendo testear los cambios externos del DOM fisilmente.

