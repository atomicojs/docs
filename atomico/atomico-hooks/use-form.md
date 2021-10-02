---
description: Communicate the component with external forms.
---

# use-form

### Module

```javascript
import { useForm, useFormListener, useFormValue } from "@atomico/hooks/use-form";
```

### useForm syntax

```javascript
const ref = useForm()
```

### useFormListener syntax

```javascript
useFormListener("reset",handler);
```

### useFormValue syntax

retrieve the serialization of the value of a form and create a hidden input to set a manual field

```javascript
const [value, setValue] = useFormValue("my-field");
```

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/NuVzTC7iXlKSxhl112pJ/src/index.jsx" %}


