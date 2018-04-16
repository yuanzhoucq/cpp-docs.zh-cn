---
title: "编译器警告 （等级 1） C4350 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4350
dev_langs:
- C++
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e05320bcfeac5ba340d286851e13439e53734a7a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4350"></a>编译器警告（等级 1）C4350
行为更改: 调用了“member1”而不是“member2”  
  
 右值不能绑定到非 const 引用。 在 Visual Studio 2003 之前的 Visual c + + 版本，就可以将右值绑定到直接初始化中的非 const 引用。 此代码现在会发出警告。  
  
 为了向后兼容，仍可以将右值绑定到非 const 引用，但只要有可能，是首选标准转换。  
  
 此警告表示从 Visual c + +.NET 2002年编译器的行为的更改。 如果启用，此警告可能可能给出的正确代码。 例如，它可以为其赋予时使用**std::auto_ptr**类模板。  
  
 如果你收到此警告，检查你的代码，以查看是否它依赖于绑定到非量引用的右值。 添加到引用的 const 或提供其他的常量引用重载可能会解决问题。  
  
 默认情况下，此警告处于关闭状态。 有关详细信息，请参阅 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
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