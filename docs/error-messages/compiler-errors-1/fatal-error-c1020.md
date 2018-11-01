---
title: 错误 C1020
ms.date: 11/04/2016
f1_keywords:
- C1020
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
ms.openlocfilehash: bdd7a6c87b0e00bd7bef174b8daf0e16cc488a5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469805"
---
# <a name="fatal-error-c1020"></a>错误 C1020

意外的 #endif

`#endif` 指令有没有匹配的 `#if`、 `#ifdef`或 `#ifndef` 指令。 确保每个 `#endif` 具有匹配的指令。

下面的示例生成 C1020：

```
// C1020.cpp
#endif     // C1020
```

可能的解决方法：

```
// C1020b.cpp
// compile with: /c
#if 1
#endif
```