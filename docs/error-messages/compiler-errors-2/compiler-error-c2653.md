---
title: "编译器错误 C2653 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2653
dev_langs:
- C++
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
caps.latest.revision: 9
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
ms.sourcegitcommit: eb0c1bf407d1478451c246cf615d031ef6c45bf9
ms.openlocfilehash: 2203cf8a09dbb05f6145ed238ab9fc03e458aaa5
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2653"></a>编译器错误 C2653
identifier︰ 不是类或命名空间名称  
  
语法要求在类、 结构、 联合或命名空间名称。  
  
下面的示例生成 C2653:  
  
```cpp  
// C2653.cpp  
// compile with: /c  
class yy {  
   void func1(int i);  
};  
  
void xx::func1(int m) {}   // C2653  
void yy::func1(int m) {}   // OK  
```  
  
C2653 也可能是如果您尝试定义*复合命名空间*，当您使用 Visual Studio 2015 Update 3 之前的 Visual c + + 版本包含一个或多个作用域嵌套命名空间名称的命名空间。 复合命名空间定义中不允许有 c + + 在 C + +&17; 之前。 从 Visual c + + 2015 Update 3 开始，编译器支持复合命名空间定义当[/std:c + + 中最新](../../build/reference/std-specify-language-standard-version.md)指定编译器选项︰  
```cpp  
// C2653b.cpp  
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,  
                          // C2429 thereafter. Use /std:c++latest to fix.
namespace a {  
   namespace b {  
      int i;  
   }  
}  
  
int main() {  
   a::b::i = 2;  
}  
```  
