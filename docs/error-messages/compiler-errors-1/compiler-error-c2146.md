---
title: 编译器错误 C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: f00de0ce491d517da11f251b89ccb9a7ae66b77d
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447268"
---
# <a name="compiler-error-c2146"></a>编译器错误 C2146

语法错误： 缺少 token 标识符 identifier 的前面

编译器预期`token`并找到`identifier`相反。  可能的原因：

1. 拼写或大小写错误。

1. 标识符的声明中缺少类型说明符。

犯了输入错误可能导致此错误。 错误[C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md)通常在之前发生此错误。

## <a name="example"></a>示例

下面的示例生成 C2146。

```
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

此外可以为 Visual Studio.NET 2003年执行的编译器一致性工作生成此错误： 缺少`typename`关键字。

下面的示例在 Visual Studio.NET 2002年中编译，但在 Visual Studio.NET 2003年中将失败：

```
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

您还会看到此错误的 Visual Studio.NET 2003年执行的编译器一致性工作： 显式专用化无法再找到从主模板的模板参数。

使用`T`显式专用化中不允许从主模板。 要使 Visual Studio.NET 2003年和 Visual Studio.NET 中有效的代码，将专用化中的模板参数的所有实例都替换显式专用化的类型。

下面的示例在 Visual Studio.NET 中进行编译，但在 Visual Studio.NET 2003年中将失败：

```
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