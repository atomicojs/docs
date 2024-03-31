# useCurrentValue

The `useCurrentValue` hook allows associating a value with `current` based on its parameter, equivalent to:

```tsx
const ref = useRef();

ref.current = value;
```

With the `useCurrentValue` hook

```tsx
useCurrentValue(value)
```
