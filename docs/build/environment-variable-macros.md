---
title: 环境变量宏
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
ms.openlocfilehash: 4691f89f1886b40637a0800ee8a6a94e4b4e06c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594293"
---
# <a name="environment-variable-macros"></a>环境变量宏

NMAKE 继承在会话开始之前存在的环境变量的宏定义。 如果变量在操作系统环境中设置的现在以 NMAKE 宏。 继承的名称转换为大写。 继承在预处理前发生。 /E 选项用于使继承从环境变量重写任何宏，并生成文件中具有相同名称的宏。

在会话中，可以重新定义环境变量宏，这将更改相应的环境变量。 此外可以更改通过 SET 命令的环境变量。 使用 SET 命令在会话中更改环境变量不会更改相应的宏，但是。

例如：

```
PATH=$(PATH);\nonesuch

all:
    echo %PATH%
```

在此示例中，更改`PATH`将更改相应的环境变量`PATH`; 它将追加`\nonesuch`到你的路径。

如果环境变量定义为字符串的语法不正确生成文件中，没有宏创建，并不生成任何警告。 如果变量的值包含美元符号 （$），NMAKE 将其解释为宏调用的开头。 使用宏会导致意外的行为。

## <a name="see-also"></a>请参阅

[特殊 NMAKE 宏](../build/special-nmake-macros.md)