---
title: 编译器错误 C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 8238dcec821256dad8101cd7ad59b2d85882c218
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345513"
---
# <a name="compiler-error-c3149"></a>编译器错误 C3149

type： 不能使用没有顶级 char 此类型

未正确指定一个声明。

例如，可能会定义在全局范围内的 CLR 类型并尝试为定义的一部分创建的变量的类型。 因为不允许使用的 CLR 类型的全局变量，编译器将生成 C3149。

若要解决此错误，声明函数或类型定义内的 CLR 类型的变量。

下面的示例生成 C3149:

```
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

下面的示例生成 C3149:

```
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
