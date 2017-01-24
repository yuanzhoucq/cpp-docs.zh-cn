---
title: "剪贴板：添加其他格式 | Microsoft Docs"
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
  - "剪贴板, 格式"
  - "自定义剪贴板数据格式"
  - "自定义格式"
  - "自定义格式, 放置于剪贴板上"
  - "格式 [C++], 剪贴板"
  - "注册自定义剪贴板数据格式"
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 剪贴板：添加其他格式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题说明如何扩展支持的格式列表，具体而言 OLE 支持的。  主题 [剪贴板：复制和粘贴数据](../mfc/clipboard-copying-and-pasting-data.md) 描述需要最小实现支持从剪贴板复制和粘贴。  如果这是所有您实现，放置在剪贴板上的格式为 `CF_METAFILEPICT`、**CF\_EMBEDSOURCE**、**CF\_OBJECTDESCRIPTOR**及可以 `CF_LINKSOURCE`。  大多数应用程序的这三需要剪贴板上的多格式。  
  
##  <a name="_core_registering_custom_formats"></a> 注册自定义格式  
 要创建自己的自定义格式，请按照您使用的同一个过程时注册任何自定义格式剪贴板：传递的格式化名称为 **RegisterClipboardFormat** 函数并使用它的返回值用作格式 . ID  
  
##  <a name="_core_placing_formats_on_the_clipboard"></a> 放置格式剪贴板上  
 若要添加多格式添加到剪贴板上放置的控件，您必须在重写从 `COleClientItem` 或 `COleServerItem` 派生的类的函数 `OnGetClipboardData` \(根据复制的数据是否本机\)。  在此函数，应使用下面的过程。  
  
#### 放置格式剪贴板上  
  
1.  创建 `COleDataSource` 对象。  
  
2.  将此数据源将本机数据格式到支持的格式列表通过调用 `COleDataSource::CacheGlobalData`的函数。  
  
3.  添加标准格式通过调用每种要支持的标准格式的 `COleDataSource::CacheGlobalData`。  
  
 此技术在 MFC OLE 示例程序 [HIERSVR](../top/visual-cpp-samples.md) \(请选中 **CServerItem** 类的 `OnGetClipboardData` 成员函数。\)  本示例中的唯一不同之处是第三不实现，因为文本支持没有其他标准格式。  
  
### 您想进一步了解什么？  
  
-   [OLE 数据对象与数据源和统一传输数据](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [OLE 拖放](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## 请参阅  
 [剪贴板：使用 OLE 剪贴板机制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)