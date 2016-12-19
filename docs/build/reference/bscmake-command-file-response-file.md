---
title: "BSCMAKE 命令文件（响应文件） | Microsoft Docs"
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
  - "BSCMAKE, 命令文件"
  - "BSCMAKE, 响应文件"
  - "命令文件"
  - "命令文件, BSCMAKE"
  - "响应文件"
  - "响应文件, BSCMAKE"
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 命令文件（响应文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以在命令文件中提供部分或全部命令行输入。  用下面的语法指定命令文件：  
  
```  
BSCMAKE @filename  
```  
  
 只有一个命令文件允许使用。  可以用 *filename* 指定路径。  在 *filename* 前使用 at 符号 \(@\)。  BSCMAKE 不采用扩展名。  可以在命令行上 *filename* 之后指定附加 *sbrfile*。  命令文件是文本文件，包含 BSCMAKE 的输入，顺序和您在命令行上指定时的顺序相同。  用一或多个空格、制表符或换行符分隔命令行参数。  
  
 下面的命令使用命令文件调用 BSCMAKE：  
  
```  
BSCMAKE @prog1.txt  
```  
  
 下面是一个示例命令文件：  
  
```  
/n /v /o main.bsc /El  
/S (  
toolbox.h  
verdate.h c:\src\inc\screen.h  
)  
file1.sbr file2.sbr file3.sbr file4.sbr  
```  
  
## 请参阅  
 [BSCMAKE 参考](../../build/reference/bscmake-reference.md)