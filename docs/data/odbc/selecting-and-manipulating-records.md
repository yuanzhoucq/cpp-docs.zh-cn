---
title: "选择和操作记录 | Microsoft Docs"
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
  - "ODBC 记录集, 选择记录"
  - "记录选择, MFC ODBC 类"
  - "记录, 选择"
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 选择和操作记录
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 SQL **SELECT** 语句从数据源选择记录时，通常会得到一个结果集，即一组来自表或查询的记录。  通过数据库类，可以使用记录集对象来选择和访问结果集。  “记录集”对象是从类 [CRecordset](../../mfc/reference/crecordset-class.md) 派生的特定于应用程序的类的对象。  当定义一个记录集类时，需要指定与之相关的数据源、要使用的表和表的列。  MFC 应用程序向导或“添加类”（如[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述）将创建一个连接到某个特定数据源的类。  该向导将编写类 `CRecordset` 的 [GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md) 成员函数以返回表名。  有关使用向导创建记录集类的更多信息，请参见[数据库支持，MFC 应用程序向导](../../mfc/reference/database-support-mfc-application-wizard.md)和[添加 MFC ODBC 使用者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)。  
  
 运行时使用 [CRecordset](../../mfc/reference/crecordset-class.md) 对象，您可以：  
  
-   检查当前记录的数据字段。  
  
-   筛选记录集或对记录集进行排序。  
  
-   自定义默认的 SQL **SELECT** 语句。  
  
-   在选定的记录中滚动。  
  
-   添加、更新或删除记录（如果数据源和记录集都是可更新的）。  
  
-   测试记录集是否允许再次查询并刷新记录集的内容。  
  
 记录集对象使用完毕后，请关闭并且销毁它。  有关记录集的更多信息，请参见[记录集 \(ODBC\)](../../data/odbc/recordset-odbc.md)。  
  
## 请参阅  
 [ODBC 和 MFC](../../data/odbc/odbc-and-mfc.md)