---
title: 编译器错误 C2748
ms.date: 11/04/2016
f1_keywords:
- C2748
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
ms.openlocfilehash: e43defbf28c76dadcc7921ca76778413c41490a6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759628"
---
# <a name="compiler-error-c2748"></a>编译器错误 C2748

创建托管数组或 WinRT 数组时必须提供数组大小或数组初始值设定项

托管数组或 WinRT 数组的格式不正确。 有关详细信息，请参阅 [数组](../../extensions/arrays-cpp-component-extensions.md)。

下面的示例生成 C2748，并演示如何修复此错误：

```cpp
// C2748.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>();   // C2748
   // try the following line instead
   array<int> ^p2 = new array<int>(2);
}
```
