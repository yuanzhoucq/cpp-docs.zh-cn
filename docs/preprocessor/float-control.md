---
title: "float_control | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.float_control"
  - "float_control_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "float_control 杂注"
  - "杂注, float_control"
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# float_control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定函数的浮点行为。  
  
## 语法  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## Flags  
 `value` *,* `setting` **\[push\]**  
 指定浮点行为。  `value` 可以是 **precise**  或 **except**。  有关详细信息，请参阅 [\/fp（指定浮点行为）](../build/reference/fp-specify-floating-point-behavior.md)。  `setting` 可以是 **on** 或 **off**。  
  
 如果 `value` 是 **precise**，则指定 **precise** 和 **except** 的设置。  **except** 只能设置为 **on** 的情况是 **precise** 也设置为 **on**。  
  
 如果添加了可选的 **push** 标记，则 `value` 的当前设置将推送到内部编译器堆栈。  
  
 **push**  
 将当前的 `float_control` 设置推送到内部编译器堆栈  
  
 **pop**  
 从内部编译器堆栈的顶部移除 `float_control` 设置，使其成为新的 `float_control` 设置。  
  
## 备注  
 当 **except** 打开时，无法关闭 `float_control precise`。  同样，当 `fenv_access` 打开时，无法关闭 **precise**。  若要通过 `float_control` 杂注从严格模式转到快速模式，请使用以下代码：  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
// The following line is needed on Itanium processors  
#pragma fp_contract(on)  
```  
  
 若要通过 `float_control` 杂注从快速模式转到严格模式，请使用以下代码：  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
// The following line is needed on Itanium processors.  
#pragma fp_contract(off)  
```  
  
 其他浮点杂注包括：  
  
-   [fenv\_access](../preprocessor/fenv-access.md)  
  
-   [fp\_contract](../preprocessor/fp-contract.md)  
  
## 示例  
 以下示例演示如何通过使用杂注 `float_control` 捕获溢出浮点异常。  
  
```  
// pragma_directive_float_control.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <float.h>  
  
double func( ) {  
   return 1.1e75;  
}  
  
#pragma float_control (except,on)  
  
int main( ) {  
   float u[1];  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);  
   if (err != 0)  
      printf_s("_controlfp_s failed!\n");  
  
   try  {  
      u[0] = func();  
      printf_s ("Fail");     
      return(1);  
   }   
  
   catch (...)  {  
      printf_s ("Pass");  
      return(0);  
   }  
}  
```  
  
  **通过**   
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)