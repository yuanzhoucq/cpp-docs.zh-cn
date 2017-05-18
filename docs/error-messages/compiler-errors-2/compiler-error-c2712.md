---
title: "编译器错误 C2712 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2712
dev_langs:
- C++
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
caps.latest.revision: 15
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 89b7d0ad3c7e175db1525c2f3fb8407240ce943c
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2712"></a>编译器错误 C2712
无法在要求对象展开的函数中使用 __try  
  
 如果您使用，则会出现错误 C2712 [/EHsc](../../build/reference/eh-exception-handling-model.md)，并且将函数与结构化的异常处理也具有需要展开 （析构） 的对象。  
  
 可能的解决方案：  
  
-   将要求 SEH 的代码移动到另一个函数中  
  
-   重写使用 SEH 的函数以避免使用具有析构函数的局部变量和参数。 在构造函数或析构函数中不要使用 SEH  
  
-   不使用 /EHsc 进行编译  
  
 如果调用使用声明的方法，也可能发生错误 C2712 [__event](../../cpp/event.md)关键字。 因为该事件可能在多线程环境中使用，编译器将生成代码，阻止操作的基础事件对象，然后将生成的代码封装在 SEH [try-finally 语句](../../cpp/try-finally-statement.md)。 因此，如果调用事件方法并按值传递其类型具有析构函数的自变量，则将发生错误 C2712。 这种情况的一种解决方法是将自变量作为常数引用进行传递。  
  
## <a name="example"></a>示例  
 如果在编译时使用，也可能发生 C2712 **/clr: pure**并声明中的函数指针的静态数组`__try`块。 静态成员需要编译器下使用动态初始化**/clr: pure**，这表明 c + + 异常处理。 但是，不允许在 `__try` 块中进行 C++ 异常处理。  
  
 **/Clr: pure**和**/clr: safe**编译器选项不推荐使用 Visual Studio 2015 中。  
  
 下面的示例生成 C2712，并演示如何修复此错误。  
  
```  
// C2712.cpp  
// compile with: /clr:pure /c  
struct S1 {  
   static int smf();  
   void fnc();  
};  
  
void S1::fnc() {  
   __try {  
      static int (*array_1[])() = {smf,};   // C2712  
  
      // OK  
      static int (*array_2[2])();  
      array_2[0] = smf;  
    }  
    __except(0) {}  
}  
```
