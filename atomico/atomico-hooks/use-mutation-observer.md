# use-mutation-observer

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useMutationObserver, useMutationObserverState } from "@atomico/hooks/use-mutation-observer";
```

### Sintaxis useMutationObserver

```typescript
useMutationObserver(
    ref: Ref<Element>,
    observe: MutationCallback,
    config?: MutationObserverInit
);
```

### Sintaxis useMutationObserver

```typescript
const mutations:MutationRecord[] =useMutationObserverState (
    ref: Ref<Element>,
    config?: MutationObserverInit
);
```

