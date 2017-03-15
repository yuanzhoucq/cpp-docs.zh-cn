---
title: "CL 选项的顺序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, 设置选项"
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# CL 选项的顺序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

选项可出现在 CL 命令行上的任何位置，但 \/link 选项除外，该选项必须出现在最后。  编译器首先处理在 [CL 环境变量](../../build/reference/cl-environment-variables.md)中指定的选项，然后从左到右读取命令行（按它遇到命令文件的顺序处理它们）。  每个选项应用于命令行上的所有文件。  如果 CL 遇到冲突选项，则使用最右边的选项。  
  
## 请参阅  
 [编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)