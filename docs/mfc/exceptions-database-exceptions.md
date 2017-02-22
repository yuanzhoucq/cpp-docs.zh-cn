---
title: "异常：数据库异常 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO [C++], 异常"
  - "数据库异常 [C++]"
  - "数据库 [C++], 异常处理"
  - "错误代码 [C++], 数据库异常处理"
  - "异常处理 [C++], 数据库"
  - "异常 [C++], 数据库"
  - "ODBC [C++], 异常"
  - "ODBC 异常 [C++]"
ms.assetid: 28daf260-f824-4be6-aecc-1f859e6dec26
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 异常：数据库异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明如何处理数据库异常。  本文的多数材料应用您是否使用开放式数据库连接 \(ODBC\) 的 MFC 类或数据访问对象 \(DAO\) 的 MFC 类。  对或其他模型的物质特定显式标记。  主题包括：  
  
-   [异常处理方法](#_core_approaches_to_exception_handling)  
  
-   [数据库异常处理的示例](#_core_a_database_exception.2d.handling_example)  
  
##  <a name="_core_approaches_to_exception_handling"></a> 异常处理方法  
 无论使用 DAO 或 ODBC，方法都是相同的。  
  
 应编写异常处理程序来处理异常情况。  
  
 捕捉到的数据库异常的最实用的方法是测试有异常方案的应用程序。  确定可能发生异常的代码的操作，并强制发生异常。  然后检查跟踪的输出查看引发何种异常，或在调试器中检查返回的错误信息。  通知哪些返回代码将显示所使用的异常方案。  
  
### 用于 ODBC 异常的错误代码  
 除了框架定义的返回代码之外，则窗体的 **AFX\_SQL\_ERROR\_XXX**的名称，某些[CDBExceptions](../mfc/reference/cdbexception-class.md) 是基于[ODBC](../data/odbc/odbc-basics.md) 的返回代码。  此类异常的返回代码具有窗体 **SQL\_ERROR\_XXX**的名称。  
  
 返回代码 \-由 Framework 和 ODBC 定义的数据库类能返回在 [m\_nRetCode](../Topic/CDBException::m_nRetCode.md) 类的 `CDBException`的数据成员的文档。  有关 ODBC 定义的返回代码的附加信息可以在 MSDN 类库中的 ODBC SDK 的*程序员参考手册*中找到。  
  
### 用于 DAO 异常的错误代码  
 对于DAO异常，更多信息通常可用。  通过 [CDaoException](../mfc/reference/cdaoexception-class.md) 对象所捕获的三个数据成员，您可以访问错误信息：  
  
-   包含[m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) 包含[CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)对象的指针，该对象为封装在对象集合的 DAO 错误的错误信息与数据库中的对象。  
  
-   [m\_nAfxDaoError](../Topic/CDaoException::m_nAfxDaoError.md) 包含从 MFC DAO 类的扩展的错误代码。  这些错误代码，所以窗体**AFX\_DAO\_ERROR\_XXX**的名称，记录在`CDaoException`的数据成员中。  
  
-   如果可以，[m\_scode](../Topic/CDaoException::m_scode.md)包含DAO 的 OLE `SCODE`。  然而，你很少需要使用此错误代码。  通常更多信息可用于其他两个数据成员。  对于更多数据成员,参见有关 `SCODE` 值。  
  
 有关DAO 错误、DAO 错误对象类型和 DAO 错误的附加信息可用于 [CDaoException](../mfc/reference/cdaoexception-class.md)类。  
  
##  <a name="_core_a_database_exception.2d.handling_example"></a> 数据库异常处理的示例  
 下面的示例尝试构造 [CRecordset](../mfc/reference/crecordset-class.md)\- 在堆的派生对象,使用 **new** 运算符，然后打开记录集 \(对于 ODBC 数据源\)。  有关 DAO 类的类似示例，请参见 “DAO异常示例”下。  
  
### ODBC 异常示例  
 [打开](../Topic/CRecordset::Open.md) 成员函数可能会引发异常 \(ODBC 类的类型，[CDBException](../mfc/reference/cdbexception-class.md) \)，因此该代码使用括号 **try** 块的 **打开** 调用。  后续 **catch** 块将捕获 `CDBException`。  可以检查异常对象，调用 `e`，但在这种情况下，足以了解尝试创建记录集已经失败。  **catch** 块显示消息并通过删除记录集对象清理。  
  
 [!code-cpp[NVC_MFCDatabase#36](../mfc/codesnippet/CPP/exceptions-database-exceptions_1.cpp)]  
  
### DAO 异常示例  
 DAO 的示例类似于 ODBC 的示例，但是，通常可以检索更多信息。  下面代码还尝试打开记录集。  如果该尝试引发异常，您可以检查异常对象的数据成员的错误信息。  前面的ODBC示例，其足以知道尝试创建记录集失败。  
  
 [!code-cpp[NVC_MFCDatabase#37](../mfc/codesnippet/CPP/exceptions-database-exceptions_2.cpp)]  
  
 此代码从异常对象的 [m\_pErrorInfo](../Topic/CDaoException::m_pErrorInfo.md) 成员获取错误消息的字符串。  当引发异常时，MFC 填充此成员。  
  
 由 `CDaoException` 对象返回的错误信息的讨论，请参见类[CDaoException](../mfc/reference/cdaoexception-class.md) [CDaoErrorInfo](../mfc/reference/cdaoerrorinfo-structure.md)。  
  
 在使用 Microsoft Jet \(.mdb\) 数据库时，许多情况下，当使用 ODBC 时，只有错误对象。  在极少数情况下，当使用 ODBC 数据源时，有多重错误，也可以通过 DAO 的 [CDaoException::GetErrorCount](../Topic/CDaoException::GetErrorCount.md)返回的基于错误数的错误集合。  每次循环，请调用 [CDaoException::GetErrorInfo](../Topic/CDaoException::GetErrorInfo.md) 重新填充 `m_pErrorInfo` 数据成员。  
  
## 请参阅  
 [异常处理](../mfc/exception-handling-in-mfc.md)