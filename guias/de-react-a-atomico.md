---
description: >-
  Atomico hereda parte dela sintaxis de React y la aplica a los webcomponents,
  con un enfoque mas cercano al estándar.
---

# De React a Atomico

#### Si ya eres desarrollador de React y conoces el api de Hooks tendrás el 80% del camino recorrido de Atomico, el 20% restante es un Atomico facilitando el api webcomponents... ahora **¿por que usar Atomico?**:

1. **Atomico no limitara tu curva de aprendizaje de React**, lo aprendido en Atomico es aplicable en React, ejemplo los hooks y virtualDOM. 
2. **Atomico solo pesa 3kB** que es el 7% de  React + React-dom.
3. **Mejor abstracción de componentes**, por ejemplo el uso del ShadowDOM evitara la necesidad de usar css-in-js como styles-components. 
4. **Componentes Agnósticos**, lo que creas con React solo funciona dentro de React, lo que creas con Atomico funciona en la web, por lo que podrás tus componentes dentro de React, Vue, Svelte o html.

Los siguientes ejemplos muestran algunas diferencias entre React y Atomico.

### Ejemplo de componente counter

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

function counter() {
  const [count, setCount] = useProp("count");
  return (
    <host>
      Count: {count}
      <button onClick={() => setCount(prevCount => prevCount - 1)}>-</button>
      <button onClick={() => setCount(prevCount => prevCount + 1)}>+</button>
    </host>
  );
}

counter.props = { count: { type: Number, value: 0 } }

const Counter = c(counter);
customElements.define(
  "my-counter",
  Counter  
);
```
{% endtab %}
{% endtabs %}

Del ejemplo destacaremos las siguientes diferencias:

1. En Atomico solo usas una importación.
2. `useProp` es como `useState`, pero con la diferencia que `useProp` referencia el estado desde la propiedad del webcomponent definida en counter.props.
3. `counter.props` nos permite crear las propiedades de nuestro webcomponent, estas son como las props de React, pero con una gran diferencia se asocian a la instancia y pueden ser leídas y modificadas referenciando el nodo, ejemplo `document.querySelector("my-counter").count = 10;`
4. `ReactDom.render` necesita una referenciamos para montar el componente, en Atomico solo necesitas crear el tag `my-counter`  para crear una nueva instancia del componente.
5. El tag host de Atomico similar a los fragmentos de React, pero este representa la instancia del webcomponent y **todo componente creado con Atomico debe retornar el tag `host`**
6. Esto solo es legibilidad, pero en Atomico no usamos mayúsculas al nombra nuestro componente, estas solo se usan al momento de crear el customElement como en la linea 16, ya que `Counter` si es instanciable

### Ejemplo de customHooks

{% tabs %}
{% tab title="React" %}
```jsx
import { useEffect, useState } from "react";

function useJsonPlaceholder(path) {
  const [state, setState] = useState();
  useEffect(() => {
    let cancel;
    setState(null);
    fetch(`https://jsonplaceholder.typicode.com/${path}`)
      .then(() => res.json())
      .then((data) => !cancel && setState(data));
    return () => (cancel = true);
  }, [path]);
}

export function Component() {
  const posts = useJsonPlaceholder("posts");
  return (
    <>
      {posts 
        ? posts.map(({ title }) => <h1>{title}</h1>)
        : "Loading..."}
    </>
  );
}
```
{% endtab %}

{% tab title="Atomico ✅" %}
```jsx
import { useEffect, useState } from "atomico";

function useJsonPlaceholder(path) {
  const [state, setState] = useState();
  useEffect(() => {
    let cancel;
    setState(null);
    fetch(`https://jsonplaceholder.typicode.com/${path}`)
      .then(() => res.json())
      .then((data) => !cancel && setState( data ));
    return () => (cancel = true);
  }, [path]);
}

function component() {
  const posts = useJsonPlaceholder("posts");
  return (
    <host>
      {posts 
        ? posts.map(({ title }) => <h1>{title}</h1>)
        : "Loading..."}
    </host>
  );
}
```
{% endtab %}
{% endtabs %}

Del ejemplo destacaremos las siguientes diferencias:

1. El api de hooks es igual.
2. el componente en Atomico retorna el tag host.

#### Hooks soportados

En Atomico encontraras los hooks mas utilitarios de React como: 

1. useRef
2. useState
3. useReducer
4. useLayoutEffect
5. useEffect
6. useMemo
7. useCallback
8. ~~useContext~~ : **No soportado**, el api de eventos es mejor practica que contexto al usar webcomponents, si buscas un homologo puedes usar [**useChannel**](../atomico/atomico-hooks/use-channel.md), basado en el api de eventos.

