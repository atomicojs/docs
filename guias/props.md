---
description: >-
  Las props en Atomico son la forma de asociar al webcomponent propiedades y
  atributos reactivos que detonan la lógica o interfaz del webcomponent.
---

# Props\(Propiedades\)

## Sintaxis

Toda función que represente el webcomponent podrá asociar el objeto estático props para la declaración de propiedades y atributos reactivos, ejemplo:

```jsx
import { c } from "atomico";

function component() {
  return <host />;
}

component.props = {
  // Declaracion simple
  value1: String,
  // Declaracion estructurada
  value2: {
    type: String,
    reflect: true,
    attr: "advaceprop",
    value: "default string",
    event: {
      type: "UpdateAdvanceProp",
      bubbles: true,
    },
  },
};

customElement.define("web-component", c(component));
```

Considere que:

1. los nombre de prop en formato Camel Case será traducido a para su uso como atributo al formato Kebab Case, este comportamiento puede ser modificado mediante la propiedad "attr" al usar una declaración estructurada.
2. Las declaraciones estructuradas requieren mínimamente la propiedad "type".
3. No todos los tipos pueden usar la propiedades "reflect".
4. La forma de declarar la propiedad "value" puede variar según el tipo.

## Declaraciones simple

Las declaraciones simples permiten asociar solo la validación de tipo.

```javascript
component.props = {
  propString: String,
  propNumber: Number,
  propObject: Object,
  propArray: Array,
  propDate: Date,
  propBool: Boolean,
  propCallback: Function,
};
```

## Declaraciones estructuradas

Mejora la definición añadiendo declaraciones utilitarias, permitiendo por ejemplo reflejar el valor de la propiedad como atributos, emitir automáticamente eventos o asociar valores por defecto. **Recuerde este tipo de declaraciones requieren mínimamente el uso de la propiedad type.**

### Prop.type

```javascript
// valid declaration
component.props = { myName: String };
// valid declaration
component.props = { myName: { type: String } };
```

| Tipo | Soporta la propiedad "reflect" |
| :--- | :--- |
| **String** | ✔️ |
| **Number** | ✔️ |
| **Boolean** | ✔️ |
| **Object** | ✔️ |
| **Array** | ✔️ |
| **Promise** | ❌ |
| **Symbol** | ❌ |
| **Function** | ❌ |

### Prop.reflect

Si la propiedad "reflect" se define como true se refleja su valor como atributo del webcomponent, esto es útil para la declaración de estados del CSS, ejemplo:

```jsx
component.props = {
  checked: {
    type: Boolean,
    reflect: true,
  },
};
```

### Prop.event

Permite despachar un evento automatico ante el cambio de valor del prop, ejemplo:

```javascript
component.props = {
  value: {
    type: String,
    event: {
      type: "change",
      bubbles: true,
      composed: true,
      detail: "any value",
      cancelable: true,
    },
  },
};
// listener
nodeComponent.addEventListener("change", handler);
```

Donde :

* `event.type` : String - opcional, nombre del evento a emitir ante el cambio de la prop
* `event.bubbles` : Boolean - opcional, indica que el evento puede ser escuchado por los contenedores.
* `event.detail` : Any - opcional, permite adjuntar informacion custom del evento
* `event.cancelable` : Boolean - opcional, indica que el evento puede ser cancelado por algun oyente
* `event.composed` : Boolean - opcional, permite que el evento sobrepase el limite del shadow-root

Las propiedades especiales del evento son las conocidas `EventInit` , puede conocer mas detalle en la [documentación adjunta](https://developer.mozilla.org/en-US/docs/Web/API/Event/Event)

### Prop.value

Atomico permite la definición de valores por defectos de las props.

```javascript
WebComponents.props = {
  valueNormal: {
    type: Number,
    value: 100,
  },
  valueObject: {
    type: Object,
    value: () => ({}),
  },
};
```

La asociación de callback como value permiten generar valores únicos para cada instancia del webcomponent, esto es útil con los tipos Object y Array ya que elimina las referencias entre instancias.

## Reactividad en el scope del webcomponent

Atomico elimina el uso de "this" dado su enfoque funcional, pero añade el hook [useProp ](hooks/useprop.md)el que permite referenciar una prop para su uso con una sintaxis es similar a useState, ejemplo:

```jsx
function component() {
  const [message, setMessage] = useProp("message");
  return (
    <host>
      Hello, {message}
      <input oninput={({ target }) => setMessage(target.value)} />
    </host>
  );
}

component.props = { message: String };
```

