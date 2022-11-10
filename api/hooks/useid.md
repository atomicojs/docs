# useId

`useId` is a Atomico Hook for generating unique IDs that can be passed to accessibility attributes.

### Syntax

```tsx
import { useId } from "atomico";

const stringId = useId();
```

### Example

Use ID generate a unique ID for each component, this id can be useful for referencing CSS selectors or creating names for inputs that only the component knows about.

```tsx
function component() {
  const id = useId();
  return <host id={id}>
    <style>{`#${id}{ display: block; color: white; }`}</style>
    <h1>useId</h1>
  </host>;
}
```
