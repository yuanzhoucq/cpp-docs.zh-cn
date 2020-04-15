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
ms.openlocfilehash: 366f0e2953e5190f80a2877804bff2fc7dbbd520
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372791"
---
# <a name="scrolling-and-scaling-views"></a>滚动和缩放视图

MFC 支持滚动的视图和自动缩放到显示这些视图的帧窗口大小的视图。 类`CScrollView`支持这两种视图。

有关滚动和缩放的详细信息，请参阅*MFC 参考*中的[CScrollView](../mfc/reference/cscrollview-class.md)类。 有关滚动示例，请参阅[涂鸦示例](../overview/visual-cpp-samples.md)。

## <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- 滚动视图

- 缩放视图

- [查看坐标](/windows/win32/gdi/window-coordinate-system)

## <a name="scrolling-a-view"></a><a name="_core_scrolling_a_view"></a>滚动视图

通常，文档的大小大于其视图可以显示的大小。 这可能是因为文档的数据增加或用户收缩设置视图的窗口。 在这种情况下，视图必须支持滚动。

任何视图都可以在其`OnHScroll`和`OnVScroll`成员函数中处理滚动条消息。 您可以在这些函数中实现滚动条消息处理，自己执行所有工作，也可以使用 类`CScrollView`为您处理滚动。

`CScrollView` 执行下列操作：

- 管理窗口和视口大小和映射模式

- 自动滚动以响应滚动条消息

您可以指定"页面"（当用户在滚动条轴中单击时）和"行"（当用户在滚动箭头中单击时）的滚动量。 规划这些值以适应视图的性质。 例如，您可能希望以 1 像素的增量滚动图形视图，但基于文本文档中的行高度以增量滚动。

## <a name="scaling-a-view"></a><a name="_core_scaling_a_view"></a>缩放视图

当希望视图自动适合其框架窗口的大小时，可以使用`CScrollView`缩放而不是滚动。 逻辑视图将拉伸或收缩，以完全适合窗口的工作区。 缩放视图没有滚动条。

## <a name="see-also"></a>另请参阅

[使用视图](../mfc/using-views.md)
