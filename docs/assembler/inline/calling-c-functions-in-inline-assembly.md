---
title: "调用内联程序集内的 C 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 关键字 [C++], 调用函数"
  - "函数调用, C 函数"
  - "函数调用, 在内联程序集中"
  - "函数 [C], 在内联程序集中调用"
  - "内联程序集, 调用函数"
  - "Visual C, 函数"
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 调用内联程序集内的 C 函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 `__asm` 块可以调用 C 函数（包括 C 库例程）。  以下示例调用 `printf` 库例程：  
  
```  
// InlineAssembler_Calling_C_Functions_in_Inline_Assembly.cpp  
// processor: x86  
#include <stdio.h>  
  
char format[] = "%s %s\n";  
char hello[] = "Hello";  
char world[] = "world";  
int main( void )  
{  
   __asm  
   {  
      mov  eax, offset world  
      push eax  
      mov  eax, offset hello  
      push eax  
      mov  eax, offset format  
      push eax  
      call printf  
      //clean up the stack so that main can exit cleanly  
      //use the unused register ebx to do the cleanup  
      pop  ebx  
      pop  ebx  
      pop  ebx  
   }  
}  
```  
  
 由于函数参数在堆栈上传递，因此仅需在调用函数之前推入所需参数（前面示例中的字符串指针）。  参数以相反顺序被推动，因此可按所需顺序结束堆栈。  模拟 C 语句  
  
```  
printf( format, hello, world );  
```  
  
 此示例按照该顺序推送指向 `world`、`hello` 和 `format` 的指针，然后调用 `printf`。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [内联汇编程序](../../assembler/inline/inline-assembler.md)