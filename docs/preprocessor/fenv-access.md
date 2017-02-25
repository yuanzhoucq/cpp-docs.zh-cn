---
title: "fenv_access | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.fenv_access"
  - "fenv_access_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fenv_access 杂注"
  - "杂注, fenv_access"
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# fenv_access
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

禁用 \(ON\) 或启用 \(OFF\) 可能更改标记测试和模式更改的优化。  
  
## 语法  
  
```  
#pragma fenv_access [ON | OFF]  
```  
  
## 备注  
 默认情况下，`fenv_access` 为 OFF。  
  
 有关浮点行为的详细信息，请参阅 [\/fp（指定浮点行为）](../build/reference/fp-specify-floating-point-behavior.md)。  
  
 具有 `fenv_access` 约束的优化类型如下：  
  
-   全局公共子表达式消除  
  
-   代码运动  
  
-   常量折叠  
  
 其他浮点杂注包括：  
  
-   [float\_control](../preprocessor/float-control.md)  
  
-   [fp\_contract](../preprocessor/fp-contract.md)  
  
## 示例  
  
```  
// pragma_directive_fenv_access_x86.cpp  
// compile with: /O2  
// processor: x86  
#include <stdio.h>  
#include <float.h>   
#include <errno.h>  
#pragma fenv_access (on)  
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
  **out\=9.999999776482582e\-003**   
## 示例  
 以下示例用于为 Itanium 处理器生成输出文件的编译器。  **\/fp:precise** 以扩展精度保留中间结果，其中大于 FLT\_MAX \(3.402823466e\+38F\) 的值可进行计算，因此求和的结果将为 1.0，手动计算也应该是这个结果。  **\/fp:strict** 以其源精度（浮点）保留中间结果，因此第一次相加将产生无限大的数（在整个表达式中保留）。  
  
```  
// pragma_directive_fenv_access_IPF.cpp  
// compile with: /O2 /fp:precise  
// processor: IPF  
// compiling with /fp:precise prints 1.0F  
// compile with /fp:strict to print infinity  
  
#include <stdio.h>  
float arr[5] = {3.402823465e+38F,   
               3.402823462e+38F,  
               3.402823464e+38F,  
               3.402823463e+38F,  
               1.0F};  
  
int main() {  
   float sum = 0;  
   sum = arr[0] + arr[1] - arr[2] - arr[3] + arr[4];  
   printf_s("%f\n", sum);  
}  
```  
  
  **1.000000**   
## 示例  
 在上一个示例中注释掉 `#pragma fenv_access (on)` 之后，请注意，由于编译器执行编译时计算，这个过程未使用控制模式，因此输出不同。  
  
```  
// pragma_directive_fenv_access_2.cpp  
// compile with: /O2  
#include <stdio.h>  
#include <float.h>   
  
int main() {  
   double z, b = 0.1, t = 0.1;  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);  
   if (err != 0) {  
      printf_s("The function _controlfp_s failed!\n");  
      return -1;  
   }  
   z = b * t;  
   printf_s ("out=%.15e\n",z);  
}  
```  
  
  **out\=1.000000000000000e\-002**   
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)