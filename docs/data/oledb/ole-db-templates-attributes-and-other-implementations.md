---
title: "OLE DB 模板、特性和其他实现 | Microsoft Docs"
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
  - "OLE DB 模板"
  - "OLE DB 模板, 关于 OLE DB 模板"
  - "OLE DB, 实现"
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# OLE DB 模板、特性和其他实现
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## ATL OLE DB 模板  
 OLE DB 模板是活动模板库 \(ATL\) 的一部分，它们通过提供实现许多常用 OLE DB 接口的类来使得高性能的 OLE DB 数据库技术使用起来很简单。  模板库中附带有创建 OLE DB 起始应用程序的向导支持。  
  
 此模板库包含两部分：  
  
-   **OLE DB 使用者模板** 用于实现 OLE DB 客户（使用者）应用程序。  
  
-   **OLE DB 提供程序模板** 用于实现 OLE DB 服务器（提供程序）应用程序。  
  
 若要使用 OLE DB 模板，应熟悉 C\+\+ 模板、COM 和 OLE DB 接口。  如果对 OLE DB 不熟悉，请参见 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)。  
  
 有关更多信息，请：  
  
-   参阅关于 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)或 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)的主题。  
  
-   创建 [OLE DB 使用者](../../data/oledb/creating-an-ole-db-consumer.md)或 [OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)。  
  
-   参阅 [OLE DB 使用者类](../../data/oledb/ole-db-consumer-templates-reference.md)列表或 [OLE DB 提供程序类](../../data/oledb/ole-db-provider-templates-reference.md)列表。  
  
-   参阅 [OLE DB 模板示例](http://msdn.microsoft.com/zh-cn/08958863-0b5f-41ad-ae99-fca7440c553c)列表。  
  
-   请参见 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)（在 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中）。  
  
## OLE DB 特性  
 [OLE DB 使用者特性](../../windows/ole-db-consumer-attributes.md)提供创建 OLE DB 使用者的便利方法。  OLE DB 特性基于 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-reference.md)插入代码，以创建 OLE DB 工作使用者和提供程序。  如需指定不为这些特性支持的功能，可将 OLE DB 模板和代码中的特性一起使用。  
  
## MFC OLE DB 类  
 MFC 库包含一个显示控件中数据库记录的类，[COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)。  该视图是一个直接连接到 `CRowset` 对象的窗体视图，并在对话框模板的控件中显示 `CRowset` 对象的字段。  它还提供对移动到第一条、下一条、上一条或最后一条记录的默认实现以及用于更新当前所查看记录的接口。  有关详细信息，请参阅`COleDBRecordView`。  
  
## OLE DB SDK 接口  
 如果 OLE DB 模板不支持 OLE DB 功能，则需使用 OLE DB 接口本身。  有关更多信息，请参见 [OLE DB 程序员参考](https://msdn.microsoft.com/en-us/library/ms713643.aspx)（在 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中）。  
  
## 请参阅  
 [OLE DB 编程](../../data/oledb/ole-db-programming.md)   
 [OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)