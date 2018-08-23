---
title: 生成文件中的命令 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99e1eb5b4800ff1046ca60d4d4874d386809e2e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366869"
---
# <a name="commands-in-a-makefile"></a>生成文件中的命令
描述块或推理规则指定的命令在依赖项已过期时要运行的块。 NMAKE 每个命令将在之前显示运行它，除非 /s 选项、 **。无提示**， **！CMDSWITCHES**，或使用 @。 如果描述块不跟命令块，NMAKE 查找匹配的推理规则。  
  
 命令块包含一个或多个命令，在其对应行的每个命令。 依赖项或规则和命令块之间可以显示没有空白的行。 但是，可以显示包含仅空格或制表符的行;此行将被解释为一个空的命令，且不发生错误。 允许命令行之间有空行。  
  
 命令行开始用一个或多个空格或制表符。 反斜杠 (\) 后跟一个换行符字符解释为命令; 空格在行的末尾使用反斜杠以继续到下一步的行的命令。 NMAKE 按原义解释反斜杠如果任何其他字符，包括空格或制表符后, 跟反斜杠。  
  
 命令前面由分号 （;） 是否紧跟命令块可以出现在依赖关系行或推理规则：  
  
```  
project.obj : project.c project.h ; cl /c project.c  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
 [命令修饰符](../build/command-modifiers.md)  
  
 [文件名部分语法](../build/filename-parts-syntax.md)  
  
 [生成文件中的内联文件](../build/inline-files-in-a-makefile.md)  
  
## <a name="see-also"></a>请参阅  
 [NMAKE 参考](../build/nmake-reference.md)