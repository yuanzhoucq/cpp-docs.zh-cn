---
title: MFC ActiveX 控件向导控件设置
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.settings
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
ms.openlocfilehash: 1578ca7f4134e51e0ba0d3c2b247dcafcb0fbd67
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405008"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>MFC ActiveX 控件向导控件设置

使用向导的此页可指定控件的行为方式。 例如，你可以基于标准 Windows 控件类型来控制控件，优化其行为和外观，或指示控件可充当其他控件的容器。

有关如何在此页上选择选项以最大程度地提高控件效率的详细信息，请参阅[MFC ActiveX 控件：优化](../../mfc/mfc-activex-controls-optimization.md)。

## <a name="uielement-list"></a>UIElement 列表

- **创建控件基于**

   在此列表中，可以选择控件应从中继承的控件类型。 此列表是可用于 `CreateWindowEx` 和 commctrl 中指定的其他公共控件的控件类的子集。 你的选择将确定 `PreCreateWindow` *ProjName*Ctrl .cpp 文件中函数的控件样式。 有关详细信息，请参阅[MFC ActiveX 控件：对 Windows 控件进行子类](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)化。

   |控制|说明|
   |-------------|-----------------|
   |**鼠标**|Windows 按钮控件|
   |**同**|Windows 组合框控件|
   |**编辑**|Windows 编辑框控件|
   |**改**|Windows 列表框控件|
   |**长度**|Windows 滚动条控件|
   |**静止**|Windows 静态控件|
   |**msctls_hotkey32**|热键公共控件|
   |**msctls_progress32**|进度栏公共控件|
   |**msctls_statusbar32**|状态栏公共控件|
   |**msctls_trackbar32**|跟踪条公共控件|
   |**msctls_updown32**|数值调节钮（或上下）公共控件|
   |**SysAnimate32**|动画公共控件|
   |**SysHeader32**|标头公共控件|
   |**SysListView32**|列表视图公共控件|
   |**SysTabControl32**|选项卡公共控件|
   |**SysTreeView32**|树视图公共控件|

- **可见时激活**

   指定在访问控件时为控件创建窗口。 默认情况下，选择 "**在可见时激活**" 选项。 如果要延迟控件激活，直至容器需要它（例如，当用户单击鼠标时），请清除此选项。 如果此功能处于关闭状态，则在需要时，控件不会产生窗口创建的费用。 有关详细信息，请参阅[关闭激活时显示选项](../../mfc/turning-off-the-activate-when-visible-option.md)。

- **运行时不可见**

   指定控件在运行时没有用户界面。 计时器是您可能希望不可见的一种控件。

- **具有 "关于" 对话框**

   指定控件具有标准的 Windows "**关于**" 对话框，该对话框显示版本号和版权信息。

   > [!NOTE]
   > 用户访问控件帮助的方式取决于您如何实现该帮助以及您是否已将控件帮助集成到容器帮助中。

   当你选择此选项时，它将 `AboutBox` 在项目控件类（C*ProjName*）中插入控制方法，并将 AboutBox 添加到项目调度映射。 默认情况下选择此选项。

- **优化的绘图代码**

   指定容器在绘制到相同设备上下文的所有容器控件之后，自动还原原始 GDI 对象。 有关此功能的详细信息，请参阅[优化控件绘制](../../mfc/optimizing-control-drawing.md)。

- **无窗口激活**

   指定控件在激活时不生成窗口。 无窗口激活允许使用非矩形控件或透明控件，无窗口控件所需的系统开销比包含窗口的控件所需的系统开销更少。 无窗口控件不允许未剪辑设备上下文或无闪烁激活。 在1996之前创建的容器不支持无窗口激活。 有关如何使用此选项的详细信息，请参阅[提供无窗口激活](../../mfc/providing-windowless-activation.md)。

- **未剪辑设备上下文**

   重写控件标头中的[COleControl：： GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) （*projname*ctrl-c）以禁用对发出的调用 `IntersectClipRect` `COleControl` 。 如果选择此选项，将提供较小的速度优势。 如果选择 "**无窗口激活**"，则此功能不可用。 有关详细信息，请参阅[使用未剪辑设备上下文](../../mfc/using-an-unclipped-device-context.md)。

- **无闪烁激活**

   消除控件的活动和非活动状态之间发生的绘图操作和伴随的视觉闪烁。 如果选择 "**无窗口激活**"，则此功能不可用。 如果设置此选项， `noFlickerActivate` 标志为[COleControl：： GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)返回的标志之一。 有关详细信息，请参阅[提供无闪烁激活](../../mfc/providing-flicker-free-activation.md)。

- **在 "插入对象" 对话框中提供**

   指定控件将在已启用容器的 "**插入对象**" 对话框中可用。 如果选择此选项， `afxRegInsertable` 标志是返回的标志之一 `AfxOleRegisterControlClass` 。 通过使用 "**插入对象**" 对话框，用户可以将新创建的或现有的对象插入到复合文档中。

- **非活动时的鼠标指针通知**

   使控件能够处理鼠标指针通知，无论控件是否处于活动状态。 如果选择此选项， `pointerInactive` 标志为[COleControl：： GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)返回的标志之一。 有关如何使用此选项的详细信息，请参阅[在非活动状态下提供鼠标交互](../../mfc/providing-mouse-interaction-while-inactive.md)。

- **作为简单框架控件**

   指定控件是其他控件的容器，方法是为控件设置 OLEMISC_SIMPLEFRAME 位。 有关详细信息，请参阅[简单框架网站包含](/windows/win32/com/simple-frame-site-containment)。

- **异步加载属性**

   允许重置任何以前的异步数据，并启动该控件的异步属性的新加载。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[应用程序设置, MFC ActiveX 控件向导](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 控件向导的控件名称](../../mfc/reference/control-names-mfc-activex-control-wizard.md)
