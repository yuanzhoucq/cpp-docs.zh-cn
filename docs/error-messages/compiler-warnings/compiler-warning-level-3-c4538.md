---
title: 编译器警告（等级 3）C4538
ms.date: 11/04/2016
f1_keywords:
- C4538
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
ms.openlocfilehash: 81634ed45ad7d09a35f8399774920f6445628dee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569359"
---
# <a name="compiler-warning-level-3-c4538"></a>编译器警告（等级 3）C4538

type： 不支持此类型上的 const/volatile 限定符

限定符关键字未正确应用到一个数组。 有关详细信息，请参阅 [数组](../../windows/arrays-cpp-component-extensions.md)。

下面的示例生成 C4538:

```
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```