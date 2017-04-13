---
title: "编译器警告 （等级 1） C4350 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4350
dev_langs:
- C++
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
caps.latest.revision: 7
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
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 141f5552c4b86e170587f42ebabf5e2e597b4e96
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4350"></a>编译器警告（等级 1）C4350
行为更改: 调用了“member1”而不是“member2”  
  
 右值不能绑定到非 const 引用。 在 Visual Studio 2003 之前的 Visual c + + 版本，就可以将右值绑定到直接初始化中的非 const 引用。 此代码现在会发出警告。  
  
 为了向后兼容，仍可以将右值绑定到非 const 引用，但只要有可能，是首选标准转换。  
  
 此警告表示从 Visual c + +.NET 2002年编译器的行为的更改。 如果启用，此警告可能可能给出的正确代码。 例如，它可以为其赋予时使用**std::auto_ptr**类模板。  
  
 如果你收到此警告，检查你的代码，以查看是否它依赖于绑定到非量引用的右值。 添加到引用的 const 或提供其他的常量引用重载可能会解决问题。  
  
 默认情况下，此警告处于关闭状态。 有关详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的示例生成 C4350:  
  
```cpp  
// C4350.cpp  
// compile with: /W1  
#pragma warning (default : 4350)  
class A {};  
  
class B  
{  
public:  
   B(B&){}  
   // try the following instead:  
   // B(const B&){}  
  
   B(A){}  
   operator A(){ return A();}  
};  
  
B source() { return A(); }  
  
int main()  
{  
   B ap(source());   // C4350  
}  
```
