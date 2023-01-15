# Tokens (CSS custom properties)

Los tokens son valores configurables de nuestro sistema de diseño representados usando css custom properties, en esta guía encontraras recomendaciones de uso para que tu proyecto escale y sea configurable sin complicaciones&#x20;

## CSS custom properties

### Contexto a nivel de :root&#x20;

El seudo selector :root nos permite definir tokens que podrán ser accedidos a nivel de todo el documento incluso shadowDOM, para aprovechar esta ventaja lo ideal es mantener el siguiente patrón.

un documento theme sea CSS o JS que defina todos los tokens como custom property a nivel de :root, ejemplo:

```css
:root{
    --my-design-system--color-primary: red;
}
```

Te invito a notar que para este caso hemos asociado el como prefijo de nombre la cadena`--my-design-system`, la idea de esto es minimizar conflicto y definir un namespace que identifique las css custom properties que nos pertenecen a nivel de sistema de diseño.

### Contexto a nivel de :host

El seudo selector :host nos permite encapsular estilos que apuntan a la instancia de nuestro webcomponent, gracias a :host podemos facilitar el acceso a las css custom properties provenientes de :root, esto es práctico ya que facilita el mantenimiento y es automatizable, ejemplo:

```css
:host{
    --color-primary: var(--my-design-system--color-primary);
}
```





