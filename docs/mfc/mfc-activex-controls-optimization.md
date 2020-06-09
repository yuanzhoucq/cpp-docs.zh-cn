---
title: MFC ActiveX 控件：优化
ms.date: 09/12/2018
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
ms.openlocfilehash: b4e12889ca1bb5f4bb423a1f1ede1c396f8d60b5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615405"
---
# <a name="mfc-activex-controls-optimization"></a>MFC ActiveX 控件：优化

本文介绍可用于优化 ActiveX 控件以提高性能的方法。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

主题[关闭 "在可见时激活" 选项](turning-off-the-activate-when-visible-option.md)并[提供鼠标交互，而非活动讨论在](providing-mouse-interaction-while-inactive.md)激活之前不创建窗口的控件。 [提供无窗口激活](providing-windowless-activation.md)的主题讨论从不创建窗口的控件（即使它们已激活）。

Windows 对 OLE 对象有两个主要缺点：它们在活动时阻止对象处于透明或非矩形状态，并且它们会将大开销添加到控件的实例化和显示。 通常，创建窗口时，会占用60% 的控件创建时间。 使用单个共享窗口（通常是容器的）和某些调度代码，控件接收相同的窗口服务，通常不会损失性能。 具有窗口的主要是对象的不必要开销。

在某些容器中使用控件时，某些优化并不一定会提高性能。 例如，在1996之前发布的容器不支持无窗口激活，因此实现此功能将不会在较旧的容器中提供权益。 不过，几乎每个容器都支持持久性，因此优化控件的持久性代码可能会提高其在任何容器中的性能。 如果你的控件专门用于一种特定类型的容器，你可能想要研究该容器支持哪些优化。 但一般情况下，您应该尝试实现与特定控件适用的这些方法，以确保控件执行和可能在各种容器中运行。

您可以在 "[控件设置](reference/control-settings-mfc-activex-control-wizard.md)" 页上通过[MFC ActiveX 控件向导](reference/mfc-activex-control-wizard.md)实现其中许多优化。

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>MFC ActiveX 控件向导 OLE 优化选项

|MFC ActiveX 控件向导中的控件设置|操作|更多信息|
|-------------------------------------------------------|------------|----------------------|
|**可见时激活**"复选框|Clear|[关闭 "在可见时激活" 选项](turning-off-the-activate-when-visible-option.md)|
|"**无窗口激活**" 复选框|Select|[提供无窗口激活](providing-windowless-activation.md)|
|"**未剪辑设备上下文**" 复选框|Select|[使用未剪辑设备上下文](using-an-unclipped-device-context.md)|
|"**无闪烁激活**" 复选框|Select|[提供无闪烁激活](providing-flicker-free-activation.md)|
|"不**活动时，鼠标指针通知**" 复选框|Select|[在非活动时提供鼠标交互](providing-mouse-interaction-while-inactive.md)|
|**优化的绘图代码**复选框|Select|[优化控件绘制](optimizing-control-drawing.md)|

有关实现这些优化的成员函数的详细信息，请参阅[COleControl](reference/colecontrol-class.md)。

有关详细信息，请参见:

- [优化持久性和初始化](optimizing-persistence-and-initialization.md)

- [提供无窗口激活](providing-windowless-activation.md)

- [关闭 "在可见时激活" 选项](turning-off-the-activate-when-visible-option.md)

- [在非活动时提供鼠标交互](providing-mouse-interaction-while-inactive.md)

- [提供无闪烁激活](providing-flicker-free-activation.md)

- [使用未剪辑设备上下文](using-an-unclipped-device-context.md)

- [优化控件绘制](optimizing-control-drawing.md)

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)
