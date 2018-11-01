---
title: 编译器错误 C2767
ms.date: 11/04/2016
f1_keywords:
- C2767
helpviewer_keywords:
- C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
ms.openlocfilehash: 6c13610b6fd7aae4b4232b836a0307867bd591d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550145"
---
# <a name="compiler-error-c2767"></a>编译器错误 C2767

托管或 WinRTarray 维度不匹配： 应有 N 个提供了 M

托管数组或 WinRT 数组的声明的格式不正确。 有关详细信息，请参阅 [数组](../../windows/arrays-cpp-component-extensions.md)。

下面的示例生成 C2767，并演示如何修复此错误：

```
// C2767.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>(2,3); // C2767
   array<int> ^p2 = new array<int>(2);   // OK
}
```