# Example with @atomico/vite

With [atomico-vite.md](../atomico-vite.md "mention") you can use @atomico/postcss-tokens in your cssLiterals with the following configuration:

1. Enable the use of postcss for cssLiterals in the `vite.config.js` file

```javascript
atomico({
    cssLiterals: { postcss: true }
});
```

2\. Add [.](./ "mention")to your postcss config, example:

```json
"postcss": {
        "plugins": {
            "@atomico/postcss-tokens": {
                "prefix": "a"
            }
        }
}
```
