---
description: >-
  With @atomico/vite, you will be able to use server-side functions in an
  environment-agnostic way, suitable for certain serverless and edge
  environments.
---

# 🧙♂ Server actions

Thanks to the use of @atomico/vite, you will be able to create applications without worrying about servers. The goal is simple: transform the JS/TS resources in the `src/api` folder into serverless or edge functions. The frontend can then import these functions, and internally, the function will perform the fetch to the serverless or edge service.&#x20;

### Example with Cloudflare.

{% tabs %}
{% tab title="src/app.ts" %}
```typescript
import type { Props } from "atomico";
import { getUserById } from "./api";

function app({id}: Props<typeof app>){
    const user = useAsync(()=>getUserById({id}),[id]);
    return <host>
        {user.name} - {user.phone}
    </host>
}

app.props = { id: Number }
```
{% endtab %}

{% tab title="src/api/index.ts" %}
```typescript
export async function getUserById({ id }:{ id: number}){
    const result = await fetch(
        `https://jsonplaceholder.typicode.com/users/${id}`
    );
    return result.json();
}
```
{% endtab %}
{% endtabs %}
