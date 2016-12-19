---
title: "访问 ODBC 和 SQL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "API 调用 [C++], 直接调用 DAO 或 ODBC"
  - "ODBC [C++], API 函数"
  - "ODBC API 函数 [C++]"
  - "ODBC API 函数 [C++], 从 MFC 调用"
  - "SQL [C++], 调用 ODBC API 函数"
  - "Windows API [C++], 从 MFC 调用"
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 访问 ODBC 和 SQL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft 基础类库封装了许多 Windows API 调用，它还让您直接调用任何 Windows API 函数。  至于 ODBC API，数据库类也提供了同样的灵活性。  尽管数据库类极大地为您减少了 ODBC 的复杂性，但是您可以在程序中的任何位置直接调用 ODBC API 函数。  
  
 与此相似，数据库类可使您无需大量使用 [SQL](../../data/odbc/sql.md)，但是如果您愿意，也可以直接使用 SQL。  可以自定义记录集对象。方法是在打开记录集时传递一个自定义 SQL 语句（或者设置默认语句部分）。  还可以使用类 [CDatabase](../../mfc/reference/cdatabase-class.md) 的 [ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md) 成员函数直接进行 SQL 调用。  
  
 有关更多信息，请参见 [ODBC：直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)和 [SQL：执行直接 SQL 调用 \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)。  
  
## 请参阅  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)