---
title: 异常：“数据库异常”
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
ms.openlocfilehash: c279c5b788cc7bd8a68fe36128c116d8df91c2eb
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095823"
---
# <a name="exceptions-database-exceptions"></a>异常：“数据库异常”

本文介绍如何处理数据库异常。 本文中的大部分资料适用于是否使用开放式数据库连接（ODBC）的 MFC 类或用于数据访问对象（DAO）的 MFC 类。 特定于某个模型或其他模型的特定内容已显式标记。 包括以下主题：

- [异常处理方法](#_core_approaches_to_exception_handling)

- [数据库异常处理示例](#_core_a_database_exception.2d.handling_example)

##  <a name="_core_approaches_to_exception_handling"></a>异常处理方法

无论你使用的是 DAO （已过时）还是 ODBC，此方法都是相同的。

应始终编写异常处理程序来处理异常情况。

捕获数据库异常的最实用方法是测试应用程序的异常情况。 确定代码中某个操作可能出现的异常，并强制发生异常。 然后检查跟踪输出以查看引发的异常，或在调试器中检查返回的错误信息。 这使您可以了解您将在您使用的异常情况下看到哪些返回代码。

### <a name="error-codes-used-for-odbc-exceptions"></a>用于 ODBC 异常的错误代码

除了由框架定义的返回代码（名称格式为**AFX_SQL_ERROR_XXX**），某些[CDBExceptions](../mfc/reference/cdbexception-class.md)还基于[ODBC](../data/odbc/odbc-basics.md)返回代码。 此类异常的返回代码具有形式为**SQL_ERROR_XXX**的名称。

数据库类可以返回的返回代码（由框架定义和 ODBC 定义）记录在类`CDBException`的[m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode)数据成员下。 有关 ODBC 定义的返回代码的其他信息，请参阅 MSDN Library 中的 ODBC SDK*程序员参考*。

### <a name="error-codes-used-for-dao-exceptions"></a>用于 DAO 异常的错误代码

对于 DAO 例外，通常有更多信息。 可以通过捕获的[CDaoException](../mfc/reference/cdaoexception-class.md)对象的三个数据成员访问错误信息：

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)包含指向[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)对象的指针，该对象封装了 DAO 与数据库关联的错误对象集合中的错误信息。

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)包含 MFC DAO 类中的扩展错误代码。 这些错误代码具有**AFX_DAO_ERROR_XXX**形式的名称，记录在中`CDaoException`的数据成员下。

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode)包含 DAO 中的 OLE **scode** （如果适用）。 不过，您很少需要使用此错误代码。 通常，其他两个数据成员中提供了详细信息。 有关**SCODE**值的详细信息，请参阅数据成员。

类[CDaoException](../mfc/reference/cdaoexception-class.md)下提供了有关 dao 错误、dao 错误对象类型和 dao 错误集合的其他信息。

##  <a name="_core_a_database_exception.2d.handling_example"></a>数据库异常处理示例

下面的示例尝试使用**new**运算符在堆上构造一个[CRecordset](../mfc/reference/crecordset-class.md)派生的对象，然后打开该记录集（对于 ODBC 数据源）。 有关 DAO 类的类似示例，请参阅下面的 "DAO 异常示例"。

### <a name="odbc-exception-example"></a>ODBC 异常示例

[Open](../mfc/reference/crecordset-class.md#open)成员函数可能会引发异常（针对 ODBC 类的类型为[CDBException](../mfc/reference/cdbexception-class.md) ），因此，此代码将使用`Open` **try**块将调用括起来。 后续**catch**块将捕获`CDBException`。 您可以检查已调用`e`的异常对象本身，但在这种情况下，必须知道创建记录集的尝试已失败。 **Catch**块将显示一个消息框，并通过删除记录集对象来清除该消息框。

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>DAO 异常示例

DAO 示例与 ODBC 的示例类似，但您通常可以检索更多种类的信息。 下面的代码还尝试打开记录集。 如果此尝试引发异常，则可以检查 exception 对象的数据成员以获取错误信息。 与上一个 ODBC 示例一样，可能足以知道创建记录集的尝试失败。

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

此代码从 exception 对象的[m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)成员获取错误消息字符串。 MFC 在引发异常时填充此成员。

有关`CDaoException`对象返回的错误信息的讨论，请参阅[CDaoException](../mfc/reference/cdaoexception-class.md)和[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)类。

使用 Microsoft Jet （.mdb）数据库时，在大多数情况下，当您使用 ODBC 时，将只有一个错误对象。 在极少数情况下，当你使用 ODBC 数据源并且存在多个错误时，可以根据[CDaoException：： GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount)返回的错误数循环浏览 DAO 的错误集合。 每次通过循环时，调用[CDaoException：： GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo)来重新填充`m_pErrorInfo`数据成员。

## <a name="see-also"></a>请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)
