---
title: 编译器错误 C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: a709a540b24756a7e08f98552c5888a55c3ea601
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735965"
---
# <a name="compiler-error-c2062"></a>编译器错误 C2062

意外的类型 "type"

编译器不需要类型名称。

下面的示例生成 C2062：

```cpp
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

由于编译器处理构造函数的参数列表中未定义的类型的方式，也可能会发生 C2062。 如果编译器遇到未定义（拼写错误）的类型，则假定该构造函数是一个表达式，并发出 C2062。 若要解决此问题，请仅使用构造函数参数列表中的已定义类型。
