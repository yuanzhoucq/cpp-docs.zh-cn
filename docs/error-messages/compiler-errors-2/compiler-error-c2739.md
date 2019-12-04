---
title: 编译器错误 C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: 18cece8d9630aa93e867329acc7cefea30da3286
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759654"
---
# <a name="compiler-error-c2739"></a>编译器错误 C2739

“number”: 显式托管或 WinRT 数组维度必须介于 1 和 32 之间

数组维度不在 1 和 32 之间。

下面的示例生成 C2739，并演示如何修复此错误：

```cpp
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```
