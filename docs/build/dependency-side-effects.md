---
title: 依赖项副作用 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a70df679434b187bc2eee4eb4aad5881db0da1c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716506"
---
# <a name="dependency-side-effects"></a>依赖项副作用

如果使用冒号 （:） 在不同位置中的两个依赖关系行中指定的目标和命令显示在行之一后，NMAKE 将解释依赖项，如同相邻或组合。 它不会调用没有命令，而是改为假定依赖项属于一个描述块，并执行与其他依赖项指定的命令的依赖关系的推理规则。 例如，此设置的规则：

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

计算如下：

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

这种效果，则不会使用两个冒号 (`::`) 使用。 例如，此设置的规则：

```Output
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

计算如下：

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

## <a name="see-also"></a>请参阅

[目标](../build/targets.md)