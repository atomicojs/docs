---
description: Ejecute useEffect pero de forma asíncrona
---

# use-async-effect

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useAsyncEffect} from "@atomico/hooks/use-async-effect";
```

### Sintaxis

```javascript
useAsyncEffect(async ()=>{
    await fetch("...");
});
```

