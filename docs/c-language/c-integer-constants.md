---
title: C 整数常量
ms.date: 02/27/2018
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
ms.openlocfilehash: 48561599896bb8a6f9ee159630ff15df6c0454be
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400514"
---
# <a name="c-integer-constants"></a>C 整数常量

整数常量  是表示整数值的十进制（基数为 10）、八进制（基数为 8）或十六进制（基数为 16）数字。 使用整数常量表示不能更改的整数值。

## <a name="syntax"></a>语法

*integer-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>

*decimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;nonzero-digit <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*decimal-constant* *digit*

*octal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;0 <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*octal-constant* *octal-digit*

*hexadecimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-prefix* *hexadecimal-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*

hexadecimal-prefix  : one of<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  **0X**

*nonzero-digit*: one of<br/>
&nbsp;&nbsp;&nbsp;&nbsp;1 2 3 4 5 6 7 8 9 

*octal-digit*: one of<br/>
&nbsp;&nbsp;&nbsp;&nbsp;0 1 2 3 4 5 6 7 

*hexadecimal-digit*: one of<br/>
&nbsp;&nbsp;&nbsp;&nbsp;0 1 2 3 4 5 6 7 8 9 <br/>
&nbsp;&nbsp;&nbsp;&nbsp;a b c d e f <br/>
&nbsp;&nbsp;&nbsp;&nbsp;A B C D E F 

*integer-suffix*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *long-long-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-suffix* *64-bit-integer-suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-long-suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;64-bit-integer-suffix 

*unsigned-suffix*: one of<br/>
&nbsp;&nbsp;&nbsp;&nbsp;u U 

*long-suffix*: one of<br/>
&nbsp;&nbsp;&nbsp;&nbsp;l L 

long-long-suffix  : one of<br/>
&nbsp;&nbsp;&nbsp;&nbsp;ll LL 

64-bit-integer-suffix  : one of<br/>
&nbsp;&nbsp;&nbsp;&nbsp;i64 I64 

i64  和 I64  后缀为 Microsoft 专用。

整数常量为正数，除非它们的前面有减号 ( **-** )。 减号解释为一元算术求反运算符。 （有关此运算符的信息，请参阅[一元算术运算符](../c-language/unary-arithmetic-operators.md)。）

如果整数常量以 **0x** 或 **0X** 开始，则它是十六进制。 如果它以数字 **0** 开始，则为八进制。 否则，将其假定为十进制。

以下整数常量是等效的：

```C
28
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

空白字符不能分隔整数常量的数字。 这些示例显示了一些有效的十进制、八进制和十六进制常量。

```C
    /* Decimal Constants */
    int                 dec_int    = 28;
    unsigned            dec_uint   = 4000000024u;
    long                dec_long   = 2000000022l;
    unsigned long       dec_ulong  = 4000000000ul;
    long long           dec_llong  = 9000000000LL;
    unsigned long long  dec_ullong = 900000000001ull;
    __int64             dec_i64    = 9000000000002I64;
    unsigned __int64    dec_ui64   = 90000000000004ui64;

    /* Octal Constants */
    int                 oct_int    = 024;
    unsigned            oct_uint   = 04000000024u;
    long                oct_long   = 02000000022l;
    unsigned long       oct_ulong  = 04000000000UL;
    long long           oct_llong  = 044000000000000ll;
    unsigned long long  oct_ullong = 044400000000000001Ull;
    __int64             oct_i64    = 04444000000000000002i64;
    unsigned __int64    oct_ui64   = 04444000000000000004uI64;

    /* Hexadecimal Constants */
    int                 hex_int    = 0x2a;
    unsigned            hex_uint   = 0XA0000024u;
    long                hex_long   = 0x20000022l;
    unsigned long       hex_ulong  = 0XA0000021uL;
    long long           hex_llong  = 0x8a000000000000ll;
    unsigned long long  hex_ullong = 0x8A40000000000010uLL;
    __int64             hex_i64    = 0x4a44000000000020I64;
    unsigned __int64    hex_ui64   = 0x8a44000000000040Ui64;
```

## <a name="see-also"></a>请参阅

[C 常量](../c-language/c-constants.md)<br/>
