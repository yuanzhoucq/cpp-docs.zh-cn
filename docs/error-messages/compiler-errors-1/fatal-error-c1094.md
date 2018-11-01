---
title: 错误 C1094
ms.date: 11/04/2016
f1_keywords:
- C1094
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
ms.openlocfilehash: 23891a783a018f6d84ea820af98992f61632984c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469649"
---
# <a name="fatal-error-c1094"></a>错误 C1094

-Zmval1： 命令行选项是与用于生成预编译标头的值不一致 (-Zmval2)

传递到值[/Yc](../../build/reference/yc-create-precompiled-header-file.md)必须是相同的值传递给[/Yu](../../build/reference/yu-use-precompiled-header-file.md) (**/Zm**值必须在所有编译中，使用或创建相同的预编译相同标头文件）。

下面的示例生成 C1094:

```
// C1094.h
int func1();
```

然后，

```
// C1094.cpp
// compile with: /Yc"C1094.h" /Zm200
int u;
int main() {
   int sd = 32;
}
#include "C1094.h"
```

然后，

```
// C1094b.cpp
// compile with: /Yu"C1094.h" /Zm300 /c
#include "C1094.h"   // C1094 compile with /Zm200
void Test() {}
```