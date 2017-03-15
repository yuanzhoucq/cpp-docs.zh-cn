---
title: "编写异常处理程序 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "异常处理, 异常处理程序"
  - "结构化异常处理, 异常处理程序"
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 编写异常处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

异常处理程序通常用于响应特定错误。  您可以使用异常处理语法筛选出您不知道如何处理的所有异常。  其他异常应该传递到为了查找特定异常而编写的其他处理程序（可能在运行库或操作系统中）。  
  
 异常处理程序使用 try\-except 语句。  
  
## 您想进一步了解什么？  
  
-   [try\-except 语句](../cpp/try-except-statement.md)  
  
-   [编写异常筛选器](../cpp/writing-an-exception-filter.md)  
  
-   [引发软件异常](../cpp/raising-software-exceptions.md)  
  
-   [硬件异常](../cpp/hardware-exceptions.md)  
  
-   [对异常处理程序的限制](../cpp/restrictions-on-exception-handlers.md)  
  
## 请参阅  
 [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)