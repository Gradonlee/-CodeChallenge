# Convert HTML Entities
Convert the characters &, <, >, " (double quote), and ' (apostrophe), in a string to their corresponding HTML entities.

### Before
```Javascript
function convertHTML(str) {
  return str;
}

convertHTML("Dolce & Gabbana");
```
### Answer
```Javascript
function convertHTML(str) {
  let entityMap = {
    '&': "&amp;",
    "<": "&lt;",
    ">": "&gt;",
    '"': "&quot;",
    "'": "&apos;"
  }
  return str.split('').reduce((accum, curr) => accum + (entityMap[curr] || curr), "")
}

convertHTML("Dolce & Gabbana");
```
### Thinking
```
||:这个就是如果 entityMap[curr]这个是 false 的话就输出 curr
```