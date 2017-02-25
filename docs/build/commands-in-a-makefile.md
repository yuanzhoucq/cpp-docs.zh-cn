---
title: "生成文件中的命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令, 生成文件"
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 生成文件中的命令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果依赖项已过期，则描述块或推理规则指定要运行的命令块。  NMAKE 在运行命令之前显示每个命令，除非使用了 \/S 选项、**.SILENT**、**\!CMDSWITCHES** 或 @。  如果描述块后面没有紧跟命令块，NMAKE 将查找匹配的推理规则。  
  
 命令块包含一个或多个命令，每个命令位于各自的命令行上。  在依赖项（或规则）和命令块之间不能出现空行。  但是可以出现只包含空格或制表符的行；该行被解释为空命令，并且不出现错误。  命令行之间允许有空行。  
  
 命令行以一个或多个空格或制表符开始。  后面紧有换行符的反斜杠 \( \\ \) 在命令中被解释为空格；在行尾使用反斜杠继续下一行命令。  如果反斜杠后紧跟有其他任何字符（包括空格或制表符），则 NMAKE 按原义解释反斜杠。  
  
 无论后面是否紧跟有命令块，前面带分号 \(;\) 的命令可以出现在依赖项行上或推理规则中：  
  
```  
project.obj : project.c project.h ; cl /c project.c  
```  
  
## 您想进一步了解什么？  
 [命令修饰符](../build/command-modifiers.md)  
  
 [文件名部分语法](../build/filename-parts-syntax.md)  
  
 [生成文件中的内联文件](../build/inline-files-in-a-makefile.md)  
  
## 请参阅  
 [NMAKE 参考](../build/nmake-reference.md)