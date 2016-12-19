---
title: "BSCMAKE 如何生成 .Bsc 文件 | Microsoft Docs"
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
  - "浏览信息文件 (.bsc), 生成"
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 如何生成 .Bsc 文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

BSCMAKE 用它最有效的方式生成或重新生成 .bsc 文件。  为了避免潜在的问题，了解生成过程是很重要的。  
  
 当 BSCMAKE 生成浏览信息文件时，它将 .sbr 文件截断为零长度。  在同一文件后面的生成过程中，零长度（或空）的 .sbr 文件通知 BSCMAKE 该 .sbr 文件没有新的信息可提供。  它使 BSCMAKE 获知不需要更新那部分文件，增量编译就足够了。  在每个生成过程中（除非已指定 \/n 选项），BSCMAKE 首先通过只使用那些已更改的 .sbr 文件来尝试增量更新文件。  
  
 BSCMAKE 查找具有用 \/o 选项指定的名称的 .bsc 文件。  如果未指定 \/o，BSCMAKE 则查找具有第一个 .sbr 文件的基名称和 .bsc 扩展名的文件。  如果此文件存在，BSCMAKE 只使用提供信息的 .sbr 文件来执行浏览信息文件的增量编译。  如果此文件不存在，BSCMAKE 则使用所有 .sbr 文件执行完全编译。  编译规则如下：  
  
-   若要使完全编译成功，所有指定的 .sbr 文件都必须存在并且都必须未截断。  如果某个 .sbr 文件被截断，则在运行 BSCMAKE 前必须重新生成此文件（通过重新编译或汇编）。  
  
-   若要使增量编译成功，.bsc 文件必须存在。  所有提供信息的 .sbr 文件（甚至空文件）都必须存在并且都必须在 BSCMAKE 命令行指定。  如果从命令行省略某个 .sbr 文件，则 BSCMAKE 将从此文件中移除其提供的信息。  
  
## 请参阅  
 [生成 .Bsc 文件](../../build/reference/building-a-dot-bsc-file.md)