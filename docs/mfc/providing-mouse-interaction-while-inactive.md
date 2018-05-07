---
title: 非活动状态时提供鼠标交互 |Microsoft 文档
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
ms.openlocfilehash: faf1ea1958d6a6381bbe1c6e7d3db26f5f5b7c17
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="providing-mouse-interaction-while-inactive"></a>不活动时提供鼠标交互
如果未立即激活你的控件，您可能仍需要它来处理`WM_SETCURSOR`和`WM_MOUSEMOVE`消息，即使该控件具有没有自己的窗口。 这可以通过实现来完成`COleControl`的实现`IPointerInactive`接口，默认处于禁用状态。 (请参阅*ActiveX SDK*有关此接口的说明。)若要启用它，包括`pointerInactive`标志返回集中的标志[COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags):  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]  
  
 如果你选择自动生成代码以包括此标志**鼠标指针通知时处于非活动状态**选项[控制设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md)页上创建控件与时**MFC ActiveX 控件向导**。  
  
 当`IPointerInactive`启用接口，容器委托`WM_SETCURSOR`和`WM_MOUSEMOVE`到它的消息。 `COleControl`实现`IPointerInactive`相应地调整鼠标坐标后会将通过控件的消息映射消息调度。 你可以通过将对应的条目添加到消息映射处理一样普通窗口消息的消息。 在您为这些消息的处理程序，应避免使用`m_hWnd`成员变量 （或使用它的任何成员函数） 不首先检查其值不**NULL**。  
  
 您可能还要不活动的控件是 OLE 拖放操作的目标。 这要求用户将对象拖动到它，此时激活控件，以便可以将该控件的窗口注册为放置目标。 若要使能够在拖动过程进行激活，重写[COleControl::GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)，并返回**POINTERINACTIVE_ACTIVATEONDRAG**标志：  
  
 [!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]  
  
 启用`IPointerInactive`接口通常表示你希望控件，使其能够在所有时间处理鼠标消息。 若要在不支持容器中获取此行为`IPointerInactive`接口，你需要使控件始终激活时可见，这意味着该控件应包括**OLEMISC_ACTIVATEWHENVISIBLE**之间标志其杂项标志。 但是，若要防止此标志从生效容器中，支持`IPointerInactive`，还可以指定**OLEMISC_IGNOREACTIVATEWHENVISIBLE**标志：  
  
 [!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)

