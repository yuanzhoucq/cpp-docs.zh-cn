---
title: 异常：从 MFC 异常宏转换
ms.date: 08/27/2018
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
ms.openlocfilehash: 330f66b1f46542082637645ad53da016b434d4a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372020"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>异常：从 MFC 异常宏转换

这是一个高级主题。

本文介绍如何转换使用 Microsoft 基础类宏编写的现有代码 - **TRY、CATCH、THROW**等 — 使用C++异常处理关键字**尝试**、**捕获**和**引发**。 **CATCH** **THROW** 主题包括：

- [转换优势](#_core_advantages_of_converting)

- [将具有异常宏的代码转换为使用C++例外](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>转换的优点

您可能不需要转换现有代码，尽管您应该了解 MFC 版本 3.0 中的宏实现在早期版本中的实现之间的差异。 这些差异和代码行为的后续更改在["例外：对版本 3.0 中的异常宏的更改"中](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)进行了讨论。

转换的主要优点是：

- 使用C++异常处理关键字的代码编译为稍小一些。EXE 或 。Dll。

- C++异常处理关键字更通用：它们可以处理任何数据类型的异常 **（int、float、char**等），而宏仅处理**float**派生自**char**它的类`CException`和类的异常。

宏和关键字之间的主要区别是，使用宏"自动"的代码在异常超出范围时删除捕获的异常。 使用关键字的代码不会，因此您必须显式删除捕获的异常。 有关详细信息，请参阅文章["例外：捕获和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)"。

另一个区别是语法。 宏和关键字的语法在三个方面有所不同：

1. 宏参数和异常声明：

   **CATCH**宏调用具有以下语法：

   **CATCH（exception_class，exception_object_pointer_name）** *exception_class* *exception_object_pointer_name* **)**

   请注意类名称和对象指针名称之间的逗号。

   **catch**关键字的异常声明使用此语法：

   **渔获***exception_type**（exception_typeexception_name）* **)**

   此异常声明语句指示 catch 块句柄的异常类型。

2. 渔获物块的划分：

   使用宏时 **，CATCH**宏（具有其参数）开始第一个 catch 块;使用宏宏，则使用宏宏（具有其参数）开始第一个 catch 块。**AND_CATCH**宏开始后续 catch 块 **，END_CATCH**宏终止 catch 块的顺序。

   使用关键字时 **，catch**关键字（其异常声明）将启动每个 catch 块。 END_CATCH**宏没有**对应点;catch 块以其右大括号结束。

3. 引发表达式：

   宏使用**THROW_LAST**重新引发当前异常。 **没有参数的引发**关键字具有相同的效果。

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>执行转换

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>使用宏转换代码以使用C++异常处理关键字

1. 找到 MFC 宏**TRY**TRY、CATCH、AND_CATCH、END_CATCH、THROW**END_CATCH**和**THROW****THROW_LAST**的所有匹配项。 **CATCH** **AND_CATCH**

2. 替换或删除以下宏的所有匹配项：

   **TRY（** 用**尝试**替换）

   **CATCH（** 用**渔获替换**）

   **AND_CATCH（** 用**渔获替换**）

   **END_CATCH（** 删除）

   **THROW（** 用**投掷**替换）

   **THROW_LAST（** 用**投掷**替换）

3. 修改宏参数，以便它们形成有效的异常声明。

   例如，更改

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   to

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. 修改 catch 块中的代码，以便根据需要删除异常对象。 有关详细信息，请参阅文章["例外：捕获和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)"。

下面是使用 MFC 异常宏的异常处理代码的示例。 请注意，由于以下示例中的代码使用宏，因此将自动删除异常`e`：

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

下一个示例中的代码使用C++异常关键字，因此必须显式删除异常：

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

有关详细信息，请参阅[异常：使用 MFC 宏和C++异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。

## <a name="see-also"></a>另请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)<br/>
