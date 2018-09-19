---
title: 编译器错误 C2767 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2767
dev_langs:
- C++
helpviewer_keywords:
- C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6301471b4797bf3a1cb6f3936e54ab8bfb536b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051888"
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