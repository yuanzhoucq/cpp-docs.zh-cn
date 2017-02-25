---
title: "编译器错误 C2001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2001"
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

常数中有换行符  
  
 字符串常数不能继续到第二行，除非进行下列操作：  
  
-   用反斜杠结束第一行。  
  
-   用一个双引号结束第一行上的字符串，并在下一行用另一个双引号开始该字符串。  
  
 用 \\n 结束第一行是不够的。  
  
## 示例  
 下面的示例生成 C2001：  
  
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
  
## 示例  
 下一行开始处位于行继续符后的空格包含在字符串常数中。  以上显示的示例都没有将换行符嵌入字符串常数中。  可以按如下所示嵌入换行符：  
  
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