---
title: 异常： 数据库异常 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 804e93c45e4fb4d95b097c78d20df6a252626a36
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387362"
---
# <a name="exceptions-database-exceptions"></a>异常：数据库异常

本文介绍如何处理数据库异常。 在本文中的材料的大多数应用是否正在使用的 MFC 类开放式数据库连接 (ODBC) 或 MFC 类的数据访问对象 (DAO)。 显式标记为特定于一个或另一个模型的材料。 包括以下主题：

- [异常处理的方法](#_core_approaches_to_exception_handling)

- [数据库异常处理示例](#_core_a_database_exception.2d.handling_example)

##  <a name="_core_approaches_to_exception_handling"></a> 异常处理的方法

是否要使用 DAO 还是 ODBC，方法是相同的。

应始终编写异常处理程序来处理异常情况。

捕获数据库异常的最实用方法是使用异常情况下测试应用程序。 确定可能发生的异常可能会在代码中，操作并强制执行要发生的异常。 然后检查跟踪输出，查看引发哪些异常，或检查在调试器中返回的错误信息。 这样您就知道的返回的代码，会看到正在使用的异常方案。

### <a name="error-codes-used-for-odbc-exceptions"></a>用于 ODBC 的异常的错误代码

除了由框架定义的返回代码，其中包含名称的窗体**AFX_SQL_ERROR_XXX**，有些[CDBExceptions](../mfc/reference/cdbexception-class.md)基于[ODBC](../data/odbc/odbc-basics.md)返回代码。 此类异常的返回代码其名称分别为窗体**SQL_ERROR_XXX**。

返回代码 — 同时框架定义和 ODBC 定义 — 数据库类可以返回下有介绍[m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode)类的数据成员`CDBException`。 ODBC SDK 中提供了有关由 ODBC 定义的返回代码的其他信息*程序员参考*MSDN 库中。

### <a name="error-codes-used-for-dao-exceptions"></a>使用 DAO 异常的错误代码

对于 DAO 的例外，通常提供了详细信息。 您可以通过三个数据成员的已捕获访问错误信息[CDaoException](../mfc/reference/cdaoexception-class.md)对象：

- [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)包含一个指向[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)对象，它封装与数据库相关联的错误对象的 DAO 的集合中的错误信息。

- [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)包含 MFC DAO 类中扩展的错误代码。 这些错误代码，其名称分别为窗体**AFX_DAO_ERROR_XXX**，记录中的数据成员下`CDaoException`。

- [m_scode](../mfc/reference/cdaoexception-class.md#m_scode)包含一个 OLE **SCODE**从 DAO，如果适用。 很少需要具有此错误代码，但是工作。 通常，其他两个数据成员中提供了详细信息。 了解更多的数据成员**SCODE**值。

在类下提供了有关 DAO 错误、 DAO 错误对象类型和 DAO 错误集合的其他信息[CDaoException](../mfc/reference/cdaoexception-class.md)。

##  <a name="_core_a_database_exception.2d.handling_example"></a> 数据库异常处理示例

下面的示例尝试构造[CRecordset](../mfc/reference/crecordset-class.md)-派生的对象在具有堆**新**运算符和然后打开记录集 （适用于 ODBC 数据源）。 DAO 类的类似示例，请参阅"DAO 异常下面的示例"。

### <a name="odbc-exception-example"></a>ODBC 异常示例

[开放](../mfc/reference/crecordset-class.md#open)成员函数可能会引发异常 (类型的[CDBException](../mfc/reference/cdbexception-class.md) ODBC 类)，因此此代码方括号`Open`调用**重**块。 后续**捕获**块将捕获`CDBException`。 可以检查异常对象本身，名为`e`，但在这种情况下是只需知道要创建记录集的尝试已失败。 **捕获**块显示一个消息框，并通过删除记录集对象清除。

[!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]

### <a name="dao-exception-example"></a>DAO 异常示例

DAO 示例适用于 ODBC 示例类似，但通常可以检索更多类型的信息。 下面的代码还会尝试打开一个记录集。 如果该尝试会引发异常，您可以检查错误的信息的异常对象的数据成员。 与前面的 ODBC 示例，它可能是因为不足以确定创建记录集的尝试失败。

[!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]

此代码获取错误消息字符串从[m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)异常对象的成员。 MFC 填充此成员时引发的异常。

有关通过返回的错误信息的讨论`CDaoException`对象，请参阅类[CDaoException](../mfc/reference/cdaoexception-class.md)并[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)。

当您正在使用 Microsoft Jet (.mdb) 数据库，并在大多数情况下使用 ODBC 时，将只有一个错误对象。 在极少数情况下时使用的 ODBC 数据源，并且有多个错误，可以循环遍历返回的错误数基于 DAO 的错误集合[CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount)。 每次循环时，调用[CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo)重填`m_pErrorInfo`数据成员。

## <a name="see-also"></a>请参阅

[异常处理](../mfc/exception-handling-in-mfc.md)

