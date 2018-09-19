---
title: 资源编译器错误 RW2001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2001
dev_langs:
- C++
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f401ce7c9a96cfeecf195b8872a704b8b1291939
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114977"
---
# <a name="resource-compiler-error-rw2001"></a>资源编译器错误 RW2001

预处理过的 RC 文件中的指令无效

RC 文件包含 **#pragma**指令。

使用 **#ifndef**预处理器指令与**RC_INVOKED**常量资源编译器定义时它可以处理的包含文件。 位置 **#pragma**指令的不是代码块中处理时**RC_INVOKED**定义常量。 仅由 C/c + + 编译器，而不是由资源编译器处理代码块中。 下面的示例代码演示了此种方法：

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma**预处理器指令没有任何意义。RC 文件。 **#Include**中经常使用预处理器指令。RC 文件以包括标头文件 （基于项目的自定义标头文件或使用其产品的一个由 Microsoft 提供的标准标头文件）。 其中包括文件包含 **#pragma**指令。 由于标头文件可以包括一个或多个其他标头文件，包含有问题的文件 **#pragma**指令可能不会即时显现。

**#Ifndef RC_INVOKED**技术包括基于项目的标头文件中的标头文件可以控制。