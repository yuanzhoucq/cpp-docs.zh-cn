---
title: 编译器错误 C2653 |Microsoft 文档
ms.custom: ''
ms.date: 11/30/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2653
dev_langs:
- C++
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8e1df7dd6337b1a3e363a5744181b12d94c879b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2653"></a>编译器错误 C2653

> *标识符*： 不是类或命名空间名称

类、 结构、 联合或此处命名空间名称，将需要的语言语法。

当你使用尚未声明为类、 结构、 联合或范围运算符的前面的命名空间的名称时，可以出现此错误。 若要解决此问题，将该名称声明，或包含的标头中声明的名称，然后使用它。

C2653 也可能是如果你尝试定义*复合命名空间*，包含一个或多个作用域嵌套命名空间名称的命名空间。 复合不允许定义在 c + + 在 C + + 17 之前的命名空间。 支持从在 Visual Studio 2015 Update 3 开始，在你指定的复合的命名空间[/std:c + + 最新](../../build/reference/std-specify-language-standard-version.md)编译器选项。 从 Visual c + + 2017 版本 15.5 开始，编译器支持复合命名空间定义时[/std:c + + 17](../../build/reference/std-specify-language-standard-version.md)指定选项。

## <a name="examples"></a>示例

此示例生成 C2653，因为作用域名称是使用但不是声明。 编译器需要的类、 结构、 联合或之前的范围运算符 （:） 的命名空间名称。

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

在代码中未编译 C + + 17 或更高版本的标准，嵌套的命名空间必须在每个嵌套级别使用显式命名空间声明：

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,
                          // C2429 thereafter. Use /std:c++17 or /std:c++latest to fix.

namespace a {             // Use this form for compliant code under /std:c++14 (the default)
   namespace b {          // or when using compilers before Visual Studio 2015 update 3.
      int i;
   }
}

int main() {
   a::b::i = 2;
}
```
