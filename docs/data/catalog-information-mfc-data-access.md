---
title: "目录信息（MFC 数据访问） | Microsoft Docs"
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
  - "目录信息数据库 [C++]"
  - "DAO [C++], 目录信息"
  - "数据库 [C++], 目录信息数据库"
  - "ODBC [C++], 目录信息"
  - "表 [C++]"
  - "表 [C++], 目录信息"
ms.assetid: c184e80f-ff17-409f-9df8-05275080bb8d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 目录信息（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

数据源表格中的信息可以包括表格名称和其中的列、表格权限、主键和外键的名称、有关预定义查询或存储过程的信息、有关表格索引的信息和有关表格的统计信息。  
  
 有关详细信息，请参阅[数据源：确定数据源 \(ODBC\) 的架构](../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)。  
  
> [!NOTE]
>  在 MFC DAO 类中，你可以获取如下所示的目录信息：使用 [CDaoDatabase::GetTableDefCount](../Topic/CDaoDatabase::GetTableDefCount.md) 和 [CDaoDatabase::GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md) 列举数据库中的表格并获取 [CDaoTableDefInfo](../mfc/reference/cdaotabledefinfo-structure.md) 结构中每个表格的信息。  
  
## 请参阅  
 [数据访问编程 \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)