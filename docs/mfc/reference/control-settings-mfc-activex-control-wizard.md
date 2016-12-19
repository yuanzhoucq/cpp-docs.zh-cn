---
title: "MFC ActiveX 控件向导控件设置 | Microsoft Docs"
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
  - "vc.appwiz.mfc.ctl.settings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控件向导，控件设置"
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
caps.latest.revision: 16
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件向导控件设置
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用此向导页可以指定控件的行为方式。  例如，可以基于标准 Windows 控件类型的控件，优化其行为和外观，或指示控件可以作为其他控件的容器。  
  
 关于如何在此页选择选项以最大化控件的效率的更多信息，请参见 [MFC ActiveX 控件：优化](../../mfc/mfc-activex-controls-optimization.md)。  
  
## UIElement 列表  
 **创建的控件基于**  
 在此列表中，选择应继承的控件的类型。  列表是 `CreateWindowEx` 可用的控件类和其他 commctrl.h 中指定的公共控件的一个子集。  您的选择将决定 *ProjName*Ctrl.cpp 文件中的 `PreCreateWindow` 函数中的控件样式。  有关详细信息，请参阅[MFC ActiveX 控件：创建 Windows 控件的子类](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md)。  
  
|控件|说明|  
|--------|--------|  
|**BUTTON**|一个 Windows 按钮控件|  
|**COMBOBOX**|一个 Windows 组合框控件|  
|**EDIT**|一个 Windows 编辑框控件|  
|**LISTBOX**|一个 Windows 列表框控件|  
|**SCROLLBAR**|一个 Windows 滚动条控件|  
|**STATIC**|一个 Windows 静态控件|  
|**msctls\_hotkey32**|热键公共控件|  
|**msctls\_progress32**|进度栏公共控件|  
|**msctls\_statusbar32**|状态栏公用控件|  
|**msctls\_trackbar32**|跟踪栏公用控件|  
|**msctls\_updown32**|数值调节钮（或上下）常见控件|  
|**SysAnimate32**|动画公用控件|  
|**SysHeader32**|标头公用控件|  
|**SysListView32**|列表视图公用控件|  
|**SysTabControl32**|选项卡公用控件|  
|**SysTreeView32**|树状视图公用控件|  
  
 **可见时激活**  
 访问时说明窗口是为控件创建的。  默认情况下，将选择**“可见时激活”**选项。  如果您要将控件激活延迟到容器需要时（例如，当用户单击鼠标时），请清除此选项。  此功能关闭时，该控件不会承担窗口创建的费用，除非必需承担。  有关详细信息，请参阅[关闭“可见时激活”选项](../../mfc/turning-off-the-activate-when-visible-option.md)。  
  
 **“运行时不可见”**  
 指定运行时没有用户界面的控件。  计时器是您希望其不可见的一类控件。  
  
 **“有关于”对话框**  
 指定具有标准的 Windows **“关于”**对话框的控件，此对话框显示该控件的版本号和版权信息。  
  
> [!NOTE]
>  用户如何访问控件的帮助取决于如何实现帮助和是否有与容器帮助集成控制的帮助。  有关如何集成帮助的更多信息，在 [MSDN Library](http://go.microsoft.com/fwlink/?linkID=150542) 网站上，搜索“添加MFC ActiveX 控件的上下文相关帮助 ”。  
  
 选择此选项时，在项目控件类中插入 `AboutBox`控件方法 \(C*ProjName*Ctrl.cpp\)，并将 AboutBox 添加到项目调度映射。  默认情况下，该选项是选中的。  
  
 **优化的绘图代码**  
 在控制所有容器之后，指定容器自动还原原始 GDI 对象，将这些原始 GDI 对象绘制成已绘制的相同设备上下文。  有关此功能的更多信息，请参见 [优化控件绘制](../../mfc/optimizing-control-drawing.md)。  
  
 **无窗口激活**  
 指定控件在激活时不产生窗口。  无窗口激活允许非矩形或透明控件，并且无窗口控件比有窗口控件所需要的系统开销更少。  无窗口激活没有考虑未剪辑的设备上下文和无闪烁激活。  1996 年以前创建的容器不支持无窗口激活。  有关如何使用此选项的更多信息，请参见[提供无窗口激活](../../mfc/providing-windowless-activation.md)。  
  
 **“未剪辑的设备上下文”**  
 重写控制表头 \(*projname*ctrl.h\) 中的 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md) 以禁用对`COleControl`生成的`IntersectClipRect` 的调用。  选择此选项时，将带来较小的速度优势。  如果选择**“无窗口激活”**，则此功能不可用。  有关详细信息，请参阅[使用未剪辑的设备上下文](../../mfc/using-an-unclipped-device-context.md)。  
  
 **无闪烁激活 \(Flicker\-Free Activation\)**  
 消除绘图操作以及可用和停用控件状态之间发生的附带视觉闪烁。  如果选择**“无窗口激活”**，则此功能不可用。  设置此选项时，`noFlickerActivate` 标志是由 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md) 返回的标志之一。  有关详细信息，请参阅[提供无闪烁激活](../../mfc/providing-flicker-free-activation.md)。  
  
 **在“插入对象”对话框中可用**  
 指定控件在已启用容器的**“插入对象”**对话框中可用。  在选择此选项时，`afxRegInsertable` 标志是由 `AfxOleRegisterControlClass` 返回的标志之一。  通过使用**“插入对象”**对话框，用户可将新创建的或现有的对象插入复合文档。  
  
 **不活动时有鼠标指针通知**  
 启用控件进程鼠标指针通知，无论控件是否可用。  在选择此选项时，`pointerInactive` 标志是由 [COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md) 返回的标志之一。  有关如何使用此选项的更多信息，请参见 [不活动时提供鼠标交互](../../mfc/providing-mouse-interaction-while-inactive.md)。  
  
 **作为简单框架控件**  
 通过为控件设置 `OLEMISC_SIMPLEFRAME` 位来指定该控件是其他控件的容器。  有关更多信息，请在[MSDN Library](http://go.microsoft.com/fwlink/?linkID=150542) 网站，搜索”简单的框架站点”。  
  
 **异步加载属性**  
 启用重置任何上个异步数据并启动新的负载异步属性控件。  
  
## 请参阅  
 [MFC ActiveX 控件向导](../../mfc/reference/mfc-activex-control-wizard.md)   
 [应用程序设置, MFC ActiveX 控件向导](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [MFC ActiveX 控件向导的控件名称](../../mfc/reference/control-names-mfc-activex-control-wizard.md)