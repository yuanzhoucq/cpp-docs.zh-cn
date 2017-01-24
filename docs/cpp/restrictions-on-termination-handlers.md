---
title: "对于终止处理程序的限制 | Microsoft Docs"
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
  - "限制, 终止处理程序"
  - "终止处理程序, 限制"
  - "try-catch 关键字 [C++], 终止处理程序"
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对于终止处理程序的限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不能使用 `goto` 语句跳入 `__try` 语句块或 `__finally` 语句块。  相反，您必须通过常规控制流进入此语句块。（但是，您可以跳出 `__try` 语句块。）此外，您不能将异常处理程序或终止处理程序嵌入 `__finally` 块。  
  
 此外，终止处理程序中允许的某些类型的代码会生成有问题的结果，因此您应小心使用它们（如果要使用）。  其中一个是跳出 `__finally` 语句块的 `goto` 语句。  如果该块正在作为正常终止的一部分执行，则不会发生任何异常。  但如果系统正在展开堆栈，则该展开会停止，并且当前函数会获取控制权，就象异常终止不存在一样。  
  
 `__finally` 语句块内的 `return` 语句存在大致相同的情况。  控制权将返回给包含终止处理程序的函数的直接调用方。  如果系统正在展开堆栈，此进程将暂停，如果没有引发过异常，则程序将继续执行。  
  
## 请参阅  
 [编写终止处理程序](../cpp/writing-a-termination-handler.md)   
 [结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)