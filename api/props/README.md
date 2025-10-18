---
description: >-
  The props in Atomico are the way to associate the webcomponent properties and
  reactive attributes that trigger the logic or interface of the webcomponent.
icon: dna
---

# Props(Properties)

Props is the Atomico recommended way to declare visible and accessible states at the instance level of your webcomponents, with props you can:

1. Access state via instance, example: `document.querySelector("my-component").myStateProp`.
2. Dispatch events on prop value change, example: `document.querySelector("my-component").addEventListener("myPropChange",console.log)`.
3. Reflect attributes as prop, example: `<my-component my-prop="....">` to `document.querySelector("my-component").myProp`.
4. define strict input types for props.

## Syntax

Any function that represents the webcomponent will be able to associate the static object props for the declaration of reactive properties and attributes, for example:

```jsx
import { c } from "atomico";

const props = {
    // Simple statement
    value1: String,
    // Structured statement
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

const MyComponent = c((props) => <host>{props.value1}</host>, { props });

customElement.define("web-component", MyComponent);
```

#### Consider that:

1. The prop names in Camel Case format will be translated to for use as an attribute to the Kebab Case format, this behavior can be modified through the "attr" property when using a structured declaration.
2. Structured declarations require the "type" property minimally.
3. Not all types can use the "reflect" properties.
4. The declaration of the "value" property can vary depending on the type.

## Simple statements

Simple statements allow setting just type validations.

```javascript
const props = {
  propString: String,
  propNumber: Number,
  propObject: Object,
  propArray: Array,
  propBool: Boolean,
  propCallback: Function,
};
```

## Structured declaration

Improve the definition by adding utility declarations, allowing for example to reflect the property's value as attributes, automatically emit events or associate default values. Remember these types of declarations minimally require the use of the type property.

### Prop.type

```javascript
// valid declaration
const props = { myName: String };
// valid declaration
const props = { myName: { type: String } };
```

| Type                                                                                                            | Supports reflect |
| --------------------------------------------------------------------------------------------------------------- | ---------------- |
| **String**                                                                                                      | ✔️               |
| **Number**                                                                                                      | ✔️               |
| **Boolean**                                                                                                     | ✔️               |
| **Object**                                                                                                      | ✔️               |
| **Array**                                                                                                       | ✔️               |
| **Promise**                                                                                                     | ❌                |
| **Symbol**                                                                                                      | ❌                |
| **Function**                                                                                                    | ❌                |
| **All references to existing types in the browser(HTMLElement, Element, Node, Date, File... more than 300** 😎) | ❌                |

### Prop.reflect

If the "reflect" property is set to true, its value is reflected as an attribute of the webcomponent, this is useful for the declaration of CSS states, example:

```jsx
const props = {
  checked: {
    type: Boolean,
    reflect: true,
  },
};
```

### Prop.event

It allows dispatching an automatic event before the prop value change, example:

```javascript
const props = {
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

Where:

* `event.type`: String - optional, name of the event to be emitted when the prop is changed
* `event.bubbles`: Boolean - optional, indicates that the event can be listened to by containers.
* `event.detail`: Any - optional, allows to attach a custom detail for the event
* `event.cancelable`: Boolean - optional, indicates that the event can be canceled by any listener
* `event.composed`: Boolean - optional, allows the event to exceed the shadow-root limit

The special properties of the event are the well-known `Event Init`, you can know more details in the [attached documentation](https://developer.mozilla.org/en-US/docs/Web/API/Event/Event).

### Prop.value

Atomico allows the definition of default values of the props.

```javascript
const props = {
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

The association of callback as value allows generating unique values for each instance of the webcomponent, this is useful with the Object and Array types since it eliminates the references between instances.

## Reactivity in the scope of the webcomponent

Atomico removes the use of "this" given its functional approach, but adds the hook \[useProp] (hooks / useprop.md) which allows to reference a prop for use with a functional syntax, eg:

```jsx
const props = { message: String };

const MyComponent = c(
  () => {
    const [message, setMessage] = useProp("message");
    return (
      <host>
        Hello, {message}
        <input oninput={({ target }) => setMessage(target.value)} />
      </host>
    );
  },
  { props }
);
```

## Recommended articles

{% content-ref url="../../guides/frequent-questions/is-it-advisable-to-declare-events-using-the-props-api.md" %}
[is-it-advisable-to-declare-events-using-the-props-api.md](../../guides/frequent-questions/is-it-advisable-to-declare-events-using-the-props-api.md)
{% endcontent-ref %}

{% content-ref url="value-cycle-as-prop.md" %}
[value-cycle-as-prop.md](value-cycle-as-prop.md)
{% endcontent-ref %}
