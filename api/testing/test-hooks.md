---
description: >-
  Realice test a hooks creados con Atomico con una instancia aislada y
  predecible
---

# atomico/test-hooks

El submodulo "atomico/test-hooks" es parte directa del core de Atomico y le permitirá ejecutar el customHook de forma controlada sin la necesidad de usar webcomponents.

```javascript
import { createHooks } from "atomico/test-hooks";
```

### createHooks

función que crea un contexto asilado que se comparte globalmente con los hooks de Atomico al momento de ejecutar el método load.

#### Instancia

```typescript
const hooks = createHooks(opcionalRender, opcionalHost);
```

Donde:

* **optionalRender**: Callback que permite reiniciar el ciclo de vida del hook, este callback será ejecutado cada vez que un hook como [useState ](../hooks/usestate.md)o [useReducer ](../hooks/usereducer.md)soliciten la actualización del scope. Atomico lo usa para renderizar nuevamente el webcomponent.
* **opcionalHost**:** **permite compartir un objeto para el hook [useHost](../hooks/usehost.md). Atomico lo usa para compartir la instancia del webcomponent.

#### Retorno de la instancia

```typescript
interface Hooks {
    load<T>(callback: () => T): T;
    clearEffect(unmounted?: boolean): () => void;
}
```

Donde

* **load**:  Función que asocia permite asociar el scope del callback a un habito de contexto global temporal.&#x20;
*   **clearEffect: **Función que activa el colector de useLayoutEffect, al ejecutar clearEffect se retornara un callback que permite finalizar la el colector para useEffect cerrando el ciclo de efectos secundarios.

    Si clearEffect recibe como parámetro true comunica el desmontaje.

### Ejemplo:

**./use-counter.js: **customHook a testear.

```typescript
import { useState } from "atomico";

export function useCounter(initialValue) {
  const [value, setValue] = useState<number>(initialValue);
  return {
    value,
    increment: () => setValue((value) => value + 1),
    decrement: () => setValue((value) => value - 1),
  };
}
```

**./use-counter.test.js: **el  ejemplo se basa en el entorno de test de [@web/test-runner](https://modern-web.dev/docs/test-runner/overview/).

```javascript
import { expect } from "@esm-bundle/chai";
import { createHooks } from "atomico/test-hooks";
import { useCounter } from "./use-counter.js";

it("Check return", () => {
  const hooks = createHooks();

  const counter = hooks.load(() => useCounter(10));

  expect(counter.value).to.equal(10);
  expect(counter.increment).to.be.an.instanceOf(Function);
  expect(counter.decrement).to.be.an.instanceOf(Function);
});
```

****
