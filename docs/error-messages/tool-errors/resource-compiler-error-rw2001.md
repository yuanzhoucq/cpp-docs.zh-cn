---
title: 资源编译器错误 RW2001
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: 900bfed9d57af0f6f5dd8fac19380bb7c382addc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190737"
---
# <a name="resource-compiler-error-rw2001"></a>资源编译器错误 RW2001

预处理后的 RC 文件中的指令无效

RC 文件包含一个 **#pragma**指令。

将 **#ifndef**预处理器指令与资源编译器在处理包含文件时定义的**RC_INVOKED**常数一起使用。 将 **#pragma**指令放在定义**RC_INVOKED**常数时未处理的代码块中。 块中的代码仅由 C/C++编译器处理，而不是由资源编译器处理。 下面的示例代码演示了此方法：

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma**预处理器指令在中没有意义。RC 文件。 **#Include**预处理器指令经常在中使用。RC 文件，其中包含一个标头文件（基于项目的自定义标头文件或由 Microsoft 提供的一种标准头文件，其中包含其中一种产品）。 其中一些包含文件包含 **#pragma**指令。 因为标头文件可以包含一个或多个其他标头文件，所以包含有问题的 **#pragma**指令的文件可能不会立即被察觉。

**#Ifndef RC_INVOKED**技术可以控制在基于项目的头文件中包含头文件。
