# Title: Caesars Cipher
One of the simplest and most widely known ciphers is a Caesar cipher, also known as a shift cipher. In a shift cipher the meanings of the letters are shifted by some set amount.
A common modern use is the [ROT13](https://www.freecodecamp.org/news/how-to-code-the-caesar-cipher-an-introduction-to-basic-encryption-3bf77b4e19f7/) cipher, where the values of the letters are shifted by 13 places. Thus  `A ↔ N` ,  `B ↔ O`  and so on.
Write a function which takes a [ROT13](https://www.freecodecamp.org/news/how-to-code-the-caesar-cipher-an-introduction-to-basic-encryption-3bf77b4e19f7/) encoded string as input and returns a decoded string.
All letters will be uppercase. Do not transform any non-alphabetic character (i.e. spaces, punctuation), but do pass them on.
### Before
  
``` Javascript
	  function rot13(str) {
	    return str;
	  }
	  
	  rot13("SERR PBQR PNZC");
```
### Answer
  
``` Javascript
	  function rot13(str) {
	    return str.replace (/[A-Z]/g, function(char) {
	      return String.fromCharCode(char.charCodeAt() + (/[A-M]/.test(char) ? 13 : -13));
	    })
	  }
	  
	  rot13("SERR PBQR PNZC");
```
### Thinking
这个解法太牛了，先正则出需要替换的 A-Z 的字母，创建函数更改，
函数中找到所对应字母 ASCII 码，然后字母前 13 位才去加法，后 13 位采取减法即为循环了
test 判断 char 是否在前 13 位的字母，如果是？则加 13，不是：则加 -13