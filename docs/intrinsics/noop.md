---
title: __noop |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __noop_cpp
- __noop
dev_langs:
- C++
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97820367f0960925dfcac1db339260cd3f52b8bc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430210"
---
# <a name="noop"></a>__noop

**Microsoft 专用**

`__noop`内部函数，则指定应忽略函数和参数列表进行分析，但没有代码生成的自变量。 它被适用于在采用可变数量的参数的全局调试函数中使用。

编译器将为`__noop`0 在编译时的内部。

## <a name="example"></a>示例

下面的代码演示如何使用`__noop`。

```
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[关键字](../cpp/keywords-cpp.md)