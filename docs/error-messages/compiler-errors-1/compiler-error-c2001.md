---
title: 编译器错误 C2001 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f56eabbcb5ca322d7549c21a56893a8e13d9261
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2001"></a>编译器错误 C2001
常量中有换行符  
  
 字符串常量不能继续在第二个行上，除非你执行以下操作：  
  
-   结束以反斜杠的第一行。  
  
-   关闭与双引号匹配的第一行中的字符串，并使用另一个双引号打开下一步的行中的字符串。  
  
 结束用 \n 的第一行是不够的。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2001:  
  
```  
// C2001.cpp  
// C2001 expected  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,  
             world");  
    printf_s("Hello,\n  
             world");  
}  
```  
  
## <a name="example"></a>示例  
 字符串常量中包括空格开头的行延续字符之后的下一行。 上面所示的示例都没有嵌入字符串常量的换行字符。 你可以嵌入换行字符，如下所示：  
  
```  
// C2001b.cpp  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,\n\  
             world");  
  
    printf_s("Hello,\  
             \nworld");  
  
    printf_s("Hello,\n"  
             "world");  
  
    printf_s("Hello,"  
             "\nworld");  
  
    printf_s("Hello,"  
             " world");  
  
    printf_s("Hello,\  
             world");  
}  
```