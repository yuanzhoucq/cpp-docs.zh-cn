---
title: MFC 中的异常处理
ms.date: 11/19/2019
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
ms.openlocfilehash: ef827af413513d1a1753f84b1cb69a66f41f690c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618857"
---
# <a name="exception-handling-in-mfc"></a>MFC 中的异常处理

本文介绍 MFC 中可用的异常处理机制。 提供两种机制：

- C + + 异常，MFC 版本3.0 及更高版本中提供

- Mfc 版本1.0 及更高版本中提供的 MFC 异常宏

如果要使用 MFC 编写新应用程序，应使用 c + + 机制。 如果现有应用程序已广泛使用该机制，则可以使用基于宏的机制。

可以轻松地将现有代码转换为使用 c + + 异常，而不是 MFC 异常宏。 本文的 "[异常：从 MFC 异常宏转换](exceptions-converting-from-mfc-exception-macros.md)" 一文中介绍了转换代码的优点和执行此操作的准则。

如果已使用 MFC 异常宏开发了应用程序，则可以继续在现有代码中使用这些宏，同时在新代码中使用 c + + 异常。 本文[中的异常：版本3.0 中的异常宏的更改](exceptions-changes-to-exception-macros-in-version-3-0.md)提供了执行此操作的指导原则。

> [!NOTE]
> 若要在代码中启用 c + + 异常处理，请在项目的 "[属性页](../build/reference/property-pages-visual-cpp.md)" 对话框的 C/c + + 文件夹中选择 "代码生成" 页上的 "启用 c + + 异常"，或使用[/ehsc](../build/reference/eh-exception-handling-model.md)编译器选项。

本文涵盖以下主题：

- [何时使用异常](#_core_when_to_use_exceptions)

- [MFC 异常支持](#_core_mfc_exception_support)

- [有关异常的详细信息](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a>何时使用异常

在程序执行过程中调用函数时，可能会发生三种类型的结果：正常执行、错误执行或异常执行。 下面介绍了每个类别。

- 正常执行

   函数可以正常执行，并返回。 某些函数将结果代码返回给调用方，指示函数的结果。 为函数严格定义可能的结果代码，并表示函数可能的结果范围。 结果代码可以指示成功或失败，甚至可以指示处于正常范围内的特定类型的故障。 例如，文件状态函数可以返回指示该文件不存在的代码。 请注意，不使用术语 "错误代码"，因为结果代码表示多个预期结果中的一个。

- 执行错误

   调用方在将自变量传递给函数或在不适当的上下文中调用函数时，将会出错。 这种情况会导致错误，并应在程序开发过程中由断言来检测。 （有关断言的详细信息，请参阅[C/c + + 断言](/visualstudio/debugger/c-cpp-assertions)。）

- 异常执行

   异常执行包括程序控件之外的条件（如内存不足或 i/o 错误）对函数的结果产生影响的情况。 异常情况应通过捕获并引发异常来处理。

使用异常特别适用于异常的执行。

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a>MFC 异常支持

无论是直接使用 c + + 异常还是使用 MFC 异常宏，都将使用[CException Class](reference/cexception-class.md) `CException` 可能由框架或应用程序引发的 CException 类或派生对象。

下表显示了 MFC 提供的预定义异常。

|Exception 类|含义|
|---------------------|-------------|
|[CMemoryException 类](reference/cmemoryexception-class.md)|内存不足|
|[CFileException 类](reference/cfileexception-class.md)|文件异常|
|[CArchiveException 类](reference/carchiveexception-class.md)|存档/序列化异常|
|[CNotSupportedException 类](reference/cnotsupportedexception-class.md)|响应不受支持服务的请求|
|[CResourceException 类](reference/cresourceexception-class.md)|Windows 资源分配异常|
|[CDaoException 类](reference/cdaoexception-class.md)|数据库异常（DAO 类）|
|[CDBException 类](reference/cdbexception-class.md)|数据库异常（ODBC 类）|
|[COleException 类](reference/coleexception-class.md)|OLE 异常|
|[COleDispatchException 类](reference/coledispatchexception-class.md)|调度（自动化）异常|
|[CUserException 类](reference/cuserexception-class.md)|使用消息框向用户发出警报的异常，然后引发一般的[CException 类](reference/cexception-class.md)|

自 3.0 版开始，MFC 已使用 C++ 异常，但仍支持其较早的异常处理宏，这些宏在形式上与 C++ 异常类似。 虽然建议不要将这些宏用于新编程，但仍可使用它们实现向后兼容。 在已使用宏的程序中，你也可以随意使用 C++ 异常。 在预处理期间，宏的计算结果为 c + + 语言的 MSVC 实现中定义的异常处理关键字，Visual C++ 版本2.0。 当你开始使用 C++ 异常时，可以保留现有异常宏。 若要了解如何混合使用宏和 c + + 异常处理，以及如何将旧代码转换为使用新机制，请参阅文章[异常：使用 Mfc 宏和 c + + 异常](exceptions-using-mfc-macros-and-cpp-exceptions.md)和[异常：从 Mfc 异常宏转换](exceptions-converting-from-mfc-exception-macros.md)。 较早的 MFC 异常宏（如果你仍在使用它们）的计算结果为 C++ 异常关键字。 请参阅[异常：版本3.0 中的异常宏更改](exceptions-changes-to-exception-macros-in-version-3-0.md)。 MFC 不直接支持 Windows NT 结构化异常处理程序（SEH），如[结构化异常处理](/windows/win32/debug/structured-exception-handling)中所述。

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a>有关异常的详细信息

以下文章说明了如何使用 MFC 库进行异常处理：

- [异常：捕捉和删除异常](exceptions-catching-and-deleting-exceptions.md)

- [异常：检查异常内容](exceptions-examining-exception-contents.md)

- [异常：释放异常中的对象](exceptions-freeing-objects-in-exceptions.md)

- [异常：从您自己的函数引发异常](exceptions-throwing-exceptions-from-your-own-functions.md)

- [异常：数据库异常](exceptions-database-exceptions.md)

- [异常：OLE 异常](exceptions-ole-exceptions.md)

下面的文章将 MFC exception 宏与 c + + 异常关键字进行比较，并说明如何改编你的代码：

- [异常：3.0 版本中对异常宏的修改](exceptions-changes-to-exception-macros-in-version-3-0.md)

- [异常：从 MFC 异常宏转换](exceptions-converting-from-mfc-exception-macros.md)

- [异常：使用 MFC 宏和 C++ 异常](exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>另请参阅

[异常和错误处理的新式 c + + 最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[如何实现：创建我自己的自定义异常类](https://go.microsoft.com/fwlink/p/?linkid=128045)
