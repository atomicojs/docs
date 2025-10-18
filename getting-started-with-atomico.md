---
description: >-
  This guide will know the essentials to start developing webcomponents with
  Atomico
icon: rocket-launch
---

# Getting started with Atomico

Thanks for being here and getting started with Atomico. Let's talk a little about what Atomico offers today:

1. Development agility, Atomico's functional approach simplifies code at all stages of development.
2. Lightweight inside and out, Atomico allows you to create a component with less code and with a low dependency impact. Approximately 3kb.
3. Really fast, Atomico has a [good performance](https://twitter.com/atomicojs/status/1391775734641745929) in the browser and an agile development experience. Let's understand what a webcomponent created with Atomico looks like:

{% code title="MyComponent.jsx" lineNumbers="true" %}
```jsx
// Imports
import { c, css } from "atomico";

// Creating Our Web Component: Custom Element Definition
export const MyComponent = c(
  // Defining Component Render Function
  ({ message }) => {
    return <host shadowDom>{message}</host>;
  },
  {
    // Defining Component Properties(props) and Attributes
    props: {
      message: String,
    },
    // Defining Encapsulated Styles for the Component
    styles: css`
      :host {
        font-size: 30px;
      }
    `,
  }
);

// Web Component Registration and Definition
customElements.define("my-component", c(component));
```
{% endcode %}

Let's analyze the code in parts ...

### 1.0 Imports <a href="#importacion" id="importacion"></a>

{% code title="MyComponent.jsx - Line: 1" %}
```javascript
import { c, css } from "atomico";
```
{% endcode %}

What have we imported?

1. `c`: Function that transforms the functional component into a standard customElement.
2. `css`: Function that allows creating the CSSStyleSheet (CSS) for our component as long as it declares the shadowDom.

### 2.0 Creating Our Web Component: Custom Element Definition

#### 2.1 Defining Component Render Function

{% code title="MyComponent.jsx - Line: 7 to 9" %}
```jsx
// Defining Component Render Function
({ message }) => {
    return <host shadowDom>{message}</host>;
}
```
{% endcode %}

Our function receives all the props (Properties and Attributes) declared in `props`, the component function declares all the logic and template of the webcomponent. An important rule within Atomico is **"📌 every component created with Atomico must always return the tag"**.

#### 2.2 Defining Component Properties(props) and Attributes

Atomico detects the prop (Properties and Attributes) of the component thanks to the association of the props object, this through the use of index and value allows you to define:

1. **index**: Name of the property and attribute.
2. **value**: type of the prop.

{% code title="MyComponent.jsx - Line: 12 to 14" %}
```javascript
// Defining Component Properties(props) and Attributes
props: {
  message: String,
},
```
{% endcode %}

From the example we can infer that Atomico will create in our webcomponent a property and attribute called `message` and this can only receive values of the `String` type.

#### 2.3 Defining Encapsulated Styles for the Component

Atomico detects the static styles of your component thanks to the association of the `styles` property:

{% code title="MyComponent.jsx - Line: 16 to 19" %}
```javascript
// Defining Encapsulated Styles for the Component
styles: css`
  :host {
    font-size: 30px;
  }
`,
```
{% endcode %}

styles accepts individual or list CSSStyleSheet (CSS) values, the return from the css function is a standard CSSStyleSheet, so it can be shared outside of Atomico.

### Web Component Registration and Definition

{% code title="MyComponent.jsx - Line: 25" %}
```javascript
// Web Component Registration and Definition
customElements.define("my-component", c(component));
```
{% endcode %}

To create our standard customElement we will have to deliver our functional component to the c function of the Atomico module, the `c` function will generate as a return a customElement that can be defined or extended.

### Example <a href="#ejemplo" id="ejemplo"></a>

[https://play.atomicojs.dev/](https://play.atomicojs.dev/)[\
](https://atomico.gitbook.io/doc/v/es/)
