---
title: "异常：使用 MFC 宏和 C++ 异常 | Microsoft Docs"
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
  - "捕捉块, 显式删除代码"
  - "捕捉块, 混合的"
  - "异常处理, MFC"
  - "异常处理, 混合语言"
  - "异常对象"
  - "异常对象, 删除"
  - "异常, MFC 宏与 C++ 关键字"
  - "堆损坏"
  - "内存泄漏, 异常对象未删除"
  - "嵌套的 catch 块"
  - "嵌套的 try 块"
  - "try-catch 异常处理, 混合 MFC 宏与 C++ 关键字"
  - "try-catch 异常处理, 嵌套的 try 块"
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异常：使用 MFC 宏和 C++ 异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文讨论针对使用 MFC 编写异常处理宏以及异常处理关键字的 C\+\+ 代码的注意事项。  
  
 本文包含以下主题：  
  
-   [混合的异常关键字和宏](#_core_mixing_exception_keywords_and_macros)  
  
-   [try 块 catch 块。](#_core_try_blocks_inside_catch_blocks)  
  
##  <a name="_core_mixing_exception_keywords_and_macros"></a> 混合的异常关键字和宏  
 可以混合使用 MFC 宏相同的异常。和 C\+\+ 异常关键字程序。  但是，您无法用 C\+\+ 在同一个块中的异常排序关键字组合 MFC 宏，当宏自动删除异常对象，当结构超出范围时，而不使用异常处理关键字的代码。  有关更多信息，请参见知识库文章 [异常：捕获异常和删除](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
 宏和关键字之间的主要差异是宏“自动”删除所捕获的异常，而异常超出范围。  使用关键字的代码不；必须显式删除。Catch 块捕捉的异常。  混合的宏和 C\+\+ 异常关键字会导致内存泄漏异常，则对象未删除时堆损坏，或者异常，则两次时删除。  
  
 下面的代码无效指针，例如，异常：  
  
 [!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/CPP/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]  
  
 出现问题，因为 `e` 中删除，在执行传入从“内部”**CATCH** 块时。  使用代替 **THROW** 语句的 `THROW_LAST` 宏会导致“extern”**CATCH** 块接收有效指针：  
  
 [!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/CPP/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]  
  
##  <a name="_core_try_blocks_inside_catch_blocks"></a> try 块 catch 块。  
 您不能再引发当前异常从位于 **CATCH** 块内部的 **try** 块内部。  下例无效：  
  
 [!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/CPP/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]  
  
 有关更多信息，请参见 [异常：检查异常的内容](../mfc/exceptions-examining-exception-contents.md)。  
  
## 请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)