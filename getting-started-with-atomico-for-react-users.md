---
description: >-
  Hi, I'm Atomico js and I bring you the React syntax for webcomponents, I think
  you and I get along very well 😊.
---

# ⚛️ Getting started with Atomico for React users

First let's say that Atomico is light since it has a size close to 3kB vs React + ReactDOM that have a size close to 60kB, now if your project is already written in React I can integrate Atomico progressively since a component created can be instantiated as a component for React thanks to [@atomico/react](packages/atomico-react.md), example:

```tsx
import { Button } from "@formas/button/react";

function App(){
   return <>
      <h1>React App!</h1>
      <Button onClick={()=>console.log("Click!")}>
         Submit
      </Button>
   </>
}
```

Magical :magic\_wand:, isn't it?... well now let's speed up your Atomico learning path:

## How to declare a component?

Atomico, like React, allows a declaration of components using only functions, example:

{% tabs %}
{% tab title="React" %}
```jsx
import { useState } from "react";
import ReactDOM from 'react-dom'

function Counter({initialCount}) {
  const [count, setCount] = useState(initialCount);
  return (
    <>
      Count: {count}
      <button onClick={() => setCount(initialCount)}>Reset</button>
      <button onClick={() => setCount(prevCount => prevCount - 1)}>-</button>
      <button onClick={() => setCount(prevCount => prevCount + 1)}>+</button>
    </>
  );
}


render(
  <Counter initialCount={1}/>, 
  document.querySelector("#counter")
);
```
{% endtab %}

{% tab title="Atomico ✅" %}
```jsx
import { c, useProp } from "atomico";

const props = { count: { type: Number, value: 0 } };

const Counter = c(
  () => {
    const [count, setCount] = useProp("count");
    return (
      <host>
        Count: {count}
        <button onClick={() => setCount((prevCount) => prevCount - 1)}>-</button>
        <button onClick={() => setCount((prevCount) => prevCount + 1)}>+</button>
      </host>
    );
  },
  { props }
);

customElements.define("my-counter", Counter);
```
{% endtab %}
{% endtabs %}

From the example we will highlight the following differences:

1. In Atomico you only use one import.
2. `useProp` is like `useState`, but with the difference that useProp references the state from the webcomponent property defined in `counter.props`.
3. `const props` allows us to create the properties of our webcomponent, these are like React's propTypes, but with a big difference they are associated with the instance and can be read and modified by referencing the node, example `document.querySelector("my-counter").count = 10;`
4. `ReactDom.render` needs a reference to mount the component, in Atomico you only need to create the `my-counter` tag to create a new instance of the component.
5. The `<host/>` tag is similar to `<> </>` for React, but `<host/>` represents the webcomponent instance and **every component created with Atomico must return the host tag**
6. This is only readability, but in Atomico by convention we do not use capital letters when naming our component, these are only used when creating the customElement as in line 16, since `Counter` is instantiable.

Now I want to invite you to learn how to declare a style using Atomico.

## How do you declare styles using Atomico?

It is common to see the use of libraries such as Emotion or styled-components to encapsulate styles in React, but these add an additional cost, be it for performance or bundle, in Atomico there is no such cost.

{% tabs %}
{% tab title="React" %}
```jsx
const Button = styled.a`
  /* This renders the buttons above... Edit me! */
  display: inline-block;
  border-radius: 3px;
  padding: 0.5rem 0;
  margin: 0.5rem 1rem;
  width: 11rem;
  background: transparent;
  color: white;
  border: 2px solid white;

  /* The GitHub button is a primary button
   * edit this to target it specifically! */
  ${props => props.primary && css`
    background: white;
    color: black;
  `}
`

render(
  <div>
    <Button
      href="https://github.com/styled-components/styled-components"
      target="_blank"
      rel="noopener"
      primary
    >
      GitHub
    </Button>

    <Button as={Link} href="/docs">
      Documentation
    </Button>
  </div>
)
```
{% endtab %}

{% tab title="Atomico  ✅" %}
```jsx
import { c, css } from "atomico";

const props = { primary: { type: Boolean, relfect: true } };

const styles = css`
  :host {
    display: inline-block;
    border-radius: 3px;
    padding: 0.5rem 0;
    margin: 0.5rem 1rem;
    width: 11rem;
    background: transparent;
    color: white;
    border: 2px solid white;
  }

  :host([primary]) {
    background: white;
    color: black;
  }
`;

export const Button = c(
  () => (
    <host shadowDom>
      <slot />
    </host>
  ),
  { props, styles }
);

customElements.define("my-button", Button);
```
{% endtab %}
{% endtabs %}

## Instances, children and slots

It is normal for React to create components that you then instantiate within other components, for example:

```tsx

function Child({children}){
    return <span>children</span>
}

function Main(){
    return <>
        <Child>text 1...</Child>
        <Child>text 2...</Child>
    </>
}
```

with Atomico there are certain differences:

### 1. With Atomico you can instantiate CustomElements using its constructor

The constructor in Atomic is the product of the c function and is the one you will use to register your webcomponent, example:

<pre class="language-tsx"><code class="lang-tsx"><strong>import { c } from "atomico";
</strong>
function myComponent(){
    return &#x3C;host>
        ...
    &#x3C;/host>
}

export const MyComponent = c(myComponent); // Constructor

customElements.define("my-component", MyComponent);
</code></pre>

According to the previous example, you can instantiate MyComponent as a JSX Component, example:

```tsx
import { c } from "atomico";
import { MyComponent } from "./my-component";

function myApp(){
    return <host>
        <MyComponent/>
    </host>;
}

export const MyApp = c(myApp);

customElements.define("my-app", MyApp);
```

This instance type allows autocompletion at the JSX level and type validation at the Typescript level.

### 2. With Atomico you can instantiate components as functions as long as these are only stateless functions

```tsx
function MyStatelessTemplateBlock(){

}

function MyComponent(){
    return <host>
        <MyStatelessTemplateBlock/>
    </host>
}
```

This will be useful for reusing templates, but always remember stateless.

{% content-ref url="guides/atomico-and-react/from-react-to-atomico/" %}
[from-react-to-atomico](guides/atomico-and-react/from-react-to-atomico/)
{% endcontent-ref %}

{% content-ref url="guides/atomico-and-react/from-react-to-atomico/virtualdom-api-differences.md" %}
[virtualdom-api-differences.md](guides/atomico-and-react/from-react-to-atomico/virtualdom-api-differences.md)
{% endcontent-ref %}
