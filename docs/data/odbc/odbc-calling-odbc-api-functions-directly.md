---
title: "ODBC：直接调用 ODBC API 函数 | Microsoft Docs"
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
  - "API [C++], 调用"
  - "目录函数 (ODBC)"
  - "目录函数 (ODBC), 调用"
  - "直接 ODBC API 调用"
  - "ODBC [C++], API 函数"
  - "ODBC [C++], 目录函数"
  - "ODBC API 函数 [C++]"
  - "ODBC API 函数 [C++], 调用"
  - "ODBC 类 [C++], 与 ODBC API 的比较"
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ODBC：直接调用 ODBC API 函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

数据库类提供的到[数据源](../../data/odbc/data-source-odbc.md)的接口比 ODBC 提供的更为简单。  因此，这些类不封装全部的 ODBC API。  对于这些类的功能以外的任何功能，都必须直接调用 ODBC API 函数。  例如，您必须直接调用 ODBC 目录函数（**::SQLColumns**、**::SQLProcedures**、**::SQLTables** 和其他一些函数）。  
  
> [!NOTE]
>  通过 MFC ODBC 类（如本主题所述）或通过 MFC 数据访问对象 \(DAO\) 类，都可以访问 ODBC 数据源。  
  
 若要直接调用 ODBC API 函数，必须采取的步骤和在无框架情况下调用所采取的步骤相同。  这些步骤是：  
  
-   为调用返回的任何结果分配存储空间。  
  
-   根据函数的参数签名，传递 ODBC **HDBC** 或 **HSTMT** 句柄。  使用 [AFXGetHENV](../Topic/AfxGetHENV.md) 宏检索 ODBC 句柄。  
  
     因为成员变量 **CDatabase::m\_hdbc** 和 **CRecordset::m\_hstmt** 是可用的，所以不需要您亲自分配和初始化这些变量。  
  
-   也许还要调用其他的 ODBC 函数为主调用做准备或者跟在主调用之后。  
  
-   调用完成后，解除分配存储空间。  
  
 有关这些步骤的更多信息，请参见 MSDN 文档中的[开放式数据库连接 \(ODBC\)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) SDK。  
  
 除这些步骤之外，您需要采取另外一些步骤检查函数返回值，确保您的程序不是在等待完成一个异步调用等。  可以通过使用 `AFX_SQL_ASYNC` 和 `AFX_SQL_SYNC` 宏简化最后的这些步骤。  有关更多信息，请参见《MFC 参考》中的[宏和全局](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)。  
  
## 请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)