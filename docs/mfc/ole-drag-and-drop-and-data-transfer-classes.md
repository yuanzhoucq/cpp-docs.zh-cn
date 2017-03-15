---
title: "OLE 拖放和数据传输类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 类 [C++]"
  - "数据传输 [C++], OLE"
  - "数据传输类 [C++]"
  - "拖放 [C++], 类"
  - "OLE 拖放 [C++], 和数据传输类"
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# OLE 拖放和数据传输类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

这些类在 OLE 数据传输。  它们允许数据传输在应用程序之间使用剪贴板或通过拖放。  
  
 [COleDropSource](../mfc/reference/coledropsource-class.md)  
 必须控制拖放操作。  此类时确定操作将启动，以及何时关闭。  在拖放操作期间也显示反馈光标。  
  
 [COleDataSource](../mfc/reference/coledatasource-class.md)  
 使用，在应用程序将数据传输的数据。  `COleDataSource` 可以显示为基本的剪贴板对象。  
  
 [COleDropTarget](../mfc/reference/coledroptarget-class.md)  
 表示拖放操作的目标。  `COleDropTarget` 对象对应到屏幕上的一个窗口。  它确定是否接受任何数据拖放到其上并实际实现拖放操作。  
  
 [COleDataObject](../mfc/reference/coledataobject-class.md)  
 用作接收器端为 `COleDataSource`。  `COleDataObject` 对象提供对 `COleDataSource` 对象中存储的数据。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)