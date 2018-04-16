---
title: "转义序列 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- "\r escape sequence"
- double backslash
- horizontal-tab 	 escape sequence
- (') single quotation mark
- "bell character \a escape sequence"
- escape sequences
- hexadecimal escape sequence
- carriage returns
- tab 	 escape sequence
- "\f escape sequence"
- quotation marks, single
- "formfeed \f escape sequence"
- "\v escape sequence"
- control character escape sequences
- " symbol in escape sequences"
- octal escape sequence
- escape characters
- "newline character \n escape sequence"
- nongraphic control characters
- question mark, literal
- "\nescape sequence"
- "vertical tab \v escape sequence"
- "\a escape sequence"
- '? symbol'
- '? symbol, escape sequence character'
- "	 escape sequence"
- backspace escape sequence
ms.assetid: 5aef377f-a76c-4d5c-aa04-8308758ad6a8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d341aa5af2b16d1a29bc4e3dfe2f97a68b73d6ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="escape-sequences"></a>转义序列
由反斜杠 (\\) 后接字母或数字组合构成的字符组合称为“转义序列”。 要在字符常量中表示换行符，单引号或某些其他字符，你必须使用转义序列。 转义序列被视为单个字符，因此，它是有效的字符常量。  
  
 转义序列通常用于指定操作，例如终端和打印机上的回车和制表符移动。 它们还用于提供非打印字符的文本表现形式和通常具有特殊意义的字符，例如双引号 (")。 下表列出 ANSI 转义序列以及它们所表示的内容。  
  
 请注意，在字符序列被错误地解释为三元组的情况下，前接反斜杠 (\\?) 的问号指定文本问号。 有关详细信息，请参阅[三元组](../c-language/trigraphs.md)。  
  
### <a name="escape-sequences"></a>转义序列  
  
|转义序列|表示|  
|---------------------|----------------|  
|**\a**|响铃（警报）|  
|**\b**|Backspace|  
|**\f**|换页|  
|**\n**|换行|  
|**\r**|回车|  
|**\t**|水平制表符|  
|**\v**|垂直制表符|  
|**\\'**|单引号|  
|**\\"**|双引号|  
|**\\\\**|反斜杠|  
|**\\?**|文本问号|  
|**\\** *ooo*|八进制表示法的 ASCII 字符|  
|**\x** hh|十六进制表示法的 ASCII 字符|  
|**\x** hhhh|十六进制表示法的 Unicode 字符（如果此转义序列用于宽字符常量或 Unicode 字符串文本）。<br /><br /> 例如，`WCHAR f = L'\x4e00'` 或 `WCHAR b[] = L"The Chinese character for one is \x4e00"`。|  
  
 **Microsoft 专用**  
  
 如果反斜杠在表中未显示的字符前面，则编译器将未定义的字符作为字符本身进行处理。 例如，`\c` 被视为 `c`。  
  
 **结束 Microsoft 专用**  
  
 转义序列允许你发送非图形控制字符到显示设备。 例如，ESC 字符 (\033) 通常用作终端或打印机的控制命令的第一个字符。 一些转义序列特定于设备。 例如，垂直制表符和换页符转义序列（\v 和 \f）不会影响屏幕输出，但它们会执行适当的打印机操作。  
  
 还可以将反斜杠 (\\) 用作继续符。 当换行符（等效于按 RETURN 键）紧接反斜杠时，编译器会忽略反斜杠和换行符并将下一行作为前一行的一部分。 这主要对长于一行的预处理器定义有用。 例如:  
  
```  
#define assert(exp) \  
( (exp) ? (void) 0:_assert( #exp, __FILE__, __LINE__ ) )  
```  
  
## <a name="see-also"></a>请参阅  
 [C 字符常量](../c-language/c-character-constants.md)