---
title: A.2 指定条件编译 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d8b0f3df67313dbf03d40077a551fe64930199d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393693"
---
# <a name="a2---specifying-conditional-compilation"></a>A.2   指定条件编译

下面的示例说明如何使用条件编译使用 OpenMP 宏`_OPENMP`([2.2 节](../../parallel/openmp/2-2-conditional-compilation.md)第 8 页上)。 与 OpenMP 编译`_OPENMP`将成为定义宏。

```
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

定义预处理器运算符允许多个要测试单个指令中的宏。

```
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```