---
title: "编译器警告（等级 1）C4533 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4533"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4533"
ms.assetid: 359fecda-d540-46e5-b214-dbabe9ef50d2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4533
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“instruction”跳过了“variable”的初始化  
  
 程序中的指令更改了控制流，因此没有执行初始化变量的指令。  下面的示例生成 C4533：  
  
```  
// C4533.cpp  
// compile with: /W1  
#include <stdio.h>  
  
struct A  
{  
   int m_data;  
};  
  
int main()  
{  
   if (1)  
   {  
      goto Label;  
   }  
  
   A a = { 100 };  
  
   Label:   // C4533  
      printf("\n%d", a.m_data);   // prints an uninitialized value  
}  
```