---
title: MFC ActiveX 控件： 优化 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], windowless
- flicker-free ActiveX controls
- MFC ActiveX controls [MFC], mouse interaction
- device contexts, unclipped for MFC ActiveX controls
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- MFC ActiveX controls [MFC], flicker-free
- windowless MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- optimizing performance, ActiveX controls
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09d441a44660310a13be264b24286ad2f0ccc6cd
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535179"
---
# <a name="mfc-activex-controls-optimization"></a>MFC ActiveX 控件：优化
本文介绍了可以用来优化更好的性能将 ActiveX 控件的方法。  

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 本文将取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。
  
 主题[启用关闭激活可见时选项](../mfc/turning-off-the-activate-when-visible-option.md)并[提供鼠标交互而处于非活动状态](../mfc/providing-mouse-interaction-while-inactive.md)讨论不创建窗口之前激活的控件。 本主题[提供无窗口激活](../mfc/providing-windowless-activation.md)讨论永远不会创建一个窗口，即使它们被激活的控件。  
  
 Windows 具有 OLE 对象的两个主要缺点： 它们导致对象不透明的或非矩形时处于活动状态，并且也将大量的系统开销添加到实例化和控件的显示。 通常情况下，创建一个窗口需要控件的创建时间的 60%。 使用单个共享的窗口 （通常是容器的） 和一些调度代码，一个控件接收相同的窗口服务，一般不会降低性能。 具有一个窗口是主要对象的不必要的开销。  
  
 某些优化不一定是提高性能时特定容器中使用您的控件。 例如，1996 年之前发布的容器不支持无窗口激活，因此实现此功能将不会提供较旧的容器中的权益。 但是，几乎每个容器支持暂留，因此优化您的控件的持久性代码很可能会提高其性能任何容器中。 如果您的控件专门用于一种特定类型的容器，可能想要研究这些优化这一项受该容器。 一般情况下，但是，您应尝试实现的许多技术中适用于您的特定控件以确保您的控件以及它可能是执行那样广泛的容器中。  
  
 您可以实现许多通过这些优化[MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)，然后在[控制设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md)页。  
  
### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>MFC ActiveX 控件向导 OLE 优化选项  
  
|在 MFC ActiveX 控件向导控件设置|操作|详细信息|  
|-------------------------------------------------------|------------|----------------------|  
|**在可见时激活**复选框|清除|[关闭激活时可见的选项](../mfc/turning-off-the-activate-when-visible-option.md)|  
|**无窗口激活**复选框|选择|[提供无窗口激活](../mfc/providing-windowless-activation.md)|  
|**剪辑的设备上下文**复选框|选择|[使用未剪辑的设备上下文](../mfc/using-an-unclipped-device-context.md)|  
|**无闪烁激活**复选框|选择|[提供无闪烁激活](../mfc/providing-flicker-free-activation.md)|  
|**将鼠标指针通知不活动时**复选框|选择|[不活动时提供鼠标交互](../mfc/providing-mouse-interaction-while-inactive.md)|  
|**优化绘制代码**复选框|选择|[优化控件绘制](../mfc/optimizing-control-drawing.md)|  
  
 有关实现这些优化的成员函数的详细信息，请参阅[COleControl](../mfc/reference/colecontrol-class.md)。  
  
 有关详细信息，请参见:  
  
-   [优化持久性和初始化](../mfc/optimizing-persistence-and-initialization.md)  
  
-   [提供无窗口激活](../mfc/providing-windowless-activation.md)  
  
-   [关闭激活时可见的选项](../mfc/turning-off-the-activate-when-visible-option.md)  
  
-   [不活动时提供鼠标交互](../mfc/providing-mouse-interaction-while-inactive.md)  
  
-   [提供无闪烁激活](../mfc/providing-flicker-free-activation.md)  
  
-   [使用未剪辑的设备上下文](../mfc/using-an-unclipped-device-context.md)  
  
-   [优化控件绘制](../mfc/optimizing-control-drawing.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)

