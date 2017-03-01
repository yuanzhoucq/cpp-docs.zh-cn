---
title: "编译器警告 （等级 1） C4382 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4382
dev_langs:
- C++
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 4571fe618b0ae89251d2748fbbcdfcb654201054
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4382"></a>编译器警告（等级 1）C4382
引发 type︰ 具有 __clrcall 析构函数或复制构造函数的类型仅陷入 /clr: pure 模块  
  
 **/Clr: pure**编译器选项已弃用 Visual Studio 2015 中。  
  
 如果使用编译的**/clr** (不**/clr: pure**)，异常处理预计要的本机类型的成员函数[__cdecl](../../cpp/cdecl.md)和 not [__clrcall](../../cpp/clrcall.md)。 本机类型与成员函数使用`__clrcall`调用约定不能使用编译的模块中捕获**/clr**。  
  
 如果将使用编译的模块中捕获异常**/clr: pure**，则可以忽略此警告。  
  
 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4382。  
  
```  
// C4382.cpp  
// compile with: /clr /W1 /c  
struct S {  
   __clrcall ~S() {}  
};  
  
struct T {  
   ~T() {}  
};  
  
int main() {  
   S s;  
   throw s;   // C4382  
  
   S * ps = &s;  
   throw ps;   // OK  
  
   T t;  
   throw t;   // OK  
}  
```
