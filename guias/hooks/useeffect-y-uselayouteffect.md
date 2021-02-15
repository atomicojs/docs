---
description: Ejecute efectos secundarios después del render sincrona o asincronamente.
---

# useEffect y useLayoutEffect

### Sintaxis

```typescript
useEffect(effectCallback, optionalArgumentList);
```

Donde :

1. `effectCallback` : Función que se ejecuta una o mas veces según `optionalArgumentList`, `effectCallback`  puede retornar una función que será ejecutada solo si ```effectCallback`` \` es nuevamente ejecutado o el webcomponent es desmontado.
2. `optionalArgumentList`:  Array de argumentos que controla la ejecución de `effectCallback`, si un argumento de `optionalArgumentList` cambia detonara que `effectCallback` sea ejecutado nuevamente sin antes limpiar los efectos suscritos por la ejecución anterior.

### Ejemplo

```javascript
const listenerClickWindow = () => {
  const handlerClick = () => {
    console.log("Click window!");
  };

  window.addEventListener("click", handlerClick);

  const unlistenerClickWindow = () =>
    window.removeEventListener("click", handlerClick);

  return unlistenerClickWindow;
};

useEffect(listenerClickWindow, []);
```

### useLayoutEffect

Replica la lógica de useEffect pero con ejecución síncrona al render.

