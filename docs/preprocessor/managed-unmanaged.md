---
title: "managed、 unmanaged |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
dev_langs: C++
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d8e2b50f7d505a4e262559b6cb69b0bab81ffcd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="managed-unmanaged"></a>managed、unmanaged
启用函数级控制以将函数编译为托管或未托管函数。  
  
## <a name="syntax"></a>语法  
  
```  
  
      #pragma managed  
#pragma unmanaged  
#pragma managed([push,] on | off)  
#pragma managed(pop)  
```  
  
## <a name="remarks"></a>备注  
 [/Clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项提供模块级别控制用于编译为托管或非托管函数。  
  
 未托管函数将为本机平台编译，因此，这一部分的程序的执行将由公共语言运行时传递给本机平台。  
  
 将函数编译为默认情况下管理时**/clr**使用。  
  
 在将应用这些杂注时：  
  
-   在函数前添加杂注，而不是在函数体内添加。  
  
-   在 `#include`语句后添加杂注。 在 `#include` 语句之前不使用这些杂注。  
  
 编译器将忽略`managed`和`unmanaged`杂注如果**/clr**不编译中使用。  
  
 当实例化模板函数后，定义时的模板的杂注状态可确定该函数是托管或未托管的。  
  
 有关详细信息，请参阅[初始化混合程序集的](../dotnet/initialization-of-mixed-assemblies.md)。  
  
## <a name="example"></a>示例  
  
```cpp  
// pragma_directives_managed_unmanaged.cpp  
// compile with: /clr  
#include <stdio.h>  
  
// func1 is managed  
void func1() {  
   System::Console::WriteLine("In managed function.");  
}  
  
// #pragma unmanaged  
// push managed state on to stack and set unmanaged state  
#pragma managed(push, off)  
  
// func2 is unmanaged  
void func2() {  
   printf("In unmanaged function.\n");  
}  
  
// #pragma managed  
#pragma managed(pop)  
  
// main is managed  
int main() {  
   func1();  
   func2();  
}  
```  
  
```Output  
In managed function.  
In unmanaged function.  
```  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)