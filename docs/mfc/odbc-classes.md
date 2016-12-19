---
title: "ODBC 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "数据库类 [C++], ODBC"
  - "ODBC 类 [C++]"
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ODBC 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些类与其他应用程序框架类便于访问为使用开放式数据库连接 \(ODBC\) 的各种数据库驱动程序可用。  
  
 使用 ODBC 数据库的程序将具有 `CDatabase` 对象和至少一个 `CRecordset` 对象。  
  
 [CDatabase](../mfc/reference/cdatabase-class.md)  
 装入与数据源的连接，通过此连接可操作数据源。  
  
 [CRecordset](../mfc/reference/crecordset-class.md)  
 装入从数据源选择的一组记录。  记录集中滚动记录到日志，更新 \(添加，编辑和删除记录\)，限定使用的筛选器选择，依次选择和\) 进行参数化。信息的记录选择运行时获取或计算。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供直接连接的一个窗体视图到记录集对象。  对话框数据交换 \(DDX\) 机制在记录集和记录视图控件之间交换数据。  同所有窗体视图，记录视图基于对话框模板资源。  当记录视图已关闭时，记录视图还支持将记录添加到记录集的记录，更新记录和关闭关联的记录集。  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 异常处理产生数据访问的失败。  此类为用途和在类库的异常处理机制的任何其他异常类相同。  
  
 [CFieldExchange](../mfc/reference/cfieldexchange-class.md)  
 提供支持记录字段交换 \(RFX\) 的上下文信息，在记录集对象和相应字段数据成员和参数数据成员之间交换数据的表数据源上的列。  类似于 [CDataExchange](../mfc/reference/cdataexchange-class.md)类，对于对话框数据交换 \(DDX\) 类似使用。  
  
## 相关类  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 封装的句柄。一个二进制大对象 \(BLOB\) \(BLOB\) 的存储空间，如位图。  `CLongBinary` 对象用于管理数据库中表中存储大量数据对象。  
  
 [CDBVariant](../mfc/reference/cdbvariant-class.md)  
 以便存储值，而不用担心值的数据类型。  `CDBVariant` 要跟踪当前值的数据类型，在联合存储。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)