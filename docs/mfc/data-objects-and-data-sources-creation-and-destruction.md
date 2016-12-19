---
title: "数据对象和数据源：创建和销毁 | Microsoft Docs"
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
  - "数据对象 [C++], 创建"
  - "数据对象 [C++], 销毁"
  - "数据源对象 [C++], 创建"
  - "数据源对象 [C++], 销毁"
  - "数据源 [C++], 和数据对象"
  - "数据源 [C++], 创建"
  - "数据源 [C++], 销毁"
  - "数据源 [C++], 角色"
  - "销毁数据对象"
  - "析构 [C++], 数据对象"
  - "析构 [C++], 数据源"
  - "对象创建 [C++], 数据源对象"
ms.assetid: ac216d54-3ca5-4ce7-850d-cd1f6a90d4f1
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 数据对象和数据源：创建和销毁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如文章[数据对象和数据源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md) 中所述，数据对象和数据源表示数据传输双方。  本文介绍何时创建和销毁这些对象和源以正确地执行数据传输，包括：  
  
-   [创建数据对象](#_core_creating_data_objects)  
  
-   [销毁数据对象](#_core_destroying_data_objects)  
  
-   [创建数据源](#_core_creating_data_sources)  
  
-   [销毁数据源](#_core_destroying_data_sources)  
  
##  <a name="_core_creating_data_objects"></a> 创建数据对象  
 数据对象由目标应用程序（客户端或服务器）使用。  目标应用程序中的数据对象是源应用程序与目标应用程序之间的连接的一端。  目标应用程序中的数据对象用于访问数据源中的数据并与之交互。  
  
 有两种常见的需要数据对象的情况。  第一种情况是使用拖放将数据放在应用程序中时。  第二种情况是从“编辑”菜单中选择“粘贴”或“选择性粘贴”时。  
  
 在拖放情况下，您无需创建数据对象。  指向现有数据对象的指针将传递到 `OnDrop` 函数。  此数据对象将由框架作为拖放操作一部分创建，还将由框架销毁。  在通过其他方式进行粘贴时并不总是这样。  有关详细信息，请参阅[销毁数据对象](#_core_destroying_data_objects)。  
  
 如果应用程序要执行粘贴或选择性粘贴操作，您应创建 `COleDataObject` 对象并调用其 `AttachClipboard` 成员函数。  这会将数据对象与剪贴板上的数据关联。  您之后可在粘贴函数中使用此数据对象。  
  
##  <a name="_core_destroying_data_objects"></a> 销毁数据对象  
 如果您按照[创建对象数据](#_core_creating_data_objects)中描述的方案操作，销毁数据对象是数据传输次要的一面。  在粘贴函数中创建的数据对象将在粘贴函数返回时由 MFC 销毁。  
  
 如果您按照另一种方法处理粘贴操作，则务必在粘贴操作完成后销毁数据对象。  在销毁数据对象之前，任何应用程序均无法成功将数据复制到剪贴板。  
  
##  <a name="_core_creating_data_sources"></a> 创建数据源  
 数据源由数据传输源使用，该源可以是数据传输客户端或数据传输服务器端。  源应用程序中的数据源是源应用程序与目标应用程序之间的连接的一端。  目标应用程序中的数据对象用于与数据源中的数据交互。  
  
 当应用程序需要将数据复制到剪贴板时，将创建数据源。  一个典型方案运行如下：  
  
1.  用户选择某数据。  
  
2.  用户从**“编辑”**菜单中选择**“复制”**（或**“剪切”**）或开始拖放操作。  
  
3.  根据程序的设计，应用程序将创建 `COleDataSource` 对象或从派生自 `COleDataSource` 的类创建对象。  
  
4.  选定数据将插入数据源，方式为调用 `COleDataSource::CacheData` 或 `COleDataSource::DelayRenderData` 组中的函数之一。  
  
5.  应用程序将调用属于步骤 3 中所创建对象的 `SetClipboard` 成员函数（或 `DoDragDrop` 成员函数，如果这是一个拖放操作）。  
  
6.  如果这是**“剪切”**操作或 `DoDragDrop` 返回 `DROPEFFECT_MOVE`，则将从文档中删除步骤 1 中所选的数据。  
  
 此方案将由 MFC OLE 示例 [OCLIENT](../top/visual-cpp-samples.md) 和 [HIERSVR](../top/visual-cpp-samples.md) 实现。  为每个应用程序的 `CView` 派生类（`GetClipboardData` 和 `OnGetClipboardData` 函数除外）查找源。  这两个函数位于 `COleClientItem` 或 `COleServerItem` 派生类实现中。  这些示例程序提供了一个很好的如何实现这些概念的示例。  
  
 如果您修改拖放操作的默认行为，则将出现您可能需要创建 `COleDataSource` 对象的另一种情况。  有关详细信息，请参阅[拖放：自定义](../mfc/drag-and-drop-customizing.md)文章。  
  
##  <a name="_core_destroying_data_sources"></a> 销毁数据源  
 数据源必须由当前负责它们的应用程序销毁。  在将数据源转交给 OLE 的情况下，如调用 [COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)，你需要调用 **pDataSrc\-\>InternalRelease**。  例如:  
  
 [!CODE [NVC_MFCListView#1](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCListView#1)]  
  
 如果您未将数据源转交给 OLE，则您将负责销毁它，与任何典型的 C\+\+ 对象一样。  
  
 有关详细信息，请参阅[拖放](../mfc/drag-and-drop-ole.md)、[剪贴板](../mfc/clipboard.md)和[操作数据对象和数据源](../mfc/data-objects-and-data-sources-manipulation.md)。  
  
## 请参阅  
 [数据对象和数据源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md)   
 [COleDataObject Class](../mfc/reference/coledataobject-class.md)   
 [COleDataSource Class](../mfc/reference/coledatasource-class.md)