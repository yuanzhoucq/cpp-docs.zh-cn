---
title: "ODBC 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.data
dev_langs: C++
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33fcc3453d36a2567330f60cec73383f842210c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-classes"></a>ODBC 类
这些类可与其他应用程序框架类以便轻松访问各种数据库为其开放式数据库连接 (ODBC) 驱动程序都可用。  
  
 使用 ODBC 数据库的程序将至少具有一个`CDatabase`对象和一个`CRecordset`对象。  
  
 [CDatabase](../mfc/reference/cdatabase-class.md)  
 封装与数据源，通过其可操作数据源的连接。  
  
 [CRecordset](../mfc/reference/crecordset-class.md)  
 封装一组从数据源选择的记录。 记录集启用滚动记录记录、 更新记录 （添加、 编辑和删除记录）、 使用筛选器，确认所选内容排序所选内容，并且信息所选内容中参数化获得或在运行时计算。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供了一种直接连接到记录集对象的视图。 对话框数据交换 (DDX) 记录集和记录视图的控件之间的机制交换数据。 如所有窗体视图中，记录视图基于对话框模板资源。 记录视图还支持在记录集移动到记录、 更新记录，和记录视图关闭时关闭关联的记录集。  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 处理从数据访问中的故障导致的异常。 此类用于与其他异常类相同的目的提供的类库的异常处理机制。  
  
 [CFieldExchange](../mfc/reference/cfieldexchange-class.md)  
 提供上下文信息，以支持记录字段交换 (RFX) 之间的字段数据成员和参数数据成员的记录集对象和相应的表列中对数据源交换数据。 类似于类[CDataExchange](../mfc/reference/cdataexchange-class.md)，它同样用于对话框数据交换 (DDX)。  
  
## <a name="related-classes"></a>相关的类  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 如位图封装为二进制大型对象 (BLOB) 存储的句柄。 `CLongBinary`对象用于管理存储在数据库表中的大型数据对象。  
  
 [CDBVariant](../mfc/reference/cdbvariant-class.md)  
 可以用来存储一个值，而无需担心值的数据类型。 `CDBVariant`跟踪当前值，该值存储在联合中的数据类型。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

