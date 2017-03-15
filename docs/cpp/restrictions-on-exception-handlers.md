---
title: "对于异常处理程序的限制 | Microsoft Docs"
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
  - "限制, 异常处理程序"
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 对于异常处理程序的限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在代码中使用异常处理程序的主要限制是不能使用 `goto` 语句跳转到 `__try` 语句块。  相反，您必须通过常规控制流进入此语句块。  您可随意跳出 `__try` 语句块和嵌套异常处理程序。  
  
## 请参阅  
 [编写异常处理程序](../cpp/writing-an-exception-handler.md)   
 [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)