---
title: "可以对默认代码做的更改（MFC 数据访问） | Microsoft Docs"
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
  - "记录视图 [C++], 自定义默认代码"
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 可以对默认代码做的更改（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)为你编写记录集类，以便选择单一表格中的所有记录。  你通常还可以采用下列一种或多种方式修改该行为：  
  
-   为记录集设置筛选器或排序顺序。  在创建记录集对象之后和调用其 **Open** 成员函数之前，在 `OnInitialUpdate` 中执行此操作。  有关详细信息，请参阅[记录集：筛选记录 \(ODBC\)](../data/odbc/recordset-filtering-records-odbc.md) 和[记录集：排序记录 \(ODBC\)](../data/odbc/recordset-sorting-records-odbc.md)。  
  
-   确定记录集的参数。  筛选后指定运行时的实际参数值。  有关详细信息，请参阅[记录集：确定记录集的参数 \(ODBC\)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
-   将自定义 SQL 字符串传递给 [Open](../Topic/CRecordset::Open.md) 成员函数。  有关使用此技术完的操作的讨论，请参阅 [SQL：自定义记录集的 SQL 语句 \(ODBC\)](../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md)。  
  
## 请参阅  
 [使用记录视图](../data/using-a-record-view-mfc-data-access.md)