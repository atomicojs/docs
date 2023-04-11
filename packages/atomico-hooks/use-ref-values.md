---
description: Consume the values of a reference without major inconvenience
---

# use-ref-values

This hook has a behavior similar to useEffect but focused on resolving the consumption of one or more references.

### Example

```jsx
import { useRef } from "atomico";
import { useRefValues } from "@atomico/hooks/use-ref-values";

function component(){
    const ref = useRef();
    
    useRefValues(
        // 👇 current will be the value assigned to ref.current
        ([current])=>{
            // 1️⃣ here the effect dependent on the reference
            // 🔴 The following line is optional
            return ()=>{
            // (Optional) here the cleanup of the reference dependent effect
            }
        },
        [ref]
    );
    
    return <host>
        <input ref={ref}/>
    </host>
}
```
