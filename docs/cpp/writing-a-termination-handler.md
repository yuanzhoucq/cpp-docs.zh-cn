---
title: "编写终止处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "异常处理, 终止处理程序"
  - "异常, 终止"
  - "处理程序"
  - "处理程序, 终止"
  - "结构化异常处理, 终止处理程序"
  - "终止处理程序"
  - "终止处理程序, 写入"
  - "try-catch 关键字 [C++], 终止处理程序"
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 编写终止处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

与异常处理程序不同，无论代码的受保护块是否已正常终止，终止处理程序总是会执行。  终止处理程序的唯一用途应该是确保无论代码的节如何完成执行，内存、句柄和文件等资源都能正确关闭。  
  
 终止处理程序使用 try\-finally 语句。  
  
## 您想进一步了解什么？  
  
-   [try\-finally 语句](../cpp/try-finally-statement.md)  
  
-   [清理资源](../cpp/cleaning-up-resources.md)  
  
-   [异常处理的操作的计时](../cpp/timing-of-exception-handling-a-summary.md)  
  
-   [终止处理程序的限制](../cpp/restrictions-on-termination-handlers.md)  
  
## 请参阅  
 [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)