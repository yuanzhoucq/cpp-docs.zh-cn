---
title: 必需和可选的头文件 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.headers
dev_langs:
- C++
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afd523bad5d70cdfc80a6e8a532b2409be535c6b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091863"
---
# <a name="required-and-optional-header-files"></a>必需和可选的头文件

每个运行时例程的说明包括一个针对该例程的必选和可选包含文件或标头 (.H) 文件的列表。 需包括必需的标头文件以获取此例程的函数声明或由另一个内部调用的例程使用的定义。 通常包括可选标头文件以利用预定义的常量、类型定义或内联宏。 下表列出了可选标头内容的一些示例：

|定义|示例|
|----------------|-------------|
|宏定义|如果将库例程作为宏实现，则宏定义可能在原始例程的标头文件之外的其他标头文件中。 例如，在标头文件 CTYPE.H 中定义 `_toupper` 宏，而在 STDLIB.H 中声明函数 `toupper`。|
|预定义的常量|许多库例程都引用在标头文件中定义的常量。 例如，`_open` 例程使用常量，如在标头文件 FCNTL.H 中定义的 `_O_CREAT`。|
|类型定义|某些库例程返回结构或将结构用作参数。 例如，流输入/输出例程使用在 STDIO.H 中定义的 `FILE` 类型的结构。|

运行库标头文件提供 ANSI/ISO C 标准推荐样式的函数声明。 编译器对在其关联的函数声明后发生的任何例程引用执行类型检查。 函数声明对于返回默认的 `int` 类型之外的其他类型的值的例程尤为重要。 未在其声明中指定适当的返回值的例程将由编译器用来返回 `int`，这可能导致出现意外结果。 有关详细信息，请参阅[类型检查](../c-runtime-library/type-checking-crt.md)。

## <a name="see-also"></a>请参阅

[CRT 库功能](../c-runtime-library/crt-library-features.md)