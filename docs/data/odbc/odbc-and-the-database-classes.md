---
title: "ODBC 和数据库类 | Microsoft Docs"
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
  - "数据库类 [C++], ODBC"
  - "MFC [C++], ODBC 和"
  - "ODBC API 函数 [C++]"
  - "ODBC 类 [C++], MFC 数据库类"
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ODBC 和数据库类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC ODBC 数据库类封装了 ODBC API 函数调用，您通常在 [CDatabase](../../mfc/reference/cdatabase-class.md) 和 [CRecordset](../../mfc/reference/crecordset-class.md) 类的成员函数中要用到这些函数调用。  例如，复杂的 ODBC 调用序列、返回记录到存储位置的绑定、错误情况的处理以及数据库类为您管理的其他操作。  因此，您使用相当简单的类接口就可通过记录集对象处理记录。  
  
> [!NOTE]
>  通过 MFC ODBC 类（如本主题所述）或通过 MFC 数据访问对象 \(DAO\) 类，都可以访问 ODBC 数据源。  
  
 尽管数据库类封装了 ODBC 功能，但它们不提供一对一的 ODBC API 函数映射。  数据库类提供更高级的抽象，模仿在 Microsoft Access 和 Microsoft Visual Basic 中找到的数据访问对象。  有关更多信息，请参见[什么是 MFC 数据库编程模型？](../../data/what-is-the-mfc-database-programming-model-q.md)  
  
## 请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)