#fleeting #javascript 

字符串基本上表示为 [UTF-16 码元](https://zh.wikipedia.org/wiki/UTF-16)的序列。在 UTF-16 编码中，每个码元都是 16 位长。这意味着最多有 216 个或 65536 个可能的字符可表示为单个 UTF-16 码元。该字符集称为[基本多语言平面（BMP）](https://zh.wikipedia.org/wiki/Unicode%E5%AD%97%E7%AC%A6%E5%B9%B3%E9%9D%A2%E6%98%A0%E5%B0%84)，包含最常见的字符，如拉丁字母、希腊字母、西里尔字母以及许多东亚字符。每个码元都可以用以 `\u` 开头的 4 个十六进制数字写在一个字符串中。

然而，整个 Unicode 字符集比 65536 大得多。额外的字符以_代理对_（surrogate pair）的形式存储在 UTF-16 中，代理对是一对 16 位码元，表示一个单个字符。为了避免歧义，配对的两个部分必须介于 `0xD800` 和 `0xDFFF` 之间，并且这些码元不用于编码单码元字符。（更准确地说，前导代理，也称为高位代理，其值在 `0xD800` 和 `0xDBFF` 之间（含），而后尾代理，也称为低位代理，其值在 `0xDC00` 和 `0xDFFF` 之间（含）。）每个 Unicode 字符由一个或者两个 UTF-16 码元组成，也称为 _Unicode 码位_（code point）。每个 Unicode 码位都可以使用 `\u{xxxxxx}` 写成一个字符串，其中 `xxxxxx` 表示 1–6 个十六进制数字。

“单独代理项（lone surrogate）”是指满足以下描述之一的 16 位码元：

- 它在范围 `0xD800` 到 `0xDBFF` 内（含）（即为前导代理），但它是字符串中的最后一个码元，或者下一个码元不是后尾代理。
- 它在范围 `0xDC00` 到 `0xDFFF` 内（含）（即为后尾代理），但它是字符串中的第一个码元，或者前一个码元不是前导代理。

除了 Unicode 字符之外，还有某些 Unicode 字符序列应视为一个视觉单元，被称为字素簇（grapheme cluster）。最常见的情况是 emoji：许多具有多种变体的 emoji 实际上是由多个 emoji 组成的，通常由 `U+200D` 字符连接。

- [[字符串创建]]
- [[访问字符]]
- [[字符串比较]]
- [[字符串原始值和字符串对象]]
- [[字符串强制转换]]

## [构造函数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String#%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0)

[`String()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/String)

创建一个新的 `String` 对象。它在作为函数调用时执行类型转换，而不是作为构造函数调用，后者通常更有用。

## [静态方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String#%E9%9D%99%E6%80%81%E6%96%B9%E6%B3%95)

[`String.fromCharCode()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode)

返回使用指定的 Unicode 值序列创建的字符串。

[`String.fromCodePoint()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/fromCodePoint)

返回使用指定的码位序列创建的字符串。

[`String.raw()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/raw)

返回从原始模板字符串创建的字符串。

## [实例属性](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String#%E5%AE%9E%E4%BE%8B%E5%B1%9E%E6%80%A7)

这些属性在 `String.prototype` 上定义，由所有 `String` 实例共享。

[`String.prototype.constructor`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/constructor)

创建实例对象的构造函数。对于 `String` 实例，初始值是 [`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/String) 构造函数。

这些属性是每个 `String` 实例的自有属性。

[`String.prototype.length`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/length)

反映字符串的 `length`。只读。

## [实例方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String#%E5%AE%9E%E4%BE%8B%E6%96%B9%E6%B3%95)

[`String.prototype.at()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/at)

返回指定索引处的字符（正好是一个 UTF-16 码元）。接受负整数，从最后一个字符串字符开始倒数。

[`String.prototype.charAt()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/charAt)

返回指定 `index` 处的字符（正好是一个 UTF-16 码元）。

[`String.prototype.charCodeAt()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt)

返回一个数字，它是给定 `index` 处的 UTF-16 码元值。

[`String.prototype.codePointAt()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/codePointAt)

返回一个非负整数值，它是从指定位置（`pos`）开始的 UTF-16 编码码位的码位值。

[`String.prototype.concat()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/concat)

合并两个（或更多）字符串的文本并返回一个新字符串。

[`String.prototype.endsWith()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith)

确定字符串是否以字符串 `searchString` 的字符结尾。

[`String.prototype.includes()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/includes)

确定调用字符串是否包含 `searchString`。

[`String.prototype.indexOf()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)

返回在调用 [`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String) 对象中第一次出现的 `searchValue` 的索引，如果未找到则返回 `-1`。

[`String.prototype.isWellFormed()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/isWellFormed)

返回一个布尔值，指示此字符串是否包含任何[单独代理项](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String#utf-16_%E5%AD%97%E7%AC%A6%E3%80%81unicode_%E7%A0%81%E4%BD%8D%E5%92%8C%E5%AD%97%E7%B4%A0%E7%B0%87)。

[`String.prototype.lastIndexOf()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/lastIndexOf)

返回在调用 [`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String) 对象中最后一次出现的 `searchValue` 的索引，如果未找到则返回 `-1`。

[`String.prototype.localeCompare()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare)

返回一个数字，用于指示一个参考字符串 `compareString` 是否在排序顺序前面或之后或与给定字符串相同。

[`String.prototype.match()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/match)

用于将正则表达式 `regexp` 与字符串匹配。

[`String.prototype.matchAll()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/matchAll)

返回所有 `regexp` 的匹配项的迭代器。

[`String.prototype.normalize()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/normalize)

返回调用字符串值的 Unicode 规范化形式。

[`String.prototype.padEnd()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd)

用给定字符串从末尾填充当前字符串并返回长度为 `targetLength` 的新字符串。

[`String.prototype.padStart()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/padStart)

用给定字符串从开头填充当前字符串并返回长度为 `targetLength` 的新字符串。

[`String.prototype.repeat()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)

返回由对象的元素重复 `count` 次组成的字符串。

[`String.prototype.replace()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace)

用于使用 `replaceWith` 替换出现的 `searchFor`。`searchFor` 可以是字符串或正则表达式，`replaceWith` 可以是字符串或函数。

[`String.prototype.replaceAll()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replaceAll)

用于使用 `replaceWith` 替换所有出现的 `searchFor`。`searchFor` 可以是字符串或正则表达式，`replaceWith` 可以是字符串或函数。

[`String.prototype.search()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/search)

搜索正则表达式 `regexp` 和调用字符串之间的匹配项。

[`String.prototype.slice()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/slice)

提取字符串的一部分并返回一个新字符串。

[`String.prototype.split()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/split)

返回一个由在出现子字符串 `sep` 时拆分调用的字符串然后填充的字符串数组。

[`String.prototype.startsWith()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith)

确定调用字符串是否以字符串 `searchString` 的字符开头。

[`String.prototype.substring()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/substring)

返回一个新字符串，其中包含来自（或之间）指定索引（或多个索引）的调用字符串的字符。

[`String.prototype.toLocaleLowerCase()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLocaleLowerCase)

字符串中的字符将转换为小写，同时尊重当前语言环境。

对于大多数语言，这将返回与 [`toLowerCase()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase) 相同的结果。

[`String.prototype.toLocaleUpperCase( [locale, ...locales])`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLocaleUpperCase)

字符串中的字符将转换为大写，同时尊重当前语言环境。

对于大多数语言，这将返回与 [`toUpperCase()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase) 相同的结果。

[`String.prototype.toLowerCase()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)

返回转换为小写的调用字符串值。

[`String.prototype.toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toString)

返回表示指定对象的字符串。重写 [`Object.prototype.toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/toString) 方法。

[`String.prototype.toUpperCase()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase)

返回转换为大写的调用字符串值。

[`String.prototype.toWellFormed()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toWellFormed)

返回一个字符串，其中包含的所有[单独代理项](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String##utf-16_%E5%AD%97%E7%AC%A6%E3%80%81unicode_%E7%A0%81%E4%BD%8D%E5%92%8C%E5%AD%97%E7%B4%A0%E7%B0%87)都替换为 Unicode 替换字符 U+FFFD。

[`String.prototype.trim()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trim)

修剪字符串开头和结尾的空格。

[`String.prototype.trimEnd()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trimEnd)

修剪字符串结尾的空格。

[`String.prototype.trimStart()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trimStart)

修剪字符串开头的空格。

[`String.prototype.valueOf()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/valueOf)

返回指定对象的原始值。重写 [`Object.prototype.valueOf()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/valueOf) 方法。

[`String.prototype[@@iterator]()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/@@iterator)

返回一个新的迭代器对象，该对象迭代 String 值的码位，将每个码位作为 String 值返回。

# 个人理解

- `at` 比 `charAt` 更灵活，可接收负整数，而且短
- `concat` 比 `+` 更严格 [String concatenation: `concat()` vs `+` operator)](https://stackoverflow.com/questions/47605/string-concatenation-concat-vs-operator)
