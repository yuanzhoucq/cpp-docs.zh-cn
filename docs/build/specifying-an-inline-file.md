---
title: "指定内联文件 | Microsoft Docs"
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
  - "文件 [C++], 内联"
  - "内联文件 [C++], 指定 NMAKE"
  - "NMAKE 程序, 内联文件"
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 指定内联文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在显示 *filename* 命令中指定两个尖括号\(\<\<\)   尖括号不能是宏展开。  
  
## 语法  
  
```  
<<[filename]  
```  
  
## 备注  
 运行命令时，尖括号由 *filename* 替换（如果已指定），或由 NMAKE 生成的唯一名称替换。  如果指定了 *filename*，它必须跟在尖括号后面，之间没有空格或制表符。  允许使用路径。  不需要或采用扩展名。  如果指定了 *filename*，则在当前目录或指定目录中创建该文件，覆盖现有的任何同名文件；否则在 TMP 目录（如果没有定义 TMP 环境变量，则在当前目录）中创建该文件。  如果重复使用以前的 *filename*，NMAKE 将替换以前的文件。  
  
## 请参阅  
 [生成文件中的内联文件](../build/inline-files-in-a-makefile.md)