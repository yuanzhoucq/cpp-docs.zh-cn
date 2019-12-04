---
title: 编译器错误 C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: c63fe7bb3686692818337e890de7fe4c80a18158
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739553"
---
# <a name="compiler-error-c2790"></a>编译器错误 C2790

"super"：该关键字只能在类成员函数体内使用

如果用户曾经尝试在成员函数的上下文之外使用关键字[super](../../cpp/super.md) ，则会出现此错误消息。

下面的示例生成 C2790：

```cpp
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```
