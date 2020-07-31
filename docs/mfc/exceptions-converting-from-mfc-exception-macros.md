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
ms.openlocfilehash: e8e7f47b66f4263ed55d73c0aac1fda73d72393c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87183807"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>异常：从 MFC 异常宏转换

这是一个高级主题。

本文介绍如何转换使用 Microsoft 基础类宏（ **TRY**、 **CATCH**、 **THROW**等）编写的现有代码，以便使用 c + + 异常处理关键字 **`try`** 、 **`catch`** 和 **`throw`** 。 主题包括：

- [转换优点](#_core_advantages_of_converting)

- [使用异常宏转换代码以使用 c + + 异常](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>转换的优点

您可能不需要转换现有代码，但您应该知道 MFC 版本3.0 中的宏实现与早期版本中的实现之间的差异。 在[版本3.0 中对异常宏的更改](exceptions-changes-to-exception-macros-in-version-3-0.md)中讨论了这些差异以及代码行为的后续更改。

转换的主要优点是：

- 使用 c + + 异常处理关键字的代码编译为略微小一些。EXE 或。.DLL.

- C + + 异常处理关键字的用途更广：它们可以处理任何可以复制的数据类型（ **`int`** 、、等 **`float`** ）的异常 **`char`** ，而宏仅处理派生自该类的类 `CException` 和类。

宏和关键字之间的主要区别在于，当异常超出范围时，使用宏 "自动" 的代码将删除捕获的异常。 使用关键字的代码不是，因此必须显式删除捕获的异常。 有关详细信息，请参阅文章[异常：捕获和删除异常](exceptions-catching-and-deleting-exceptions.md)。

另一个差异是语法。 宏和关键字的语法在以下三个方面有所不同：

1. 宏参数和异常声明：

   **CATCH**宏调用具有以下语法：

   **CATCH （** *exception_class*， *exception_object_pointer_name* **）**

   请注意类名称和对象指针名称之间的逗号。

   关键字的异常声明 **`catch`** 使用以下语法：

   **catch （** *exception_type* *exception_name* **）**

   此异常声明语句指示 catch 块处理的异常的类型。

2. Catch 块的 Delimitation：

   对于宏， **catch**宏（带有其自变量）从第一个 catch 块开始;**AND_CATCH**宏会开始后面的 catch 块， **END_CATCH**宏将终止 CATCH 块的序列。

   对于关键字， **`catch`** 关键字（带有异常声明）会开始每个 catch 块。 **END_CATCH**宏没有对应项;catch 块以右大括号结束。

3. Throw 表达式：

   宏使用**THROW_LAST**来重新引发当前异常。 **`throw`** 不带参数的关键字具有相同的效果。

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>执行转换

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>使用宏将代码转换为使用 c + + 异常处理关键字

1. 查找 MFC 宏**TRY**、 **CATCH**、 **AND_CATCH**、 **END_CATCH**、 **THROW**和**THROW_LAST**的所有匹配项。

2. 替换或删除以下所有宏：

   **尝试**（将其替换为 **`try`** ）

   **CATCH** （替换为 **`catch`** ）

   **AND_CATCH** （将其替换为 **`catch`** ）

   **END_CATCH** （删除）

   **THROW** （替换为 **`throw`** ）

   **THROW_LAST** （将其替换为 **`throw`** ）

3. 修改宏参数，使其构成有效的异常声明。

   例如，更改

   [!code-cpp[NVC_MFCExceptions#6](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   实例部署到 Windows Azure 虚拟机 (VM) 中的

   [!code-cpp[NVC_MFCExceptions#7](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. 修改 catch 块中的代码，使其删除必要的异常对象。 有关详细信息，请参阅文章[异常：捕获和删除异常](exceptions-catching-and-deleting-exceptions.md)。

下面是使用 MFC 异常宏的异常处理代码示例。 请注意，由于以下示例中的代码使用宏，因此例外会 `e` 自动删除：

[!code-cpp[NVC_MFCExceptions#8](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

下一个示例中的代码使用 c + + 异常关键字，因此必须显式删除异常：

[!code-cpp[NVC_MFCExceptions#9](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

有关详细信息，请参阅[异常：使用 MFC 宏和 c + + 异常](exceptions-using-mfc-macros-and-cpp-exceptions.md)。

## <a name="see-also"></a>另请参阅

[异常处理](exception-handling-in-mfc.md)<br/>
