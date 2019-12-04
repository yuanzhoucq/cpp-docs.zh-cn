---
title: 编译器错误 C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: 8dc7b521243c4eafdc22fab851812b6c12b004cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755910"
---
# <a name="compiler-error-c2146"></a>编译器错误 C2146

语法错误：标识符 "identifier" 之前缺少 "token"

编译器需要 `token`，但 `identifier` 改为找到。  可能的原因：

1. 拼写错误或大小写错误。

1. 标识符声明中缺少类型说明符。

此错误可能是由打字错误引起的。 错误[C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md)通常在此错误之前出现。

## <a name="example"></a>示例

下面的示例生成 C2146。

```cpp
// C2146.cpp
class CDeclaredClass {};

class CMyClass {
   CUndeclared m_myClass;   // C2146
   CDeclaredClass m_myClass2;   // OK
};

int main() {
   int x;
   int t x;   // C2146 : missing semicolon before 'x'
}
```

## <a name="example"></a>示例

对于 Visual Studio .NET 2003：缺少 `typename` 关键字，因此也可能会生成此错误。

下面的示例在 Visual Studio .NET 2002 中进行编译，但在 Visual Studio .NET 2003 中将失败：

```cpp
// C2146b.cpp
// compile with: /c
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};

template <typename T>
X<T>::Y func() { }   // C2146

// OK
template <typename T>
typename X<T>::Y func() { }
```

## <a name="example"></a>示例

您还会看到此错误是对 Visual Studio .NET 2003 执行的编译器一致性工作的结果：显式专用化不再从主模板中查找模板参数。

显式专用化中不允许使用主模板中的 `T`。 要使代码在 Visual Studio .NET 2003 和 Visual Studio .NET 中有效，请将专用化中的模板参数的所有实例替换为显式专用化的类型。

下面的示例在 Visual Studio .NET 中进行编译，但在 Visual Studio .NET 2003 中将失败：

```cpp
// C2146_c.cpp
// compile with: /c
template <class T>
struct S;

template <>
struct S<int> {
   T m_t;   // C2146
   int m_t2;   // OK
};
```
