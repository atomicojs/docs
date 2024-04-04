---
description: >-
  It is not recommended to use the props API to create an event, as this
  callback associated as props will have the following limitations:
---

# Is it advisable to declare events using the props API?

1. Its name cannot have the `on` prefix since, if it does, Atomico will recognize it as a property expecting to listen to the event.
2. It can only have one listener, limiting others from observing the event.

### **We recommend**:

1. Using the [**useEvent**](../../api/hooks/useevent.md) hook to dispatch component-level events or any custom hook.
2. Using the [**Prop.event**](../../api/props/#prop.event) API to dispatch events when the observed prop changes.

Always prefer the two previously mentioned methods, as they allow you to:

1. Define if the event bubbles.
2. Define if the event is cancelable.
3. Define if the bubbling event can penetrate the shadow DOM.
4. Define a custom constructor for the event.
5. Having multiple listeners for the event

### When is it recommended to use a callback as a prop?

Cuando se busca comunicar parametros o leer el retorno de este, ejemplo:

```tsx
const MyForm = c(
  ({ getPosts }) => {
    const posts = useAsync(getPosts, []);

    return <host></host>;
  },
  {
    props: {
      getPosts: {
        type: Function,
        value: async (): Promise<{ id: number; title: string }[]> => [],
      },
    },
  }
);
```
