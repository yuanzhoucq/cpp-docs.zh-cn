---
title: 编译器错误 C2748
ms.date: 11/04/2016
f1_keywords:
- C2748
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
ms.openlocfilehash: a85ee151d9a4d62cc4b95248d669ff924365a95a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655632"
---
# <a name="compiler-error-c2748"></a>编译器错误 C2748

创建托管数组或 WinRT 数组时必须提供数组大小或数组初始值设定项

托管数组或 WinRT 数组的格式不正确。 有关详细信息，请参阅 [数组](../../windows/arrays-cpp-component-extensions.md)。

下面的示例生成 C2748，并演示如何修复此错误：

```
// C2748.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>();   // C2748
   // try the following line instead
   array<int> ^p2 = new array<int>(2);
}
```