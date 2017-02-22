---
title: "数学错误 M6110 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6110"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6110"
ms.assetid: aac9ae37-6a6d-46e9-85d4-dfe03f1c3e11
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 数学错误 M6110
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆栈溢出（Stack Overflow）  
  
 浮点表达式导致浮点堆栈溢出。  
  
 除 8087\/287\/387 协处理器通常支持的八个级别外，还可以捕获最多七个级别的堆栈溢出浮点异常。  
  
 程序以退出代码 138 终止。