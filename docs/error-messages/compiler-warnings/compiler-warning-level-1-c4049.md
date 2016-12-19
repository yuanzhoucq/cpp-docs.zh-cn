---
title: "编译器警告（等级 1）C4049 | Microsoft Docs"
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
  - "C4049"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4049"
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4049
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器限制 : 显示终止行号  
  
 文件包含的源行多于 16,777,215 \(2<sup>24</sup>\-1\)。  编译器在 16,777,215 处停止编号。  
  
 对于在行 16,777,215 之后的代码：  
  
-   映像将不包含这些行号的任何调试信息。  
  
-   报告某些诊断时可能使用了错误的行号。  
  
-   .asm 列表 \(\/FAs\) 可能具有错误行号。