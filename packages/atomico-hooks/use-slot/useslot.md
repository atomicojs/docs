# useSlot

### Module

```javascript
import { useSlot } from "@atomico/hooks/use-slot";
```

### Syntax

```javascript
const optionalFilter = (element)=> element instanceof MyCustomElement;
const childNodes = useSlot(ref, optionalFilter);
```

Where:

1. `ref`: Reference of the slot to observe.
2. `childNodes`: List of nodes assigned to the observed slot.

### Live example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/RjrShAkF1NYMkBbyNOaP/src/index.jsx" %}

