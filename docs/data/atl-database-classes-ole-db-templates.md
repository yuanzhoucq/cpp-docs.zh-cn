---
title: "ATL 数据库类（OLE DB 模板） | Microsoft Docs"
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
  - "数据库类 [C++], ATL"
  - "数据库类 [C++], OLE DB"
  - "OLE DB 模板 [C++], ATL 数据库类"
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# ATL 数据库类（OLE DB 模板）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft 提供多种 OLE DB 实现，即一组对存储在不同信息源和格式中的数据提供统一访问的 COM 接口。  
  
 OLE DB 模板是 ATL 中的 C\+\+ 模板，它们通过提供实现许多常用 OLE DB 接口的类来使得高性能的 OLE DB 数据库技术使用起来很简单。  
  
 此模板库包含两部分：  
  
-   [OLE DB 使用者模板](../data/oledb/ole-db-consumer-templates-cpp.md) 用于实现 OLE DB 客户（使用者）应用程序。  
  
-   [OLE DB 提供程序模板](../data/oledb/ole-db-provider-templates-cpp.md) 用于实现 OLE DB 服务器（提供程序）应用程序。  
  
 另外，[OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)提供一种创建 OLE DB 使用者的便利方法。  OLE DB 特性基于 OLE DB 使用者模板插入代码，以创建工作 OLE DB 使用者。  
  
 请注意：MFC 库包含一个用以显示控件中数据库记录的类，[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)。  该视图是一个直接连接到 `CRowset` 对象的窗体视图，并在对话框模板的控件中显示 `CRowset` 对象的字段。  
  
 有关详细信息，请参阅 [OLE DB 编程](../data/oledb/ole-db-programming.md) 和 [OLE DB 程序员的指南。](http://go.microsoft.com/fwlink/?LinkId=121548)。  
  
## 请参阅  
 [创建 OLE DB 使用者](../data/oledb/creating-an-ole-db-consumer.md)   
 [创建 OLE DB 提供程序](../data/oledb/creating-an-ole-db-provider.md)   
 [OLE DB 使用者模板参考](../data/oledb/ole-db-consumer-templates-reference.md)   
 [OLE DB 提供程序模板参考](../data/oledb/ole-db-provider-templates-reference.md)   
 [OLE DB Templates Samples](http://msdn.microsoft.com/zh-cn/08958863-0b5f-41ad-ae99-fca7440c553c)