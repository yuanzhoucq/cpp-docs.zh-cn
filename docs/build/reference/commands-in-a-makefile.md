---
title: 生成文件中的命令
ms.date: 11/04/2016
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
ms.openlocfilehash: fcb8737070931cf95d7bfb3971a84e22c7ad70a4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824473"
---
# <a name="commands-in-a-makefile"></a>生成文件中的命令

描述块或推理规则指定要运行如果依赖项已过期的命令块。 NMAKE 之前，将显示每个命令运行它，除非 /S， **。无提示**， **！CMDSWITCHES**，或\@使用。 如果描述块未遵循由命令块，NMAKE 查找匹配的推断规则。

命令块包含一个或多个命令，在其对应行的每个命令。 依赖项或规则与命令块之间可以显示没有空白的行。 但是，可以显示包含仅空格或制表符的行;这行解释为一个空的命令，并且不会出现错误。 允许命令行之间有空行。

命令行开始用一个或多个空格或制表符。 换行字符后跟一个反斜杠 (\) 被解释为命令; 中的空间在行尾使用反斜杠以继续到下一行上的命令。 NMAKE 按原义解释反斜杠如果任何其他字符，包括空格或选项卡上后, 跟反斜杠。

命令前面加一个分号 （;） 是否紧跟命令块中显示的一个依赖项的行或推理规则：

```
project.obj : project.c project.h ; cl /c project.c
```

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

[命令修饰符](command-modifiers.md)

[文件名部分语法](filename-parts-syntax.md)

[生成文件中的内联文件](inline-files-in-a-makefile.md)

## <a name="see-also"></a>请参阅

[NMAKE 参考](nmake-reference.md)
