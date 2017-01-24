---
title: "多字节字符序列的解释 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.character.multibyte"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "MBCS [C++], 区域设置代码页"
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 多字节字符序列的解释
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大多数 Microsoft 运行库中的例程在多字节字符识别多字节字符多字节代码序列与页相关。  输出值受区域设置的 `LC_CTYPE` 类设置影响；有关更多信息，请参见 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  这些不带 `_l` 后缀的函数的版本使用为该区域设置相关的行为的当前区域设置；带有 `_l` 后缀的版本相同，只不过它们使用传递的区域设置参数。  
  
### 区域设置相关 Multibyte 例程  
  
|例程|使用|  
|--------|--------|  
|[\_mbclen、mblen、\_mblen\_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|验证并返回在多字节字符的字节数|  
|[strlen、wcslen、\_mbslen、\_mbslen\_l、\_mbstrlen、\_mbstrlen\_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|对于多字节字符字符串：验证在字符串中的每个字符；返回字符串的长度  对于宽字符串：返回字符串的长度。|  
|[mbstowcs、\_mbstowcs\_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs\_s, \_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|将多字节字符序列转换为宽字符的对应顺序|  
|[mbtowc、\_mbtowc\_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|将多字节字符转换为相应的宽字符|  
|[wcstombs、\_wcstombs\_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs\_s、\_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|将宽字符的顺序转换为多字节字符的对应序列|  
|[wctomb、\_wctomb\_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb\_s、\_wctomb\_s\_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|将宽字符转换为相应的多字节字符|  
  
## 请参阅  
 [国际化](../c-runtime-library/internationalization.md)   
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)