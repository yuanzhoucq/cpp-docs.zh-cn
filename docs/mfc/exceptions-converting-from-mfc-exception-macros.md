---
title: 异常： 从 MFC 异常宏转换 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- converting exceptions [MFC]
- exception objects [MFC]
- conversions [MFC], code written with MFC macros
- keywords [MFC], macros
- macrosv, C++ keywords
- exception objects [MFC], deleting
- CException class [MFC], deleting CException class objects
- exceptions [MFC], converting
- exceptions [MFC], deleting exception objects
- catch blocks [MFC], delimiting
- exception handling [MFC], converting exceptions
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8953cc28e35974f7a2a63754533ffd851ca62a3e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>异常：从 MFC 异常宏转换
这是一个高级的主题。  
  
 此文章介绍了如何使用 Microsoft 基础类宏编写的现有代码转换-**重**，**捕获**，**引发**，依次类推-若要使用 c + + 异常处理关键字**重**，**捕获**，和`throw`。 包括以下主题：  
  
-   [转换优点](#_core_advantages_of_converting)  
  
-   [转换使用异常宏用于 c + + 异常的代码](#_core_doing_the_conversion)  
  
##  <a name="_core_advantages_of_converting"></a> 转换的优点  
 你可能不需要转换现有代码，尽管你应注意的 mfc 版本 3.0 宏实现和早期版本中的实现之间的差异。 中讨论了这些差异和代码行为的后续更改[异常： 3.0 版本中对异常宏更改](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)。  
  
 转换的主要优势是：  
  
-   使用 c + + 异常处理关键字的代码会编译为略低。EXE 或。DLL。  
  
-   C + + 异常处理关键字是更通用： 它们可以处理可以复制任何数据类型的异常 (`int`， **float**， `char`，依次类推)，而宏处理仅的类异常`CException`和从它派生类。  
  
 宏和关键字的主要区别是"自动"使用宏的代码，当异常超出范围时将删除捕获的异常。 代码使用关键字不存在，则必须显式删除捕获的异常。 有关详细信息，请参阅文章[异常： 捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
 另一个区别是语法。 宏和关键字的语法在三个方面不同：  
  
1.  宏自变量和异常声明：  
  
     A**捕获**宏调用具有以下语法：  
  
     **捕获 (** *exception_class*， *exception_object_pointer_name* **)**  
  
     请注意之间的类名称和对象指针名称的逗号。  
  
     异常声明**捕获**关键字使用以下语法：  
  
     **捕获 (** *exception_type* *exception_name * * *)**  
  
     此异常声明语句指示的一种异常的 catch 块处理。  
  
2.  界定的 catch 块内的方式：  
  
     使用宏，**捕获**宏 （使用其自变量） 开始的第一个 catch 块;`AND_CATCH`宏开始后续 catch 块内，与`END_CATCH`宏终止 catch 块的序列。  
  
     与关键字，**捕获**关键字 （替换其异常声明） 开始每个 catch 块。 没有到`END_CATCH`宏; 阻止其右大括号以结束该 catch。  
  
3.  引发表达式：  
  
     宏使用`THROW_LAST`重新引发当前异常。 `throw`关键字，使用任何参数时，具有相同的效果。  
  
##  <a name="_core_doing_the_conversion"></a> 进行转换  
  
#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>要转换宏用于使用 c + + 异常处理关键字的代码  
  
1.  查找所有匹配项的 MFC 宏**重**，**捕获**， `AND_CATCH`， `END_CATCH`，**引发**，和`THROW_LAST`。  
  
2.  替换或删除所有出现的以下宏：  
  
     **请尝试**(将其替换为**重**)  
  
     **捕获**(将其替换为**捕获**)  
  
     `AND_CATCH` (将其替换为**捕获**)  
  
     `END_CATCH` （将其删除）  
  
     **引发**(将其替换为`throw`)  
  
     `THROW_LAST` (将其替换为`throw`)  
  
3.  修改宏自变量，以便它们构成有效的异常声明。  
  
     例如，更改  
  
     [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]  
  
     更改为  
  
     [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]  
  
4.  修改的 catch 块中的代码，以便它删除根据需要的异常对象。 有关详细信息，请参阅文章[异常： 捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
 下面是异常处理代码中使用 MFC 异常宏的示例。 请注意，因为下面的示例中的代码使用宏，该异常`e`会被自动删除：  
  
 [!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]  
  
 下一步的示例中的代码使用 c + + 异常关键字，因此必须显式删除异常：  
  
 [!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]  
  
 有关详细信息，请参阅[异常： 使用 MFC 宏和 c + + 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。  
  
## <a name="see-also"></a>请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)

