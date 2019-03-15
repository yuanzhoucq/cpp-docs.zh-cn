---
title: 描述块
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: da9265d6b0026bb47496d3aa58847824b5d634d2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825109"
---
# <a name="description-blocks"></a>描述块

描述块是由命令块可以依次后接一个依赖关系行：

```
targets... : dependents...
    commands...
```

依赖关系行指定一个或多个目标与零个或多个依赖项。 目标必须是在行的开头。 不允许从一个冒号 （:） 的依赖项的独立目标; 空格或制表符。 若要拆分的行，目标或依赖项之后，使用反斜杠 (\)。 如果目标不存在，具有较早的时间戳比依赖，或者是[伪目标](pseudotargets.md)，NMAKE 执行的命令。 如果依赖于其他位置是目标并不存在或已过期相对于其自己的依赖项，NMAKE 更新当前依赖项之前更新依赖项。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

[目标](targets.md)

[依赖项](dependents.md)

## <a name="see-also"></a>请参阅

[NMAKE 参考](nmake-reference.md)
