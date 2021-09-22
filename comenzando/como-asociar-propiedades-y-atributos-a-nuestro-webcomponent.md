# ¿Cómo asociar propiedades y Atributos a nuestro webcomponent?

Atomico agiliza la creación de propiedades y atributos para tus webcomponents mediante la asociación del objeto props.

```javascript
function component(props){
    return html`<host>${props.myProp}</host>`;
}

component.props = {
    // DECLARACION SIMPLE
    myProp  : String,
    // DECLARACION ESTRUCTURADA
    myProp  : {
        type : String
    }
}
```

A través de este objeto puedes definir la props\(Propiedades y Atributos\) de tu webcomponent y cada prop posee su declaración:

1. \*\*\*\*[**Declaraciones simples**](../api/props.md#declaraciones-simple) permiten definir solo el [tipo de la prop](../api/props.md#prop-type)
2. \*\*\*\*[**Declaraciones estructuradas**](../api/props.md#declaraciones-estructuradas) permiten definir el [tipo de la prop](../api/props.md#prop-type) y efectos como: 
   1. \*\*\*\*[**Reflejar el valor como atributo.**](../api/props.md#prop-reflect) 
   2. \*\*\*\*[**Emitir un evento ante el cambio del valor**](../api/props.md#prop-event)**.**
   3. \*\*\*\*[**Poseer un valor de inicio.**](../api/props.md#prop-value) ****
   4. **Redefinir el atributo.**

Las declaraciones pueden trabajar de forma conjunta y su uso depende de la necesidad de tu componente.



Todo valor  capturado desde la instancia del webcomponent será entregado al componente funcional mediante el primer parámetro props, internamente el componente puede actualizar los estados de las props mediante el  ****el tag **host** o el ****hook [**useProp**](../api/hooks/useprop.md).

### prop y useProp

```javascript
const [myProp,setMyProp] = useProp("count");
```



### 





