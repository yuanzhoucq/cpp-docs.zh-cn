---
title: "TN040：MFC/OLE 就地调整大小和缩放 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "就地激活, 缩放和调整大小"
  - "就地调整大小"
  - "TN040"
  - "缩放和就地激活"
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN040：MFC/OLE 就地调整大小和缩放
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此注释将讨论与就地编辑，服务器应如何完成正确缩放和就地调整的相关问题。  就地激活，WYSIWYG 概念进一步深化容器和服务器的相互协作以及尤其是解释 OLE 规范大致相同。  
  
 由于在支持就地激活方面，容器和服务器之间亲密的交互，使得最终用户需要保持一系列期望值：  
  
-   此演示显示 \( `COleServerItem::OnDraw` 重写绘制的图元文件\) 应查找相同的，当进行编辑绘制时 \(除编辑工具不可见以外\)。  
  
-   当容器缩放时，服务器窗口也相应缩放！  
  
-   容器和服务器应使用同一指标显示编辑的对象。  这意味着使用基于每英寸 *逻辑* 像素 \- 非物理英寸的像素数目的映射模式，当呈现在显示设备时。  
  
> [!NOTE]
>  由于就地激活仅适用于嵌入对象 \(不适用于链接的\)，所以缩放也仅适用于嵌入对象。  用于放大的您将看到两个 `COleServerDoc` 和 `COleServerItem` 中的 API。  这个分化的原因为链接中嵌入项中都有效的函数仅在 `COleServerItem` 中\(这允许存在常规实现\) 而仅在嵌入项中有效的函数位于 `COleServerDoc` 类 \(从服务端看，它为 `document` 是嵌入的\) 。  
  
 大多数的开销在服务器实现放置，因为服务器必须知道容器的缩放比例和修改其编辑相应的接口。  但服务器如何确定容器使用的缩放因子？  
  
## 缩放的 MFC 支持  
 当前缩放比例可以通过调用 `COleServerDoc::GetZoomFactor` 决定。  调用此，当文档不是就地激活时将始终导致 100% 缩放（或 1:1 缩放）。  就地激活时，调用它，则可能返回 100% 以外的内容。  
  
 有关正确缩放的示例，请参见 MFC OLE 示例 [HIERSVR](../top/visual-cpp-samples.md)。  HIERSVR 缩放事实上是复杂的，因为它显示文本而文本通常不是线性的 \(提示、版式约定、设计宽度和高度都是复杂因素\)。  但是，HIERSVR 是实现的正确缩放合理地引用，同时 MFC 指南 [SCRIBBLE](../top/visual-cpp-samples.md) \(步骤 7\) 也是一样。  
  
 `COleServerDoc::GetZoomFactor` 决定基于多种不同的度量的缩放比例可从容器或从 `COleServerItem` 和 `COleServerDoc` 类实现。  为简单起见，以下公式决定当前缩放因素：  
  
```  
Position Rectangle (PR) / Container Extent (CE)  
```  
  
 容器确定 POSITION RECTANGLE （位置矩形）。  当容器调用服务器的 `COleServerDoc::OnSetItemRects` \(同时调用 `COleClientItem::SetItemRects`\)时，在就地激活调用和更新 `COleClientItem::OnGetItemPosition` 时，它返回到服务器。  
  
 CONTAINER EXTENT 计算时稍微复杂。  如果容器已调用 `COleServerItem::OnSetExtent` \(同时调用 `COleClientItem::SetExtent`\)，则 CONTAINER EXTENT 是基于每逻辑英寸像素数量的转换为像素的值。  如果容器未调用 SetExtent \(通常是这种情况\) ，则 CONTAINER EXTENT 是从 `COleServerItem::OnGetExtent`返回的大小。  因此，如果容器调用了 SetExtent，则框架假设容器将调用它与 100% 原始大小 \(从 **COleServerItem::GetExtent**返回的值\)。  声明另一种方法，框架假定容器显示项的 100% \(不多不少\)。  
  
 请务必注意，尽管 `COleServerItem::OnSetExtent` 和  `COleServerItem::OnGetExtent` 具有类似的名称，但它们没有相同特性的项。  调用 `OnSetExtent` 将告知服务器容器中多少对象是可见的 \(忽略缩放比例\)，而容器调用 `OnGetExtent` 来确定对象的理想大小。  
  
 通过查看相关的每个 API，您可以获取更清晰的描写：  
  
