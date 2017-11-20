---
title: "编译器警告 （等级 4） C4701 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4701
dev_langs: C++
helpviewer_keywords: C4701
ms.assetid: d7c76c66-1f3f-4d3c-abe4-5d94c84a5a1f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 696e3086f139d70ada9afdf1af02a007cbe1609f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4701"></a>编译器警告（等级 4）C4701
可能未初始化的本地变量 name，然后使用  
  
 本地变量*名称*可能已使用没有为其分配一个值。 这可能导致不可预知的结果。  
  
## <a name="example"></a>示例  
 以下代码生成了 C4701 和 C4703。  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr) // C4701 and C4703  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
```Output  
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used  
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used  
  
```  
  
 若要更正此警告，请初始化该变量，如以下示例所示：  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p = nullptr;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr)  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [编译器警告 （等级 4） C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)   
 [警告、 /sdl 和改进未初始化的变量检测](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)