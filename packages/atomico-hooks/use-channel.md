---
description: create connection between components to share internal states
---

# use-channel

Now, Atomico includes a context API as part of its core. We recommend implementing it as an alternative to using `useChannel`.

{% content-ref url="../../api/hooks/usecontext/" %}
[usecontext](../../api/hooks/usecontext/)
{% endcontent-ref %}

\
An alternative to React's context but solely based on hooks.

### Modulo

```javascript
import { useChannel } from "@atomico/hooks/use-channel";
```

### Syntax

```javascript
const channel = "MyChannel";
const [parentValue, setChildValue] = useChannel(channel);
```

Where :

1. `channel`: `String`, defines the name of the event to be used to generate the channel.
2. `parentValue`: Value inherited by the parent component.
3. `setChildValue`: `Callback`, defines a value for nested components.

### Example

{% embed url="https://webcomponents.dev/edit/collection/n2tZyzx4LMKqk1jNE0e9/34DlYUfeqmk0sO3BUa31/src/index.jsx" %}

This hook is used by [@atomico/components/router](../atomico-components/keen-slider.md)