## COleServerItem::OnGetExtent  
 此函数应该返回“原始大小”在项 HIMETRIC 单位中。  最佳的情况下认为“原始大小”就是将其定义为打印时可见的大小。  此处要返回的大小是针对于特定项的常数 \(就像图元文件，提供特定项常数\)。  缩放应用于项时，此大小不会更改。  它通常不更改，当容器通过调用 `OnSetExtent`向项提供更多或较少空间。  演示更改的示例可以是基于容器发送的最后大小而包装文本的无“边距”功能的简单文本编辑器示例。  如果服务器更改，服务器可能应在系统注册表中设置 OLEMISC\_RECOMPOSEONRESIZE 位 \(请参见 OLE SDK 文档有关此选项的更多信息。\)  
  
## COleServerItem::OnSetExtent  
 当容器显示“或多或少”对象时，此函数调用。  大多数容器根本不会调用此方法。  默认实现存储最后 “m\_sizeExtent" 中容器接收的值，用于在计算上面介绍的 CONTAINER EXTENT 值时的 `COleServerDoc::GetZoomFactor`。  
  
## COleServerDoc::OnSetItemRects  
 当文档处于就地活动状态时，此函数调用。  当容器更新项的位置或裁剪项时，其将调用。  POSITION RECTANGLE，如上所述，提供计算缩放比例时的计算分子。  服务器可以请求更改项位置通过调用 `COleServerDoc::RequestPositionChange`。  容器不确定能否响应此请求通过调用 `OnSetItemRects` \(同时调用 **COleServerItem::SetItemRects**\)。  
  
## COleServerDoc::OnDraw  
 要意识到通过重写 `COleServerItem::OnDraw` 生产同一元文件来创建元文件是重要的，而不管当前缩放比例。  容器将根据需要缩放图元文件。  这是视图的 `OnDraw` 和服务器项目的 `OnDraw`之间的重要区别。  处理视图缩放，项只需创建一个 *zoomable* 元文件和让容器确定执行正确缩放。  
  
 最佳的情况下确保服务器正确的行为将使用 `COleServerDoc::GetZoomFactor` 的实现，如果文档处于就地活动状态。  
  
## 就地调整的 MFC 支持  
 MFC 完全实现了 OLE 2 规范所述的就地调整接口。  用户接口通过 `COleResizeBar` 类支持，其为一个自定义消息 **WM\_SIZECHILD**，同时在 `COleIPFrameWnd` 中特殊处理此消息。  
  
 您可能想要框架提供的其他处理此消息的实现。  如上所述，框架将就地调整结果分配到容器管理 \- 服务器响应缩放比例的更改。  如果容器在处理 `COleClientItem::OnChangeItemPosition` \(作为调用 `COleServerDoc::RequestPositionChange` 的结果调用\) 时对同时 CONTAINER EXTENT 和 POSITION RECTANGLE 起抵制，就地然后调整会导致在编辑窗口中显示“或多或少”项。  如果容器仅在处理 `COleClientItem::OnChangeItemPosition`时设置 POSITION RECTANGLE 起抵制，则缩放比例将更改，该项将“放大或缩小”显示。  
  
 服务器可以控制 \(某种程度上\) 在协商时发生的情况。  电子表格，例如在用户就地编辑项调整窗口时，可能显示更多或更少的单元格。  字处理程序可能选择更改“页边距”以便与窗口相同并重新包装文本到新的边距。  服务器通过在更改原始大小 \(从 `COleServerItem::OnGetExtent`返回的大小\)实现此，在调整的大小时。  此将导致 POSITION RECTANGLE 和 CONTAINER EXTENT 等比改变，从而导致相同比例因子，但比视图区域较大或较小。  此外，文档多或少或的会在由 `OnDraw` 在生成的元文件中可见。  在这种情况下，当用户调整项，而不是显示的区域时，文档自己会更改，。  
  
 可以实现自定义调整并仍利用通过在 `COleIPFrameWnd` 类中重写 **WM\_SIZECHILD** 消息而由 `COleResizeBar` 提供的用户界面。  有关 **WM\_SIZECHILD** 规范的更多信息，请参见 [技术说明 24](../mfc/tn024-mfc-defined-messages-and-resources.md)。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)