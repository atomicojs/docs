---
description: Componente modal genérico responsivo.
---

# modal

## Modulo

```javascript
import {
  Modal, // HTMLElement
} from "@atomico/components/modal";
```

## Ejemplo

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

## Propiedades

**showAfterMs / show-after-ms**: `String`, define los milisegundos a esperar para la activación del modal.

**show**: `Boolean`, define si mostrar o no el modal.

**padding:** `String responsivo`, define un padding para el contenido del modal, ejemplo:

1. `padding="1rem"`
2. `padding="1rem, 2rem 720px, 3rem 1080px"`

**position**: `String responsivo`, define la posición del contenido dentro del modal, ejemplo:

1. `position="center"`
2. `position="center top"`
3. `position="center bottom"`
4. `position="left center"`
5. `position="right center"`
6. `position="center, right bottom 1080px"`

**fullSize / full-size**: `Boolean`, Habilita el uso background en el modal, este se complementa con el slot background para adjuntar contenido personalizado en el fondo.

**fullSizeClosed / full-size-closed**: `Boolean`, define si el clic en el background oculta el modal.

