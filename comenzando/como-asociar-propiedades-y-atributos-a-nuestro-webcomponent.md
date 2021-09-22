# Propiedades y atributos

Atomico agiliza la creación de propiedades y atributos para tus webcomponents mediante la configuración del objeto props.

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

1. \*\*\*\*[**Declaraciones simples**](../api/props.md#declaraciones-simple) permiten definir solo el tipo de la prop
2. \*\*\*\*[**Declaraciones estructuradas**](../api/props.md#declaraciones-estructuradas) permiten definir el tipo y efectos como: 
   1. Reflejar el valor como atributo. 
   2. Emitir un evento ante el cambio del valor.
   3. Poseer un valor de inicio. 
   4. Redefinir el atributo.

Todo valor  capturado desde la instancia del webcomponent será entregado al componente funcional mediante el primer parámetro props, internamente el componente puede actualizar los estados de las props mediante el hook **useProp** o el tag **host**.

### useProp\(&lt;myProp&gt;\)

```javascript
const [myProp,setMyProp] = useProp("count");
```



### 





