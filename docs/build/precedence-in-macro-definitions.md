---
title: "宏定义中的优先级 | Microsoft Docs"
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
  - "宏, 优先级"
  - "NMAKE 程序, 宏定义中的优先级"
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 宏定义中的优先级
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果宏有多个定义，NMAKE 使用优先级最高的一个。  以下列表由高至低显示了优先级的顺序：  
  
1.  在命令行上定义的宏  
  
2.  在生成文件或包含文件中定义的宏  
  
3.  继承的环境变量宏  
  
4.  在 Tools.ini 文件中定义的宏  
  
5.  预定义的宏，如 [CC](../build/command-macros-and-options-macros.md) 和 [As](../build/command-macros-and-options-macros.md)  
  
 使用 \/E 选项使从环境变量中继承的宏重写同名的生成文件宏。  使用 **\!UNDEF** 重写命令行。  
  
## 请参阅  
 [定义 NMAKE 宏](../build/defining-an-nmake-macro.md)