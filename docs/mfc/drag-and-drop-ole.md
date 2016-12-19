---
title: "拖放 (OLE) | Microsoft Docs"
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
  - "拖放 [C++]"
  - "拖放 [C++], 关于 OLE 拖放"
  - "文件管理器拖放支持"
  - "OLE 应用程序, 拖放"
  - "OLE 拖放"
  - "OLE 服务器应用程序, 拖放"
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 拖放 (OLE)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE 拖放功能是复制和粘贴数据的主的快捷方式。  当使用剪贴板复制或粘贴数据时，需要给定数的步骤。  在选择数据，单击 **剪切** 或 **复制** 从 **编辑** 菜单、移动到目标文件，或窗口应用程序，所需位置光标，然后单击 **粘贴** 从 **编辑** 菜单。  
  
 OLE 拖放与文件管理器拖放机制不同，只能处理文件名和专门设计将文件名传递到应用程序。  OLE 拖放更泛型。  它可以在剪贴板还会将拖放的所有数据。  
  
 如果使用 OLE 拖放时，可以从进程移除两个步骤。  您可以从源窗口放置 \(“源”的\) 数据，将其拖动到所需目标放置目标 \(“”\)，并通过释放鼠标按钮上。  操作比复制\/粘贴序列就无需菜单中需要和快速。  唯一的要求是放置源和放置目标都必须打开和至少部分显示在屏幕上。  
  
 使用 OLE 拖放数据传输，可以从一个位置到另一个文档中，文档之间差异，或在应用程序之间。  在容器应用或服务器，因此，任何应用程序可以是源放置，放置目标或同时作为可以实现。  如果应用程序有实现的放置源和放置目标支持，请允许在子窗口，或在一个窗口中。  此功能可以使您的应用程序更易于使用。  
  
 如果您仅希望使用的 OLE 拖放功能，请参见 [拖放：自定义](../mfc/drag-and-drop-customizing.md)。  在相应情景可以用来解释的方法创建非 OLE 应用程序放置源。  文章 [拖放：实现放置目标](../mfc/drag-and-drop-implementing-a-drop-target.md) 描述如何实现 OLE 和非应用程序支持 OLE 的放置目标。  检查示例 [OCLIENT](../top/visual-cpp-samples.md) [HIERSVR](../top/visual-cpp-samples.md)MFC OLE、和也将是有用。  
  
 如果尚未将文章 [数据对象与数据源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md) 系列，因此您可能希望进行。  演示数据传输这些情景的基本知识，以及如何实现在应用程序。  
  
 有关拖放的更多信息，请参见：  
  
-   [拖放：实现放置源](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [拖放：实现放置目标](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [拖放：自定义](../mfc/drag-and-drop-customizing.md)  
  
## 请参阅  
 [OLE](../mfc/ole-in-mfc.md)   
 [数据对象和数据源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md)