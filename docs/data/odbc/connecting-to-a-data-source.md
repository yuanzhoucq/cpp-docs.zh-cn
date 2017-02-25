---
title: "连接到数据源 | Microsoft Docs"
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
  - "连接 [C++], 数据源"
  - "数据源 [C++], 连接"
  - "数据库连接 [C++], MFC ODBC 类"
  - "数据库连接 [C++], ODBC"
  - "数据库 [C++], 连接"
  - "ODBC 连接 [C++], using"
  - "ODBC 数据源 [C++], 连接"
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 连接到数据源
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ODBC 数据源是数据、访问该数据所需的信息以及该数据源位置的特定集合，其中的数据源位置可用数据源名称描述。  从程序的观点看，数据源包括数据、DBMS、网络（如果有）和 ODBC。  
  
 若要访问数据源提供的数据，您的程序必须首先建立到数据源的连接。  通过该连接管理所有的数据访问。  
  
 数据源连接通过类 [CDatabase](../../mfc/reference/cdatabase-class.md) 进行封装。  `CDatabase` 对象连接到数据源后，您就可以：  
  
-   构造从表或查询中选择记录的 [recordsets](../../mfc/reference/crecordset-class.md)。  
  
-   管理[事务](../../data/odbc/transaction-odbc.md)，如果数据源支持所需的事务级别，则可以批处理更新以使所有更改同时提交到数据源，或者整个事务回滚以保持数据源不变。  
  
-   紧接执行语句。[SQL](../../data/odbc/sql.md)  
  
 完成数据源连接后，关闭 `CDatabase` 对象，并且销毁该对象或者再使用它建立新的连接。  有关数据源连接的更多信息，请参见[数据源 \(ODBC\)](../../data/odbc/data-source-odbc.md)。  
  
## 请参阅  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)