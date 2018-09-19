---
title: 编译器警告 （等级 2） C4056 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4056
dev_langs:
- C++
helpviewer_keywords:
- C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e069867d4aef749f9f6e42f46a34745d9e8aa62
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067502"
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