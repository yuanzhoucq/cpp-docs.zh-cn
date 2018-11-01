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
ms.openlocfilehash: 59b83438d5341fd6a139af64a2f365a739438741
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525887"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>异常：从 MFC 异常宏转换

这是一个高级的主题。

此文章介绍了如何使用 Microsoft 基础类宏编写的现有代码转换 —**尝试**，**捕获**，**引发**，等等 — 若要使用 c + + 异常处理关键字**尝试**，**捕获**，并**引发**。 包括以下主题：

- [转换的优点](#_core_advantages_of_converting)

- [将代码与使用 c + + 异常的异常宏转换](#_core_doing_the_conversion)

##  <a name="_core_advantages_of_converting"></a> 将转换的优点

可能不需要转换现有的代码，但应注意的 MFC 版本 3.0 中的宏实现与早期版本中的实现之间的差异。 中讨论了这些差异和代码行为中的后续更改[异常： 3.0 版中的异常宏将变为](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)。

转换的主要优势是：

- 使用 c + + 异常处理关键字的代码编译为略小。EXE 或。DLL。

- C + + 异常处理关键字是更灵活： 它们可以处理可以复制任何数据类型的异常 (**int**， **float**， **char**，依此类推)，而宏处理异常的类仅`CException`和从它派生的类。

宏和关键字之间的主要区别是"自动"使用宏的代码，当异常超出范围时将删除捕获的异常。 使用关键字的代码却没有，因此您必须显式删除捕获的异常。 有关详细信息，请参阅文章[异常： 捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

另一个区别是语法。 宏和关键字的语法与以下三个方面不同：

1. 宏参数和异常声明：

   一个**捕获**宏调用具有以下语法：

   **捕获 (** *exception_class*， *exception_object_pointer_name* **)**

   请注意，类名和对象指针名称之间的逗号。

   异常声明**捕获**关键字将使用此语法：

   **捕获 (** *exception_type* *exception_name* **)**

   此异常声明语句指示的类型的异常 catch 块处理。

2. 界定的 catch 块的方式：

   使用宏**捕获**（使用其自变量） 的宏开始第一个 catch 块; **AND_CATCH**宏开始后续 catch 块中，并**END_CATCH**宏终止的 catch 块的顺序。

   使用关键字**捕获**关键字 （替换其异常声明） 开始每个 catch 块。 没有到没有对应**END_CATCH**宏; 的 catch 块结尾其右大括号。

3. 引发表达式：

   使用宏**THROW_LAST**重新引发当前异常。 **引发**关键字，使用任何自变量具有相同的效果。

##  <a name="_core_doing_the_conversion"></a> 执行转换

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>要转换使用宏来使用 c + + 异常处理关键字的代码

1. 查找所有匹配项的 MFC 宏**尝试**，**捕获**， **AND_CATCH**， **END_CATCH**，**引发**，并**THROW_LAST**。

2. 替换或删除所有出现的以下宏：

   **请尝试**(将其替换为**尝试**)

   **捕获**(将其替换为**捕获**)

   **AND_CATCH** (将其替换为**捕获**)

   **END_CATCH** （删除）

   **引发**(将其替换为**引发**)

   **THROW_LAST** (将其替换为**引发**)

3. 修改宏参数，以便它们形成有效的异常声明。

   例如，更改

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   更改为

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. 修改在 catch 块中的代码，以便删除根据异常对象。 有关详细信息，请参阅文章[异常： 捕捉和删除异常](../mfc/exceptions-catching-and-deleting-exceptions.md)。

下面是使用 MFC 异常宏的异常处理代码的示例。 请注意，因为在下面的示例代码使用宏，该异常`e`自动删除：

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

下一示例中的代码使用 c + + 异常关键字，因此必须显式删除异常：

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

有关详细信息，请参阅[异常： 使用 MFC 宏和 c + + 异常](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)。

## <a name="see-also"></a>请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)<br/>
