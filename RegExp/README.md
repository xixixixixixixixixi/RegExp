# RegExp
常用正则表达式

| 字符         |等价类            | 含义                                 | 
|-------------|-----------------|--------------------------------------| 
| \d          |  [0-9]          | 数字字符                               | 
| \w          |  [a-zA-Z_0-9]   | 单词字符，包括字母(小写、大写)、数字和下划线 | 
| \s          |  [\t\n\x0B\f\r] | 空白字符                               | 
| [a-zA-Z0-9] |  \w             | 字母(小写、大写)、数字                   | 
| \b          |                 | 单词边界                               |  
| .           |                 | 除了回车符和换行符之外的所有字符           | 
| *           |                 | 出现零次或多次（任意次）                  | 
| +           |                 | 出现一次或多次（至少出现一次）             | 
| ?           |                 | 出现零次或一次（最多出现一次）             |  
| x{3}        |                 | 出现3次                                | 
| ^           |                 | 以xxx开头                              | 
| $           |                 | 以xxx结尾                              | 

#### 判断用户输入的是不是合法的用户名（长度6-20个字符，只能包括字母、数字、下划线）

```
function isValidUsername(str){
  var reg = /^\w{6,20}$/g;
  return reg.test(str);
}
```

#### 判断用户输入的是不是手机号

```
function isPhoneNum(str){
  var reg = /^1[3578]\d{9}$/g;
  return reg.test(str)
}
```

#### 判断用户输入的是不是邮箱

```
function isEmail(str){
  var reg = /^\w+@\w+\.\w+/g
  return reg.test(str)
}
```

#### 去除字符串两边的空白字符

```
function trim(str) {
  var reg = /^\s+|\s+$/g;
  return str.replace(reg,'')
}
```

#### 得到字符串里所有的颜色

```
var subj = "color: #121212; background-color: #AA00ef; width: 12px; bad-colors: f#fddee "
var colorReg = /#([0-9a-fA-F]{6}|[0-9a-fA-F]{3})(?=;)/g
console.log( subj.match(colorReg) )
```

#### 贪婪模式与非贪婪模式

* 在贪婪（默认）模式下，正则引擎尽可能多的重复匹配字符。
    `'123456789'.match(/\d{3,5}/g); //["12345", "6789"]`
* 在非贪婪模式下，正则引擎尽可能少的重复匹配字符。
    `'123456789'.match(/\d{3,5}?/g); //["123", "456", "789"]`
