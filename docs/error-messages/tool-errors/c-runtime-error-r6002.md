---
title: "C 运行时错误 R6002 | Microsoft Docs"
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
  - "R6002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6002"
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
caps.latest.revision: 10
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C 运行时错误 R6002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未加载浮点支持  
  
 未链接必需的浮点库。  
  
### 通过检查以下可能的原因进行修复  
  
1.  该程序通过选项（如 \/FPi87，该选项要求有协处理器）被编译或链接，但该程序运行在一台未安装协处理器的计算机上。  
  
2.  `printf_s` 或 `scanf_s` 函数的格式字符串包含浮点格式规范，而该程序不包含任何浮点值或变量。  
  
3.  编译器仅当必要时才通过加载浮点支持以最小化程序大小。  编译器无法检测到格式字符串中的浮点格式规范，因此编译器未加载必要的浮点例程。  
  
4.  使用浮点参数以符合浮点格式规范，或在程序的其他地方执行浮点赋值。  该操作将导致加载浮点支持。  
  
5.  在由混合语言编写的程序中，当程序进行链接时在 FORTRAN 库之前指定了 C 库。  重新链接并最后指定 C 库。