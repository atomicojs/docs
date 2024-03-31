---
description: Allows the host that instantiates this useProvider to become the context.
---

# useProvider

This hook enables you to take control of the context from the component that instantiates `useProvider`, thus avoiding the need to instantiate the context node in the DOM.

### Example of the useProvider hook:

```tsx
import { createContext, useProvider, c } from "atomico";

export const Theme = createContext({
    color: "white",
    background: "black"
});

export const App = c(()=>{
    useProvider(Theme,{
        color: "red",
        background: "yellow"
    });
    
    return <host shadowDom><slot/></host>
});


```

### Objective

Avoid creating an instantiable context node in the DOM.

