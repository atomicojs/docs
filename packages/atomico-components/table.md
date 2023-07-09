# @atomico/table

**Webcomponent** built with [Atomico JS](https://atomicojs.dev/), Simple to use and customize table. Includes additional support for React and Preact.

{% embed url="https://codepen.io/uppercod/pen/qBoVpZP" %}

{% embed url="https://github.com/atomicojs/components/tree/master/src/components/table" %}

### Modules

{% tabs %}
{% tab title="Default" %}
```javascript
import { Table, Tr, Td } from "@atomico/table";
```
{% endtab %}

{% tab title="Elements" %}
```javascript
// Import that does not associate the tagName by default
import { Table, Tr, Td } from "@atomico/table/elements";
```
{% endtab %}

{% tab title="React" %}
```javascript
import { Table, Tr, Td } from "@atomico/table/react";
```
{% endtab %}

{% tab title="Preact" %}
```javascript
import { Table, Tr, Td } from "@atomico/table/preact";
```
{% endtab %}

{% tab title="Html CDN" %}
```java
<script 
    type="module" 
    src="http://esm.sh/@atomico/table"></script>
    
<atomico-table></atomico-table>
```
{% endtab %}
{% endtabs %}

### Custom properties

<table><thead><tr><th width="359.8875855909497">Global</th><th>Description</th></tr></thead><tbody><tr><td>--table--radius</td><td>table borde-radius</td></tr><tr><td>--table--background</td><td>table background </td></tr><tr><td>--table--border</td><td>table borde </td></tr><tr><td>--table--border-split</td><td>border dividing cells</td></tr><tr><td>--table--row-gap</td><td>row spacing</td></tr><tr><td>--table--row-radius</td><td>row border-radius</td></tr><tr><td>--table--row-shadow</td><td>row box-shadow</td></tr><tr><td>--table--row-background</td><td>row background </td></tr><tr><td>--table--row-header-radius</td><td>border-radius of the row declared as slot="header"</td></tr><tr><td>--table--row-header-shadow</td><td>box-shadow of the row declared as slot="header"</td></tr><tr><td>--table--row-header-background</td><td>background of the row declared as slot="header"</td></tr><tr><td>--table--row-last-radius</td><td>borde-radius de la ultima fila</td></tr><tr><td>--table--cell-align</td><td>cell alignment, default middle</td></tr><tr><td>--table--cell-padding</td><td>cell padding</td></tr><tr><td>--table--cell-header-padding</td><td>padding of the cell inside the Tr declared as slot="header"</td></tr></tbody></table>

### Properties Table

**collapse**: `boolean`, collapses the rows of the table, if breakpoint is defined the component will automatically define this props when detecting the match with breakpoint.

**breakpoint**: `string`, media query to observe to copal the table.

### Properties Tr

**sticky:** `boolan`**,**The table row will set its position according to the scroll position

{% hint style="info" %}
The following properties are automatically defined by the component to declare state.
{% endhint %}

**td**: `array` ,list of Td nodes associated with the TR component

**collapse**: `boolean`, property defined according to the state of the parent.

**last:** last row of the table

### Properties Td

**width**: string, cell width.



### Examples

**React**

{% embed url="https://stackblitz.com/edit/atomico-table-react?embed=1&file=src/App.tsx&view=preview" %}

