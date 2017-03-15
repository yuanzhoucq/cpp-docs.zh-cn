---
title: "环境变量宏 | Microsoft Docs"
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
  - "环境变量, NMAKE 中的宏"
  - "宏, 环境变量"
  - "NMAKE 程序, 环境变量宏"
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 环境变量宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE 继承会话开始前就存在的环境变量的宏定义。  如果变量是在操作系统环境中设置的，则可以用作 NMAKE 宏。  继承的名称被转换为大写。  继承在预处理前发生。  使用 \/E 选项使从环境变量继承的宏重写生成文件中的任何同名宏。  
  
 可以在会话中重新定义环境变量宏，这将更改相应的环境变量。  还可以用 SET 命令更改环境变量。  但是，使用 SET 命令更改会话中的环境变量不会更改相应的宏。  
  
 例如：  
  
```  
PATH=$(PATH);\nonesuch  
  
all:  
    echo %PATH%  
```  
  
 在该示例中，更改 `PATH` 从而更改了相应的环境变量 `PATH`；它将 `\nonesuch` 追加到路径中。  
  
 如果为环境变量定义的字符串的语法在生成文件中不正确，则没有宏创建，也没有警告生成。  如果变量的值包含美元符号 \($\)，则 NMAKE 将它解释为宏调用的开始。  使用宏会导致意外行为。  
  
## 请参阅  
 [特殊 NMAKE 宏](../build/special-nmake-macros.md)