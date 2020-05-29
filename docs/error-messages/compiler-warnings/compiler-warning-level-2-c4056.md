---
title: 编译器警告（等级2） C4056
ms.date: 11/04/2016
f1_keywords:
- C4056
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
ms.openlocfilehash: 6046c41bfe9d787732a2cbd50ce3b0d0d9fdb26f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174344"
---
# <a name="compiler-warning-level-2-c4056"></a>编译器警告（等级2） C4056

浮点常量算术溢出

浮点常量算法生成的结果超出了允许的最大值。

此警告可能是由于在常量算法期间执行了编译器优化导致的。 如果关闭优化（[/od](../../build/reference/od-disable-debug.md)），则可以安全地忽略此警告。

下面的示例生成 C4056：

```cpp
// C4056.cpp
// compile with: /W2 /LD
#pragma warning (default : 4056)
float fp_val = 1.0e300 * 1.0e300;   // C4056
```
