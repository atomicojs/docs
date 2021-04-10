---
description: Componente modal genérico responsivo.
---

# modal

### Modulo

```javascript
import {
    Modal // HTMLElement
} from "@atomico/components/modal";
```

### Ejemplo

{% tabs %}
{% tab title="HTML" %}
```markup
<atomico-modal show-after-ms="5000">
    <div>
        <img src="./image.jpg"/>
        <button data-closed>Cerrar</button>
    </div>
</atomico-modal>
```
{% endtab %}

{% tab title="IMPORT" %}
```javascript
import { Modal } from "@atomico/components/modal";

customElements.define("atomico-modal", Modal);
```
{% endtab %}
{% endtabs %}

### Propiedades

| Props | Tipo | Descripción |
| :--- | :--- | :--- |
| showAfterMs | Number | Segundos a esperar para mostrar el modal |
| show | Boolean | De ser true se muestra el modal. |
| position | String. &lt; center \| left \| right, center \|  top \| bottom &gt; | Posición del modal |
| fullSize  | Boolean | De ser true el modal creara un background a pantalla completa. |
| fullSizeClosed | Boolean | De ser true el modal puede ser cerrado al hacer clic en el background. |



