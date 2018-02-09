---
title: "C 整数常量 | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c23e90d235e1ad2a8cca577c5cfbf2be55b52b6
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2018
---
# <a name="c-integer-constants"></a>C 整数常量

“整数常量”是表示整数值的十进制（基数为 10）、八进制（基数为 8）或十六进制（基数为 16）数字。 使用整数常量表示不能更改的整数值。

## <a name="syntax"></a>语法

*integer-constant*:  
&nbsp;&nbsp;*decimal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*octal-constant* *integer-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*hexadecimal-constant* *integer-suffix*<sub>opt</sub>  

*decimal-constant*:  
&nbsp;&nbsp;*nonzero-digit*  
&nbsp;&nbsp;*decimal-constant* *digit*  

*octal-constant*:  
&nbsp;&nbsp;**0**  
&nbsp;&nbsp;*octal-constant* *octal-digit*  

*hexadecimal-constant*:  
&nbsp;&nbsp;**0x**  *hexadecimal-digit*  
&nbsp;&nbsp;**0X**  *hexadecimal-digit*  
&nbsp;&nbsp;*hexadecimal-constant* *hexadecimal-digit*  

*nonzero-digit*: one of  
&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**  

*octal-digit*: one of  
&nbsp;&nbsp;**0 1 2 3 4 5 6 7**  

*hexadecimal-digit*: one of  
&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**  
&nbsp;&nbsp;**a b c d e f**  
&nbsp;&nbsp;**A B C D E F**  
  
*integer-suffix*:  
&nbsp;&nbsp;*unsigned-suffix* *long-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*long-suffix* *unsigned-suffix*<sub>opt</sub>  
&nbsp;&nbsp;*unsigned-suffix* *64-bit-integer-suffix*<sub>opt</sub>

*unsigned-suffix*: one of  
&nbsp;&nbsp;**u U**  

*long-suffix*: one of  
&nbsp;&nbsp;**l L**  
  
*64-bit-integer-suffix*:  one of &nbsp;&nbsp;**i64 I64**  

整数常量为正数，除非它们的前面有减号 (**-**)。 减号解释为一元算术求反运算符。 （有关此运算符的信息，请参阅[一元算术运算符](../c-language/unary-arithmetic-operators.md)。）

如果整数常量以 **0x** 或 **0X**  开始，则它是十六进制。 如果它以数字 **0** 开始，则为八进制。 否则，将其假定为十进制。

下列行是等效的：

```C
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

空白字符不能分隔整数常量的数字。 这些示例显示有效的十进制、八进制和十六进制常量。

```C
/* Decimal Constants */
10
132
32179

/* Octal Constants */
012
0204
076663

/* Hexadecimal Constants */
0xa or 0xA
0x84
0x7dB3 or 0X7DB3
```

## <a name="see-also"></a>请参阅

[C 常量](../c-language/c-constants.md)  
