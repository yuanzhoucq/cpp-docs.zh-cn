---
title: MFC ActiveX 控件： 优化 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: c91f147637b53250f8d373af9950d6205c82d3e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355306"
---
# <a name="mfc-activex-controls-optimization"></a>MFC ActiveX 控件：优化
此文章介绍了可用于优化 ActiveX 控件的更好的性能的技术。  
  
 主题[打开关闭激活可见时选项](../mfc/turning-off-the-activate-when-visible-option.md)和[提供鼠标交互时处于非活动状态](../mfc/providing-mouse-interaction-while-inactive.md)讨论不创建窗口之前激活的控件。 主题[提供无窗口激活](../mfc/providing-windowless-activation.md)讨论永远不会创建一个窗口，即使它们激活的控件。  
  
 Windows 有 OLE 对象的两个主要缺点： 它们会阻止对象透明或非矩形时处于活动状态，并且它们可以将大量的系统开销添加到的实例化和显示控件。 通常情况下，创建一个窗口将 60%的控件的创建时间。 使用单个共享的窗口 （通常是容器的） 和一些调度代码，控件接收到的相同的窗口服务，通常不到的性能损失。 具有一个窗口是主要对象不必要的开销。  
  
 在某些容器中使用你的控件时，某些优化不能一定改进性能。 例如，1996 年之前发布的容器不支持无窗口激活，因此实现此功能将不会提供较旧容器中的一项优势。 但是，几乎每个容器都支持持久性，以便优化你的控件的持久性代码将可能提高其性能任何容器中。 如果你的控件专门用于一种特定类型的容器，则你可能想要研究这些优化这一项受该容器。 一般情况下，但是，你应尝试实现许多中适用于特定控件，以确保你的控件以及它可能执行这些技术可以在多种不同的容器。  
  
 你可以实现许多通过这些优化[MFC ActiveX 控件向导](../mfc/reference/mfc-activex-control-wizard.md)上[控制设置](../mfc/reference/control-settings-mfc-activex-control-wizard.md)页。  
  
### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>MFC ActiveX 控件向导 OLE 优化选项  
  
|在 MFC ActiveX 控件向导控件设置|操作|详细信息|  
|-------------------------------------------------------|------------|----------------------|  
|**在可见时激活**复选框|清除|[关闭激活时可见的选项](../mfc/turning-off-the-activate-when-visible-option.md)|  
|**无窗口激活**复选框|选择|[提供无窗口激活](../mfc/providing-windowless-activation.md)|  
|**剪辑的设备上下文**复选框|选择|[使用未剪辑的设备上下文](../mfc/using-an-unclipped-device-context.md)|  
|**闪烁激活**复选框|选择|[提供无闪烁激活](../mfc/providing-flicker-free-activation.md)|  
|**将鼠标指针不活动时通知**复选框|选择|[不活动时提供鼠标交互](../mfc/providing-mouse-interaction-while-inactive.md)|  
|**优化绘制代码**复选框|选择|[优化控件绘制](../mfc/optimizing-control-drawing.md)|  
  
 有关实现这些优化的成员函数的详细信息，请参阅[COleControl](../mfc/reference/colecontrol-class.md)。 通过使用，如列出的成员函数[无窗口操作](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df)和[处于非活动状态的指针处理函数](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df)。  
  
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

