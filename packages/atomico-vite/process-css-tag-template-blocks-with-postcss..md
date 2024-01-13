---
description: >-
  With @atomico/vite, you will be able to analyze your CSS tag template to be
  optimized or to support utilities from the PostCSS ecosystem like Tailwind.
---

# ⚙ Process CSS tag template blocks with PostCSS.

<figure><img src="../../.gitbook/assets/Group 259.png" alt=""><figcaption></figcaption></figure>

### Config

<pre class="language-javascript"><code class="lang-javascript"><strong>import atomico from "@atomico/vite";
</strong>
export default {
  plugins: atomico({
    cssLiterals: { 
      postcss: true,
      // Optional, minify the css code
      minify: true
    },
  }),
};
</code></pre>

{% hint style="danger" %}
This configuration will only work if the use of PostCSS has already been configured, either at the package.json#postcss level or in postcss.config.json.
{% endhint %}
