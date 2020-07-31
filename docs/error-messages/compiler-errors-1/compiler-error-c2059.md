---
title: 编译器错误 C2059
ms.date: 03/26/2019
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: 52b389806f5bacac78750bc745cd77699eb59735
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212873"
---
# <a name="compiler-error-c2059"></a>编译器错误 C2059

语法错误： "token"

令牌导致语法错误。

下面的示例为声明的行生成错误消息 `j` 。

```cpp
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

若要确定错误的原因，不仅要检查错误消息中列出的行，还应检查它上面的行。 如果检查行不产生关于问题的线索，请尝试注释掉错误消息中列出的行，并且可能会在其上方显示多行。

如果错误消息出现在紧跟变量后面的符号上 **`typedef`** ，请确保在源代码中定义了该变量。

当预处理器符号名称被重新用作标识符时，将引发 C2059。 在下面的示例中，编译器将视为 `DIGITS.ONE` 数字1，这对于作为枚举元素名称无效：

```cpp
#define ONE 1

enum class DIGITS {
    ZERO,
    ONE // error C2059
};
```

如果符号的计算结果为 nothing （当使用 **/d**_符号_进行编译时可能出现这种情况），则可能会出现 C2059 **=** 。

```cpp
// C2059a.cpp
// compile with: /DTEST=
#include <stdio.h>

int main() {
   #ifdef TEST
      printf_s("\nTEST defined %d", TEST);   // C2059
   #else
      printf_s("\nTEST not defined");
   #endif
}
```

可能出现 C2059 的另一种情况是：编译的应用程序在函数的默认参数中指定了结构。 参数的默认值必须是表达式。 初始值设定项列表（例如，用来初始化结构的列表）不是表达式。  若要解决此问题，请定义构造函数以执行所需的初始化。

下面的示例生成 C2059：

```cpp
// C2059b.cpp
// compile with: /c
struct ag_type {
   int a;
   float b;
   // Uncomment the following line to resolve.
   // ag_type(int aa, float bb) : a(aa), b(bb) {}
};

void func(ag_type arg = {5, 7.0});   // C2059
void func(ag_type arg = ag_type(5, 7.0));   // OK
```

对于格式错误的强制转换，可能出现 C2059。

下面的示例生成 C2059：

```cpp
// C2059c.cpp
// compile with: /clr
using namespace System;
ref class From {};
ref class To : public From {};

int main() {
   From^ refbase = gcnew To();
   To^ refTo = safe_cast<To^>(From^);   // C2059
   To^ refTo2 = safe_cast<To^>(refbase);   // OK
}
```

如果尝试创建包含句点的命名空间名称，则也会发生 C2059。

下面的示例生成 C2059：

```cpp
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

如果可限定名称（ `::` 、 `->` 和）的运算符 `.` 必须后跟关键字，则可能出现 C2059 **`template`** ，如以下示例中所示：

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::Rebind<X>::Other AX; // error C2059
};
```

默认情况下，C++ 会假定 `AY::Rebind` 不是模板；因此，后面的 `<` 解释为小于号。  必须显式告知编译器 `Rebind` 是模板，以便其正确分析尖括号。 若要更正此错误，请 **`template`** 在依赖类型的名称上使用关键字，如下所示：

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::template Rebind<X>::Other AX; // correct
};
```
