---
title: 编译器警告 （等级 2） C4056
ms.date: 11/04/2016
f1_keywords:
- C4056
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
ms.openlocfilehash: 59c66f2f7dcbd1e20463df613b1b7deae6a1c349
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586896"
---
# <a name="compiler-warning-level-2-c4056"></a>编译器警告 （等级 2） C4056

浮点常量算法中溢出

浮点常量算术将生成的结果超出允许的最大值。

此警告可能被引起常数算法期间执行的编译器优化。 如果消失时关闭优化，可以放心地忽略此警告 ([/Od](../../build/reference/od-disable-debug.md))。

下面的示例生成 C4056:

```
// C4056.cpp
// compile with: /W2 /LD
#pragma warning (default : 4056)
float fp_val = 1.0e300 * 1.0e300;   // C4056
```