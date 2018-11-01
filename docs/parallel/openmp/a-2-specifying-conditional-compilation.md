---
title: A.2   指定条件编译
ms.date: 11/04/2016
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
ms.openlocfilehash: 92ae22ffac1b1a1c3fc45a9a7a883203ff6d251e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491216"
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