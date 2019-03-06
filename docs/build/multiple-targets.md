---
title: 多个目标
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
ms.openlocfilehash: 28ac69a6e724b4e7c6fe838e0de3703cbdf0cfaa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421423"
---
# <a name="multiple-targets"></a>多个目标

NMAKE 评估单个的依赖项中的多个目标就像每个单独的描述块中指定。

例如，以下...

```Output
bounce.exe leap.exe : jump.obj
   echo Building...
```

...是计算如下：

```Output
bounce.exe : jump.obj
   echo Building...
leap.exe : jump.obj
   echo Building...
```

## <a name="see-also"></a>请参阅

[目标](../build/targets.md)
