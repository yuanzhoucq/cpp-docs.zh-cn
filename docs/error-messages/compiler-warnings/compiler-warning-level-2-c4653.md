---
title: "编译器警告（等级 2）C4653 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4653"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4653"
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 2）C4653
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器选项“option”与预编译头不一致；忽略当前命令行选项  
  
 用“使用预编译头”\([\/Yu](../../build/reference/yu-use-precompiled-header-file.md)\) 选项指定的选项与创建预编译头时指定的选项不一致。  该编译使用的是创建编译头时指定的选项。  
  
 在编译预编译头期间为“包结构”选项 \([\/Zp](../../build/reference/zp-struct-member-alignment.md)\) 指定了不同的值时会出现此警告。