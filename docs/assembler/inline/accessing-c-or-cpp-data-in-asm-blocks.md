---
title: "访问 __asm 块中的 C 或 C++ 数据 | Microsoft Docs"
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
  - "__asm 关键字 [C++], 数据成员"
  - "数据访问 [C++], 在 __asm 块中"
  - "数据成员 [C++], 在 __asm 块中"
  - "__asm 块中的结构类型"
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 访问 __asm 块中的 C 或 C++ 数据
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 内联程序集的一个重大便利就是能够按名称引用 C 或 C\+\+ 变量。  `__asm` 块可引用任何符号，包括位于块所在的范围内的变量名称。  例如，如果 C 变量 `var` 位于范围内，则指令  
  
```  
__asm mov eax, var  
```  
  
 在 EAX 中存储 `var` 的值。  
  
 如果类、结构或联合成员具有唯一的名称，则 `__asm` 块可以只使用该成员名称来引用它，无需在句点 \(**.**\) 运算符之前指定变量或 `typedef` 名称。  但是，如果成员名称不是唯一的，则必须在紧靠句点运算符前面放置变量或 `typedef` 名称。  例如，以下示例中的结构共享 `same_name` 作为其成员名称：  
  
 如果使用以下类型声明变量  
  
```  
struct first_type hal;  
struct second_type oat;  
```  
  
 对成员 `same_name` 的所有引用都必须使用变量名称，因为 `same_name` 不是唯一的。  但成员 `weasel` 具有唯一的名称，因此您可以只使用其成员名称来引用它：  
  
```  
// InlineAssembler_Accessing_C_asm_Blocks.cpp  
// processor: x86  
#include <stdio.h>  
struct first_type  
{  
   char *weasel;  
   int same_name;  
};  
  
struct second_type  
{  
   int wonton;  
   long same_name;  
};  
  
int main()  
{  
   struct first_type hal;  
   struct second_type oat;  
  
   __asm  
   {  
      lea ebx, hal  
      mov ecx, [ebx]hal.same_name ; Must use 'hal'  
      mov esi, [ebx].weasel       ; Can omit 'hal'  
   }  
   return 0;  
}  
```  
  
 请注意，省略变量名只是为了方便编码。  无论变量名是否存在，都会生成相同的程序集指令。  
  
 您可以在 C\+\+ 中访问数据成员而无需考虑访问限制。  但是，您无法调用成员函数。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [在 \_\_asm 块中使用 C 或 C\+\+](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)