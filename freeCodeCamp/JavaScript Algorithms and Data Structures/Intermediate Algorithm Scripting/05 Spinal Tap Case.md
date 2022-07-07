# Spinal Tap Case

Convert a string to spinal case. Spinal case is all-lowercase-words-joined-by-dashes.


### Before
```Javascript
function spinalCase(str) {
  return str;
}

spinalCase('This Is Spinal Tap');
```
### Answer
```Javascript
function spinalCase(str) {
  return str.split(/\s|_|\B(?=[A-Z])/).join("-").toLowerCase();
}

spinalCase('This Is Spinal Tap');
```
### Thinking
```
先正则 \s：所有空格
    |：表示 或 的意思
    _：下划线
    \B:单词中间的占位符（\b ：非单词中间的占位符）
    （？=）：先行断言（lookahead）用来判断占位符后面是否满足括号内的内容，若满足才匹配这个占位符
    [A-Z]：匹配是否满足其中的单个字符
 然后再 join 回去，每个单词中间间隔-，然后再全部小写（先全部小写就没法正则了）
 ```