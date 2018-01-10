---
title: "异常： 使用 MFC 宏和 c + + 异常 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6597f43deee73addff8e8f2045a38d7b1109fc0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>异常：使用 MFC 宏和 C++ 异常
此文章介绍了有关编写使用 MFC 异常处理宏和 c + + 异常处理关键字的代码的注意事项。  
  
 本文介绍了以下主题：  
  
-   [混合使用异常关键字和宏](#_core_mixing_exception_keywords_and_macros)  
  
-   [Try catch 块内的块](#_core_try_blocks_inside_catch_blocks)  
  
##  <a name="_core_mixing_exception_keywords_and_macros"></a>混合使用异常关键字和宏  
 可以混合使用 MFC 异常宏和 c + + 异常关键字的同一程序中。 但不是能与同一个块中的 c + + 异常关键字混合 MFC 宏，因为宏异常对象时自动删除它们超出范围，而使用异常处理关键字的代码不。 有关详细信息，请参阅文章[异常： 捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
 宏和关键字之间的主要区别是当异常超出范围时，宏将"自动"删除捕获的异常。 使用关键字的代码却不;在 catch 块中捕获到异常时，必须显式删除。 混合使用宏和 c + + 异常关键字可以导致内存泄漏时未删除异常对象，或当异常被两次删除堆损坏。  
  
 下面的代码，例如，使异常指针无效：  
  
 [!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]  
  
 出现问题的原因`e`时执行将跳出"内部"删除**捕获**块。 使用`THROW_LAST`宏而不是**引发**语句将导致"外部"**捕获**块接收有效指针：  
  
 [!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]  
  
##  <a name="_core_try_blocks_inside_catch_blocks"></a>Try Catch 块内的块  
 无法重新中引发当前异常**重**块内**捕获**块。 下面的示例而无效：  
  
 [!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]  
  
 有关详细信息，请参阅[异常： 检查异常内容](../mfc/exceptions-examining-exception-contents.md)。  
  
## <a name="see-also"></a>请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)

