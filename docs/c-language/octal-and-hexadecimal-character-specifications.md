---
title: 八进制和十六进制字符规范 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f5709ef6fdcaaceecc79cd635374ee77d537100
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="octal-and-hexadecimal-character-specifications"></a>八进制和十六进制字符规范
序列 \\ooo 表示可以将 ASCII 字符集中的任何字符指定为三位数八进制字符代码。 八进制整数的数字值用于指定所需字符或宽字符的值。  
  
 同样，序列 \xhhh 可使用户将任何 ASCII 字符指定为十六进制字符代码。 例如，可以将 ASCII 退格符指定为常规 C 转义序列 (\b)，或者也可以将其编码为 \010（八进制）或 \x008（十六进制）。  
  
 在八进制转义序列中只能使用 0 到 7 的数字。 八进制转义序列绝不能长于三位且不能由第一个不是八进制数字的字符结尾。 虽然不需要使用所有三个数字，但必须至少使用其中一个。 例如，ASCII 退格符的八进制表示形式是 \10，字母 A 的八进制表示形式是 \101，如 ASCII 图表中所提供。  
  
 同样，对十六进制转义序列必须至少使用一个数字，但是您可以忽略第二个和第三个数字。 因此，可以将退格符的十六进制转义序列指定为 \x8、\x08 或 \x008。  
  
 八进制或十六进制转义序列的值必须在字符常量的类型 unsigned char 和宽字符常量的类型 `wchar_t` 的可表示值的范围内。 有关宽字符常量的信息，请参阅[多字节和宽字符](../c-language/multibyte-and-wide-characters.md)。  
  
 不同于八进制转义常量，转义序列中的十六进制数字的数量不受限制。 十六进制转义序列在第一个不是十六进制数字的字符处结尾。 由于十六进制数字包含字母 a 到 f，因此必须小心谨慎，确保转义序列在预期的数字处终止。 为了避免混淆，您可以将八进制或十六进制字符定义放入宏定义：  
  
```  
#define Bell '\x07'  
```  
  
 对于十六进制值，可以拆开字符串以清楚地显示正确的值：  
  
```  
"\xabc"    /* one character  */  
"\xab" "c" /* two characters */  
```  
  
## <a name="see-also"></a>请参阅  
 [C 字符常量](../c-language/c-character-constants.md)