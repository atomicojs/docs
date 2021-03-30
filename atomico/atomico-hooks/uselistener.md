---
description: >-
  Permite escuchar un evento de una referencia o del host sin la necesidad de
  vinculación al virtualDOM
---

# useListener

### Instalación

```bash
npm install @atomico/kit
```

### Modulo

```javascript
import { useListener, useListenerRef } from "@atomico/kit/use-listener";
```

### Sintaxis

Este Hook es un proxy para el método `addEventListener`.

#### useListener

```javascript
useListener(eventName, handler, optionalOptions);
```

donde : 

1. `eventName` : Nombre del evento a suscribir.
2. `handler` : Callback que procesa el evento suscrito.
3. `optionalOptions`: Opciones del evento.

#### useListenerRef

```javascript
useListener(ref,eventName, handler, optionalOptions);
```

donde : 

1. `ref`: Referencia a asociar el evento.
2. `eventName` : Nombre del evento a suscribir.
3. `handler` : Callback que procesa el evento suscrito.
4. `optionalOptions`: Opciones del evento.

