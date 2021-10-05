# Avanzado

### Propiedades especiales

| Propiedad | Tipo | Efecto |
| :--- | :--- | :--- |
| shadowDom | Boolean | Habilita el uso del shadowDOM en el nodo |
| renderOnce | Boolean | Renderiza el nodo solo una vez, esto optimiza el proceso de actualización ya que el nodo es ignorado entre actualizaciones.  |
| $&lt;name&gt; | any | el prefijo $ permite definir en todos los casos &lt;name&gt;  como atributo |

### render

Por defecto el render viene configurado para ser usado dentro del webcomponent leyendo el retorno de la función, pero este puede ser usado fuera de Atomico, ejemplo:

{% tabs %}
{% tab title="function h" %}
```javascript
import { h, render } from "atomico";


render(
    h("host",{ style: {background:"red"} }
        h("h1",null,"Text content...")
    ),
    document.querySelector("#app")
);
```
{% endtab %}

{% tab title="JSX" %}
```jsx
import { h, render } from "atomico";


render(
    <host style={{background:"red"}}>
        <h1>Text content...</h1>
    </host>,
    document.querySelector("#app")
);
```
{% endtab %}

{% tab title="Template string\(html\)" %}
```javascript
import { html, render } from "atomico";


render(
    html`<host style=${background:"red"}>
        <h1>Text content...</h1>
    </host>`,
    document.querySelector("#app")
);
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
El primer nodo del render siempre debe ser el tag host.
{% endhint %}

### Constructor con custom element

Esta técnica te permite usar cualquier custom element registrado sin la necesidad de conocer su `tag-name` para su uso, ejemplo:

```jsx
function component(){
    return <host/>
}
// 1️⃣ Creamos el custom element
const Component = c(component);

// 2️⃣ Registramos el custom element
customElements.define("my-component", Component);

function app(){
    return <host>
        <Component/>
    </host>
}
```

Esto posee ciertas ventajas como:

1. Eliminar el apalancamiento del tag-name
2. inferir los tipos de las props y autocompleteado solo si usas JSX y Atomico. 

### Constructor con DOM

Atomico permite el uso del DOM, para ello establece como constructor su nodo creado o recuperado, ejemplo:

```jsx
function component(){

    const Div = useMemo(()=>document.createElement("div"));
    
    return <host>
        <Div style="color: black">content...</Div>
    </host>
}
```

### Constructores dinámicos

Atomico asociara como constructor a la variable asociada a la instancia, ejemplo:

```jsx
function component({ subComponent }){
    const TagName = `my-${subComponent}`;
    
    return <host>
        <TagName/>
    </host>
}
```

### Nodos estáticos 

Atomico permite reutilizar nodos estáticos, mejorando enormemente el performance, ejemplo:

```jsx
const header = <header></header>;

function component(){
    return <host>
        {header}
    </host>
}
```

Considere el uso de nodos estáticos como una técnica contextual, no es una regla.

