---
title: "创建内联文件文本 | Microsoft Docs"
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
  - "内联文件, 创建文本"
  - "NMAKE 程序, 内联文件"
  - "文本, 内联文件"
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 创建内联文件文本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

内联文件可以是临时的，也可以是永久的。  
  
## 语法  
  
```  
  
      inlinetext  
.  
.  
.  
<<[KEEP | NOKEEP]  
```  
  
## 备注  
 在命令后的第一行上指定 *inlinetext*。  用两个尖括号\(\<\<\)在单独一行的行首标记结束。  文件包含分隔括号前面的所有 *inlinetext*。  *inlinetext* 可以有宏展开和替换，但是没有指令或生成文件注释。  空格、制表符和换行符按原义处理。  
  
 临时文件在会话期间存在，并可由其他命令重复使用。  在右尖括号后指定 **KEEP** 以在 NMAKE 会话后保留文件；未命名的文件以生成的文件名保留在磁盘上。  为临时文件指定 **NOKEEP** 或什么都不指定。  **KEEP** 和 **NOKEEP** 不区分大小写。  
  
## 请参阅  
 [生成文件中的内联文件](../build/inline-files-in-a-makefile.md)