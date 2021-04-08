---
description: >-
  Declare un estado basado en una expresión responsiva similar al uso del tag
  img[srcset].
---

# use-responsive-state

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useResponsiveState } from "@atomico/hooks/use-responsive-state";
```

### Sintaxis

```jsx
const expression= "phone, tablet 720px, destop 1080px";
const state= useResponsiveState(expression);
```

Donde:

* `state`: string,  Estado actual segun la comparacion entre expercion y matchMedia.
* `expression`: string, Exprecion que declara los estados serializados.

### Expresiones

```text
"<defaultState>, <caseState> <size>"
```

Donde:

* `defaultState`: Estado por defecto este no puede contener el uso de comas `","`.
* `caseState`: Estado a mostrar si hay coincidencia de matchMedia.
  * size: expresión de tamaño a observar, ejemplo:
    * "1080px": \(min-width: 1080px\)
    * "1080x720px": \(min-width: 1080px\) and \(min-height: 720px\)
    * "50rem": \(min-width: 50rem\)
    * "50em": \(min-width: 50em\)



