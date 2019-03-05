---
title: TN040:MFC OLE 就地调整大小和缩放
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
ms.openlocfilehash: e2f6c6acfefaae877790fd2cc0926bc2474c79b8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283756"
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040:MFC/OLE 就地调整大小和缩放

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。

本说明将讨论与就地编辑以及服务器应如何完成正确的缩放和就地调整大小有关的问题。 借助就地激活，所见即所得 (WYSIWYG) 概念在容器和服务器的相互协作方面得到了进一步深化，具体而言就是能够以大致相同的方式解释 OLE 规范。

由于支持就地激活的容器和服务器之间的密切交互，最终用户有很多期望将得到满足：

- 当针对编辑进行绘制时，演示文稿显示（在 `COleServerItem::OnDraw` 重写中绘制的元文件）的外观应该完全相同（除了编辑工具不可见之外）。

- 当容器缩放时，服务器窗口也相应地缩放！

- 容器和服务器应使用同一指标显示要编辑的对象。 这意味着要使用基于数量的映射模式*逻辑*每英寸像素数 — 不是物理像素 / 英寸，呈现显示设备上时。

> [!NOTE]
>  由于就地激活仅适用于嵌入的（而非链接的）项，缩放也仅适用于嵌入对象。 您将在用于缩放的 `COleServerDoc` 和 `COleServerItem` 中看到 API。 此分歧的原因是有效的链接和嵌入的项的函数位于`COleServerItem`（这允许您以具有常规实现） 并仅对嵌入对象有效的函数位于`COleServerDoc`类 (从服务器的角度来看，它是**文档**在嵌入)。

大多数负担在都服务器实现器上，因为服务器必须知道容器的缩放系数并相应地修改其编辑界面。 但服务器如何确定使用容器的缩放系数

## <a name="mfc-support-for-zooming"></a>MFC 对缩放的支持

当前缩放系数可通过调用 `COleServerDoc::GetZoomFactor` 确定。 在文档未处于就地活动状态时调用它将始终生成 100% 缩放系数（也称为 1:1 比例）。 在文档处于就地活动状态时调用它可能返回 100% 以外的缩放系数。

有关正确进行缩放的示例，请参阅 MFC OLE 示例[HIERSVR](../visual-cpp-samples.md)。 HIERSVR 中的缩放实际上很复杂，因为它显示了文本，而文本通常不是以线性方式（提示、排字约定、设计宽度和高度共同让问题复杂化了）缩放的。 尽管如此，HIERSVR 是实现正确的缩放的合理参考，是 MFC 教程如此[SCRIBBLE](../visual-cpp-samples.md) （第 7 步）。

`COleServerDoc::GetZoomFactor` 根据从容器或从 `COleServerItem` 和 `COleServerDoc` 类的实现获得的很多不同的指标确定缩放系数。 简而言之，当前缩放系数由以下公式确定：

```
Position Rectangle (PR) / Container Extent (CE)
```

POSITION RECTANGLE 由容器确定。 当调用 `COleClientItem::OnGetItemPosition` 时，POSITION RECTANGLE 在就地激活期间将返回到服务器，当容器调用服务器的 `COleServerDoc::OnSetItemRects`（通过调用 `COleClientItem::SetItemRects`）时，POSITION RECTANGLE 将会更新。

CONTAINER EXTENT 在计算时稍微复杂一些。 如果容器已调用 `COleServerItem::OnSetExtent`（通过调用 `COleClientItem::SetExtent`），则 CONTAINER EXTENT 是转换为基于每逻辑英寸的像素数的像素的此值。 如果容器尚未调用 SetExtent（通常是这种情况），则 CONTAINER EXTENT 是从 `COleServerItem::OnGetExtent` 返回的大小。 因此，如果容器尚未调用 SetExtent，框架将假定，如果它未容器会调用它的原始大小为 100%(从返回的值`COleServerItem::GetExtent`)。 换句话说，框架假定容器正在显示项的 100%（不多不少）。

请务必注意，尽管 `COleServerItem::OnSetExtent` 和 `COleServerItem::OnGetExtent` 具有类似的名称，但它们不操作项的同一特性。 容器将调用 `OnSetExtent` 以告知服务器容器中多少对象是可见的（无论缩放系数如何），并调用 `OnGetExtent` 来确定对象的理想大小。

