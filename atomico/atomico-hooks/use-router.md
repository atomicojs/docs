# use-router

Conjunto de hooks para trabajar con rutas a base del evento popstate, la referencia de las expresiones de ruta puede encontrarlas en [https://github.com/uppercod/exp-route](https://github.com/uppercod/exp-route)

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { 
    useRouter, 
    useRoute, 
    useRouteMatch, 
    useRedirect, 
    redirect, 
    getPath 
} from "@atomico/hooks/use-router";
```

### Sintaxis  useRouter

```jsx
const view = useRouter({
    "/":()=><h1>home</h1>,
    "user/{id}":({ id })=><my-user id={id}/>,
})
```

### Sintaxis useRoute

```jsx
const view = useRoute("/",()=><h1>home</h1>);
```

### Sintaxis useRouteMatch

```jsx
const match = useRouteMatch();

const isHome = match("/home");
```

