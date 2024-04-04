---
description: Dispatch events from the webcomponent without referencing the context(this)
---

# useEvent

## Syntax

```javascript
const dispatchEvent = useEvent(myEvent, eventInit);
```

Where:

* dispatchEvent: **callback,** dispatches the event from the webcomponent and allows defining the detail by receiving a first parameter
* myEvent: **string**, name of the event to dispatch.
* eventInit: **optional object**, event configuration.

## Examples

{% tabs %}
{% tab title="Basic" %}
```jsx
import { useEvent } from "atomico";

function component() {
  const dispatchEvent = useEvent("clickButton", {
    bubbles: true,
    composed: true,
  });
  return (
    <host>
      <button onclick={() => dispatchEvent()}>button</button>
    </host>
  );
}
```
{% endtab %}

{% tab title="Detail" %}
```javascript
import { useEvent } from "atomico";

function component() {
  const dispatchEvent = useEvent("clickButton", {
    bubbles: true,
    composed: true,
  });
  return (
    <host>
      <button onclick={() => {
        const detail = "my-component"; // 👈
        dispatchEvent(detail);         // 👈
      }}>button</button>
    </host>
  )c
```
{% endtab %}

{% tab title="Typescript ⚡ " %}
```typescript
import { Host, useEvent } from "atomico";

type DetailClickButton = {id: number};
//                             👇 declaration to associate event to JSX/TSX
function component():Host<{onclickButton: CustomEvent<DetailClickButton>}> {
//                             👇 type for detail
  const dispatchEvent = useEvent<DetailClickButton >("clickButton", {
    bubbles: true,
    composed: true,
  });
  return (
    <host>
      <button onclick={() => {
        //            👇 Detail
        dispatchEvent({id:100});
      }}>button</button>
    </host>
  );
}
```
{% endtab %}
{% endtabs %}

## Event customization

The second parameter of `useEvent` allows customizing the behavior of the even:

```typescript
interface EventInit {
  // Allows the event to be dispatched upstream to the node's containers.
  bubbles?: boolean;
  // Allows the event to traverse the shadowDOM event capture.
  composed?: boolean;
  // Allows the event to be canceled.
  cancelable?: boolean;
  // Allows customizing the event builder, ideal for event instance-based communication.
  base?: Event | CustomEvent;
}
```

## Recommended articles

{% content-ref url="../../guides/frequent-questions/how-to-declare-events-for-your-component-at-the-type-level-for-tsx.md" %}
[how-to-declare-events-for-your-component-at-the-type-level-for-tsx.md](../../guides/frequent-questions/how-to-declare-events-for-your-component-at-the-type-level-for-tsx.md)
{% endcontent-ref %}