通过查看每个相关的 API，您可以更清楚地了解情况：

## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent

此函数应返回采用项的 HIMETRIC 单位的“原始大小”。 考虑“原始大小”的最佳方法是将其定义为它在打印时可能显示的大小。 此处返回的大小是特定项内容的常量（与元文件非常相似，它也是特定项的常量）。 将缩放应用于项时，此大小不会更改。 当容器通过调用 `OnSetExtent` 为项提供更多或更少的空间时，此大小通常不更改。 更改的一个示例可能是根据容器发送的最后一个范围为文本换行的没有“边距”功能的简单文本编辑器。 如果某台服务器确实发生更改，该服务器可能应该在系统注册表中设置 OLEMISC_RECOMPOSEONRESIZE 位（有关此选项的详细信息，请参阅 OLE SDK 文档。）

## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent

此函数在容器显示对象的“更多或更少”时调用。 大多数容器完全不会调用此函数。 默认实现将从容器接收的最后一个值存储在“m_sizeExtent”中，当计算上面所述的 CONTAINER EXTENT 值时，将在 `COleServerDoc::GetZoomFactor` 中使用它。

## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects

仅当文档处于就地活动状态时才调用此函数。 当容器更新项的位置或应用于项的剪辑，将调用此函数。 如上所述，POSITION RECTANGLE 提供了计算缩放系数时的分子。 服务器可以通过调用 `COleServerDoc::RequestPositionChange` 请求更改项位置。 容器可能会或可能不响应此请求通过调用`OnSetItemRects`(通过调用`COleServerItem::SetItemRects`)。

## <a name="coleserverdocondraw"></a>COleServerDoc::OnDraw

请务必认识到，通过重写 `COleServerItem::OnDraw` 创建的元文件将生成完全相同的元文件，无论当前缩放系数如何。 容器将根据需要缩放元文件。 这是视图的 `OnDraw` 和服务器项的 `OnDraw` 之间的重要区别。 查看句柄缩放，项只需创建*可缩放*图元文件并将其放到要执行适当的缩放的容器。

确保服务器行为方式正常的最佳方法是在文档处于就地活动状态时使用 `COleServerDoc::GetZoomFactor` 的实现。

## <a name="mfc-support-for-in-place-resizing"></a>MFC 对就地调整大小的支持

MFC 完全实现了 OLE 2 规范中所述的就地调整界面的大小。 通过支持用户界面`COleResizeBar`类、 自定义消息 WM_SIZECHILD 和在此消息的特殊处理`COleIPFrameWnd`。

您可能希望为此消息实现不同于框架提供的处理的处理。 如上所述，框架将就地调整大小的结果交给容器处理 - 服务器响应缩放系数的更改。 如果容器的反应是通过在处理其 `COleClientItem::OnChangeItemPosition`（称为调用 `COleServerDoc::RequestPositionChange` 的结果）时同时设置 CONTAINER EXTENT 和 POSITION RECTANGLE，则就地调整大小将导致在编辑窗口中显示项的“更多或更少”。 如果容器的反应只是在处理 `COleClientItem::OnChangeItemPosition` 时设置 POSITION RECTANGLE，则缩放系数将更改，项将被显示“放大或缩小”。

服务器可以（在一定程度上）控制协商期间发生的事情。 例如，电子表格可能选择在用户调整窗口的大小并就地编辑项时显示更多或更少单元格。 字处理器可能选择将“页边距”更改为与窗口的相同，并将文本重新包装到新边距。 服务器通过在完成大小调整时更改原始大小（从 `COleServerItem::OnGetExtent` 返回的大小）达到此目的。 此将导致 POSITION RECTANGLE 和 CONTAINER EXTENT 进行相同程度的更改，从而产生相同的比例系数，但更大或更小的查看区域。 此外，更多或更少的文档将在 `OnDraw` 生成的元文件中可见。 在这种情况下，当用户调整项（而不只是查看区域）的大小时，文档本身会更改。

可以实现自定义大小调整，同时利用提供的用户界面`COleResizeBar`通过重写中的 WM_SIZECHILD 消息在`COleIPFrameWnd`类。 有关具体细节 WM_SIZECHILD 的详细信息，请参阅[技术说明 24](../mfc/tn024-mfc-defined-messages-and-resources.md)。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
