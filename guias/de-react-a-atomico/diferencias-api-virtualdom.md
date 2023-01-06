---
description: >-
  Guía  que definen algunas diferencias que existen entre Atomico y React al
  momento de trabajar el DOM.
---

# Diferencias api virtualDOM

El virtualDOM de Atomico es:

1. Cercano al DOM estándar
2. Cobertura adicional a los webcomponents.

### Componentes como constructores

Atomico no soporta el uso de funciones para construir el componente como tradicionalmente lo hacemos en React, para que el componente pueda ser instanciado como constructor debe ser un webcomponent o un Nodo real

{% tabs %}
{% tab title="❌ No soportado" %}
```jsx
function Component(){
    return <host></host>
}

function App(){
    return <host>
        <Component/>
    </host>
}
```
{% endtab %}

{% tab title="✔️ Soportado" %}
```jsx
function component(){
    return <host></host>
}

const Component = c(component);
customElements.define("my-component",Component)

function app(){
    return <host>
        <Component/>
    </host>
}
```
{% endtab %}

{% tab title="✔️ Soportado" %}
```jsx
function app(){
    const Div = document.createElement("div");
    return <host>
        <Image/>
        <Div/>
    </host>
}
```
{% endtab %}
{% endtabs %}

### Asociación de eventos.

Atomico al igual que React necesita el uso del prefijo `on` para anunciar un evento, pero existe una diferencia **Atomico no manipula el nombre del evento por lo que `onClick` es distinto a `onclick`**, el objetivo de esta diferencia es dar soporte a los eventos personalizados.

```jsx
<div>
    <button onclick={console.log}>click</button>
    <button onMyCustomEvent={console.log}>click</button>
    <button onmy-event={console.log}>click</button>
    <button onmouseover={console.log}>click</button>
</div>
```

### Keyes

la propiedad key en Atomico puede ser del tipo String, Number, Symbol u otra referencia inmutable.

```jsx
<div>
    <div key={1}>1</div>
    <div key={symbol}>1</div>
    <div key={immutable}>1</div>
</div>
```

### dangerouslySetInnerHTML

```jsx
<div innerHTML={`<h1>html!</h1>`}/>
```
