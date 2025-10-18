---
description: Atomico's virtualDOM is designed to enhance the use of webcomponents.
icon: puzzle-piece
---

# VirtualDOM

## Syntax

### JSX

```jsx
import { c } from "atomico";

const MyComponent = c(() => {
  const handlerClick = () => console.log("click!");
  return (
    <host shadowDom onclick={handlerClick}>
      <h1>content</h1>
      <slot></slot>
    </host>
  );
});

customElements.define("my-component", MyComponent);
```

**Atomico supports jsx-runtime**, alternatively you can import the `h` function to declare manual of the JSX pragma, eg:

```javascript
/**@jsx h*/
import { h } from "atomico";
```

## Return rule

```jsx
import { c } from "atomico";

const MyComponent = c(() => {
  // The webcomponent should always return the host tag
  return (
    <host shadowDom>
      <slot></slot>
    </host>
  );
});

customElements.define("my-component", MyComponent);
```

An important rule of Atomico's virtualDOM is that **every webcomponent must return the `<host/>` tag** since it represents the state of the webcomponent's DOM, such as:

1. Enable the use of the shadowDOM by declaring the `shadowDom` property.
2. Association of events, attributes or properties.
3. Template of the webcomponent.

## Template

### Event Association

Atomico considers that a property must be associated as an event if it is of the function type and begins with the prefix 'on', eg:

```jsx
<host onclick={() => console.log("click!")}></host>;
<host onMyEvent={() => console.log("MyEvent!")}></host>;
<input oninput={() => console.log("click!")} />;
<slot onslotchange={() => console.log("update slot!")} />;
```

### Simple lists

```jsx
<host>
  {[1, 2, 3].map((value) => (
    <span>{value}</span>
  ))}
</host>
```

### Lists with keys

```jsx
<host>
  {[1, 2, 3].map((value) => (
    <span key={value}>{value}</span>
  ))}
</host>
```

the key property can receive values of the type of any type that allows generating a reference to the node, eg:

```jsx
<host>
  {listaInmutable.map((objeto) => (
    <span key={objeto}>{objeto.value}</span>
  ))}
</host>
```

### Node references

A technique inherited from React, it allows obtaining the reference of the node to which the Ref object is associated through the ref property, example:

```jsx
const ref = useRef();

<host ref={ref}></host>; // The reference will be the instance 
                         // of the custom Element

<input ref={ref}/>; // The reference will be the input
```

The references must be immutable objects, to create it there is the [**useRef** ](../hooks/useref.md)hook that creates a reference for each instance of the webcomponent.

### shadowDom property

This property allows you to declare the use of the shadowDom, eg:

```jsx
<host shadowDom></host>;
// The use of shadow Dom is not exclusive to the host tag
// can be used for any node that supports it
<div shadowDom></div>;
```

### Method association

You can declare a method by declaring a function in the host tag without using the prefix on in its name, eg:

```jsx
// Template
<host myMethod={() => console.log("method!")}></host>;
// Use from the DOM
document.querySelector("my-component").myMethod();
```

If when creating or updating the DOM it does not detect the use of the property, it will be associated as a method of this, thus allowing it to be accessed from the DOM, eg:

```jsx
const myElement = new MyElement();

await myElement.updated;

myElement.myMethod();
```

To access the DOM safely wait for the resolution of the updated property created by the [render cycle](../testing/test-dom.md).
