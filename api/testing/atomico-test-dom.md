---
description: Facilita el testing del DOM asociado a un árbol de componentes.
---

# atomico/test-dom

### fixture

función que permite mantener el render sobre un nodo único para cada ejecución de `it`, el contenedor de desmontara al finalizar cada ejecución de `it`.

```javascript
import { html } from "atomico";
import { expect } from "@esm-bundle/chai";
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

esto permite que cada ejecución de fixture dentro de `it` se relacione con el contenedor usado para el test, permitiendo testear los cambios externos del DOM fisilmente, ejemplo:

```javascript
import { html } from "atomico";
import { expect } from "@esm-bundle/chai";
import { fixture } from "atomico/test-dom";
import { Component } from "./component.js";


describe("my test", () => {
  it("my-component", async () => {
    // primera instancia del render, este retornara el componente
    const component = fixture(html`<${Component}>
        <span>content...</span>
    </${Component}>`);

    await component.updated;
    
    // actualiza el contenido del tag span de la primera instancia del render
    fixture(html`<${Component}>
        <span>new content...</span>
    </${Component}>`);
    
    await component.updated;

    expect(
          component.querySelector("span").textContent
    ).to.equal("new content...");
  });
});
```



