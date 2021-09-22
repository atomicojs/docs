# Avanzado

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

