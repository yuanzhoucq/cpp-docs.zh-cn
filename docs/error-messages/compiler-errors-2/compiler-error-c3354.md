---
title: 编译器错误 C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: e5945b2112d1d03e4f18944d15028229cce4b668
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738591"
---
# <a name="compiler-error-c3354"></a>编译器错误 C3354

“%$I”：该函数用于创建不能有返回类型“type”的委托

以下类型作为 `delegate`的返回类型无效：

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
