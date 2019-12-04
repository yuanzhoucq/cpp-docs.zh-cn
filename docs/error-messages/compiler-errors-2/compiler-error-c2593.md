---
title: 编译器错误 C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: 2a385e35376ddce528678980705595bfb98aca95
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759342"
---
# <a name="compiler-error-c2593"></a>编译器错误 C2593

"operator identifier" 不明确

为重载运算符定义了多个可能的运算符。

如果对一个或多个实际参数使用显式强制转换，则可能会修复此错误。

下面的示例生成 C2593：

```cpp
// C2593.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};
void operator+( X, X );
void operator+( A, B );
D d;

int main() {
   d +  d;         // C2593, D has an A, B, and X
   (X)d + (X)d;    // OK, uses operator+( X, X )
}
```

使用 `CArchive` 对象序列化浮点变量可能导致此错误。 编译器将 `<<` 运算符标识为不明确。 `CArchive` 可以进行C++序列化的基元类型只能是固定大小类型 `BYTE`、`WORD`、`DWORD`和 `LONG`。 所有整数类型都必须强制转换为这些类型之一以进行序列化。 必须使用 `CArchive::Write()` 成员函数存档浮点类型。

下面的示例演示如何将浮点变量（`f`）存档 `ar`存档：

```
ar.Write(&f, sizeof( float ));
```
