---
title: "MFC ActiveX 控件向导控件设置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.ctl.settings
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 35ec579e6f777a3dffd87adc5a86af2ea38b30f4
ms.lasthandoff: 02/24/2017

---
# <a name="control-settings-mfc-activex-control-wizard"></a>MFC ActiveX 控件向导控件设置
使用向导的此页可以指定希望该控件的行为方式。 例如，可以基于标准 Windows 控件类型上的控件、 优化其行为和外观，或指示该控件可以作为其他控件的容器。  
  
 有关如何选择此页上的选项，以使该控件的效率最大化的详细信息，请参阅[MFC ActiveX 控件︰ 优化](../../mfc/mfc-activex-controls-optimization.md)。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **创建基于控件**  
 在此列表中，您可以选择的控件应从中继承的控件的种类。 列表是可用于的控件类的一个子集`CreateWindowEx`和 commctrl.h 中指定的其他常用控件。 你的选择确定在控件的样式`PreCreateWindow`，此功能在*ProjName*Ctrl.cpp 文件。 有关详细信息，请参阅[MFC ActiveX 控件︰ 子类化 Windows 控件](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
|控件|描述|  
|-------------|-----------------|  
|**按钮**|Windows 按钮控件|  
|**组合框**|Windows 组合框控件|  
|**编辑**|Windows 编辑框控件|  
|**列表框**|Windows 列表框控件|  
|**滚动条**|Windows 滚动条控件|  
|**静态**|Windows 静态控件|  
|**msctls_hotkey32**|热键公共控件|  
|**msctls_progress32**|进度栏公共控件|  
|**msctls_statusbar32**|状态栏公共控件|  
|**msctls_trackbar32**|跟踪栏公共控件|  
|**msctls_updown32**|数值调节按钮 （或向上向下） 公共控件|  
|**SysAnimate32**|动画公共控件|  
|**SysHeader32**|标头的公共控件|  
|**SysListView32**|列表视图公共控件|  
|**SysTabControl32**|选项卡上的公共控件|  
|**SysTreeView32**|树视图公共控件|  
  
 **可见时激活**  
 指定在访问时，在为控件创建一个窗口。 默认情况下，**可见时激活**选择选项。 如果您想要控件激活延迟到容器需要 （例如，当用户单击鼠标），则清除此选项。 此功能关闭时，控件将不会产生窗口创建的费用直到需要为止。 有关详细信息，请参阅[关闭激活时可见选项](../../mfc/turning-off-the-activate-when-visible-option.md)。  
  
 **在运行时不可见**  
 指定控件在运行时有没有用户界面。 计时器是控件的一种可能想要不可见。  
  
 **具有一个关于框中对话框**  
 指定该控件具有标准的 Windows**有关**对话框中，后者会显示版本号和版权信息。  
  
> [!NOTE]
>  用户如何访问控件的帮助取决于帮助的实现方式以及是否有与容器帮助集成控件帮助。 有关如何集成帮助，请在详细信息[MSDN Library](http://go.microsoft.com/fwlink/linkid=150542)网站中搜索"将上下文相关帮助添加到 MFC ActiveX 控件"。  
  
 当选择此选项时，它将插入`AboutBox`控制项目控件类中的方法 (C*ProjName*Ctrl.cpp) 并将 aboutbox 添加到项目调度映射。 默认情况下，该选项是选中的。  
  
 **优化绘制代码**  
 指定容器还原原始的 GDI 对象自动毕竟容器控件中，绘制到相同设备上下文，绘制完。 有关此功能的详细信息，请参阅[优化控件绘制](../../mfc/optimizing-control-drawing.md)。  
  
 **无窗口激活**  
 指定该控件不会被激活时生成一个窗口。 对于非矩形或透明控件，允许无窗口激活，无窗口控件需要更少的系统开销比有窗口控件需要。 无窗口控件不允许为剪辑的设备上下文或无闪烁激活。 1996 年以前创建的容器不支持无窗口激活。 有关如何使用此选项的详细信息，请参阅[提供无窗口激活](../../mfc/providing-windowless-activation.md)。  
  
 **剪辑的设备上下文**  
 重写[COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)中控制标头 (*projname*ctrl.h) 若要禁用对调用`IntersectClipRect`所做的`COleControl`。 当选择此选项时，它提供了一个小的速度优势。 如果您选择**无窗口激活**，此功能将不可用。 有关详细信息，请参阅[使用未剪辑的设备上下文](../../mfc/using-an-unclipped-device-context.md)。  
  
 **无闪烁激活**  
 消除了绘图操作和伴随的可视闪烁控件的活动和非活动状态之间发生。 如果您选择**无窗口激活**，此功能将不可用。 当设置此选项，`noFlickerActivate`标志是一个由返回的标志[COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)。 有关详细信息，请参阅[提供无闪烁激活](../../mfc/providing-flicker-free-activation.md)。  
  
 **可在插入对象对话框**  
 指定该控件可在**插入对象**已启用容器的对话框。 当选择此选项，`afxRegInsertable`标志是一个由返回的标志`AfxOleRegisterControlClass`。 通过使用**插入对象**对话框中，则用户可以插入新创建或现有的对象到复合文档。  
  
 **当非活动状态时，鼠标指针发送通知**  
 使处理鼠标指针通知，该控件是否控件处于活动状态。 当选择此选项，`pointerInactive`标志是一个由返回的标志[COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags)。 有关如何使用此选项的详细信息，请参阅[提供鼠标交互时处于非活动状态](../../mfc/providing-mouse-interaction-while-inactive.md)。  
  
 **作为简单框架控件**  
 指定控件通过设置为其他控件的容器`OLEMISC_SIMPLEFRAME`位控件。 有关详细信息上, [MSDN Library](http://go.microsoft.com/fwlink/linkid=150542)网站中搜索"简单框架站点包容"。  
  
 **以异步方式加载属性**  
 允许所有以前的异步数据重置并启动新的加载该控件的异步属性。  
  
## <a name="see-also"></a>另请参阅  
 [MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)   
 [MFC ActiveX 控件向导的应用程序设置](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控件向导的控件名称](../../mfc/reference/control-names-mfc-activex-control-wizard.md)


