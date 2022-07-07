# Missing letters
Find the missing letter in the passed letter range and return it.

If all letters are present in the range, return undefined.
### Before
```Javascript
function fearNotLetter(str) {
  return str;
}

fearNotLetter("abce");
```
### Answer
```Javascript
function fearNotLetter(str) {
  let alphabet = "abcdefghijklmnopqrstuvwxyz";
  let startingPoint = alphabet.indexOf(str[0])
  console.log(alphabet[0])
  for(let i = 0; i <str.length; i++) {
    if (str[i] !== alphabet[startingPoint + i]) {
      return alphabet[startingPoint + i];
    }
  }
  return undefined;
}

```
### Thinking
```
用 indexOf 先确定 str 的起始点在哪儿
遍历 alphabet，alphabet 所对应的位置不存在该 character 时直接返回，
    
```