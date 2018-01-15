---
title: "fenv_access |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 623c9cb9af1d7df137aa7ee92071e34ad99a6331
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fenvaccess"></a>fenv_access
禁用 (ON) 或启用 (OFF) 可能更改标记测试和模式更改的优化。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma fenv_access [ON | OFF]  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，`fenv_access` 为 OFF。  
  
 浮点行为的详细信息，请参阅[/fp （指定浮点行为）](../build/reference/fp-specify-floating-point-behavior.md)。  
  
 具有 `fenv_access` 约束的优化类型如下：  
  
-   全局公共子表达式消除  
  
-   代码运动  
  
-   常量折叠  
  
 其他浮点杂注包括：  
  
-   [float_control](../preprocessor/float-control.md)  
  
-   [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>示例  
  
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
  
```Output  
out=9.999999776482582e-003  
```  
  
## <a name="example"></a>示例  
 以下示例用于为 Itanium 处理器生成输出文件的编译器。 **/fp： 精确**手动计算也应该在其中更大的值不是 FLT_MAX (3.402823466 e + 38F) 可以自动计算和因此求和将具有 1.0 结果的扩展精度保留中间结果。 **/fp: strict**保留中间结果以其源精度 (float)，因此第一次相加将产生无限大，这保留在整个表达式。  
  
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
  
```Output  
1.000000  
```  
  
## <a name="example"></a>示例  
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
  
```Output  
out=1.000000000000000e-002  
```  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)