---
title: "异常：从 MFC 异常宏转换 | Microsoft Docs"
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
  - "捕捉块, 分隔"
  - "CException 类, 删除 CException 类对象"
  - "转换, 使用 MFC 宏编写的代码"
  - "转换异常"
  - "异常处理, 转换异常"
  - "异常对象"
  - "异常对象, 删除"
  - "异常, 转换"
  - "异常, 删除异常对象"
  - "关键字 [C++], 宏"
  - "宏, C++ 关键字"
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异常：从 MFC 异常宏转换
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这是一个高级主题。  
  
 本文说明如何转换现有代码编写使用 Microsoft 基础类 \- 宏 **TRY**，**CATCH**，**THROW**，等使用异常处理关键字 **try**、**catch**和 `throw`的 C\+\+。  主题包括：  
  
-   [转换优点](#_core_advantages_of_converting)  
  
-   [转换与异常宏使用 C\+\+ 异常的代码](#_core_doing_the_conversion)  
  
##  <a name="_core_advantages_of_converting"></a> 转换的优点  
 您可能不需要转换现有代码，所以，虽然您应该知道在宏实现在 MFC 3.0 版及实现之间的差异。早期版本。  这些差异和后续更改。代码行为在 [异常：指向异常宏在版本 3.0 中的更改](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)讨论。  
  
 转换的主要优点是：  
  
-   代码使用异常处理关键字的 C\+\+ 编译为一个稍微小的 .EXE 或 .DLL。  
  
-   异常处理关键字的 C\+\+ 更通用的：可以处理这些属性可以复制任意数据类型的异常 \(`int`、**浮动**，`char`，依此类推\)，则宏，而只需要处理异常从其派生的类和 `CException` 类。  
  
 当异常超出范围时，宏和关键字之间的主要差异在于该代码使用宏“自动”删除所捕获的异常。  使用关键字的代码不，因此，必须显式删除所捕获的异常。  有关更多信息，请参见知识库文章 [异常：捕获异常和删除](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
 另一不同之处是语法。  宏和关键字的语法在三个方面不同：  
  
1.  宏的参数和异常声明：  
  
     **CATCH** 宏调用具有以下语法：  
  
     **CATCH\(** *exception\_class*，*exception\_object\_pointer\_name* \#\#\#\)  
  
     请注意是类名和名称对象指针间的逗号。  
  
     **catch** 关键字的异常声明使用此语法：  
  
     **catch\(** *exception\_type* *exception\_name*\#\#\#\)  
  
     此异常声明语句指示异常类型的 catch 块中处理。  
  
2.  Catch 块中的一个：  
  
     宏，**CATCH** 宏 \(带有参数\) 开始第一个 Catch 块；`AND_CATCH` 宏开始后续 catch 块，catch 块，`END_CATCH` 宏终止序列。  
  
     关键字，**catch** 关键字 \(使用的异常声明\) 开始每个 catch 块。  没有复制为 `END_CATCH` 宏；catch 块的右大括号。结束  
  
3.  引发表达式：  
  
     宏使用 `THROW_LAST` 重新引发当前异常。  `throw` 关键字，而参数，这具有同样的效果。  
  
##  <a name="_core_doing_the_conversion"></a> 执行转换。  
  
#### 转换代码使用宏使用的 C\+\+ 异常处理关键字  
  
1.  查找 MFC 宏 **TRY**、**CATCH**、`AND_CATCH`、`END_CATCH`、**THROW**和 `THROW_LAST`的所有匹配项。  
  
2.  替换或删除以下宏的所有匹配项：  
  
     **TRY** \(请用 **try**替换它。\)  
  
     **CATCH** \(请用 **catch**替换它。\)  
  
     `AND_CATCH` \(用 **catch**替换它。\)  
  
     `END_CATCH` \(其删除。\)  
  
     **THROW** \(用 `throw`替换它。\)  
  
     `THROW_LAST` \(将 `throw`替换为该\)  
  
3.  修改的参数，以便形成有效的异常声明。  
  
     例如，若要更改  
  
     [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_1.cpp)]  
  
     设置为  
  
     [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_2.cpp)]  
  
4.  修改在执行 catch 块中的代码，以便根据需要删除异常对象。  有关更多信息，请参见知识库文章 [异常：捕获异常和删除](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
 使用 MFC 宏异常，这是异常处理代码的示例。  请注意，因为在下面示例中的代码使用宏，将引发异常 `e` 自动删除：  
  
 [!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_3.cpp)]  
  
 在下一示例中的代码使用了 C\+\+ 异常关键字，因此，必须显式删除异常：  
  
 [!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/CPP/exceptions-converting-from-mfc-exception-macros_4.cpp)]  
  
 有关更多信息，请参见 [异常：使用 MFC 宏和 C\+\+ 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。  
  
## 请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)