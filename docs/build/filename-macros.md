---
title: "文件名宏 | Microsoft Docs"
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
  - "NMAKE 中的文件名宏"
  - "宏, NMAKE"
  - "NMAKE 程序, 文件名宏"
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 文件名宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文件名宏被预定义为依赖项中指定的文件名（而不是磁盘上的完整文件名指定）。  在调用时不需要将这些宏括在括号内；只需按如下方式指定 $。  
  
|宏|含义|  
|-------|--------|  
|**$@**|当前所指定的当前目标的全名（路径、基名称、扩展名）。|  
|**$$@**|当前所指定的当前目标的全名（路径、基名称、扩展名）。  仅在作为依赖项中的依赖项时有效。|  
|**$\***|当前目标的路径和基名称，没有文件扩展名。|  
|**$\*\***|当前目标的所有依赖项。|  
|**$?**|时间戳比当前目标的时间戳晚的所有依赖项。|  
|**$\<**|时间戳比当前目标的时间戳晚的依赖文件。  仅在推理规则的命令中有效。|  
  
 若要指定部分预定义文件名宏，请追加宏修饰符并将修饰的宏括在括号内。  
  
|修饰符|结果文件名部分|  
|---------|-------------|  
|**D**|驱动器和目录|  
|**B**|基名称|  
|**F**|基名称和扩展名|  
|**R**|驱动器、目录和基名称|  
  
## 请参阅  
 [特殊 NMAKE 宏](../build/special-nmake-macros.md)