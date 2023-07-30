# When and why to use shadowDom?

Cuando usar el shadowDom

El shadowDom es la mejor forma de protejer nuestro contenido si este reprecenta 2 tipos de logica:

1. Manejo de slots
2. Menejos de estilos propios del webcomponent.

## Manejo de slots

Los slots nos permiten reflejar nodos existentes en el lightDOM dentro del shadowDOM, ejemplo:

<figure><img src="../../.gitbook/assets/web_1366_7.png" alt=""><figcaption></figcaption></figure>

Esto es realmente util, ya que podemos agrupar slots segun su name en  un lugar espesifico del webcomponent

Te invitamos a aprender mas de los slots a través de la siguiente guia

{% content-ref url="../atomico-design-patterns/slot.md" %}
[slot.md](../atomico-design-patterns/slot.md)
{% endcontent-ref %}

## Manejos de estilos

El shadowDOM te permite algo fantástico, proteger tu CSS de estilos globales, esto tiene 2 grandes ventajas:

1. La apariencia de nuestro componente no se vera afectada por declaraciones globales de CSS.
2. Las customProperties serán la forma de configurar nuestro componente.

Te invitamos a aprender mas de manejo de estilos en atomico a travez de la siguiente guia:

