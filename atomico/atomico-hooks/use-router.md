---
description: >-
  Ocupe el sistema de ruta del navegador(popState o Hash ) y aplique captura de
  parámetros de ruta de forma simple
---

# use-router

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { 
    useRouter, 
    useRoute, 
    redirect, 
    getPath 
} from "@atomico/hooks/use-router";
```

### Sintaxis

Esta librería usa  [`@uppercod/exp-route`](https://github.com/uppercod/exp-route) para mas información de expresiones de ruta verifique la documentación de la librería adjunta. 

#### useRouter

```jsx
const result = useRouter({
    "/":()=>"home",
    // required parameter
    "/user/{param}":({param})=> param,
    // parametro opcional
    "/client/[param]":({param})=>param
    // comodin spread
    "/[...notFound]":({notFound})=>notFound
});
```

#### useRoute

```javascript
const result = useRoute("/[...anyParam]", ({ anyParam }) => {});
```



