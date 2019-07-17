---
title: 编译器错误 C2653
ms.date: 11/30/2017
f1_keywords:
- C2653
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
ms.openlocfilehash: 2882764e1c0a84634c500d920f327fbebc4b19a9
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447943"
---
# <a name="compiler-error-c2653"></a>编译器错误 C2653

> '*标识符*： 不是类或命名空间名称

语言语法要求在类、 结构、 联合或此处命名空间名称。

使用尚未声明为类、 结构、 联合或范围运算符的前面的命名空间的名称时，可能出现此错误。 若要解决此问题，请声明名称或包括声明的名称，然后使用它的标头。

C2653 也可能是如果你尝试定义*复合命名空间*，包含一个或多个作用域嵌套命名空间名称的命名空间。 中不允许使用复合命名空间定义C++在 c++17 之前。 指定时，Visual Studio 2015 Update 3 开始支持复合的命名空间[/std: c + + 最新](../../build/reference/std-specify-language-standard-version.md)编译器选项。 从 Visual Studio 2017 版本 15.5 中，编译器支持复合命名空间定义时[/std: c + + 17](../../build/reference/std-specify-language-standard-version.md)指定选项。

## <a name="examples"></a>示例

此示例生成 C2653，因为使用但未声明的范围名称。 编译器需要类、 结构、 联合或范围运算符 （::） 之前的命名空间名称。

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

在代码中不编译为 C + + 17 或更高版本的标准，嵌套的命名空间必须在每个嵌套级别使用的显式命名空间声明：

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual Studio 2015 Update 3,
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
