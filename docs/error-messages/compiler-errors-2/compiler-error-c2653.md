---
title: "编译器错误 C2653 |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2653
dev_langs: C++
helpviewer_keywords: C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8b2cca7e855256e9caf5a72e6f8b4a6e2924eca6
ms.sourcegitcommit: 78f3f8208d49b7c1d87f4240f4a1496b7c29333e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="compiler-error-c2653"></a>编译器错误 C2653
identifier： 不是类或命名空间名称  
  
语法要求类、 结构、 联合或命名空间名称。  
  
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
  
C2653 也可能是如果你尝试定义*复合命名空间*，当你使用 Visual c + + 在 Visual Studio 2015 Update 3 之前的版本时，包含一个或多个作用域嵌套命名空间名称的命名空间。 复合不允许定义在 c + + 在 C + + 17 之前的命名空间。 从 Visual c + + 2015 版本 15.5 开始，编译器支持复合命名空间定义时[/std:c + + 17](../../build/reference/std-specify-language-standard-version.md)指定编译器选项：  
```cpp  
// C2653b.cpp  
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,  
                          // C2429 thereafter. Use /std:c++17 to fix (or /std:c++latest in 15.3)
namespace a {  
   namespace b {  
      int i;  
   }  
}  
  
int main() {  
   a::b::i = 2;  
}  
```  

在 Visual Studio 2017 版本 15.3，/std:c + + 最新交换机是必需的。
