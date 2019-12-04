---
title: 编译器错误 C3224
ms.date: 11/04/2016
f1_keywords:
- C3224
helpviewer_keywords:
- C3224
ms.assetid: 129be22f-8f3e-4fc6-9ccd-d27d8ef91251
ms.openlocfilehash: 23a83a90c5583a427ffae9a7e69e531981ddd7cc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757626"
---
# <a name="compiler-error-c3224"></a>编译器错误 C3224

“type”：没有任何重载泛型类采用“number”泛型类型参数

编译器找不到适当的重载。

下面的示例生成 C3224：

```
// C3224.cs
// compile with: /target:library
public class C<T> {}
public class C<T,U> {}
```

然后，

```cpp
// C3224b.cpp
// compile with: /clr
#using "C3224.dll"
int main() {
   C<int,int,int>^ c = gcnew C<int,int,int>();   // C3224
   C<int,int>^ c2 = gcnew C<int,int>();   // OK
}
```
