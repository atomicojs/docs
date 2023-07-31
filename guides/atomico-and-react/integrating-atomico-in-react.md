# Integrating Atomico in React

Atomico integrates very easily into React, either using [**@atomico/exports**](integrating-atomico-in-react.md#atomico-exports) or [**@atomico/react**](integrating-atomico-in-react.md#atomico-react).

## @atomico/exports

CLI that decorates the package.json according to the code to be exported in order to share your code optimally. By using the --wrappers flag the CLI will detect the export of webcomponents and automatically create a wrapper for React, Preact and Vue.

You can learn more about [**@atomico/exports**](integrating-atomico-in-react.md#atomico-exports) in the following guide:

{% content-ref url="../../packages/introduction/" %}
[introduction](../../packages/introduction/)
{% endcontent-ref %}

### @atomico/react

With this package you will be able to create wrappers for your Webcomponents in React, even managing to make SSR of your webcomponents in environments like Next.js with these wrappers.

You can learn more about [**@atomico/react**](integrating-atomico-in-react.md#atomico-react) in the following guide:

{% content-ref url="../../packages/atomico-react.md" %}
[atomico-react.md](../../packages/atomico-react.md)
{% endcontent-ref %}



