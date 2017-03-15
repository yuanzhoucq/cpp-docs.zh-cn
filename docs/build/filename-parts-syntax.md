---
title: "文件名部分语法 | Microsoft Docs"
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
  - "NMAKE 中的文件名部分语法"
  - "NMAKE 程序, 语法"
  - "语法, 文件名部分"
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 文件名部分语法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命令中的文件名部分语法表示第一个依赖项文件名（可能为暗含的依赖项）的组成部分。  文件名组成部分是为文件指定的（而不是它在磁盘上存在的）驱动器、路径、基名称和扩展名。  使用 **%s** 表示完整文件名。  使用 **%&#124;**\[*parts*\]**F**（百分号后面跟着一个竖线字符）表示部分文件名，其中 *parts* 可以是零个或多个下列字母（按任意顺序排列）。  
  
|Letter|说明|  
|------------|--------|  
|无字母|完整名称（等同于 **%s**）|  
|**d**|驱动器|  
|**p**|路径|  
|**f**|文件基名称|  
|**e**|文件扩展名|  
  
 例如，如果文件名为 c:\\prog.exe，则：  
  
-   %s 将为 c:\\prog.exe  
  
-   %&#124;F 将为 c:\\prog.exe  
  
-   %&#124;dF 将为 c  
  
-   %&#124;pF 将为 c:\\  
  
-   %&#124;fF 将为 prog  
  
-   %&#124;eF 将为 exe  
  
## 请参阅  
 [生成文件中的命令](../build/commands-in-a-makefile.md)