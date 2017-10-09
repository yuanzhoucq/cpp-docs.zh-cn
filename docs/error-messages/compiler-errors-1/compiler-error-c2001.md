---
title: "编译器错误 C2001 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: aedba438451089aa2d71e06da7ce189ab97d4190
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

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
