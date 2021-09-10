# ¿Cómo asociar propiedades y Atributos a nuestro webcomponent?

Constantemente  usamos atributos o propiedades en el HTML para definir estados, manifestar apariencia o generar interacción, ejemplo la instancia  del tag input:

```markup
<input type="checkbox" checked>
```

Define gracias al uso de **Atributos** que  nuestro tag input es del tipo `checkbox` y su estado `checked` es `true`. Podríamos lograr lo mismo usando **propiedades:**

```javascript
const input = document.createElement("input");

input.type = "checkbox";
input.checked = true;
```

Atomico te permite generar ese formato de atributos y propiedades, para construir los atributos y propiedades deberás definir un objeto llamado **props** a tu componente:

```javascript
import {c, html } from "atomico";

function component(){
    return html`<host></host>`
}

component.props = {}

customElements.define("mi-componente",c(component));
```

A este objeto **props** podemos definirle mediante índice y valor lo siguiente:

* índice: propiedad y atributo que poseerá nuestro webcomponent.
* valor: tipo de dato a usar para dicha propiedad y atributo. 

Comenzaremos  con las declaraciones simples.

```javascript
component.props = {
    miMensaje: String
}
```

Con lo anterior hemos creado en nuestro componente 1 propiedad llamada `miMensaje` y un atributo llamado `mi-mensaje`, el que podríamos definir externamente de la siguiente forma:

{% tabs %}
{% tab title="Atributo" %}
```markup
<mi-componente mi-mensaje="hola mundo"></mi-componente>
```
{% endtab %}

{% tab title="Propiedad" %}
```javascript
const component = document.createElement("mi-componente");

component.miMensaje = "hola mundo"
```
{% endtab %}
{% endtabs %}

Quiero que notes que el uso de guion en el atributo y es porque atomico transforma las prop camelCase a kebakCase

