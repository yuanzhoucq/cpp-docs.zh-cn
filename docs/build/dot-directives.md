---
title: "点指令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, dot directives
- dot directives in NMAKE
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9958b13a6f06b0024ec2d4dd304abfe93b16741e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dot-directives"></a>点指令
指定描述块，在行的开头之外的点指令。 点指令以句点开头 (。 ) 后, 跟一个冒号 （:）。 允许使用空格和选项卡。 点指令名称区分大小写并且应为大写。  
  
|指令|目标|  
|---------------|-------------|  
|**.忽略：**|将忽略由命令，从指定的生成文件的末尾的位置返回非零退出代码。 默认情况下，如果 NMAKE 将暂停命令返回非零退出代码。 若要还原错误检查，请使用**！CMDSWITCHES**。 若要忽略为单个命令的退出代码，请使用短划线 （-） 修饰符。 若要忽略对整个文件的退出代码，请使用 / 我。|  
|**.宝贵：** *目标*|保留*目标*磁盘上如果暂停命令来更新它们; 如果不起作用命令处理中断通过删除的文件。 用一个或多个空格或制表符分隔的目标名称。 默认情况下，NMAKE 删除目标，如果生成中断按 CTRL + C 或 CTRL + BREAK。 每次使用**。宝贵**适用于整个生成文件; 多个规范是累积。|  
|**.无提示：**|取消显示执行命令，从指定的生成文件的末尾的位置。 默认情况下，NMAKE 显示它调用的命令。 若要还原回显，请使用**！CMDSWITCHES**。 若要取消回显的单个命令，请使用 **@** 修饰符。 若要取消整个文件的回显，请使用 /s 选项。|  
|**.后缀：**`list`|列出推理规则匹配; 的扩展预定义以包括以下扩展：.exe.obj.asm.c.cpp.cxx.bas.cbl。 对于.pas.res.rc.f.f90|  
  
 若要更改**。后缀**列表顺序，或若要指定新列表，请清除列表中，并指定新的设置。 若要清除列表中，指定位于冒号后没有扩展：  
  
```  
.SUFFIXES :  
```  
  
 若要将其他后缀添加到列表的末尾，指定  
  
```  
.SUFFIXES : suffixlist  
```  
  
 其中*suffixlist*是其他后缀，用一个或多个空格或制表符分隔的列表。 若要查看的当前设置**。后缀**，使用 /P.运行 NMAKE  
  
## <a name="see-also"></a>请参阅  
 [NMAKE 参考](../build/nmake-reference.md)