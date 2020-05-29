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
ms.openlocfilehash: d339ec98dabc6cb24fc7106c4c7238cd6a14a71b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365534"
---
# <a name="exception-handling-in-mfc"></a>MFC 中的异常处理

本文介绍了 MFC 中可用的异常处理机制。 有两种机制可用：

- C++例外，在 MFC 版本 3.0 及更高版本中提供

- MFC 异常宏，在 MFC 版本 1.0 及更高版本提供

如果要使用 MFC 编写新应用程序，则应使用C++机制。 如果现有应用程序已广泛使用该机制，则可以使用基于宏的机制。

您可以轻松转换现有代码以使用C++异常而不是 MFC 异常宏。 在["例外：从 MFC 异常宏转换"](../mfc/exceptions-converting-from-mfc-exception-macros.md)一文中介绍了转换代码和准则的优点。

如果您已经使用 MFC 异常宏开发了应用程序，则可以在现有代码中继续使用这些宏，同时在新代码中使用C++异常。 "[例外：对版本 3.0 中异常宏的更改](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)"提供了执行此操作的指导原则。

> [!NOTE]
> 要在代码中启用C++异常处理，请选择"在项目[属性页](../build/reference/property-pages-visual-cpp.md)"对话框的 C/C++ 文件夹中的代码生成页上启用C++异常，或使用[/EHsc](../build/reference/eh-exception-handling-model.md)编译器选项。

本文涵盖以下主题：

- [何时使用异常](#_core_when_to_use_exceptions)

- [MFC 异常支持](#_core_mfc_exception_support)

- [有关异常的进一步阅读](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a>何时使用例外

在程序执行期间调用函数时，可能会出现三类结果：正常执行、错误执行或异常执行。 下面将介绍每个类别。

- 正常执行

   函数可以正常执行并返回。 某些函数将结果代码返回给调用方，指示函数的结果。 对函数严格定义可能的结果代码，并代表函数的可能结果范围。 结果代码可以指示成功或失败，甚至可以指示在正常期望范围内的特定类型的故障。 例如，文件状态函数可以返回指示该文件不存在的代码。 请注意，不使用术语"错误代码"，因为结果代码表示许多预期结果之一。

- 错误执行

   调用方在将参数传递给函数或在不适当的上下文中调用函数时犯了一些错误。 这种情况会导致错误，并且应在程序开发期间由断言检测到它。 （有关断言的详细信息，请参阅[C/C++断言](/visualstudio/debugger/c-cpp-assertions)。

- 异常执行

   异常执行包括程序无法控制的情况（如内存不足或 I/O 错误）影响函数结果的情况。 异常情况应通过捕获和引发异常来处理。

使用异常特别适用于异常执行。

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a>MFC 异常支持

无论是直接使用C++异常还是使用 MFC 异常宏，都将使用框架或应用程序可能引发的[Cexception 类](../mfc/reference/cexception-class.md)或`CException`派生对象。

下表显示了 MFC 提供的预定义异常。

|Exception 类|含义|
|---------------------|-------------|
|[C内存异常类](../mfc/reference/cmemoryexception-class.md)|内存不足|
|[文件例外类](../mfc/reference/cfileexception-class.md)|文件异常|
|[CArchiveException 类](../mfc/reference/carchiveexception-class.md)|存档/序列化异常|
|[CNotSupportedException 类](../mfc/reference/cnotsupportedexception-class.md)|对不支持的服务请求的响应|
|[CResourceException 类](../mfc/reference/cresourceexception-class.md)|窗口资源分配异常|
|[CDaoException 类](../mfc/reference/cdaoexception-class.md)|数据库异常（DAO 类）|
|[国开行例外类](../mfc/reference/cdbexception-class.md)|数据库异常（ODBC 类）|
|[COleException 类](../mfc/reference/coleexception-class.md)|OLE 异常|
|[COle调度例外类](../mfc/reference/coledispatchexception-class.md)|派单（自动化）异常|
|[用户例外类](../mfc/reference/cuserexception-class.md)|使用消息框提醒用户，然后引发泛型[Cexception 类的异常](../mfc/reference/cexception-class.md)|

自 3.0 版开始，MFC 已使用 C++ 异常，但仍支持其较早的异常处理宏，这些宏在形式上与 C++ 异常类似。 虽然建议不要将这些宏用于新编程，但仍可使用它们实现向后兼容。 在已使用宏的程序中，你也可以随意使用 C++ 异常。 在预处理期间，宏将评估 Visual C++ 版本 2.0 中C++语言的 MSVC 实现中定义的异常处理关键字。 当你开始使用 C++ 异常时，可以保留现有异常宏。 有关混合宏和C++异常处理以及转换旧代码以使用新机制的信息，请参阅文章["例外：使用 MFC 宏C++异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)和[异常：从 MFC 异常宏转换](../mfc/exceptions-converting-from-mfc-exception-macros.md)。 较早的 MFC 异常宏（如果你仍在使用它们）的计算结果为 C++ 异常关键字。 请参阅[异常：对版本 3.0 中的异常宏的更改](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)。 MFC 不直接支持 Windows NT 结构化异常处理程序 （SEH），如[结构化异常处理](/windows/win32/debug/structured-exception-handling)中所述。

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a>关于异常的进一步阅读

以下文章解释使用 MFC 库进行异常处理：

- [异常：捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [异常：检查异常内容](../mfc/exceptions-examining-exception-contents.md)

- [异常：释放异常中的对象](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [异常：从您自己的函数引发异常](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [异常：数据库异常](../mfc/exceptions-database-exceptions.md)

- [异常：OLE 异常](../mfc/exceptions-ole-exceptions.md)

以下文章将 MFC 异常宏与C++异常关键字进行比较，并解释如何调整代码：

- [异常：3.0 版本中对异常宏的修改](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [异常：从 MFC 异常宏转换](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [异常：使用 MFC 宏和 C++ 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>另请参阅

[用于异常和错误处理的现代C++最佳实践](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[如何操作：创建自己的自定义异常类](https://go.microsoft.com/fwlink/p/?linkid=128045)
