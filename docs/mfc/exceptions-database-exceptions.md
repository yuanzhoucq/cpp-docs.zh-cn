---
title: 异常： 数据库异常 |Microsoft 文档
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
ms.openlocfilehash: 2168bc530accfdde6fad4d41cd68e94d3088f153
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-database-exceptions"></a>异常：数据库异常
此文章介绍了如何处理数据库异常。 你正在使用的 MFC 类开放式数据库连接 (ODBC) 或 MFC 类数据访问对象 (DAO) 可应用于大部分这篇文章中的材料。 显式标记为特定于一个或另一模型的材料。 包括以下主题：  
  
-   [对异常处理的方法](#_core_approaches_to_exception_handling)  
  
-   [数据库异常处理示例](#_core_a_database_exception.2d.handling_example)  
  
##  <a name="_core_approaches_to_exception_handling"></a> 对异常处理的方法  
 无论你正在使用 DAO 或 ODBC，这种方法都是相同的。  
  
 你应始终编写异常处理程序来处理异常条件。  
  
 捕获数据库异常的最有效方法是测试应用程序与异常情况。 确定可能的异常时，可能会出现在代码中，运算并强制发生的异常。 然后检查以查看引发哪些异常，跟踪输出，或检查在调试器中的返回的错误信息。 这样，你知道的返回的代码，你将看到为你使用的异常方案。  
  
### <a name="error-codes-used-for-odbc-exceptions"></a>用于 ODBC 异常的错误代码  
 除了由框架定义的返回代码，还可以在窗体的名称**AFX_SQL_ERROR_XXX**，有些[CDBExceptions](../mfc/reference/cdbexception-class.md)基于[ODBC](../data/odbc/odbc-basics.md)返回代码。 具有窗体的名称，此类异常的返回代码**SQL_ERROR_XXX**。  
  
 返回代码-框架定义，又 ODBC 定义-数据库类可以返回记录在[m_nRetCode](../mfc/reference/cdbexception-class.md#m_nretcode)类数据成员`CDBException`。 ODBC SDK 中提供了有关由 ODBC 的返回代码的其他信息*程序员参考*MSDN 库中。  
  
### <a name="error-codes-used-for-dao-exceptions"></a>用于 DAO 异常的错误代码  
 对于 DAO 异常，通常提供了详细信息。 您可以通过捕获的三个数据成员访问错误信息[CDaoException](../mfc/reference/cdaoexception-class.md)对象：  
  
-   [m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)包含的指针[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)封装与数据库关联的错误对象 DAO 的集合中的错误信息的对象。  
  
-   [m_nAfxDaoError](../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)包含来自 MFC DAO 类扩展的错误代码。 这些错误代码，具有名称，在窗体**AFX_DAO_ERROR_XXX**，记录中的数据成员下`CDaoException`。  
  
-   [m_scode](../mfc/reference/cdaoexception-class.md#m_scode)包含 OLE`SCODE`从 DAO，如果适用。 很少需要与此错误代码，但是工作。 通常的其他两个数据成员中提供了详细信息。 请参阅，了解有关详细信息的数据成员`SCODE`值。  
  
 在类下提供了有关 DAO 错误、 DAO 错误对象类型和 DAO 错误集合的其他信息[CDaoException](../mfc/reference/cdaoexception-class.md)。  
  
##  <a name="_core_a_database_exception.2d.handling_example"></a> 数据库异常处理示例  
 下面的示例尝试构造[CRecordset](../mfc/reference/crecordset-class.md)-派生对象上具有堆**新**运算符和然后打开的记录集 （ODBC 数据源）。 DAO 类的类似示例，请参阅"DAO 异常示例"下面。  
  
### <a name="odbc-exception-example"></a>ODBC 异常示例  
 [打开](../mfc/reference/crecordset-class.md#open)成员函数可能会引发异常 (类型的[CDBException](../mfc/reference/cdbexception-class.md) ODBC 类)，因此该代码方括号**打开**调用**重**块。 后续**捕获**块将捕获`CDBException`。 你可以检查异常对象本身，调用`e`，但在这种情况下就可以知道创建记录集的尝试已失败。 **捕获**块显示一个消息框，并通过删除记录集对象清理。  
  
 [!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/cpp/exceptions-database-exceptions_1.cpp)]  
  
### <a name="dao-exception-example"></a>DAO 异常示例  
 DAO 示例是类似于 ODBC 的示例，但你通常可以检索更多类型的信息。 下面的代码也尝试打开记录集。 如果该尝试会引发异常，你可以检查错误信息的异常对象的数据成员。 因为与前面的 ODBC 示例，它可能是足够，以了解创建记录集的尝试失败。  
  
 [!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/cpp/exceptions-database-exceptions_2.cpp)]  
  
 此代码获取错误消息字符串从[m_pErrorInfo](../mfc/reference/cdaoexception-class.md#m_perrorinfo)异常对象的成员。 会引发异常时，MFC 将填充此成员。  
  
 有关通过返回的错误信息的讨论`CDaoException`对象，请参阅类[CDaoException](../mfc/reference/cdaoexception-class.md)和[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)。  
  
 当您正在使用 Microsoft Jet (.mdb) 数据库，并在大多数情况下在使用 ODBC 时，将只有一个对象时出错。 在极少数情况下当你使用 ODBC 数据源，且有多个错误，可以循环访问返回的错误数基于 DAO 的错误集合[CDaoException::GetErrorCount](../mfc/reference/cdaoexception-class.md#geterrorcount)。 每次执行循环时，调用[CDaoException::GetErrorInfo](../mfc/reference/cdaoexception-class.md#geterrorinfo)重填`m_pErrorInfo`数据成员。  
  
## <a name="see-also"></a>请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)

