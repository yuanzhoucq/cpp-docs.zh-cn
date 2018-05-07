---
title: 使用窗口对象 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- child windows [MFC], working with
- window objects [MFC], working with
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4c00649c51e34bbbac7adbf7aa5f3c7d04790ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-window-objects"></a>使用窗口对象
使用两种类型的活动的 windows 调用：  
  
-   处理 Windows 消息  
  
-   在窗口中绘制  
  
 若要处理 Windows 消息在任何窗口中，包括你自己的子窗口，请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)将消息映射到你的 c + + 窗口类。 然后消息处理程序成员函数中编写你的类。  
  
 框架应用程序中的大部分绘图发生在视图中，其[OnDraw](../mfc/reference/cview-class.md#ondraw)每当必须绘制窗口的内容就会调用成员函数。 如果你的窗口是子节点的视图，您可能委派某些视图的绘制到子窗口通过让`OnDraw`调用你的窗口的成员函数之一。  
  
 在任何情况下，你将需要设备上下文的绘图区域。 你可以使用常用的钢笔、 画笔和其他与你的窗口关联的设备上下文中包含的图形对象。 也可以修改这些对象以获取你需要的绘制效果。 与你根据需要设置的设备上下文，调用成员函数的类[CDC](../mfc/reference/cdc-class.md) （设备上下文类） 绘制线条、 形状和文本; 若要使用颜色; 并使用坐标系统。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [消息处理和映射](../mfc/message-handling-and-mapping.md)  
  
-   [在视图中绘制](../mfc/drawing-in-a-view.md)  
  
-   [设备上下文](../mfc/device-contexts.md)  
  
-   [图形对象](../mfc/graphic-objects.md)  
  
## <a name="see-also"></a>请参阅  
 [窗口对象](../mfc/window-objects.md)

