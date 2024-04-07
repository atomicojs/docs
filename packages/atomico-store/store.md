---
description: >-
  It is a minimalist solution for synchronizing the state of applications or
  component systems that require controlled bidirectional data management.
---

# Store

## Getting Started

Stores in Atomico are web components with behavior similar to the Atomico context API, for example:

### **Creating the store**

```tsx
import { createContext } from "@atomico/store";

const MyStore = createContext({ counter: 0 });

customElements.define("my-store", MyStore);
```

### **Defining the store**

```tsx
import { c } from "atomico";
import { MyStore } from "./my-store";

export const MyApp = c(() => {
  return (
    <host>
      <MyStore state={{ counter: 0 }}>
        <slot />
      </MyStore>
    </host>
  );
});
```

### **Consuming the store**

```tsx
import { c } from "atomico";
import { useStore } from "@atomico/store";
import { MyStore } from "./my-store";

export const MyApp = c(() => {
  const store = useStore(MyStore);
  return (
    <host>
      <button onclick={() => store.counter++}>
        Increment: {store.counter}
      </button>
    </host>
  );
});
```

### Bidirectional State Management?

If you're familiar with the Atomico context API, you'll know it's unidirectional, meaning the parent dispatches updates to the child. @atomico/store is bidirectional, allowing any store consumer to synchronize. This means the parent can dispatch updates to the child, and the child can dispatch updates to the parent.
