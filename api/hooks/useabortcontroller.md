---
description: >-
  Atomico now introduces a new hook called useAbortController, which allows
  aborting the execution of asynchronous calls, example:
---

# useAbortController

The idea is to create an instance of AbortController every time the hook's parameters change. Each parameter change will abort the previously generated controller, thus cancelling any subscribed promises.

### Example

```tsx
import { useAsync, useAbortController } from 'atomico';

async function getUser(id: number, signal: AbortSignal) {
  return fetch(`/id/${id}`, { signal });
}

function myComponent({ userId }: Props<typeof myComponent>) {
  const { signal } = useAbortController([userId]);

  const user = useAsync(getUser, [userId, signal]);

  return <host>{user.name}</host>;
}

myComponent.props = { userId: { type: Number, value: 0 } };
```

The significant advantage of using useAbortController is the automatic cancellation of asynchronous processes that depend on it when modifying the arguments provided to useAbortController (similar to useEffect).





