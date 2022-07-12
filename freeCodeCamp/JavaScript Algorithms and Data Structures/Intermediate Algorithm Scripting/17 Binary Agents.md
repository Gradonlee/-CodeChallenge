# Title: Binary Agents
Return an English translated sentence of the passed binary string.

The binary string will be space separated.
### Before
  
``` Javascript
function binaryAgent(str) {
    return str;
}

binaryAgent("01000001 01110010 01100101 01101110 00100111 01110100 00100000 01100010 01101111 01101110 01100110 01101001 01110010 01100101 01110011 00100000 01100110 01110101 01101110 00100001 00111111");
```
### Answer
  
``` Javascript
function binaryAgent(str) {
    return str.split(' ').map(function(e) {
        return String.fromCharCode(parseInt(e, 2));
    }).join('')
}
```
### Thinking
split 分开再 map 遍历所有的二进制字符串

String.fromCharCode(): 返回由指定的 UTF-16 代码单元序列创建的字符串。

parseInt():解析一个字符串并返回指定基数的十进制整数，radiu:2 指的是返回二进制的

再返回 join 过的