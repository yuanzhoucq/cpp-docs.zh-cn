---
title: 编译器错误 C3149 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3149
dev_langs:
- C++
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a522bfd3ba236661f206d8d4e4b550179c06b3f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033116"
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
