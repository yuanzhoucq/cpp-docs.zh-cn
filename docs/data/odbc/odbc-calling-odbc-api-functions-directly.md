---
title: ODBC： 直接调用 ODBC API 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 386bc03234ccb29b293a413944f221189f466c80
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336590"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC：直接调用 ODBC API 函数
数据库类为提供更简单的接口[数据源](../../data/odbc/data-source-odbc.md)比 ODBC。 因此，类不封装所有 ODBC API。 类的功能以外的任何功能，您必须直接调用 ODBC API 函数。 例如，你必须调用 ODBC 目录函数 (`::SQLColumns`， `::SQLProcedures`， `::SQLTables`，等等) 直接。  
  
> [!NOTE]
>  ODBC 数据源是可通过 MFC ODBC 类，如本主题中所述或 MFC 数据访问对象 (DAO) 类的访问。  
  
 若要调用 ODBC API 函数直接，必须采取步骤和在没有框架调用采取的步骤相同。 这些步骤：  
  
-   为该调用将返回任何结果分配存储空间。  
  
-   通过 ODBC`HDBC`或`HSTMT`处理，具体取决于函数的参数签名。 使用[AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv)宏来检索 ODBC 句柄。  
  
     成员变量`CDatabase::m_hdbc`和`CRecordset::m_hstmt`，以便不需要分配并初始化这些自己。  
  
-   可能是调用其他 ODBC 函数来准备或执行的主要调用后续操作。  
  
-   完成后，解除分配存储空间。  
  
 有关这些步骤的详细信息，请参阅[开放式数据库连接 (ODBC)](https://msdn.microsoft.com/library/ms710252.aspx) MSDN 文档中的 SDK。  
  
 除了这些步骤中，您需要采取额外步骤来检查函数返回值，确保您的程序不等待的异步调用完成后，依次类推。 可以通过使用 AFX_SQL_ASYNC 和 AFX_SQL_SYNC 宏来简化这些最后几个步骤。 有关详细信息，请参阅[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)中*MFC 参考*。  

## <a name="see-also"></a>请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)
