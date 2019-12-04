---
title: 编译器错误 C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 263eb03b7a9f45458f8d8b586adc6f1cfc5805be
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745975"
---
# <a name="compiler-error-c3149"></a>编译器错误 C3149

"type"：不能在没有顶级 "char" 的情况下使用此类型

未正确指定声明。

例如，你可能在全局范围内定义了 CLR 类型，并尝试在定义中创建类型为的变量。 由于不允许使用 CLR 类型的全局变量，编译器将生成 C3149。

若要解决此错误，请在函数或类型定义中声明 CLR 类型的变量。

下面的示例生成 C3149：

```cpp
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

下面的示例生成 C3149：

```cpp
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
