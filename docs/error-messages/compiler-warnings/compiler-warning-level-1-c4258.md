---
title: "编译器警告（等级 1）C4258 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4258"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4258"
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4258
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“variable”: 忽略 For 循环中的定义；使用封闭范围中的定义  
  
 在 [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) 和 [\/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) 下，[for](../../cpp/for-statement-cpp.md) 循环中定义的变量在 **For** 循环结束之后超出范围。  如果在包含 **For** 循环的范围内再次使用与循环变量同名但在封闭循环中定义的变量，则出现此警告。  例如：  
  
```  
// C4258.cpp  
// compile with: /Zc:forScope /W1  
int main()  
{  
   int i;  
   {  
      for (int i =0; i < 1; i++)  
         ;  
      i = 20;   // C4258 i (in for loop) has gone out of scope  
   }  
}  
```