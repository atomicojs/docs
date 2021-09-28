---
description: Consume una promesa reflejando el retorno y estado de esta
---

# use-promise

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { usePromise } from "@atomico/hooks/use-promise";
```

### Sintaxis

```jsx
const [result, status: "pending"|"fulfilled"|"rejected"] = usePromise(
  asyncFunction: ()=>Promise<any>,
  runFunction: boolean,
  optionalArguments?: any[]
);
```

Donde :

* `result`: Retorno de la promesa
* `status`: Estado de la promesa:
  * `""`: Sin ejecutar.
  * `"pending"`: En ejecución.
  * `"fulfilled"`: Ejecutada sin error
  * `"rejected"`: Ejecutada con error
* `asyncFunction`: función asíncrona.
* `runFunction`: `booleano`, de ser `true` ejecutara la promesa y definirá el status.
* `optionalArguments`: Opcional `any[]`, permite regenerar la promesa a través de argumentos.

