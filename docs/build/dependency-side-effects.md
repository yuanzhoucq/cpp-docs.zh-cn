---
title: 依赖项副作用
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
ms.openlocfilehash: 1479fac4defa45545ffd06ab30fd53ae0c2506af
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422632"
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
