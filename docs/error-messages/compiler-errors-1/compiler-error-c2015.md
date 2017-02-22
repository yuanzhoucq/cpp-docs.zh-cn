---
title: "编译器错误 C2015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2015"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2015"
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C2015
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

常数中的字符太多  
  
 一个字符常数包含的字符多于两个。  标准字符常数只能包含一个字符，长字符常数只能包含两个字符。  
  
 转义序列（如 \\t）将被转换为单个字符。  
  
## 示例  
 下面的示例生成 C2015：  
  
```  
// C2015.cpp  
// compile with: /c  
  
char test1 = 'error';   // C2015  
char test2 = 'e';   // OK  
```  
  
## 示例  
 当使用 Microsoft 扩展将字符常数转换为整数时，也可能发生 C2015。下面的示例生成 C2015：  
  
```  
// C2015b.cpp  
#include <stdio.h>  
  
int main()   
{  
    int a = 'abcde';   // C2015  
  
    int b = 'a';   // 'a' = ascii 0x61  
    printf_s("%x\n", b);  
}  
```