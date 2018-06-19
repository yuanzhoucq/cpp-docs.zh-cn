---
title: ODBC： 直接调用 ODBC API 函数 |Microsoft 文档
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
ms.openlocfilehash: 55b95c5dd48631f9c724aebd163ce948c3469850
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089708"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC：直接调用 ODBC API 函数
数据库类为提供更简单的接口[数据源](../../data/odbc/data-source-odbc.md)比 ODBC。 因此，类不封装所有 ODBC API。 对于任何类的功能以外的功能，必须直接调用 ODBC API 函数。 例如，你必须调用 ODBC 目录函数 (**:: SQLColumns**， **:: SQLProcedures**， **:: SQLTables**，等) 直接。  
  
> [!NOTE]
>  ODBC 数据源是通过 MFC ODBC 类，如本主题中所述，或通过 MFC 数据访问对象 (DAO) 类访问。  
  
 若要调用 ODBC API 函数直接，必须采取步骤和在无框架情况下的调用采取的步骤相同。 这些步骤：  
  
-   将存储分配为该调用将返回任何结果。  
  
-   将传递一个 ODBC **HDBC**或**HSTMT**处理，具体取决于该函数的参数签名。 使用[AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv)宏来检索 ODBC 句柄。  
  
     成员变量**CDatabase::m_hdbc**和**CRecordset::m_hstmt**都可用，因此不需要分配和初始化这些自己。  
  
-   可能是调用其他 ODBC 函数，来准备或执行主调用后续操作。  
  
-   完成后，取消分配存储空间。  
  
 有关这些步骤的详细信息，请参阅[开放式数据库连接 (ODBC)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) MSDN 文档中的 SDK。  
  
 除了这些步骤，需要执行额外的步骤来检查函数返回值，请确保你的程序未等待的异步调用完成后，依次类推。 你可以通过使用来简化这些最后一个步骤`AFX_SQL_ASYNC`和`AFX_SQL_SYNC`宏。 有关详细信息，请参阅[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)中*MFC 参考*。  

  
## <a name="see-also"></a>请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)
