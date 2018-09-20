---
title: MFC ActiveX 控件向导控件设置 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.settings
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4533406b186142dd69f5ea7ad94cfb8a3c89d987
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423049"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>MFC ActiveX 控件向导控件设置

使用向导的此页可以指定希望该控件的行为方式。 例如，可以基于标准 Windows 控件类型上的控件、 优化其行为和外观，或指示该控件可以充当其他控件的容器。

有关如何选择效率最大化的控件的此页上的选项的详细信息，请参阅[MFC ActiveX 控件： 优化](../../mfc/mfc-activex-controls-optimization.md)。

## <a name="uielement-list"></a>UIElement 列表

- **创建基于控件**

   在此列表中，可以选择控件应从中继承的控件的类型。 列表是可用于控制类的一个子集`CreateWindowEx`和 commctrl.h 中指定的其他公共控件。 你的选择确定在控件的样式`PreCreateWindow`函数，在*ProjName*Ctrl.cpp 文件。 有关详细信息，请参阅[MFC ActiveX 控件： 子类化 Windows 控件](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。

   |控件|描述|
   |-------------|-----------------|
   |**按钮**|Windows 按钮控件|
   |**组合框**|Windows 组合框控件|
   |**编辑**|Windows 编辑框控件|
   |**列表框**|Windows 列表框控件|
   |**滚动条**|Windows 在滚动条控件|
   |**静态**|Windows 静态控件|
   |**msctls_hotkey32**|热键常见控件|
   |**msctls_progress32**|进度栏公共控件|
   |**msctls_statusbar32**|状态栏公共控件|
   |**msctls_trackbar32**|跟踪栏公用控件|
   |**msctls_updown32**|数值调节钮按钮 （或向上向下） 公共控件|
   |**SysAnimate32**|动画公共控件|
   |**SysHeader32**|标头公共控件|
   |**SysListView32**|列表视图公共控件|
   |**SysTabControl32**|选项卡上的公共控件|
   |**SysTreeView32**|树视图公共控件|

- **可见时激活**

   指定在访问时，为控件创建一个窗口。 默认情况下**可见时激活**选择选项。 如果你想要的操作延迟控件激活容器需要它 （例如，当用户单击鼠标），则清除此选项。 关闭此功能后，该控件不会产生窗口创建的费用之前所需。 有关详细信息，请参阅[关闭激活时可见选项](../../mfc/turning-off-the-activate-when-visible-option.md)。

- **在运行时不可见**

   指定控件在运行时具有的用户界面。 计时器是控件的一种你可能想要不可见。

- **具有一个关于框对话框**

   指定控件具有标准 Windows**有关**对话框中，后者将显示版本号和版权信息。

   > [!NOTE]
   > 用户如何访问控件的帮助取决于帮助的实现方式以及是否有与容器帮助集成控制帮助。 有关如何集成帮助，在详细信息[MSDN 库](http://go.microsoft.com/fwlink/p/?linkid=150542)网站中，搜索"将上下文相关帮助添加到 MFC ActiveX 控件"。

   当选择此选项时，它将插入`AboutBox`控制方法在项目控件类 (C*ProjName*Ctrl.cpp) 并将 AboutBox 添加到项目调度映射。 默认情况下，该选项是选中的。

- **优化绘制代码**

   指定的容器的原始 GDI 对象会自动还原毕竟容器控件，这些绘制到相同设备上下文、 绘制控件。 有关此功能的详细信息，请参阅[优化控件绘制](../../mfc/optimizing-control-drawing.md)。

- **无窗口激活**

   指定控件不会被激活时生成一个窗口。 对于非矩形或透明控件，允许无窗口激活，无窗口控件需要更少的系统开销比有窗口控件需要。 无窗口控件不允许的剪辑的设备上下文或无闪烁激活。 1996 年以前创建的容器不支持无窗口激活。 有关如何使用此选项的详细信息，请参阅[提供无窗口激活](../../mfc/providing-windowless-activation.md)。

- **剪辑的设备上下文**

   重写[colecontrol:: Getcontrolflags](../../mfc/reference/colecontrol-class.md#getcontrolflags)中的控制标头 (*projname*ctrl.h) 若要禁用对调用`IntersectClipRect`所做的`COleControl`。 在选择此选项，它提供了一个小的速度优势。 如果选择**无窗口激活**，此功能不可用。 有关详细信息，请参阅[使用未剪辑的设备上下文](../../mfc/using-an-unclipped-device-context.md)。

- **无闪烁激活**

   消除了绘制操作和控件的活动和非活动状态之间发生的随附 visual 闪烁。 如果选择**无窗口激活**，此功能不可用。 当设置此选项，`noFlickerActivate`标志是由返回的标志之一[colecontrol:: Getcontrolflags](../../mfc/reference/colecontrol-class.md#getcontrolflags)。 有关详细信息，请参阅[提供无闪烁激活](../../mfc/providing-flicker-free-activation.md)。

- **可在插入对象对话框**

   指定控件将推出**插入对象**已启用容器对话框。 选择此选项时`afxRegInsertable`标志是由返回的标志之一`AfxOleRegisterControlClass`。 通过使用**插入对象**对话框中，则用户可以插入新创建或复合文档到现有对象。

- **鼠标指针通知时处于非活动状态**

   使进程将鼠标指针通知，该控件是否控件处于活动状态。 选择此选项时`pointerInactive`标志是由返回的标志之一[colecontrol:: Getcontrolflags](../../mfc/reference/colecontrol-class.md#getcontrolflags)。 有关如何使用此选项的详细信息，请参阅[提供鼠标交互而处于非活动状态](../../mfc/providing-mouse-interaction-while-inactive.md)。

- **可作为简单框架控件**

   指定的控件是通过设置控件位 OLEMISC_SIMPLEFRAME 其他控件的容器。 有关详细信息，在[MSDN 库](http://go.microsoft.com/fwlink/p/?linkid=150542)网站中，搜索"简单的框架站点包容"。

- **以异步方式加载属性**

   允许重置所有以前的异步数据，并启动新的控件的异步属性加载。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[应用程序设置, MFC ActiveX 控件向导](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[MFC ActiveX 控件向导的控件名称](../../mfc/reference/control-names-mfc-activex-control-wizard.md)

