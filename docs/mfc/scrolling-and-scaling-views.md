---
title: "滚动和缩放视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4191adb10693ea224a89fb62c09a2299c3a6bee2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="scrolling-and-scaling-views"></a>滚动和缩放视图
MFC 支持的向下滚动和视图视图自动缩放到显示它们的框架窗口的大小。 类`CScrollView`支持这两种类型的视图。  
  
 有关滚动和缩放的详细信息，请参阅类[CScrollView](../mfc/reference/cscrollview-class.md)中*MFC 参考*。 有关滚动的示例，请参阅[Scribble 示例](../visual-cpp-samples.md)。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   滚动视图  
  
-   缩放视图  
  
-   [视图坐标](http://msdn.microsoft.com/library/windows/desktop/dd145205)  
  
##  <a name="_core_scrolling_a_view"></a>滚动视图  
 经常文档的大小大于其视图可以显示的大小。 这可能是因为增加了文档的数据或用户缩小帧视图窗口。 在这种情况下，视图必须支持滚动。  
  
 任何视图可以处理中的滚动条消息其`OnHScroll`和`OnVScroll`成员函数。 你可以在这些函数中，或者实现滚动条消息处理你自己，执行所有工作，或者可以使用`CScrollView`类来为您处理滚动。  
  
 `CScrollView` 执行下列操作：  
  
-   管理窗口和视区大小和映射模式  
  
-   滚动条消息的响应进行自动滚动  
  
 你可以指定多少 （当用户单击滚动箭头）"页"（当用户单击滚动条轴中） 和"行"滚动。 计划这些值以满足你的视图的性质。 例如，你可能想要滚动 1 个像素的增量图形视图中但在基于文本文档中的行高度的增量。  
  
##  <a name="_core_scaling_a_view"></a>缩放视图  
 如果你想要自动调整其框架窗口的大小的视图，你可以使用`CScrollView`缩放而不是滚动。 逻辑视图被拉伸或收缩以完全适合窗口的工作区。 缩放后的视图具有任何滚动条。  
  
## <a name="see-also"></a>另请参阅  
 [使用视图](../mfc/using-views.md)

