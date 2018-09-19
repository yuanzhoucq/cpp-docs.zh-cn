---
title: 编译器错误 C2146 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2146
dev_langs:
- C++
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d75a9a6e2d7ad4b32f9c6ffa41287aa25399eb4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092149"
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

使用`T`显式专用化中不允许从主模板。 有关有效的 Visual Studio.NET 2003年和 Visual Studio.NET 版本的 Visual c + + 中的代码，将专用化中的模板参数的所有实例都替换显式专用化的类型。

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