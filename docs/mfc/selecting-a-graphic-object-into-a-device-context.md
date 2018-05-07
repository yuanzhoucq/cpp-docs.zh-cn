---
title: 将图形对象选入设备上下文 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc605be317d51c985e32fbad038d846b056e5fe6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>将图形对象选入设备上下文
本主题适用于在一个窗口设备上下文中使用图形对象。 检查完[创建图形对象](../mfc/one-stage-and-two-stage-construction-of-objects.md)，必须将它选入设备上下文代替那里存储的默认对象：  
  
 [!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]  
  
## <a name="lifetime-of-graphic-objects"></a>图形对象的生存期  
 返回的图形对象[SelectObject](../mfc/reference/cdc-class.md#selectobject)是"临时"。 也就是说，它将被删除[OnIdle](../mfc/reference/cwinapp-class.md#onidle)类的成员函数`CWinApp`的下次程序获取空闲时间。 只要你使用返回的对象`SelectObject`在没有将控制返回到主消息循环的单个函数，您将具有没问题。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [图形对象](../mfc/graphic-objects.md)  
  
-   [图形对象的一阶段和两阶段构建](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [设备上下文](../mfc/device-contexts.md)  
  
-   [在视图中绘制](../mfc/drawing-in-a-view.md)  
  
## <a name="see-also"></a>请参阅  
 [图形对象](../mfc/graphic-objects.md)

