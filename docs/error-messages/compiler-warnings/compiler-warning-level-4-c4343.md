---
title: 编译器警告（等级 4）C4343
ms.date: 11/04/2016
f1_keywords:
- C4343
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
ms.openlocfilehash: c8f0bb514a3da932500f986e50a20af0947827c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403982"
---
# <a name="compiler-warning-level-4-c4343"></a>编译器警告（等级 4）C4343

\#杂注 optimize("g",off) 重写 /Og 选项

此警告（仅在 Itanium 处理器系列 (IPF) 编译器中有效）报告 pragma [optimize](../../preprocessor/optimize.md) 重写 [/Og](../../build/reference/og-global-optimizations.md) 编译器选项。

下面的示例生成 C4343：

```
// C4343.cpp
// compile with: /Og /W4 /LD
// processor: IPF
#pragma optimize ("g", off)   // C4343
```