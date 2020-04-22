# week02 作业

# 编写带括号的四则运算产生式

```
<Number> ::= "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"
<DecimalNumber> ::= "0" | (("1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9") <Number>*)
<PrimaryExpression> ::= <DecimalNumber> | "(" <LogicalExpression>")"
                        <MultiplicativeExpression> ::= <PrimaryExpression> |
                        <MultiplicativeExpression> "*" <PrimaryExpression> |
                        <MultiplicativeExpression> "/" <PrimaryExpression> |

<AdditiveExpression> ::= <MultiplicativeExpression> |
                        <AdditiveExpression> "+" <MultiplicativeExpression> |
                        <AdditiveExpression> "-" <MultiplicativeExpression>

<LogicalExpression> ::= <AdditiveExpression> |
                        <LogicalExpression> "||" <AdditiveExpression> |
                        <LogicalExpression> "&&" <AdditiveExpression>
```

# 尽可能寻找你知道的计算机语言，尝试把它们分类

JavaScript: 2 型语言(上下文无关文法)

# 写一个正则表达式 匹配所有 Number 直接量

```
<Number> ::= /^[+-]?(0|([1-9]\d*))(\.\d+)?$/
```

# 写一个 UTF-8 Encoding 的函数

```
function encodeUtf8(text) {
    const code = encodeURIComponent(text);
    const bytes = [];
    for (var i = 0; i < code.length; i++) {
        const c = code.charAt(i);
        if (c === '%') {
            const hex = code.charAt(i + 1) + code.charAt(i + 2);
            const hexVal = parseInt(hex, 16);
            bytes.push(hexVal);
            i += 2;
        } else bytes.push(c.charCodeAt(0));
    }
    return bytes;
}
```

# 写一个正则表达式，匹配所有的字符串直接量，单引号和双引号

```
<string> ::= /[\u0021-\u007E]{6,16}|[\x21-\x7E]{6,16}|(['"])(?:(?!\1).)*?\1/
```
