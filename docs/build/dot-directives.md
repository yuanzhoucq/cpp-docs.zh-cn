---
title: "点指令 | Microsoft Docs"
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
  - "NMAKE 中的点指令"
  - "NMAKE 程序, 点指令"
ms.assetid: ab35da65-30b6-48b7-87d6-61503d7faf9f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 点指令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在描述块之外的行首指定点指令。  点指令以一个句点 \( .\) 开头，后跟一个冒号 \(:\)。  允许使用空格或制表符。  点指令名区分大小写并且应为大写。  
  
|指令|用途|  
|--------|--------|  
|**.IGNORE :**|忽略从指定该指令的位置到生成文件末尾之间，由命令返回的非零退出代码。  默认情况下，如果命令返回非零退出代码，NMAKE 将暂停。  若要还原错误检查，请使用 **\!CMDSWITCHES**。  若要忽略单个命令的退出代码，请使用短划线 \(\-\) 修饰符。  若要忽略整个文件的退出代码，请使用 \/I 选项。|  
|**.PRECIOUS :** *targets*|若更新 *targets* 的命令暂停，则将其保留在磁盘上；若命令通过删除文件处理中断，则该指令无效。  用一或多个空格或制表符分隔目标名称。  默认情况下，如果通过使用 Ctrl\+C 或 Ctrl\+Break 组合键中断生成，NMAKE 将删除目标。  **.PRECIOUS** 的每一次使用都应用于整个生成文件；多次指定是累计的。|  
|**.SILENT :**|取消从指定该指令的位置到生成文件末尾之间的已执行命令的显示。  默认情况下，NMAKE 显示它调用的命令。  若要还原回显，请使用 **\!CMDSWITCHES**。  若要取消单个命令的回显，请使用 **@** 修饰符。  若要取消整个文件的回显，请使用 \/S 选项。|  
|**.SUFFIXES :** `list`|列出推理规则匹配的扩展名；预定义包括以下扩展名：.exe .obj .asm .c .cpp .cxx .bas .cbl .for .pas .res .rc .f .f90|  
  
 若要更改 **.SUFFIXES** 列表顺序或指定新列表，请清除此列表并指定新的设置。  若要清除此列表，请不要在冒号后指定扩展名：  
  
```  
.SUFFIXES :  
```  
  
 若要将其他后缀添加到列表的末尾，请指定  
  
```  
.SUFFIXES : suffixlist  
```  
  
 其中 *suffixlist* 是附加后缀的列表，由一或多个空格或制表符分隔。  若要查看 **.SUFFIXES** 的当前设置，请运行选项为 \/P 的 NMAKE。  
  
## 请参阅  
 [NMAKE 参考](../build/nmake-reference.md)