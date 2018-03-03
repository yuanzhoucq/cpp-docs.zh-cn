---
title: "ATL 数据库类 （OLE DB 模板） |Microsoft 文档"
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
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ca7607c037cdb1f6a42a2267d64ef274d1041cb2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="atl-database-classes-ole-db-templates"></a>ATL 数据库类（OLE DB 模板）
Microsoft 提供了多个 OLE DB，一组提供对各种信息源和格式中的数据的统一访问的 COM 接口的实现。  OLE DB 正式不推荐使用;本文档适用于开发人员而维护旧代码。 新的应用程序应使用 ODBC 连接到 SQL 数据源。
  
 OLE DB 模板是 ATL 中的 c + + 模板，轻松地通过提供实现许多常用 OLE DB 接口的类，使用 OLE DB 数据库技术。  
  
 此模板库包含两个部分：  
  
-   [OLE DB 使用者模板](../data/oledb/ole-db-consumer-templates-cpp.md)用于实现 OLE DB 客户端 （使用者） 应用程序。  
  
-   [OLE DB 提供程序模板](../data/oledb/ole-db-provider-templates-cpp.md)用于实现的 OLE DB 服务器 （提供程序） 应用程序。  
  
 此外， [OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)让你方便地创建 OLE DB 使用者。 OLE DB 属性将插入基于 OLE DB 使用者模板来创建使用 OLE DB 使用者代码。  
  
 MFC 库包含一个类，请注意[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)，在控件中显示数据库记录。 视图是直接连接到窗体视图`CRowset`对象，并显示字段的`CRowset`对话框模板的控件中的对象。  
  
 有关详细信息，请参阅[OLE DB 编程](../data/oledb/ole-db-programming.md)和[OLE DB 程序员指南](http://go.microsoft.com/fwlink/p/?linkid=121548)。  
  
## <a name="see-also"></a>请参阅  
 [创建 OLE DB 使用者](../data/oledb/creating-an-ole-db-consumer.md)   
 [创建 OLE DB 提供程序](../data/oledb/creating-an-ole-db-provider.md)   
 [OLE DB 使用者模板参考](../data/oledb/ole-db-consumer-templates-reference.md)   
 [OLE DB 提供程序模板参考](../data/oledb/ole-db-provider-templates-reference.md)   
 [OLE DB 模板示例](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)