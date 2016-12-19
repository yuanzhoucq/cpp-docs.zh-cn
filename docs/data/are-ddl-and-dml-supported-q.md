---
title: "是否支持 DDL 和 DML？ | Microsoft Docs"
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
  - "MFC ODBC 中的数据操作语言 [C++]"
  - "数据库 [C++], 在 DAO 中访问"
  - "数据库 [C++], DDL 访问权限"
  - "数据库 [C++], DML 访问权限"
  - "DDL [C++], MFC 支持"
  - "DML [C++]"
  - "DML [C++], MFC ODBC"
ms.assetid: 07f96d81-78d4-4bec-9138-b15d68fd5ce0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 是否支持 DDL 和 DML？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC DAO 类支持两种数据库访问：  
  
-   **数据定义语言 \(DDL\)** 可以创建和删除数据库，创建和删除表，定义表字段和索引，以及执行其他影响数据库结构的操作。  
  
-   **数据操作语言 \(DML\)** 可以运行查询、添加、删除和编辑记录，以及通过其他方式操作数据库的内容。  
  
 MFC ODBC 类仅支持 DML，但可以直接调用 ODBC API 函数来执行 DDL 任务。  
  
## 请参阅  
 [关于数据访问的常见问题](../data/data-access-frequently-asked-questions-mfc-data-access.md)