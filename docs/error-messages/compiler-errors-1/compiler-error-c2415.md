---
title: "编译器错误 C2415 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2415"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2415"
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2415
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不正确的操作数类型  
  
 该操作码不使用此类型的操作数。  
  
### 通过检查以下可能的原因进行修复  
  
1.  该操作码不支持所使用的操作数数目。  检查程序集语言参考手册以确定正确的操作数数目。  
  
2.  较新的处理器支持带有附加类型的指令。  调整选项[\/arch（最小 CPU 体系结构）](../../build/reference/arch-minimum-cpu-architecture.md) 以使用更高版本的处理器。