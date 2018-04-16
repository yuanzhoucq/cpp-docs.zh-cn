---
title: "记录视图 （MFC 数据访问） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e698cad29405fce4b5a0d23e166217502753dc1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="record-views--mfc-data-access"></a>记录视图（MFC 数据访问）
本部分仅适用于 MFC ODBC 类。 有关 OLE DB 记录视图的信息，请参阅[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)和[使用 OLE DB 记录视图](../data/oledb/using-ole-db-record-views.md)。  
  
 若要支持基于窗体的数据访问应用程序，该类库提供类[CRecordView](../mfc/reference/crecordview-class.md)。 记录视图是窗体视图对象，其控件直接对应的字段数据成员[记录集](../data/odbc/recordset-odbc.md)对象 （和间接到查询结果或在数据源上的表中的相应列）。 如其基本类[CFormView](../mfc/reference/cformview-class.md)，`CRecordView`基于对话框模板资源。  
  
## <a name="form-uses"></a>窗体用途  
 窗体对于各种数据访问任务十分有用：  
  
-   输入数据  
  
-   执行数据只读检查  
  
-   更新数据  
  
## <a name="further-reading-about-record-views"></a>关于记录视图的其他阅读材料  
 本主题中的材料同时适用于基于 ODBC 和基于 DAO 的类。 将 `CRecordView` 用于 ODBC并且将 `CDaoRecordView` 用于 DAO。  
  
 包括以下主题：  
  
-   [记录视图类的功能](../data/features-of-record-view-classes-mfc-data-access.md)  
  
-   [记录视图的数据交换](../data/data-exchange-for-record-views-mfc-data-access.md)  
  
-   [你在使用记录视图中的角色](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)  
  
-   [设计和创建记录视图](../data/designing-and-creating-a-record-view-mfc-data-access.md)  
  
-   [使用记录视图](../data/using-a-record-view-mfc-data-access.md)  
  
## <a name="see-also"></a>请参阅  
 [数据访问编程 (MFC/ATL)](../data/data-access-programming-mfc-atl.md)   
 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)