---
title: "动态集的 ODBC 驱动程序要求 | Microsoft Docs"
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
  - "驱动程序, 对于动态集"
  - "驱动程序, ODBC"
  - "动态集"
  - "ODBC 驱动程序, 动态集"
  - "ODBC 记录集, 动态集"
  - "记录集, 动态集"
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 动态集的 ODBC 驱动程序要求
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 MFC ODBC 数据库类中，动态集是具有动态属性的记录集。这些动态集以某些方式与数据源保持同步。  MFC 动态集（不是仅向前记录集）需要具有 2 级 API 一致性的 ODBC 驱动程序。  如果您的[数据源](../../data/odbc/data-source-odbc.md)驱动程序符合 1 级 API 集，则仍能使用可更新和只读的快照以及仅向前记录集，但不能使用动态集。  但是只要 1 级驱动程序支持扩展的获取和键集驱动游标，它就可以支持动态集。  
  
 在 ODBC 术语中，动态集和快照都称为“游标”。  游标是用于在记录集中跟踪其位置的一种机制。  有关动态集驱动程序要求的更多信息，请参见[动态集](../../data/odbc/dynaset.md)。  有关游标的更多信息，请参见 MSDN 文档中的[开放式数据库连接 \(ODBC\)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) SDK。  
  
> [!NOTE]
>  对于可更新记录集，ODBC 驱动程序必须支持定位更新语句或 **::SQLSetPos** ODBC API 函数。  如果这两个都支持，则 MFC 使用 **::SQLSetPos** 函数以提高效率。  另外还有一种选择，对于快照您可以使用游标库。游标库提供可更新快照所需要的支持（静态游标和定位更新语句）。  
  
## 请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)