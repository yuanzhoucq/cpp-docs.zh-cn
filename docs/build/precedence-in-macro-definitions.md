---
title: 宏定义中的优先级
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 8829b3cdbc7b2324ef3d118f8ca45dd2a1621e7e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619072"
---
# <a name="precedence-in-macro-definitions"></a>宏定义中的优先级

如果宏有多个定义，NMAKE 使用优先级最高的定义。 以下列表显示优先级，按从高到低的顺序：

1. 在命令行上定义的宏

1. 宏生成文件中定义或包含文件

1. 继承的环境变量宏

1. Tools.ini 文件中定义的宏

1. 预定义的宏，如[CC](../build/command-macros-and-options-macros.md)和[AS](../build/command-macros-and-options-macros.md)

使用 /E 使继承从环境变量重写具有相同名称的生成文件宏的宏。 使用 **！UNDEF**重写命令行。

## <a name="see-also"></a>请参阅

[定义 NMAKE 宏](../build/defining-an-nmake-macro.md)