---
description: >-
  With Atomico, asynchrony is really easy thanks to the fact that they will
  allow you to know the status of the process or suspend the rendering of the
  component.
---

# ⏳ Atomico and Asynchrony

Atomico has 3 great hooks to solve asynchronous tasks:

1. [usePromise](../api/hooks/usepromise.md): Processes asynchronous tasks and shows the status and resolution of these
2. [useAsync](../api/hooks/useasync-and-usesuspense.md#useasync): Allows you to pause rendering until a promise is resolved
3. [useSuspense](../api/hooks/useasync-and-usesuspense.md): Allows to know the paused states product of the use of useAsync nested in the component

