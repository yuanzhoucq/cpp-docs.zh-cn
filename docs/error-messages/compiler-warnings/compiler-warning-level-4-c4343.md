---
title: 编译器警告（等级 4）C4343
ms.date: 11/04/2016
f1_keywords:
- C4343
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
ms.openlocfilehash: acc14d9679aed932b65041bf3eb109a8d0964c89
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683279"
---
# <a name="compiler-warning-level-4-c4343"></a>编译器警告（等级 4）C4343

\#pragma optimize （"g"，off）重写/Og 选项

此警告（仅在 Itanium 处理器系列 (IPF) 编译器中有效）报告 pragma [optimize](../../preprocessor/optimize.md) 重写 [/Og](../../build/reference/og-global-optimizations.md) 编译器选项。

下面的示例生成 C4343：

```cpp
// C4343.cpp
// compile with: /Og /W4 /LD
// processor: IPF
#pragma optimize ("g", off)   // C4343
```