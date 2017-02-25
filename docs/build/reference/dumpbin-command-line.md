---
title: "DUMPBIN 命令行 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "dumpbin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DUMPBIN 程序, 命令行"
ms.assetid: e6ad17d3-965d-41aa-9dfd-75bb073718d4
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# DUMPBIN 命令行
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要运行 DUMPBIN，请使用下列语法：  
  
```  
DUMPBIN [options] files...  
```  
  
 指定一个或多个二进制文件，以及控制信息所需的任何选项。  DUMPBIN 将该信息显示到标准输出。  可以将输出重定向到文件，或者使用 \/OUT 选项为输出指定文件名。  
  
 当在文件上运行 DUMPBIN 但未指定选项时，DUMPBIN 显示 \/SUMMARY 输出。  
  
 当键入命令 `dumpbin` 但没有任何其他命令行输入时，DUMPBIN 显示汇总其选项的用法语句。  
  
## 请参阅  
 [C\/C\+\+ 生成工具](../../build/reference/c-cpp-build-tools.md)   
 [DUMPBIN 参考](../../build/reference/dumpbin-reference.md)