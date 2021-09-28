---
description: Recupere un nodo superior al webcomponent actual.
---

# use-parent

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useParent, useParentPath } from "@atomico/hooks/use-parent";
```

### Sintaxis useParent

```jsx
const ref = useParent(matches: string, composed?: boolean);
```

Donde:

* `matches`: string,  aplica a los padres el método \`Element.matches\` y retorna la confidencia como referencia.
* `ref`: referencia con el nodo que coincida con matches
* `composed`: boolean, de ser true escapa del bloque del shadowDOM.

### Sintaxis useParentPath

```jsx
const children = useParentPath(composed: boolean);
```

Donde:

* `composed`: boolean, de ser true escapa del bloque del shadowDOM.
* `children`: Lista de nodos padres ordenados de forma ascendente.

