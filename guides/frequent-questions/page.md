# Can I use Atomico in browsers without ESM support?

Yes, but Atomico doesn't only depend on ESM, it also depends on the following api's that you will have to cover with Polyfill or some bundle tool.

1. ESM modules: [documentation ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)- [caniuse](https://caniuse.com/es6-module)
2. CustomElements: [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Window/customElements) - [caniuse](https://caniuse.com/mdn-api\_window\_customelements)
3. ShadowRoot: [documentation](https://developer.mozilla.org/en-US/docs/Web/API/ShadowRoot) - [caniuse](https://caniuse.com/mdn-api\_shadowroot)
4. Map: [documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Map) - [caniuse](https://caniuse.com/mdn-html\_elements\_map)
5. Symbol and Symbol.for: [documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Symbol/for) - [caniuse](https://caniuse.com/mdn-api\_element\_prepend)
6. append and prepend: [documentation ](https://developer.mozilla.org/en-US/docs/Web/API/Element/prepend)- [caniuse](https://caniuse.com/mdn-api\_element\_prepend)
7. Declarative Shadow DOM: **Only for using SSR with webcomponents that use shadowDOM**. [documentation](https://developer.chrome.com/es/articles/declarative-shadow-dom/)

Let's understand that today Atomico covers 94% of existing browsers without the need for polyfills or packers, the 6% not covered are usually browsers like ie11 or others.

If you depend on the uncovered segment of browsers you can use the following tools to support the apis necessary for Atomico to work.

[polyfill-fastly.io](https://polyfill-fastly.io/v3/polyfill.min.js?features=Element.prototype.append%2CSymbol%2CElement.prototype.prepend%2CMap) to associate Map, Symbol, append and prepend.

[https://github.com/Rich-Harris/shimport](https://github.com/Rich-Harris/shimport) to associate esm.

[https://github.com/ungap/custom-elements](https://github.com/ungap/custom-elements) to associate customElements apis.

