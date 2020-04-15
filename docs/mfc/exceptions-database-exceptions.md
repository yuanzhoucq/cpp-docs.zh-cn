---
title: 异常：数据库异常
ms.date: 09/17/2019
helpviewer_keywords:
- DAO [MFC], exceptions
- exceptions [MFC], database
- exception handling [MFC], databases
- ODBC exceptions [MFC]
- ODBC [MFC], exceptions
- database exceptions [MFC]
- databases [MFC], exception handling
- error codes [MFC], database exception handling
ms.assetid: 28daf260-f824-4be6-aecc-1f859e6dec26
ms.openlocfilehash: 894960338a7e8c293054ade00e0cdf3295648bb7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366627"
---
# <a name="exceptions-database-exceptions"></a>异常：数据库异常

本文介绍如何处理数据库异常。 无论使用开放数据库连接 （ODBC） 的 MFC 类还是数据访问对象 （DAO） 的 MFC 类，本文中的大多数材料都适用。 特定于一个或另一个模型的材料被显式标记。 主题包括：

- [异常处理方法](#_core_approaches_to_exception_handling)

- [数据库异常处理示例](#_core_a_database_exception.2d.handling_example)

## <a name="approaches-to-exception-handling"></a><a name="_core_approaches_to_exception_handling"></a>异常处理方法

无论您是使用 DAO（过时）还是 ODBC，这种方法都是一样的。

应始终编写异常处理程序来处理异常条件。

捕获数据库异常的最实用方法是使用异常方案测试应用程序。 确定代码中操作可能发生的异常，并强制发生异常。 然后检查跟踪输出以查看引发哪些异常，或检查调试器中返回的错误信息。 这样，您就可以知道您将为正在使用的异常方案看到哪些返回代码。

### <a name="error-codes-used-for-odbc-exceptions"></a>用于 ODBC 异常的错误代码

除了框架定义的返回代码（其中**具有AFX_SQL_ERROR_XXX表单**的名称外，某些[CDB 例外](../mfc/reference/cdbexception-class.md)代码基于[ODBC](../data/odbc/odbc-basics.md)回邮代码。 此类异常的返回代码**具有SQL_ERROR_XXX窗体**的名称。

数据库类可以返回的返回代码（无论是框架定义的代码还是定义 ODBC 的代码）都记录在`CDBException`类[m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode)数据成员下。 有关 ODBC 定义的返回代码的其他信息，请参阅 MSDN 库中的 ODBC SDK*程序员参考*。

### <a name="error-codes-used-for-dao-exceptions"></a>用于 DAO 异常的错误代码

对于 DAO 异常，详细信息通常可用。 您可以通过捕获的[CDaoException](../mfc/reference/cdaoexception-class.md)对象的三个数据成员访问错误信息：

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)包含指向[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)对象的指针，该对象将错误信息封装在 DAO 与数据库关联的错误对象集合中。

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)包含来自 MFC DAO 类的扩展错误代码。 这些错误代码**AFX_DAO_ERROR_XXX窗体的名称**，在 中`CDaoException`的数据成员下记录。

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode)包含 DAO 的 OLE **SCODE（** 如果适用）。 但是，您很少需要使用此错误代码。 通常，其他两个数据成员中提供了更多信息。 有关**SCODE**值的更多，请参阅数据成员。

有关 DAO 错误、DAO 错误对象类型和 DAO 错误集合的其他信息可在类[CDaoException](../mfc/reference/cdaoexception-class.md)下提供。

## <a name="a-database-exception-handling-example"></a><a name="_core_a_database_exception.2d.handling_example"></a>数据库异常处理示例

下面的示例尝试使用**新**运算符在堆上构造[CRecordset](../mfc/reference/crecordset-class.md)派生对象，然后打开记录集（对于 ODBC 数据源）。 有关 DAO 类的类似示例，请参阅下面的"DAO 异常示例"。

### <a name="odbc-exception-example"></a>ODBC 异常示例

[Open](../mfc/reference/crecordset-class.md#open)成员函数可能会引发异常（ODBC 类的[CDBException](../mfc/reference/cdbexception-class.md)类型），因此此代码使用`Open`**try**块将调用括在一起。 后续**catch**块将捕获`CDBException`。 您可以检查名为`e`的异常对象本身，但在这种情况下，它足以知道创建记录集的尝试已失败。 **catch**块显示一个消息框，并通过删除记录集对象进行清理。

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>DAO 异常示例

DAO 示例与 ODBC 的示例类似，但通常可以检索更多类型的信息。 以下代码还尝试打开记录集。 如果该尝试引发异常，则可以检查异常对象的数据成员以查找错误信息。 与前面的 ODBC 示例一样，可能足以知道创建记录集的尝试失败。

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

此代码从异常对象的[m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)成员获取错误消息字符串。 MFC 在引发异常时填充此成员。

有关`CDaoException`对象返回的错误信息的讨论，请参阅[类 CDaoexception](../mfc/reference/cdaoexception-class.md)和[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)。

当您使用 Microsoft Jet （.mdb） 数据库时，在大多数情况下，当您使用 ODBC 时，将只有一个错误对象。 在极少数情况下，当您使用 ODBC 数据源且存在多个错误时，您可以根据 CDaoException 返回的错误数循环访问 DAO 的错误集合[：：：getErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount)。 每次通过循环时，调用[CDaoException：：GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo)以重新填充`m_pErrorInfo`数据成员。

## <a name="see-also"></a>另请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
