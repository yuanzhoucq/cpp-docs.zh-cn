---
title: "运行 NMAKE | Microsoft Docs"
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
  - "命令文件"
  - "命令文件, NMAKE"
  - "NMAKE 程序, 运行"
  - "NMAKE 程序, 目标"
  - "响应文件, NMAKE"
  - "目标"
  - "目标, 生成"
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 运行 NMAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
NMAKE [option...] [macros...] [targets...] [@commandfile...]  
```  
  
## 备注  
 NMAKE 只生成指定的 *targets*；如果未指定，则生成生成文件中的第一个目标。  第一个生成文件目标可以是生成其他目标的[伪目标](../build/pseudotargets.md)。  NMAKE 使用指定 \/F 选项的生成文件；如果未指定 \/F 选项，则使用当前目录下的生成文件。  如果未指定生成文件，则 NMAKE 使用推理规则生成命令行 *targets*。  
  
 `commandfile` 文本文件（或响应文件）包含命令行输入。  其他输入可以位于 @`commandfile` 之前或之后。  允许使用路径。  在 `commandfile` 中，换行符被视为空格。  如果宏定义包含空格，则将宏定义用引号引起来。  
  
## 您想进一步了解什么？  
 [NMAKE 选项](../build/nmake-options.md)  
  
 [Tools.ini 和 NMAKE](../build/tools-ini-and-nmake.md)  
  
 [从 NMAKE 退出代码](../build/exit-codes-from-nmake.md)  
  
## 请参阅  
 [NMAKE 参考](../build/nmake-reference.md)