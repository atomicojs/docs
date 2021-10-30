---
description: >-
  La siguiente guia define algunos tips a considerar al momento de crear
  webcomponents con Atomico
---

# 🎯 Tips

### Nombre de la función

Escriba el componente funcional usando el primer carácter en minúsculas, ya que la declaración funcional no es instanciable como constructor en JSX.

```jsx
function component() {
  return <host />;
}
```

Esto evitara confusiones al momento de deducir cual es el constructor de la instancia del componente.[ Atomico si posee soporte a las instancias como Constructores, ver casos.](https://atomico.gitbook.io/doc/v/espanol/api/virtualdom/avanzado#constructor-con-custom-element)

### useProp

utilice preferentemente useProp en los siguientes casos:

1. Al modificar la prop desde el interior del componente.

```jsx
function component() {
  const [value = 0, setValue] = useProp("value");
  return (
    <host>
      <h1>{value}</h1>
      <button onclick={() => setValue(value + 1)}>Increment</button>
    </host>
  );
}

component.props = {
  value: Number,
};
```

1. Al asilar la logica de la prop en un customHook.

```jsx
function useCounter(prop) {
  const [value, setValue] = useProp(prop);
  return {
    value,
    increment() {
      setValue(value + 1);
    },
  };
}
```

En la mayoría de los casos bajar la prop desde el primer argumento de la función es mas simple y declarativo, ejemplo:

```jsx
function component({ value }) {
  return <host>{value}</host>;
}

component.props = {
  value: Number,
};
```

[Atomico posee soporte de tipos tanto en JSDOC como Typescript al inferir los tipos de las props.](https://atomico.gitbook.io/doc/v/espanol/api/virtualdom/avanzado#constructor-con-custom-element)

### Prefiera el uso de estilos estáticos

```jsx
function component() {
  return <host shadowDom />;
}

component.styles = css`
  :host {
    display: block;
  }
`;
```

Esto no descarta el uso dentro del tag style, ya que en ocasiones es la solución a la definición de estilos condicionales o variables al la lógica y fuera del alcance de las custom properties.
