---
title: "异常：3.0 版本中对异常宏的修改 | Microsoft Docs"
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
  - "C++ 异常处理, 升级注意事项"
  - "CATCH 宏"
  - "异常, 更改了什么"
  - "THROW_LAST 宏"
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异常：3.0 版本中对异常宏的修改
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这是一个高级主题。  
  
 在 MFC 3.0 版及更高版本中，异常处理宏已经改为使用 C\+\+ 异常。  本文说明了这些更改将如何影响现有的代码使用宏的行为。  
  
 本文涵盖以下主题：  
  
-   [异常类型和 CATCH 宏](#_core_exception_types_and_the_catch_macro)  
  
-   [重新抛出异常](#_core_re.2d.throwing_exceptions)  
  
##  <a name="_core_exception_types_and_the_catch_macro"></a> 异常类型和 CATCH 宏  
 MFC 在早期版本中，宏 **CATCH** 使用 MFC 运行时类型信息确定异常类型；异常类型是确定的，也就是说，在 catch 处确定了。  如果有 C\+\+ 异常，而异常类型总是由抛出异常对象的类型处确定。  极少数情况下，这将导致抛出对象的指针与抛出对象的类型的不兼容。  
  
 下面的示例阐释了 MFC 3.0 版及早期版本之间的差异造成的结果：  
  
 [!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]  
  
 此代码块在版本 3.0有不同表现，因为控件始终传递给第一个 **catch** 块以匹配异常声明。  抛出表达式表达式的结果。  
  
 [!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]  
  
 抛出**CException\***，即使被构造为**CCustomException**。  在 MFC 2.5 版及更早版本中的**CATCH** 使用 `CObject::IsKindOf` 宏测试运行时的类型。  因为表达式。  
  
 [!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]  
  
 为 true，第一个 Catch 块捕捉异常。  在版本 3.0中，使用 C\+\+ 异常实现许多异常处理的宏，第二个 Catch 块与抛出的 `CException`匹配。  
  
 这样的代码很少见。  当异常对象传递到接受**CException\***的另一个函数时，执行“pre\-throw”过程，最后抛出异常。  
  
 为了解决此问题，则将函数抛出表达式移到调用代码中，在生成异常时，抛出为编译器所知的实际类型的异常。  
  
##  <a name="_core_re.2d.throwing_exceptions"></a> 重新抛出异常  
 catch 块不会抛出相同异常的指针。  
  
 例如，此代码在旧版本有效，但是，在 3.0 版本会有意外结果：  
  
 [!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/CPP/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]  
  
 使用 catch 块的 **THROW** 删除指针 `e`，因此外部catch 块将接收了无效的指针。  使用 `THROW_LAST` 重新抛出 `e`。  
  
 有关更多信息，请参见 [异常：捕获和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
## 请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)