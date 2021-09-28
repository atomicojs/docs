---
description: Comunica el componente con formularios externos.
---

# use-form

### Instalación

```bash
npm install @atomico/hooks
```

### Modulo

```javascript
import { useForm, useFormListener, useFormValue } from "@atomico/hooks/use-form";
```

### Sintaxis useForm

```javascript
const ref = useForm()
```

### Sintaxis useFormListener

```javascript
useFormListener("reset",handler);
```

### Sintaxis useFormValue

Recupera el valor serializado de un formulario y crea un input hidden para definir un field manualmente 

```javascript
const [value, setValue] = useFormValue("my-field");
```

