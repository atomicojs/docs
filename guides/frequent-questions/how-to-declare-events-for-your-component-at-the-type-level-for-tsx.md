# How to declare events for your component at the type level for TSX?

Atomico permite fácilmente declarar eventos a nivel de tipos usando el tipo Host

## Ejemplo

<pre class="language-tsx"><code class="lang-tsx">import { Host, c, useEvent } from "atomico";

type CustomDetail = { timestamp: number };

const MyComponent = c(
  (): Host&#x3C;{ onMyCustomEvent: CustomEvent&#x3C;CustomDetail> }> => {
    const dispatch = useEvent&#x3C;CustomDetail>("MyCustomEvent");
    return (
      &#x3C;host>
        &#x3C;button
          onclick={() => {
            dispatch({ timestamp: Date.now() });
          }}
        >Click&#x3C;/button>
      &#x3C;/host>
    );
  }
);

<strong>
</strong>
</code></pre>

In the previous code, we have declared the `onMyCustomEvent` event at the type level. According to the template logic, this event will be dispatched every time the button is clicked, and the detail attached to this event will be of type `CustomDetail`.
