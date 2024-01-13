# 🏗 Compile your code to be distributed optimally as a package.

```bash
npx library src/**/*
```

the above script will send all files found in the `src` folder to vite, example output:

```bash
# Input                        # Output
/src                            /lib
  /my-component-1.tsx             /my-component-1.js
  /my-component-2.tsx             /my-component-2.tsx
  /my-component-3.tsx             /my-component-3.tsx
```

{% hint style="success" %}
This script can be combined with [@atomico/exports](../introduction/) to improve the generation of your package.json
{% endhint %}
