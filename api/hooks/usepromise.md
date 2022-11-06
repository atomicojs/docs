---
description: Easily observe asynchronous processes
---

# usePromise

The purpose of this hook is to facilitate the consumption of promises.

### Syntax

```tsx
import { usePromise } from "atomico";

const callback = (id: number)=>Promise.resolve(id);
const args:Parameters<typeof callback> = [1];
const autorun = true;

const promise = usePromise( callback, args, autorun );
```

where:

* `callback` : asynchronous function.
* `args`: arguments that callback requires.
* `autorun`: by default true, it automatically executes the promise, if it is false the execution of the promise is suspended.
* `promise` : return object, at the type level it defines the following properties:
  * `pending`: boolean, defines if the promise is executed but pending resolution.
  * `fulfilled`: boolean , defines if the promise has been fulfilled
  * `result`: result of the promise.
  * `rejected`: boolean, defines if the promise has been rejected.

{% hint style="info" %}
**Note**: When using Typescript Do not force the types for the second argument of usePromise, as usePromise will infer them from your callback.

It is preferable to use ternary or if to condition the reading of states, since this will help the definition of result&#x20;
{% endhint %}

### Example

```tsx
import { usePromise } from "atomico";

const getUsers = (id: number) => Promise.resolve({ id, name: "Atomico" });

function component() {
  const promise = usePromise(getUsers, [1]);

  return (
    <host>
      {promise.fulfilled ? (
        <h1>Done {promise.result.name}!</h1>
      ) : promise.pending ? (
        <h1>Loading...</h1>
      ) : (
        <h1>Error!</h1>
      )}
    </host>
  );
}
```

{% hint style="info" %}
**Note**: At the type level, autocompletion is conditional on the state you are looking to observe.
{% endhint %}

