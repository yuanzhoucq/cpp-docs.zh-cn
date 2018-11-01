---
title: 描述块
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: 214963b5c3f633e8d029cee0500d4bd5fab6ed53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490588"
---
# <a name="description-blocks"></a>描述块

描述块是由命令块可以依次后接一个依赖关系行：

```
targets... : dependents...
    commands...
```

依赖关系行指定一个或多个目标与零个或多个依赖项。 目标必须是在行的开头。 不允许从一个冒号 （:） 的依赖项的独立目标; 空格或制表符。 若要拆分的行，目标或依赖项之后，使用反斜杠 (\)。 如果目标不存在，具有较早的时间戳比依赖，或者是[伪目标](../build/pseudotargets.md)，NMAKE 执行的命令。 如果依赖于其他位置是目标并不存在或已过期相对于其自己的依赖项，NMAKE 更新当前依赖项之前更新依赖项。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

[目标](../build/targets.md)

[依赖项](../build/dependents.md)

## <a name="see-also"></a>请参阅

[NMAKE 参考](../build/nmake-reference.md)