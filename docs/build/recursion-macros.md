---
title: "递归宏 | Microsoft Docs"
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
  - "宏, 递归"
  - "NMAKE 程序, 递归宏"
  - "递归宏"
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 递归宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用递归宏递归调用 NMAKE。  递归会话继承命令行和环境变量宏以及 Tools.ini 信息。  它们不继承生成文件定义的推理规则或 **.SUFFIXES** 和 **.PRECIOUS** 规范。  若要将宏传递到递归 NMAKE 会话，请要么在递归调用之前用 SET 设置环境变量，在命令中为递归调用定义宏，要么在 Tools.ini 中定义宏。  
  
|宏|定义|  
|-------|--------|  
|**MAKE**|最初用于调用 NMAKE 的命令。<br /><br /> $\(MAKE\) 宏提供 nmake.exe 的完整路径。|  
|**MAKEDIR**|调用 NMAKE 时的当前目录。|  
|**MAKEFLAGS**|当前有效的选项。  用作 `/$(MAKEFLAGS)`。注意，未包括 \/F。|  
  
## 请参阅  
 [特殊 NMAKE 宏](../build/special-nmake-macros.md)