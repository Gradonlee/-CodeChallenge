# Search and Replace
Perform a search and replace on the sentence using the arguments provided and return the new sentence.

First argument is the sentence to perform the search and replace on.

Second argument is the word that you will be replacing (before).

Third argument is what you will be replacing the second argument with (after).

Note: Preserve the case of the first character in the original word when you are replacing it. For example if you mean to replace the word Book with the word dog, it should be replaced as Dog
### Before
```Javascript
function myReplace(str, before, after) {
  return str;
}

myReplace("A quick brown fox jumped over the lazy dog", "jumped", "leaped");
```
### Answer
```Javascript
function myReplace(str, before, after) {
  if(before[0] === before[0].toUpperCase()) {
    after = after[0].toUpperCase() + after.slice(1)
    console.log(after);
  }
  if(before[0] === before[0].toLowerCase()) {
    after = after[0].toLowerCase() + after.slice(1)
    console.log(after);
  }
 
  return str.replace(before, after)
}

myReplace("A quick brown fox Jumped over the lazy dog", "Jumped", "leaped");
```
### Thinking
```
假设两种情况，如果before 首字母大写，则after 首字母大写，如果首字母小写则 after 首字母小写
    因为 JavaScript 语言的特殊关系，无法使用 after[0] = after[0].toLowerCase() 来替换单个 character，所以直接整个 after 替换
```