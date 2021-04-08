---
description: creé conexión entre componentes para compartir estados internos
---

# use-channel

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useChannel} from "@atomico/hooks/use-channel";
```

### Sintaxis

```javascript
const channel = "MyChannel";
const [parentValue, setChildValue ] = useChannel(channel);
```

Donde : 

1. channel: String, define el nombre del evento a utilizar para generar la el canal.
2. parentValue : Valor heredado por el componente padre.
3. setChildValue: Callback, define un valor para los componentes anidados.

### Example

Este hook es usado por [@atomico/components/router](../atomico-components/router.md)

