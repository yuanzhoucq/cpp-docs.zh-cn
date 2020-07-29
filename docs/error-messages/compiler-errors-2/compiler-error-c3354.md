---
title: 编译器错误 C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: fdc5de7493decf1f44617ab22a00fb5e8852116f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231970"
---
# <a name="compiler-error-c3354"></a>编译器错误 C3354

“%$I”：该函数用于创建不能有返回类型“type”的委托

以下类型作为的返回类型无效 **`delegate`** ：

- 指向函数的指针

- 指向成员的指针

- 指向成员函数的指针

- 对函数的引用

- 对成员函数的引用

以下示例生成 C3354：

```cpp
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
