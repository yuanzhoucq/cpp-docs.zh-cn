---
title: 编译器错误 C2143
ms.date: 11/04/2016
f1_keywords:
- C2143
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
ms.openlocfilehash: 310083a650f842c6c0f0912efe1ceddb66c4fd6f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214745"
---
# <a name="compiler-error-c2143"></a>编译器错误 C2143

语法错误： "token2" 之前缺少 "token1"

编译器需要一个特定的令牌（即，非空白语言元素），并找到另一个令牌。

检查[c + + 语言参考](../../cpp/cpp-language-reference.md)，确定代码语法不正确的位置。 由于编译器在遇到导致问题的行后可能会报告此错误，因此请检查错误之前的几行代码。

C2143 可能会在不同的情况下发生。

如果可限定名称的运算符（ `::` 、 `->` 和 `.` ）必须后跟关键字，则会发生这种情况 **`template`** ，如本示例所示：

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143
    {
    };
};
```

默认情况下，C++ 会假定 `Ty::PutFuncType` 不是模板；因此，后面的 `<` 解释为小于号。  必须显式告知编译器 `PutFuncType` 是模板，以便其正确分析尖括号。 若要更正此错误，请 **`template`** 在依赖类型的名称上使用关键字，如下所示：

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct
    {
    };
};
```

当使用 **/clr**并且 **`using`** 指令具有语法错误时，可能会发生 C2143：

```cpp
// C2143a.cpp
// compile with: /clr /c
using namespace System.Reflection;   // C2143
using namespace System::Reflection;
```

当你尝试使用 CLR 语法编译源代码文件时，如果未使用 **/clr**，也会出现这种情况：

```cpp
// C2143b.cpp
ref struct A {   // C2143 error compile with /clr
   void Test() {}
};

int main() {
   A a;
   a.Test();
}
```

语句后面的第一个非空白字符 **`if`** 必须是左括号。 编译器无法转换任何其他内容：

```cpp
// C2143c.cpp
int main() {
   int j = 0;

   // OK
   if (j < 25)
      ;

   if (j < 25)   // C2143
}
```

在检测到错误的行上或紧靠该行的上面某行中缺少右大括号、圆括号或分号时，可能发生 C2143：

```cpp
// C2143d.cpp
// compile with: /c
class X {
   int member1;
   int member2   // C2143
} x;
```

或者类声明中存在无效的标记时：

```cpp
// C2143e.cpp
class X {
   int member;
} x;

class + {};   // C2143 + is an invalid tag name
class ValidName {};   // OK
```

或者一个标签未附加到语句时。 如果必须单独放置标签，例如，在复合语句的末尾，请将其附加到 null 语句：

```cpp
// C2143f.cpp
// compile with: /c
void func1() {
   // OK
   end1:
      ;

   end2:   // C2143
}
```

对 c + + 标准库中的类型进行非限定调用时，可能发生此错误：

```cpp
// C2143g.cpp
// compile with: /EHsc /c
#include <vector>
static vector<char> bad;   // C2143
static std::vector<char> good;   // OK
```

或者缺少 **`typename`** 关键字：

```cpp
// C2143h.cpp
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};
template <typename T>
X<T>::Y X<T>::memFunc() {   // C2143
// try the following line instead
// typename X<T>::Y X<T>::memFunc() {
   return Y();
}
```

或者尝试定义显式实例化：

```cpp
// C2143i.cpp
// compile with: /EHsc /c
// template definition
template <class T>
void PrintType(T i, T j) {}

template void PrintType(float i, float j){}   // C2143
template void PrintType(float i, float j);   // OK
```

在 C 程序中，变量必须在函数的开始处声明，并且不能在函数执行非声明指令后声明。

```C
// C2143j.c
int main()
{
    int i = 0;
    i++;
    int j = 0; // C2143
}
```
