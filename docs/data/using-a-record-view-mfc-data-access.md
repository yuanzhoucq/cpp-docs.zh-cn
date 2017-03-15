---
title: "使用记录视图（MFC 数据访问） | Microsoft Docs"
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
  - "记录视图, 自定义默认代码"
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 使用记录视图（MFC 数据访问）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题介绍了自定义向导为你编写的记录视图的默认代码的常用方式。  通常，你需要用[筛选器](../data/odbc/recordset-filtering-records-odbc.md)或[参数](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)限制记录选择，可能是对记录[排序](../data/odbc/recordset-sorting-records-odbc.md)，自定义 SQL 语句。  
  
 此信息对 [CRecordView](../mfc/reference/crecordview-class.md) \(ODBC\) 和 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md) \(DAO\) 均适用。  
  
 `CRecordView` 或 `CDaoRecordView` 的用法与 [CFormView](../mfc/reference/cformview-class.md) 的用法非常相似。  基本的方法是使用记录视图显示或更新单个记录集的记录。  此外，你还可以使用其他记录集，如[记录视图：从另一个记录集填充列表框](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)所述。  
  
## 请参阅  
 [记录视图（MFC 数据访问）](../data/record-views-mfc-data-access.md)   
 [ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)