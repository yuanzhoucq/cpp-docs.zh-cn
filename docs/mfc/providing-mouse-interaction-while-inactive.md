---
title: 非活动状态时提供鼠标交互 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9394a3c161b82fa95de0e2ae0c590aec87493a85
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418731"
---
# <a name="providing-mouse-interaction-while-inactive"></a>不活动时提供鼠标交互

如果未立即激活您的控件，您仍可能需要它处理 WM_SETCURSOR 和 WM_MOUSEMOVE 消息，即使该控件具有没有其自己的窗口。 这可以通过启用`COleControl`的实现`IPointerInactive`接口，它默认处于禁用状态。 (请参阅*ActiveX SDK*有关此接口的说明。)若要启用该功能，包括 pointerInactive 标志标志返回的集中[colecontrol:: Getcontrolflags](../mfc/reference/colecontrol-class.md#getcontrolflags):

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]

如果你选择自动生成代码以包括此标志**鼠标指针通知时处于非活动状态**选项卡上[控制设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md)页面时创建您的控件具有**MFC ActiveX 控件向导**。

当`IPointerInactive`启用接口，该容器委托 WM_SETCURSOR 和 WM_MOUSEMOVE 消息到它。 `COleControl`实现`IPointerInactive`适当地调整鼠标坐标后会将控件的消息映射通过消息调度。 您可以通过将相应的条目添加到消息映射处理就像普通窗口消息的消息。 在这些消息的处理程序中，避免使用*m_hWnd*成员变量 （或使用它的任何成员函数） 不首先检查其值不**NULL**。

此外可以将未激活的控件是 OLE 拖放操作的目标。 这要求用户将对象拖到它，此时激活控件，以便可以将控件的窗口注册为放置目标。 若要使以在拖动过程进行激活，请重写[COleControl::GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)，并返回 POINTERINACTIVE_ACTIVATEONDRAG 标志：

[!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]

启用`IPointerInactive`接口通常表示你希望控件，使其能够在任何时候处理鼠标消息。 若要在不支持的容器中获取此行为`IPointerInactive`需要能够始终时可见，请激活您的控件接口，这意味着该控件应包括在其各种标志 OLEMISC_ACTIVATEWHENVISIBLE 标志。 但是，若要防止从此标志，并且在容器中的生效支持`IPointerInactive`，还可以指定 OLEMISC_IGNOREACTIVATEWHENVISIBLE 标志：

[!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)

