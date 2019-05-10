---
title: 编译器警告 （等级 2） C4056
ms.date: 11/04/2016
f1_keywords:
- C4056
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
ms.openlocfilehash: 59c66f2f7dcbd1e20463df613b1b7deae6a1c349
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349862"
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