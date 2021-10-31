# tsconfig.json

### ¿TSX o TS?

Una de las ventajas de Typescript es el apoyo a React, Atomico hereda esos beneficios al usar JSX permitiendo ganar jsx-runtime, autocompletado de propiedades, atributos y eventos al construir su código usando TSX. Esto no invalida el uso de TS al crear webcomponents con Atomico, la selección dependerá directamente del desarrollador.

### Configuracion de TSX con Typescript

```javascript
{
    "jsx": "react-jsx",
    "jsxImportSource": "atomico",
}
```

`jsx` y `jsxImportSource`  garantiza el uso de jsx-runtime con Atomico en Typescript, eliminado la necesidad de usar jsxFactory al usar JSX.
