---
title: 滚动和缩放视图
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- scaling views [MFC]
- message handling [MFC], scroll bars in view class [MFC]
- scroll bars [MFC], messages
- scrolling views [MFC]
ms.assetid: f98a3421-c336-407e-97ee-dbb2ffd76fbd
ms.openlocfilehash: 7d26bc656dec3fdcbb8fc5ea4918ec7d59bc5afc
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777572"
---
# <a name="scrolling-and-scaling-views"></a>滚动和缩放视图

MFC 支持视图，向下滚动并查看自动调整为显示它们的框架窗口的大小。 类`CScrollView`支持这两种类型的视图。

有关滚动和缩放的详细信息，请参阅类[CScrollView](../mfc/reference/cscrollview-class.md)中*MFC 参考*。 有关滚动的示例，请参阅[Scribble 示例](../overview/visual-cpp-samples.md)。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- 滚动视图

- 缩放视图

- [视图坐标](/windows/desktop/gdi/window-coordinate-system)

##  <a name="_core_scrolling_a_view"></a> 滚动视图

经常文档的大小大于其视图可以显示的大小。 这可能会导致增加文档的数据或用户缩小帧视图的窗口。 在这种情况下，该视图必须支持滚动。

任何视图可以处理中的滚动条消息及其`OnHScroll`和`OnVScroll`成员函数。 你可以在这些函数中，或者实现滚动条消息处理执行所有工作，也可以使用`CScrollView`类来为您处理滚动。

`CScrollView` 执行下列操作：

- 管理窗口和视区大小和映射模式

- 在滚动条消息的响应中自动滚动

您可以指定多少滚动"page"（当用户单击滚动条轴中） 和"行"（当用户单击中滚动箭头）。 计划这些值以满足您的视图的性质。 例如，你可能想要向下滚动以 1 像素为增量的图形视图，但根据文本文档中的行高度的增量。

##  <a name="_core_scaling_a_view"></a> 缩放视图

当你想要自动符合其框架窗口的大小的视图时，可以使用`CScrollView`缩放而不是滚动。 逻辑视图被拉伸或收缩以完全适合窗口的工作区。 缩放的视图具有任何滚动条。

## <a name="see-also"></a>请参阅

[使用视图](../mfc/using-views.md)
