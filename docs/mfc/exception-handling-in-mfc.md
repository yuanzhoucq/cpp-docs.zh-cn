---
title: "MFC 中的异常处理 | Microsoft Docs"
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
  - "异常程序执行 [C++]"
  - "将异常存档 [C++]"
  - "断言 [C++], 何时使用异常"
  - "本机 [C++], 异常"
  - "C++ 异常处理, 启用"
  - "C++ 异常处理, MFC 应用程序"
  - "C++ 异常处理, 类型"
  - "类库 [C++], 异常支持"
  - "DAO [C++], 异常"
  - "数据库异常 [C++]"
  - "错误处理 [C++], 异常和"
  - "错误 [C++], 由断言检测"
  - "异常处理 [C++], MFC"
  - "异常宏 [C++]"
  - "异常 [C++], MFC 宏与 C++ 关键字"
  - "函数调用, 结果"
  - "关键字 [C++], 异常处理"
  - "宏 [C++], 异常处理"
  - "宏 [C++], MFC 异常宏"
  - "内存 [C++], 内存不足异常"
  - "MFC [C++], 异常"
  - "ODBC 异常 [C++]"
  - "OLE 异常 [C++], MFC 异常处理"
  - "内存不足异常 [C++]"
  - "预定义的异常 [C++]"
  - "针对不支持的服务的请求"
  - "资源分配异常"
  - "资源 [C++], 分配"
  - "序列化 [C++], 异常"
  - "Windows [C++], 资源分配异常"
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 中的异常处理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这篇文章解释了 MFC 中可用的处理异常的机制。  这两种机制都可用：  
  
-   C\+\+ 异常，在 MFC 3.0 及更高版本  
  
-   MFC 宏，异常具有 MFC 1.0 及更高版本  
  
 使用 MFC，则编写新应用程序，应使用 C\+\+ 机制。  可以使用基于宏的机制，则现有的应用程序已经使用该机制广泛。  
  
 您可以轻松地将现有代码使用 C\+\+ 异常而不是异常 MFC 宏。  转换代码和准则中的优点来执行中的文章 [异常：从 MFC 异常宏转换](../mfc/exceptions-converting-from-mfc-exception-macros.md)中描述。  
  
 使用 MFC 宏异常，如果已经开发一个应用程序，则可以通过使用这些宏在现有代码，所以，如果使用 C\+\+ 异常在新的代码。  文章 [异常：3.0 版本中对异常宏的修改](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) 为这样的准则。  
  
> [!NOTE]
>  若要启用 C\+\+ 异常处理。代码，选择上启用代码、生成页面的 C\+\+ 异常。项目中 [属性页](../ide/property-pages-visual-cpp.md) 对话框的 C\/C\+\+ 文件夹或使用 \/GX 编译器选项。  默认为 \/GX \-，禁用异常处理。  
  
 本文涵盖以下主题：  
  
-   [何时使用异常](#_core_when_to_use_exceptions)  
  
-   [MFC异常支持](#_core_mfc_exception_support)  
  
-   [有关异常的其他阅读材料](#_core_further_reading_about_exceptions)  
  
##  <a name="_core_when_to_use_exceptions"></a> 何时使用异常  
 当函数在程序执行时调用，因此三个类别可以发生：常规执行、不正确执行或执行异常。  介绍每个类别。  
  
-   常规执行  
  
     函数可能操作通常并返回。  某些函数返回结果代码，向调用方指示函数的结果。  可能的结果代码为函数严格定义并表示范围函数的可能结果。  结果代码指示成功或失败或者甚至可以指示为在所需范围中正常失败的特定类型。  例如，函数可以返回文件状态表示的代码文件不存在。  请注意未使用术语“错误代码”，因为结果代码表示许多预期结果之一。  
  
-   不正确执行  
  
     调用方在不适当的上下文在某种错误出现参数传递给函数或调用函数。  此问题导致错误，程序在开发期间，因此，应由断言检测到它。有关约束的更多信息，请参见 [C\/C\+\+ 断言](../Topic/C-C++%20Assertions.md)。  
  
-   异常执行  
  
     异常由执行程序在控件外的条件，例如内存不足或 I\/O 错误，影响函数的结果的情况。  应由捕获和处理异常情况引发的异常。  
  
 使用异常为异常执行尤为合适。  
  
##  <a name="_core_mfc_exception_support"></a> MFC异常支持  
 是否直接使用 C\+\+ 异常或异常使用 MFC 宏，您将使用 [CException Class](../mfc/reference/cexception-class.md) 或 `CException`\- 可能引发由框架还是由应用程序的派生对象。  
  
 下表显示MFC结构提供的值。  
  
|异常类|含义|  
|---------|--------|  
|[CMemoryException Class](../mfc/reference/cmemoryexception-class.md)|内存不足。|  
|[CFileException Class](../mfc/reference/cfileexception-class.md)|文件异常|  
|[CArchiveException Class](../mfc/reference/carchiveexception-class.md)|存档\/序列化异常|  
|[CNotSupportedException Class](../mfc/reference/cnotsupportedexception-class.md)|请求的响应不支持服务|  
|[CResourceException Class](../mfc/reference/cresourceexception-class.md)|Windows 资源分配异常|  
|[CDaoException Class](../mfc/reference/cdaoexception-class.md)|数据库异常 DAO \(类\)|  
|[CDBException Class](../mfc/reference/cdbexception-class.md)|数据库异常 DAO \(ODBC类\)|  
|[COleException Class](../mfc/reference/coleexception-class.md)|OLE 异常|  
|[COleDispatchException Class](../mfc/reference/coledispatchexception-class.md)|计划 \(自动化\) 异常|  
|[CUserException Class](../mfc/reference/cuserexception-class.md)|有消息通知用户的异常，然后引发一般 [CException Class](../mfc/reference/cexception-class.md)|  
  
> [!NOTE]
>  MFC 支持 C\+\+ 异常和 MFC 宏异常。  MFC 不直接支持 NTFS 结构化异常处理程序 \(SEH\) \(SEH\)，如 [结构化异常处理](http://msdn.microsoft.com/library/windows/desktop/ms680657)所述。  
  
##  <a name="_core_further_reading_about_exceptions"></a> 有关异常的其他阅读材料  
 使用异常传递的，MFC 库说明下列文章：  
  
-   [异常：捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)  
  
-   [异常：检查异常内容](../mfc/exceptions-examining-exception-contents.md)  
  
-   [异常：释放异常中的对象](../mfc/exceptions-freeing-objects-in-exceptions.md)  
  
-   [异常：从您自己的函数引发异常](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)  
  
-   [异常：数据库异常](../mfc/exceptions-database-exceptions.md)  
  
-   [异常：OLE 异常](../mfc/exceptions-ole-exceptions.md)  
  
 下列文章比较使用 C\+\+ 异常关键字的 MFC 异常宏并阐释可以如何调整代码：  
  
-   [异常：3.0 版本中对异常宏的修改](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)  
  
-   [异常：从 MFC 异常宏转换](../mfc/exceptions-converting-from-mfc-exception-macros.md)  
  
-   [异常：使用 MFC 宏和 C\+\+ 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)  
  
## 请参阅  
 [C\+\+ 异常处理](../cpp/cpp-exception-handling.md)   
 [如何：创建 My 自定义异常类？](http://go.microsoft.com/fwlink/?LinkId=128045)