---
title: MFC 中的异常处理
ms.date: 11/04/2016
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
ms.openlocfilehash: 4b520072bd0c07e261f2cf4baf51d7ea3d14a5ab
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694551"
---
# <a name="exception-handling-in-mfc"></a>MFC 中的异常处理

本文介绍 MFC 中可用的异常处理机制。 提供了两种机制：

- 提供 MFC 版本 3.0 和更高版本的 c + + 异常

- MFC 异常宏，可用在 MFC 版本 1.0 及更高版本

如果您要编写使用 MFC 的新应用程序，应使用 c + + 机制。 如果你的现有应用程序已广泛使用该机制，可以使用基于宏的机制。

您可以轻松地转换现有代码以使用 c + + 异常，而不是 MFC 异常宏。 文章中所述将转换你的代码和执行此操作的指导原则的优势[异常： 从 MFC 异常宏转换](../mfc/exceptions-converting-from-mfc-exception-macros.md)。

如果您已开发了使用 MFC 异常宏的应用程序，则可以继续使用这些宏在现有代码中，同时在新代码中使用 c + + 异常。 文章[异常： 3.0 版中的异常宏将变为](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)提供的指导可用于执行此操作。

> [!NOTE]
>  若要启用 c + + 异常处理代码中，项目的 C/c + + 文件夹中的代码生成页上选择启用 c + + 异常[属性页](../ide/property-pages-visual-cpp.md)对话框中或使用[/EHsc](../build/reference/eh-exception-handling-model.md)编译器选项。

本文介绍了以下主题：

- [何时使用异常](#_core_when_to_use_exceptions)

- [MFC 异常支持](#_core_mfc_exception_support)

- [有关异常的更多参考资料](#_core_further_reading_about_exceptions)

##  <a name="_core_when_to_use_exceptions"></a> 何时使用异常

在程序执行期间调用的函数时，可能出现的结果的三个类别： 常规执行、 错误执行或不正常执行。 下面描述了每个类别。

- 正常执行

   该函数可能正常执行，并返回。 一些函数返回给调用方指示该函数的结果的结果代码。 可能的结果代码严格定义的函数，表示函数的可能结果的范围。 结果代码可以指示成功或失败，或甚至可以指示特定类型的故障，期望在正常范围内。 例如，文件状态函数可以返回代码，指示该文件不存在。 请注意因为结果代码表示很多预期的结果中的一个未使用术语"错误代码"。

- 错误的执行

   调用方是犯一些在将参数传递给函数或调用不适当的上下文中的函数。 这种情况下导致错误，并且应检测到通过在程序开发过程中的断言。 (有关断言的详细信息，请参阅[C/c + + 断言](/visualstudio/debugger/c-cpp-assertions)。)

- 不正常执行

   不正常执行包括其中外部程序的控制，例如低内存或 I/O 错误条件会影响函数的结果的情况。 应通过捕获和引发异常处理异常情况。

使用异常是尤其适用于不正常执行。

##  <a name="_core_mfc_exception_support"></a> MFC 异常支持

无论是直接使用 c + + 异常，还是使用 MFC 异常宏，将使用[CException 类](../mfc/reference/cexception-class.md)或`CException`-派生的对象的框架或您的应用程序可能会引发。

下表显示了由 MFC 提供的预定义的异常。

|Exception 类|含义|
|---------------------|-------------|
|[CMemoryException 类](../mfc/reference/cmemoryexception-class.md)|内存不足|
|[CFileException 类](../mfc/reference/cfileexception-class.md)|文件异常|
|[CArchiveException 类](../mfc/reference/carchiveexception-class.md)|存档/序列化异常|
|[CNotSupportedException 类](../mfc/reference/cnotsupportedexception-class.md)|若要为不支持的服务请求的响应|
|[CResourceException 类](../mfc/reference/cresourceexception-class.md)|Windows 资源分配异常|
|[CDaoException 类](../mfc/reference/cdaoexception-class.md)|数据库异常 （DAO 类）|
|[CDBException 类](../mfc/reference/cdbexception-class.md)|数据库异常 （ODBC 类）|
|[COleException 类](../mfc/reference/coleexception-class.md)|OLE 异常|
|[COleDispatchException 类](../mfc/reference/coledispatchexception-class.md)|调度 （自动化） 异常|
|[CUserException 类](../mfc/reference/cuserexception-class.md)|异常可提示用户提供一个消息框，然后引发泛型[CException 类](../mfc/reference/cexception-class.md)|

> [!NOTE]
>  MFC 支持 c + + 异常和 MFC 异常宏。 MFC 不直接支持 Windows NT 结构化异常处理程序 (SEH) 中所述[结构化异常处理](/windows/desktop/debug/structured-exception-handling)。

##  <a name="_core_further_reading_about_exceptions"></a> 有关异常的更多参考资料

以下文章说明了使用 MFC 库进行异常处理：

- [异常：捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [异常：检查异常内容](../mfc/exceptions-examining-exception-contents.md)

- [异常：释放异常中的对象](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [异常：从自己的函数引发异常](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [异常：数据库异常](../mfc/exceptions-database-exceptions.md)

- [异常：OLE 异常](../mfc/exceptions-ole-exceptions.md)

以下文章比较 MFC 异常宏与 c + + 异常关键字并解释如何调整你的代码：

- [异常：3.0 版本中对异常宏的修改](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [异常：从 MFC 异常宏转换](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [异常：使用 MFC 宏和 C++ 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>请参阅

[C++ 异常处理](../cpp/cpp-exception-handling.md)<br/>
[如何： 创建我自己的自定义异常类](http://go.microsoft.com/fwlink/p/?linkid=128045)

