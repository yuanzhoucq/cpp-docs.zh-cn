---
title: 编译器错误 C2637
ms.date: 11/04/2016
f1_keywords:
- C2637
helpviewer_keywords:
- C2637
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
ms.openlocfilehash: a17bd95cf1727d058e0cbd9e3dfb93c500da9fb5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758250"
---
# <a name="compiler-error-c2637"></a>编译器错误 C2637

"identifier"：不能修改指向数据成员的指针

指向数据成员的指针不能具有调用约定。 若要解决此问题，请删除调用约定或声明指向成员函数的指针。

下面的示例生成 C2637：

```cpp
// C2637.cpp
// compile with: /c
struct S {};
int __stdcall S::*pms1;   // C2637

// OK
int S::*pms2;
int (__stdcall S::*pms3)(...);
```
