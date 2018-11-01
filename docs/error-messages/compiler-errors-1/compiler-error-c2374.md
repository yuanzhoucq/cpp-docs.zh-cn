---
title: 编译器错误 C2374
ms.date: 11/04/2016
f1_keywords:
- C2374
helpviewer_keywords:
- C2374
ms.assetid: 73b51965-e91c-4e21-9732-f71c1449d22e
ms.openlocfilehash: 44f2d9d8c80af2111e7c63d976ef39cfa4809e48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483299"
---
# <a name="compiler-error-c2374"></a>编译器错误 C2374

“identifier”：重定义；多次初始化

不止一次初始化了标识符。

下面的示例生成 C2374：

```
// C2374.cpp
// compile with: /c
int i = 0;
int i = 1;   // C2374
int j = 1;   // OK
```