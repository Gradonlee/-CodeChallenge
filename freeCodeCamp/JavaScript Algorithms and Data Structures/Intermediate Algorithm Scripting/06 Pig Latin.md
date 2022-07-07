# Pig Latin
Pig Latin is a way of altering English Words. The rules are as follows:

- If a word begins with a consonant, take the first consonant or consonant cluster, move it to the end of the word, and add ay to it.

- If a word begins with a vowel, just add way at the end.
---
Translate the provided string to Pig Latin. Input strings are guaranteed to be English words in all lowercase.
### Before
```Javascript
function translatePigLatin(str) {
  return str;
}

translatePigLatin("consonant");
```
### Answer
```Javascript
function translatePigLatin(str) {
  return str.replace(/([^aeiou]*)(\w*)/,(match, before, after) => 
    `${after}${before || "w"}ay`
  )
}

translatePigLatin("consonant");
```
### Thinking
```
return str 用正则运算的 replace
    正则运算:
        [^aeiou]*:从头开始贪婪匹配无限个除开[aeiou]的数字，一旦匹配到了就停止
        \w*:匹配到任何字母及数字
    match 表示匹配到的字串也就是/([^aeiou]*)(\w*)/所返回的
    before 表示([^aeiou]*)
    after表示(\w*)
    ||:表示前者若不存在则选择后者
```