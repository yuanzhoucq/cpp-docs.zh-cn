---
title: "编译器错误 C2414 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2414"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2414"
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2414
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非法的操作数数目  
  
### 通过检查以下可能的原因进行修复  
  
1.  该操作码不支持所使用的操作数数目。  检查程序集语言参考手册以确定正确的操作数数目。  
  
2.  较新的处理器支持具有不同操作数数目的指令。  调整选项[\/arch（最小 CPU 体系结构）](../../build/reference/arch-minimum-cpu-architecture.md) 以使用更高版本的处理器。