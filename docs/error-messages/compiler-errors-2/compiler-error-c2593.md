---
title: 编译器错误 C2593 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2593
dev_langs:
- C++
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a3b0d1a8574aa5c05bbca023a1209cf1801f57e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042723"
---
# <a name="compiler-error-c2593"></a>编译器错误 C2593

运算符 identifier 不明确

重载运算符为定义了多个可能的运算符。

如果在上一个或多个实际参数使用显式强制转换，可能会修复此错误。

下面的示例生成 C2593:

```
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

此错误可能由序列化浮点变量 using`CArchive`对象。 编译器标识`<<`为不明确的运算符。 唯一的基元的 c + + 类型`CArchive`可以序列化是固定大小类型`BYTE`， `WORD`， `DWORD`，和`LONG`。 所有的整数类型必须转换为以下类型之一，以进行序列化。 必须使用存档浮点类型`CArchive::Write()`成员函数。

下面的示例演示如何将浮点变量 (`f`) 到存档`ar`:

```
ar.Write(&f, sizeof( float ));
```