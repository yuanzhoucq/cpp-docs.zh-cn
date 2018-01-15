---
title: "跟踪器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- trackers [MFC]
- OLE applications [MFC], trackers
- applications [OLE], trackers
- tracking OLE items [MFC]
- OLE containers [MFC], trackers
- CDC class [MFC], trackers
- CRectTracker class [MFC], implementing trackers
- OLE server applications [MFC], trackers
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 29e4d3c556a5f7b6b3aed5daa0285ea6c2c15447
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="trackers"></a>跟踪器
[CRectTracker](../mfc/reference/crecttracker-class.md)类提供在你的应用程序和你的用户通过提供各种显示样式的矩形项之间的用户界面。 这些样式包括纯色、 阴影，或虚线边框。阴影的图案涵盖项;和调整大小图柄，可在外部或内部边框位于。 跟踪器通常与 OLE 项结合使用，对象即，派生自`COleClientItem`。 跟踪器矩形提供项的当前状态的视觉提示。  
  
 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)演示了使用跟踪器和从角度来看的 OLE 客户端项的容器应用程序的常见界面。 演示不同的样式和跟踪器对象的功能，请参阅 MFC 常规示例[跟踪器](../visual-cpp-samples.md)。  
  
 OLE 应用程序中实现跟踪器的详细信息，请参阅[跟踪器： 在 OLE 应用程序中实现跟踪器](../mfc/trackers-implementing-trackers-in-your-ole-application.md)  
  
## <a name="see-also"></a>请参阅  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleClientItem 类](../mfc/reference/coleclientitem-class.md)
