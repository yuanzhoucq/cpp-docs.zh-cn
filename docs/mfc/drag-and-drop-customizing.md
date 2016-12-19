---
title: "拖放：自定义 | Microsoft Docs"
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
  - "拖放, 调用 DoDragDrop"
  - "拖放, COleDataSource 对象"
  - "拖放, 自定义行为"
  - "拖放, 在非 OLE 应用程序内实现"
  - "OLE 拖放, 自定义行为"
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 拖放：自定义
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

拖放功能的默认实现。大多数应用程序即可。  但是，一些应用程序可能需要此标准行为更改。  本文说明的必要步骤更改这些默认值。  另外，可以使用此技术建立不支持复合文档作为放置源的应用程序。  
  
 如果自定义标准 OLE 拖放行为，或者存在非 OLE 应用程序，必须创建一个 `COleDataSource` 对象包含的数据。  当用户启动拖放操作时，应从代码调用此对象的 `DoDragDrop` 函数而非从其他类支持拖放操作。  
  
 或者，可以创建一个 `COleDropSource` 对象控制放置并根据要更改行为类型重写某些函数。  此放置源对象传递给 `COleDataSource::DoDragDrop` 函数更改这些默认行为。  这些不同选项允许在如何的灵活性支持在应用程序中执行拖放操作。  有关数据源的更多信息，请参见知识库文章 [数据对象与数据源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md)。  
  
 可以重写函数自定义拖放操作：  
  
|重写|自定义：|  
|--------|----------|  
|`OnBeginDrag`|当你调用`DoDragDrop`后，抓取怎么实例化。|  
|`GiveFeedback`|可视反馈，例如光标外观，此外放置结果。|  
|`QueryContinueDrag`|拖放操作终止。  此函数使您在拖动操作期间检查键修改状态。|  
  
## 请参阅  
 [拖放 \(OLE\)](../mfc/drag-and-drop-ole.md)   
 [COleDropSource Class](../mfc/reference/coledropsource-class.md)   
 [COleDataSource Class](../mfc/reference/coledatasource-class.md)