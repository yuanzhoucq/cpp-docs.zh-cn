---
title: "命令修饰符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令修饰符"
  - "NMAKE 程序, 命令修饰符"
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 命令修饰符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以在命令前面指定一个或多个命令修饰符，可以选择用空格或制表符将其分隔。  与命令一样，修饰符也必须缩进。  
  
|修饰符|用途|  
|---------|--------|  
|@*command*|防止显示命令。  不取消命令显示。  默认情况下，NMAKE 回显所有已执行的命令。  使用 \/S 选项取消显示整个生成文件；使用 **.SILENT** 取消显示部分生成文件。|  
|**–**\[`number` \]*命令*|关闭 *command* 的错误检查。  默认情况下，当命令返回非零退出代码时，NMAKE 暂停。  如果使用 \-`number`，当退出代码超过 `number` 时，NMAKE 停止。  空格或制表符不能出现在短划线和*数字之间。*`number` 和*命令* 之间必须出现至少一个空格或制表符。  使用 \/I 选项关闭整个生成文件的错误检查；使用 **.IGNORE** 关闭部分生成文件的错误检查。|  
|**\!** *命令*|如果 *command* 使用 **$\*\***（依赖项中的所有依赖文件）或 **$?**，则为每个依赖文件执行 *command*。（依赖项中时间戳比目标的时间戳晚的所有依赖文件）。|  
  
## 请参阅  
 [生成文件中的命令](../build/commands-in-a-makefile.md)