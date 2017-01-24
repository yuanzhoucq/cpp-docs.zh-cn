---
title: "记录视图（MFC 数据访问） | Microsoft Docs"
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
  - "DAO [C++], 记录视图"
  - "数据库 [C++], 记录视图"
  - "窗体 [C++], 数据访问任务"
  - "MFC [C++], 记录视图"
  - "ODBC 记录集 [C++], 记录视图"
  - "记录视图 [C++]"
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 记录视图（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本部分仅适用于 MFC ODBC 和 DAO 类。  有关 OLE DB 记录视图的详细信息，请参阅 [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) 和[使用 OLE DB 记录视图](../data/oledb/using-ole-db-record-views.md)。  
  
 类库提供了类 [CRecordView](../mfc/reference/crecordview-class.md) 和类 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) 以便支持基于窗体的数据访问应用程序。  记录视图是一个窗体视图对象，其控件直接映射到[记录集](../data/odbc/recordset-odbc.md)对象的字段数据成员（间接映射到查询结果的相应列或数据源的相应表格）。  和其基类 [CFormView](../mfc/reference/cformview-class.md) 一样，`CRecordView` 和 `CDaoRecordView` 也是基于对话框模板资源。  
  
## 窗体用途  
 窗体对于各种数据访问任务十分有用：  
  
-   输入数据  
  
-   执行数据只读检查  
  
-   更新数据  
  
## 关于记录视图的其他阅读材料  
 本主题中的材料同时适用于基于 ODBC 和基于 DAO 的类。  将 `CRecordView` 用于 ODBC并且将 `CDaoRecordView` 用于 DAO。  
  
 包括以下主题：  
  
-   [记录视图类的功能](../data/features-of-record-view-classes-mfc-data-access.md)  
  
-   [记录视图的数据交换](../data/data-exchange-for-record-views-mfc-data-access.md)  
  
-   [您在使用记录视图中的角色](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)  
  
-   [设计和创建记录视图](../data/designing-and-creating-a-record-view-mfc-data-access.md)  
  
-   [使用记录视图](../data/using-a-record-view-mfc-data-access.md)  
  
## 请参阅  
 [数据访问编程 \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)   
 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)