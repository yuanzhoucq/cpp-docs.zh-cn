---
title: "编译器警告 （等级 1） C4750 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4750
dev_langs:
- C++
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 84f0628de933344eb23dc6325679abdcd3699c3a
ms.openlocfilehash: 6e22ef89b92a5b584979abbd370f82b482cf74e0
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4750"></a>编译器警告（等级 1）C4750
“identifier”：函数 with _alloca() 内嵌到循环中  
  
 Identifier 函数强制的内联展开[_alloca](../../c-runtime-library/reference/alloca.md)循环，它可能会导致堆栈溢出时执行该循环内的函数。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  确保 identifier 函数不会修改与[__forceinline](../../cpp/inline-functions-cpp.md)说明符。  
  
2.  确保 identifier 函数不包含[_alloca](../../c-runtime-library/reference/alloca.md)在循环中包含的函数。  
  
3.  请不要指定[/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md)， [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)， [/Ox](../../build/reference/ox-full-optimization.md)，或[/Og](../../build/reference/og-global-optimizations.md)编译开关。  
  
4.  位置[_alloca](../../c-runtime-library/reference/alloca.md) ，此功能在[尝试-除非语句](../../cpp/try-except-statement.md)，会捕获堆栈溢出。  
  
## <a name="example"></a>示例  
 下面的代码示例在循环中调用 `MyFunction` ，并且 `MyFunction` 调用 `_alloca` 函数。 `__forceinline` 修饰符导致 `_alloca` 函数内联扩展。  
  
```  
// c4750.cpp  
// compile with: /O2 /W1 /c  
#include <intrin.h>  
  
char * volatile newstr;  
  
__forceinline void myFunction(void) // C4750 warning  
{  
// The _alloca function does not require a __try/__except   
// block because the example uses compiler option /c.  
    newstr = (char * volatile) _alloca(1000);  
}  
  
int main(void)  
{  
    for (int i=0; i<50000; i++)  
       myFunction();  
    return 0;  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [_alloca](../../c-runtime-library/reference/alloca.md)
