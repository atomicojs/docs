---
description: >-
  suspend the execution of a render until the resolution of an asynchronous
  process
---

# useAsync and useSuspense

## useAsync

with a similar approach to React's use hook, **but with scope approach**.

**scope approach?** yes, this hook seeks to resolve a promise from a callback return, this allows you to regenerate the promise according to the scope, example:



{% tabs %}
{% tab title="JSX" %}
```tsx
import { useAsync } from "atomico";

const getUser = (userId) => fetch(`users/${userId}`).then((res) => res.json());

function component({ userId }) {
  const user = useAsync(getUser, [userId]);
  return (
    <host>
      <h1>name: {user.name}</h1>
    </host>
  );
}

component.props = { userId: Number }
```
{% endtab %}

{% tab title="TSX" %}
```tsx
import { Props, useAsync } from "atomico";

const getUser = (userId: number): Promise<{ name: string }> =>
  fetch(`users/${userId}`).then((res) => res.json());

function component({ userId }: Props<typeof component>) {
  const user = useAsync(getUser, [userId]);
  return (
    <host>
      <h1>name: {user.name}</h1>
    </host>
  );
}

component.props = { userId: Number };
```
{% endtab %}
{% endtabs %}

where:

* `getUser`: async callback.
* `[ userId ]`: arguments that if changed regenerate the promise.
* `user` : promise return

Like useEffect, the promise will be executed every time the arguments to the second parameter of useAsync change.

{% hint style="warning" %}
Rendering will be suspended until the promise is resolved or rejected, the resolution of the promises can be observed with useSuspense
{% endhint %}

## useSuspense

allows to listen to all useAsync executions nested in the component, example:

```tsx
function component() {
  const status = useSuspense();
  return (
    <host shadowDom>
      {status.pending ? "Loading..." : status.fulfilled ? "Done!" : "Error!"}~
      <slot />
    </host>
  );
}
```
