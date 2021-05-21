---
description: Mejora la experiencia de desarrollo de Atomico con Typescript.
---

# 📜 Typescript

## ¿Tsx o Ts?

Una de las ventajas de Typescript es el apoyo a React, Atomico hereda esos beneficios al usar JSX permitiendo ganar jsx-runtime, autocompletado de propiedades, atributos y eventos al construir su código usando TSX. Esto no invalida el uso de TS al crear webcomponents con Atomico, la selección dependerá directamente del desarrollador.

### Configuración recomendada

```javascript
{
  "compilerOptions": {
    "checkJs": true,
    "allowJs": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "strictFunctionTypes": true,
    "strictPropertyInitialization": true,
    "noImplicitReturns": true,
    "alwaysStrict": true,
    "esModuleInterop": true,
    "declaration": true,
    "target": "ES2017",
    "jsx": "react-jsx",
    "jsxImportSource": "atomico",
    "module": "ESNext",
    "moduleResolution": "Node"
  }
}
```

de la configuración se destaca:

1. `jsx` y `jsxImportSource`  garantiza el uso de jsx-runtime con Atomico en Typescript, eliminado la necesidad de usar jsxFactory al usar JSX.
2. `noImplicitAny`, para completar el retorno de las props use el tipo `Props`. Es valido eliminar el uso de `noImplicityAny`,  ya que en ocasiones puede ser muy estricto ante situaciones de tipo variadas, hay que recordar que JS por naturaleza es dinámico.

{% hint style="info" %}
Atomico posee una construcción de tipo basa en mi experiencia\([@uppercod](https://twitter.com/uppercod)\), estoy atento a sus recomendaciones ya que busco dar soporte completo a Typescript.
{% endhint %}

## Componente

### Props&lt;typeof component.props&gt;

Permite recuperar los tipos del objeto `props` asociado a la función.

```typescript
import { Props, c } from "atomico";

function component(props: Props<typeof component.props>) {}

component.props = {
    propString: String,
    propObject: {
        type: Object,
        value: (): { prop?: number } => ({}),
    },
};

customElements.define("my-component", c(component));
```

### c\( component \)

c evaluara si el componente posee un formato valido.

```typescript
// CASO 1
function component(props) {}

c(component); // ✔️

// CASO 3
function component(props) {}

component.props = {
    value: {
        type: Number,
        value: "...",
    },
};

c(component); // ❌ -  la propiedad value debe ser del tipo declarado en type
```

## Hooks

La mayoría de los hooks infieren los tipos, pero otros requieren una declaración para mejorar la experiencia de tipado, ejemplo:

### useProp

```typescript
const [value, setValue] = useProp<number>("value");
```

Fuerza el tipo `number`para `value` y `setValue`, segun el ejemplo `value` solo puede ser del tipo `number`.

### useState

**useState infiere el tipo en la mayoría de los casos,** pero el no usar un estado inicial impide un tipado estricto, pude corregir esto de la siguiente manera:

```typescript
const [value, setValue] = useState<number>();
```

Fuerza el tipo `number` para `value` y `setValue`, segun el ejemplo `value` solo puede ser del tipo `number`.

### useRef

```typescript
const ref = useRef<HTMLInputElement>useRef();
```

Fuerza que **ref.current** se `HTMLInputElement`.

