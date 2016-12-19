---
title: "使用 DAO 还是 ODBC？ | Microsoft Docs"
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
  - "DAO [C++], 与 ODBC"
  - "数据库类 [C++], DAO"
  - "数据库类 [C++], ODBC"
  - "ODBC [C++], 与 DAO"
ms.assetid: 9f67613f-0056-4ece-8c3a-9872e9563d57
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 DAO 还是 ODBC？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  从 Visual C\+\+ .NET 起，Visual C\+\+ 环境和向导不再支持 DAO（不过提供了 DAO 类，仍可供您使用）。  Microsoft 建议对新项目使用 OLE DB 模板或 ODBC。  DAO 只应用于维护现有的应用程序。  
  
 使用哪一组 MFC 类？  这取决于具体要求：  
  
-   如果完全使用 ODBC 数据源，特别是在客户端\/服务器情形中，MFC ODBC 类提供更好的性能，则使用 ODBC 类。  
  
-   如果主要使用 Microsoft Jet \(.mdb\) 数据库，或者 Microsoft Jet 数据库引擎可以直接读取的其他数据库格式，则使用 DAO 类。  有关这些数据库的列表，请参见[使用 DAO 和 ODBC 可以访问哪些数据库？](../data/what-data-sources-can-i-access-with-dao-and-odbc-q.md)  
  
-   当需要 Microsoft Jet 数据库引擎的速度和 DAO 类的额外功能时，通过 DAO 类访问 ODBC 数据源。  
  
    > [!NOTE]
    >  DAO 需要额外的硬盘空间。  
  
 DAO 类具有以下优点：  
  
-   在某些情况下，特别是在使用 Microsoft Jet \(.mdb\) 数据库时，具有更佳的性能。  
  
-   与 ODBC 类兼容并且与 Microsoft Access Basic 和 Microsoft Visual Basic 兼容。  
  
-   可以访问校验规则。  
  
-   能够指定表之间的关系。  
  
-   更丰富的数据访问模型，并且支持数据定义语言 \(DDL\) 和数据操作语言 \(DML\)。  有关更多信息，请参见 [数据库定义和操作](../data/are-ddl-and-dml-supported-q.md)。  
  
 下表汇总了主要差异，以帮助您进行选择。  
  
### 在 MFC DAO 和 ODBC 类之间选择  
  
|可以进行下列操作|使用 DAO 类？|使用 ODBC 类？|  
|--------------|---------------|----------------|  
|访问 .MDB 文件|是|是|  
|访问 ODBC 数据源|是|是|  
|可用于 16 位|否|是|  
|可用于 32 位|是|是|  
|可用于 64 位|否|是|  
|数据库压缩|是|否|  
|数据库引擎支持|Microsoft Jet 数据库引擎|目标 DBMS|  
|DDL 支持|是|只通过直接 ODBC 调用|  
|DML 支持|是|是|  
|MFC 实现的特性|DAO 核心函数的“包装”|简化的抽象而不是 ODBC API 的“包装”|  
|优化|.mdb 文件 \(Microsoft Access\)|任何有相应驱动程序的 DBMS，特别是在客户端\/服务器情形中|  
|事务支持|基于每个解决方案，对于 ODBC 数据则基于每个数据库|基于每个数据库|  
  
 记住，ODBC 驱动程序的功能千差万别。  有关更多信息，请参见 ODBC Programmer's Reference（《 ODBC 程序员参考》）和 ODBC 驱动程序的帮助文件。  
  
## 请参阅  
 [关于数据访问的常见问题](../data/data-access-frequently-asked-questions-mfc-data-access.md)