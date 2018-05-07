---
title: MFC ActiveX 控件向导控件设置 |Microsoft 文档
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
ms.openlocfilehash: 2161cea739d918bc0f5772a6cb08c29082a6e670
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="control-settings-mfc-activex-control-wizard"></a>MFC ActiveX 控件向导控件设置
向导的此页用于指定你希望如何控制行为。 例如，你可以基于标准的 Windows 控件类型上的控件、 优化其行为和外观，或指示该控件可以充当其他控件的容器。  
  
 有关如何选择此页上的选项，以最大化控件的效率的详细信息，请参阅[MFC ActiveX 控件： 优化](../../mfc/mfc-activex-controls-optimization.md)。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **创建基于控制**  
 在此列表中，你可以选择的控件应从中继承的控件的种类。 列表是可用于的控件类的一个子集`CreateWindowEx`和 commctrl.h 中指定的其他公共控件。 你的选择确定在控件的样式`PreCreateWindow`函数中*ProjName*Ctrl.cpp 文件。 有关详细信息，请参阅[MFC ActiveX 控件： 子类化 Windows 控件](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
|控件|描述|  
|-------------|-----------------|  
|**按钮**|Windows 按钮控件|  
|**组合框**|Windows 组合框控件|  
|**编辑**|Windows 编辑框控件|  
|**列表框**|Windows 列表框控件|  
|**滚动条**|Windows 滚动条控件|  
|**静态**|Windows 静态控件|  
|**msctls_hotkey32**|热键公共控件|  
|**msctls_progress32**|一个进度栏公共控件|  
|**msctls_statusbar32**|状态栏公共控件|  
|**msctls_trackbar32**|跟踪栏公共控件|  
|**msctls_updown32**|数值调节按钮 （或启动关闭） 公共控件|  
|**SysAnimate32**|动画公共控件|  
|**SysHeader32**|标头公共控件|  
|**SysListView32**|列表视图公共控件|  
|**SysTabControl32**|选项卡上的公共控件|  
|**SysTreeView32**|树视图公共控件|  
  
 **可见时激活**  
 指定在访问时，为控件创建一个窗口。 默认情况下，**可见时激活**选项。 如果你想要的操作延迟控件激活容器要求它 （例如，当用户单击鼠标时），则清除此选项。 当此功能关闭时，该控件不会产生窗口创建的费用之前需要。 有关详细信息，请参阅[关闭激活时可见选项](../../mfc/turning-off-the-activate-when-visible-option.md)。  
  
 **在运行时不可见**  
 指定该控件具有在运行时没有用户界面。 计时器是控件的一种你可能想要不可见。  
  
 **具有关于对话框**  
 指定该控件具有标准的 Windows**有关**对话框中，后者将显示版本号和版权信息。  
  
> [!NOTE]
>  用户如何访问控件的帮助取决于帮助的实现方式和是否已与容器帮助集成的控件帮助。 有关详细信息，有关如何在集成的帮助， [MSDN 库](http://go.microsoft.com/fwlink/p/?linkid=150542)网站中，搜索"将上下文相关帮助添加到 MFC ActiveX 控件"。  
  
 当选择此选项时，它将插入`AboutBox`控制项目控件类中的方法 (C*ProjName*Ctrl.cpp) 并将 AboutBox 添加到项目调度映射。 默认情况下，该选项是选中的。  
  
 **优化绘制代码**  
 指定容器还原原始的 GDI 对象自动在所有容器控件中，它绘制到相同的设备上下文，然后绘制。 有关此功能的详细信息，请参阅[优化控件绘制](../../mfc/optimizing-control-drawing.md)。  
  
 **无窗口激活**  
 指定控件不会激活它时生成一个窗口。 非矩形或透明控件，允许无窗口激活，无窗口控件要求需要比有窗口控件的系统开销更少。 无窗口控件不允许的剪辑的设备上下文或闪烁激活。 1996 年以前创建的容器不支持无窗口激活。 有关如何使用此选项的详细信息，请参阅[提供无窗口激活](../../mfc/providing-windowless-activation.md)。  
  
 **剪辑的设备上下文**  
 重写[COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)中的控制标头 (*projname*ctrl.h) 若要禁用对的调用`IntersectClipRect`由`COleControl`。 当选择此选项时，它提供了小的速度优势。 如果你选择**无窗口激活**，此功能不可用。 有关详细信息，请参阅[使用未剪辑的设备上下文](../../mfc/using-an-unclipped-device-context.md)。  
  
 **无闪烁激活**  
 消除了绘制操作和伴随的可视闪烁活动和非活动状态的控件之间发生。 如果你选择**无窗口激活**，此功能不可用。 当设置此选项，`noFlickerActivate`标志是通过返回的标志之一[COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)。 有关详细信息，请参阅[提供无闪烁激活](../../mfc/providing-flicker-free-activation.md)。  
  
 **可用在插入对象对话框**  
 指定控件可在**插入对象**已启用容器的对话框。 当选择此选项，`afxRegInsertable`标志是通过返回的标志之一`AfxOleRegisterControlClass`。 通过使用**插入对象**对话框中，则用户可以插入新创建或现有将对象插入复合文档。  
  
 **当处于非活动状态时，鼠标指针发送通知**  
 是否控件处于活动状态，请启用过程鼠标指针通知，该控件。 当选择此选项，`pointerInactive`标志是通过返回的标志之一[COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)。 有关如何使用此选项的详细信息，请参阅[提供鼠标交互时处于非活动状态](../../mfc/providing-mouse-interaction-while-inactive.md)。  
  
 **作为简单框架控件**  
 指定控件通过设置为其他控件的容器`OLEMISC_SIMPLEFRAME`的控制位。 有关详细信息，在[MSDN 库](http://go.microsoft.com/fwlink/p/?linkid=150542)网站中，搜索"简单帧站点包含"。  
  
 **以异步方式加载属性**  
 允许任何以前的异步数据重置并启动新负载的控件的异步属性。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)   
 [应用程序设置，MFC ActiveX 控件向导](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控件向导的控件名称](../../mfc/reference/control-names-mfc-activex-control-wizard.md)

