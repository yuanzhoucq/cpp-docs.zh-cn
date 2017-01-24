---
title: "BSCMAKE 命令行 | Microsoft Docs"
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
  - "BSCMAKE, 命令行"
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 命令行
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要运行 BSCMAKE，请使用下列命令行语法：  
  
```  
BSCMAKE [options] sbrfiles  
```  
  
 选项只能出现在命令行的 `options` 字段中。  
  
 *sbrfiles* 字段指定一个或多个由编译器或汇编程序创建的 .sbr 文件。  用空格或制表符分隔 .sbr 文件名。  必须指定扩展名；没有默认扩展名。  可以用文件名指定路径，也可以使用操作系统通配符（\* 和 ?）。  
  
 在增量编译过程中，可以指定不是原始生成部分的新 .sbr 文件。  如果要使所有提供的信息都保留在浏览信息文件中，必须指定最初用于创建 .bsc 文件的所有 .sbr 文件（包括被截断的文件）。  如果省略某个 .sbr 文件，则该文件在浏览信息文件中提供的信息将被移除。  
  
 不要为完全编译指定截断的 .sbr 文件。  完全编译需要所有指定的 .sbr 文件提供的信息。  在执行完全编译之前，重新编译项目并为每个空文件新建一个 .sbr 文件。  
  
 下列命令运行 BSCMAKE，从三个 .sbr 文件生成一个称为 MAIN.bsc 的文件：  
  
```  
BSCMAKE main.sbr file1.sbr file2.sbr  
```  
  
 有关相关信息，请参见 [BSCMAKE 命令文件](../../build/reference/bscmake-command-file-response-file.md)和 [BSCMAKE 选项](../../build/reference/bscmake-options.md)。  
  
## 请参阅  
 [BSCMAKE 参考](../../build/reference/bscmake-reference.md)