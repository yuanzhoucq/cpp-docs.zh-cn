---
title: float_control | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
dev_langs:
- C++
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1525b92b43a688cdec970c646613aa4474d44cc3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="floatcontrol"></a>float_control
指定函数的浮点行为。  
  
## <a name="syntax"></a>语法  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## <a name="flags"></a>Flags  
 `value``setting` **[推送]**  
 指定浮点行为。 `value` 可以是**精确**或**除**。 有关详细信息，请参阅 [/fp（指定浮点行为）](../build/reference/fp-specify-floating-point-behavior.md)。 `setting` 可以是**上**或**关闭**。  
  
 如果`value`是**精确**的设置**精确**和**除**指定了。 **除**只能设置为**上**时**精确**也设置为**上**。  
  
 如果可选**推送**令牌添加，当前设置`value`推送到内部编译器堆栈。  
  
 **push**  
 将当前的 `float_control` 设置推送到内部编译器堆栈  
  
 **pop**  
 删除`float_control`从内部编译器堆栈顶部的设置，并成为新`float_control`设置。  
  
## <a name="remarks"></a>备注  
 无法打开`float_control precise`关闭时**除**上。 同样，**精确**无法关闭时`fenv_access`上。 若要通过 `float_control` 杂注从严格模式转到快速模式，请使用以下代码：  
  
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
  
-   [fenv_access](../preprocessor/fenv-access.md)  
  
-   [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>示例  
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
  
```Output  
Pass  
```  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)