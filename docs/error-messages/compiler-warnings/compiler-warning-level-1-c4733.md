---
title: "编译器警告（等级 1）C4733 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4733"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4733"
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4733
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

内联 asm 分配到“FS:0”: 处理程序未注册为安全处理程序  
  
 在 FS:0 修改值以添加新的异常处理程序的函数不可以使用安全异常，因为该处理程序不可被注册为有效的异常处理程序（请参见 [\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)）。  
  
 若要解决此警告，或者移除 FS:0 定义，或者关闭此警告并使用 [.SAFESEH](../../assembler/masm/dot-safeseh.md) 指定安全异常处理程序。  
  
 下面的示例生成 C4733：  
  
```  
// C4733.cpp  
// compile with: /W1 /c  
// processor: x86  
#include "stdlib.h"  
#include "stdio.h"  
void my_handler()  
{  
   printf("Hello from my_handler\n");  
   exit(1);  
}  
  
int main()  
{  
   _asm {  
      push    my_handler  
      mov     eax, DWORD PTR fs:0  
      push    eax  
      mov     DWORD PTR fs:0, esp   // C4733  
   }  
  
   *(int*)0 = 0;  
}  
```