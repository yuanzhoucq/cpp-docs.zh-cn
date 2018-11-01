---
title: 错误 C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: e2309b93be65b049c35abf96572e144a0a518007
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614274"
---
# <a name="fatal-error-c1017"></a>错误 C1017

无效的整数常量表达式

中的表达式`#if`指令不存在或计算结果不为常量。

定义使用的常量`#define`必须具有值，如果中使用的计算结果为整数常量`#if`， `#elif`，或`#else`指令。

下面的示例生成 C1017:

```
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

可能的解决方法：

```
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

因为`CONSTANT_NAME`计算结果为一个字符串，而不是整数，`#if`指令生成错误 C1017。

在其他情况下，预处理器计算未定义的常数为零。 这会导致意外的结果，如下面的示例中所示。 `YES` 未定义，因此它的计算结果为零。 表达式`#if``CONSTANT_NAME`的计算结果为 false，并且将使用在代码`YES`由预处理器删除。 `NO` 为还未定义 （零），因此`#elif``CONSTANT_NAME==NO`计算结果为 true (`0 == 0`)，从而导致预处理器将中的代码`#elif`语句部分 — 完全相反的预期行为。

```
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

若要查看完全编译器如何处理预处理器指令，请使用[/P](../../build/reference/p-preprocess-to-a-file.md)， [/E](../../build/reference/e-preprocess-to-stdout.md)，或[/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)。