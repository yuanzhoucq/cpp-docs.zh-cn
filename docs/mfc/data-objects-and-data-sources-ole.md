---
title: "数据对象和数据源 (OLE) | Microsoft Docs"
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
  - "数据对象 [C++], 定义"
  - "数据源 [C++], 定义"
  - "数据传输 [C++]"
  - "数据传输 [C++], 定义"
  - "OLE [C++], 数据对象"
  - "OLE [C++], 数据源"
  - "OLE [C++], 数据传输"
ms.assetid: 8f68eed8-0ce8-4489-a4cc-f95554f89090
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 数据对象和数据源 (OLE)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用剪贴板或拖放时，可以将执行的数据传输，因此，数据源有一个和一个目标。  一个应用程序对复制的数据，而另一应用程序接受它粘贴的。  转发需要的每端对相同数据的不同操作但为了向前成功。  Microsoft 基础类 \(MFC\)库提供表示此转发的每端的两类：  
  
-   实现的数据源 \(由 `COleDataSource` 对象表示\) 传输数据的源端。  这些按源应用程序创建数据，则将复制到剪贴板时，或者在拖放操作的数据时提供。  
  
-   实现的数据对象 \(由 `COleDataObject` 对象表示\) 数据传输的目标边。  它们创建时，目的应用的数据删除到该时，或者当请求运行从剪贴板中粘贴操作。  
  
 下列文章阐释了如何在应用程序中使用对象数据和数据源。  这是因为两者可能会需要复制和粘贴数据，此信息适用于容器和服务器应用。  
  
-   [数据对象和数据源：创建和销毁](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [数据对象和数据源：操作](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## 本节内容  
 [拖放](../mfc/drag-and-drop-ole.md)  
  
 [Clipboard](../mfc/clipboard.md)  
  
## 请参阅  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleDataObject Class](../mfc/reference/coledataobject-class.md)   
 [COleDataSource Class](../mfc/reference/coledatasource-class.md)