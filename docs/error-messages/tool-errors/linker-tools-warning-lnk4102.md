---
title: "链接器工具警告 LNK4102 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4102"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4102"
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接器工具警告 LNK4102
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

导出删除的析构函数“name”；映像可能不能正确运行  
  
 程序尝试导出删除析构函数。  产生的删除操作可能会跨 DLL 边界进行，以便进程可以释放不属于它的内存。  请确保给定的符号未在 .def 文件中列出，并且该符号未作为链接器命令行中 **\/IMPORT** 或 **\/EXPORT** 选项的参数列出。  
  
 如果您正在重新生成 C 运行库，则可以忽略此消息。