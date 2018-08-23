---
title: 浮点控制 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9b94e5b8eccdc63735c7cb25faa7eacb1e23670
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539170"
---
# <a name="floatcontrol"></a>float_control
指定函数的浮点行为。  
  
## <a name="syntax"></a>语法  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## <a name="flags"></a>Flags  
 
*值*，*设置* *[推送]*  
指定浮点行为。 *值*可以是`precise`或`except`。 有关详细信息，请参阅 [/fp（指定浮点行为）](../build/reference/fp-specify-floating-point-behavior.md)。 *设置*可以处于`on`或`off`。  
  
如果*值*是`precise`，为设置`precise`和`except`指定了。 `except` 只能设置为`on`时`precise`也设置为`on`。  
  
如果可选*推送*令牌添加，当前设置为*值*推送到内部编译器堆栈。  
  
*push*  
推送当前**float_control**设置到内部编译器堆栈  
  
*pop*  
移除**float_control**从内部编译器堆栈的顶部设置，并成为新**float_control**设置。  
  
## <a name="remarks"></a>备注  
 
当 `float_control precise` 打开时，无法关闭 `except`。 同样，当 `precise` 打开时，无法关闭 `fenv_access`。 若要从严格模式转到快速模式与**float_control**杂注，使用以下代码：  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
```  
  
若要从快速模式转到严格模式，与**float_control**杂注，使用以下代码：  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
```  
  
其他浮点杂注包括：  
  
- [fenv_access](../preprocessor/fenv-access.md)  
  
- [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>示例  
 
下面的示例演示如何通过使用杂注捕获溢出浮点异常**float_control**。  
  
```cpp  
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
