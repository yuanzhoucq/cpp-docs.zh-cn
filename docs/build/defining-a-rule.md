---
title: "定义规则 | Microsoft Docs"
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
  - "定义推理规则"
  - "NMAKE 程序, 推理规则"
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 定义规则
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*fromext* 表示依赖文件的扩展名，*toext* 表示目标文件的扩展名。  
  
```  
.fromext.toext:  
   commands  
```  
  
## 备注  
 扩展名不区分大小写。  可以调用宏来表示 *fromext* 和 *toext*；宏在预处理期间展开。  *fromext* 前的句点 \(.\) 必须出现在行首。  冒号 \(:\) 前面是零个或零个以上的空格或制表符。  后面只能跟空格或制表符、分号 \(;\)（用于指定命令）、数字符号 \(\#\)（用于指定注释）或换行符。  不允许使用其他的空格。  和在描述块中一样指定命令。  
  
## 您想进一步了解什么？  
 [规则中的搜索路径](../build/search-paths-in-rules.md)  
  
## 请参阅  
 [推理规则](../build/inference-rules.md)