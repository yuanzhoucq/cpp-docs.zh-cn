---
title: "CBasePane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBasePane::get_accKeyboardShortcut"
  - "CBasePane.get_accKeyboardShortcut"
  - "CBasePane.accSelect"
  - "get_accDefaultAction"
  - "accSelect"
  - "CBasePane.accHitTest"
  - "CBasePane.get_accRole"
  - "get_accKeyboardShortcut"
  - "CBasePane::Serialize"
  - "CBasePane"
  - "CBasePane::get_accDefaultAction"
  - "get_accParent"
  - "CBasePane::accSelect"
  - "accLocation"
  - "CBasePane.get_accDescription"
  - "get_accName"
  - "CBasePane::get_accChildCount"
  - "CBasePane.get_accChild"
  - "CBasePane::accHitTest"
  - "accHitTest"
  - "get_accHelp"
  - "CBasePane.get_accChildCount"
  - "CBasePane.get_accValue"
  - "CBasePane::get_accDescription"
  - "get_accChildCount"
  - "CBasePane.accLocation"
  - "CBasePane.PreTranslateMessage"
  - "CBasePane.get_accName"
  - "PreTranslateMessage"
  - "CBasePane::get_accFocus"
  - "get_accDescription"
  - "CBasePane::get_accRole"
  - "get_accValue"
  - "CBasePane.Serialize"
  - "CBasePane::accLocation"
  - "get_accRole"
  - "CBasePane::get_accChild"
  - "get_accFocus"
  - "CBasePane::get_accHelp"
  - "CBasePane.get_accDefaultAction"
  - "CBasePane.get_accHelp"
  - "CBasePane::PreTranslateMessage"
  - "CBasePane::get_accState"
  - "CBasePane.get_accParent"
  - "CBasePane::get_accParent"
  - "get_accChild"
  - "CBasePane::get_accValue"
  - "Serialize"
  - "get_accState"
  - "CBasePane.get_accState"
  - "CBasePane.get_accFocus"
  - "CBasePane::get_accName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accHitTest method"
  - "accLocation method"
  - "accSelect method"
  - "CBasePane class"
  - "get_accChild method"
  - "get_accChildCount method"
  - "get_accDefaultAction method"
  - "get_accDescription method"
  - "get_accFocus method"
  - "get_accHelp method"
  - "get_accKeyboardShortcut method"
  - "get_accName method"
  - "get_accParent method"
  - "get_accRole method"
  - "get_accState method"
  - "get_accValue method"
  - "PreTranslateMessage method"
  - "Serialize method"
ms.assetid: 8163dd51-d7c7-4def-9c74-61f8ecdfad82
caps.latest.revision: 43
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 44
---
# CBasePane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所有窗格的基类在MFC。  
  
## 语法  
  
```  
class CBasePane : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CBasePane::CBasePane`|默认构造函数。|  
|`CBasePane::~CBasePane`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CBasePane::accHitTest`|调用由框架来检索子元素或子对象中给出的点在屏幕上。  （重写 [CWnd::accHitTest](../Topic/CWnd::accHitTest.md)。）|  
|`CBasePane::accLocation`|调用由框架检索指定对象的当前屏幕位置。  （重写 [CWnd::accLocation](../Topic/CWnd::accLocation.md)。）|  
|[CBasePane::AccNotifyObjectFocusEvent](../Topic/CBasePane::AccNotifyObjectFocusEvent.md)|`CBasePane` 不使用此方法。|  
|`CBasePane::accSelect`|调用由框架修改选择或移动指定对象的键盘焦点。  （重写 [CWnd::accSelect](../Topic/CWnd::accSelect.md)。）|  
|[CBasePane::AddPane](../Topic/CBasePane::AddPane.md)|添加一个窗格到停靠管理器。|  
|[CBasePane::AdjustDockingLayout](../Topic/CBasePane::AdjustDockingLayout.md)|调用重定向到停靠管理器调整停靠格式。|  
|[CBasePane::AdjustLayout](../Topic/CBasePane::AdjustLayout.md)|调用由结构，当窗格应调整其内部格式。|  
|[CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)|计算控件条的水平大小。|  
|[CBasePane::CanAcceptPane](../Topic/CBasePane::CanAcceptPane.md)|确定另一个窗格是否可以停靠到窗格。|  
|[CBasePane::CanAutoHide](../Topic/CBasePane::CanAutoHide.md)|确定窗格是否支持自动隐藏模式。|  
|[CBasePane::CanBeAttached](../Topic/CBasePane::CanBeAttached.md)|确定窗格是否可以停靠到另一个窗格。|  
|[CBasePane::CanBeClosed](../Topic/CBasePane::CanBeClosed.md)|确定窗格是否可以关闭的。|  
|[CBasePane::CanBeDocked](../Topic/CBasePane::CanBeDocked.md)|确定窗格是否可以停靠到另一个窗格。|  
|[CBasePane::CanBeResized](../Topic/CBasePane::CanBeResized.md)|确定窗格是否可调整大小。|  
|[CBasePane::CanBeTabbedDocument](../Topic/CBasePane::CanBeTabbedDocument.md)|指定窗格是否可以转换为选项卡式MDI文档。|  
|[CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md)|确定窗格是否可以浮动。|  
|[CBasePane::CanFocus](../Topic/CBasePane::CanFocus.md)|指定窗格是否可以接收焦点。|  
|[CBasePane::CopyState](../Topic/CBasePane::CopyState.md)|复制特定窗格的状态。|  
|[CBasePane::CreateDefaultMiniframe](../Topic/CBasePane::CreateDefaultMiniframe.md)|如果窗格可以浮点数，创建一个和框架窗口。|  
|[CBasePane::CreateEx](../Topic/CBasePane::CreateEx.md)|创建窗格控件。|  
|[CBasePane::DockPane](../Topic/CBasePane::DockPane.md)|停靠一个窗格到另一个窗格或到框架窗口。|  
|[CBasePane::DockPaneUsingRTTI](../Topic/CBasePane::DockPaneUsingRTTI.md)|使用运行时类型信息，停靠窗格。|  
|[CBasePane::DockToFrameWindow](../Topic/CBasePane::DockToFrameWindow.md)|停靠一个窗格停靠到框架。|  
|[CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)|确定另一个窗格是否可以动态插入此窗格和父框架。|  
|[CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md)|启用窗格的停靠到主框架。|  
|[CBasePane::EnableGripper](../Topic/CBasePane::EnableGripper.md)|启用或禁用手柄。  手柄有效，用户可以通过拖动它将重新定位窗格。|  
|`CBasePane::FillWindowRect`|内部使用。|  
|[CBasePane::FloatPane](../Topic/CBasePane::FloatPane.md)|浮动窗格。|  
|`CBasePane::get_accChild`|调用由框架检索一 `IDispatch` 接口的地址指定的子级。  （重写 [CWnd::get\_accChild](../Topic/CWnd::get_accChild.md)。）|  
|`CBasePane::get_accChildCount`|调用由框架检索属于该子对象的数目。  （重写 [CWnd::get\_accChildCount](../Topic/CWnd::get_accChildCount.md)。）|  
|`CBasePane::get_accDefaultAction`|调用由框架检索描述对象的默认事件的字符串。  （重写 [CWnd::get\_accDefaultAction](../Topic/CWnd::get_accDefaultAction.md)。）|  
|`CBasePane::get_accDescription`|调用由框架检索描述指定对象的可视外观的字符串。  （重写 [CWnd::get\_accDescription](../Topic/CWnd::get_accDescription.md)。）|  
|`CBasePane::get_accFocus`|调用由框架检索具有键盘焦点的对象。  （重写 [CWnd::get\_accFocus](../Topic/CWnd::get_accFocus.md)。）|  
|`CBasePane::get_accHelp`|调用由框架检索对象的属性帮助字符串。  （重写 [CWnd::get\_accHelp](../Topic/CWnd::get_accHelp.md)。）|  
|[CBasePane::get\_accHelpTopic](../Topic/CBasePane::get_accHelpTopic.md)|调用由框架检索与指定的对象和适当的主题标识符在该文件中WinHelpfile的完整路径。  （重写 [CWnd::get\_accHelpTopic](../Topic/CWnd::get_accHelpTopic.md)。）|  
|`CBasePane::get_accKeyboardShortcut`|调用由框架检索对象的指定热键。  （重写 [CWnd::get\_accKeyboardShortcut](../Topic/CWnd::get_accKeyboardShortcut.md)。）|  
|`CBasePane::get_accName`|调用由框架检索指定对象的名称。  （重写 [CWnd::get\_accName](../Topic/CWnd::get_accName.md)。）|  
|`CBasePane::get_accParent`|调用由框架检索对象的父级的 `IDispatch` 接口。  （重写 [CWnd::get\_accParent](../Topic/CWnd::get_accParent.md)。）|  
|`CBasePane::get_accRole`|调用由框架检索描述指定对象的角色信息。  （重写 [CWnd::get\_accRole](../Topic/CWnd::get_accRole.md)。）|  
|[CBasePane::get\_accSelection](../Topic/CBasePane::get_accSelection.md)|调用由框架检索此对象的选定的子级。  （重写 [CWnd::get\_accSelection](../Topic/CWnd::get_accSelection.md)。）|  
|`CBasePane::get_accState`|调用由框架检索指定对象的当前状态。  （重写 [CWnd::get\_accState](../Topic/CWnd::get_accState.md)。）|  
|`CBasePane::get_accValue`|调用由框架检索指定对象的值。  （重写 [CWnd::get\_accValue](../Topic/CWnd::get_accValue.md)。）|  
|[CBasePane::GetCaptionHeight](../Topic/CBasePane::GetCaptionHeight.md)|返回标题高度。|  
|[CBasePane::GetControlBarStyle](../Topic/CBasePane::GetControlBarStyle.md)|返回控制条样式。|  
|[CBasePane::GetCurrentAlignment](../Topic/CBasePane::GetCurrentAlignment.md)|返回当前窗格对齐。|  
|[CBasePane::GetDockingMode](../Topic/CBasePane::GetDockingMode.md)|返回窗格的当前停靠模式。|  
|[CBasePane::GetDockSiteFrameWnd](../Topic/CBasePane::GetDockSiteFrameWnd.md)|返回指向是窗格的停靠站点的窗口。|  
|[CBasePane::GetEnabledAlignment](../Topic/CBasePane::GetEnabledAlignment.md)|返回适合窗格的CBRS\_ALIGN\_样式。|  
|[CBasePane::GetMFCStyle](../Topic/CBasePane::GetMFCStyle.md)|返回窗格样式特定于MFC。|  
|[CBasePane::GetPaneIcon](../Topic/CBasePane::GetPaneIcon.md)|返回的句柄窗格图标。|  
|`CBasePane::GetPaneRect`|内部使用。|  
|[CBasePane::GetPaneRow](../Topic/CBasePane::GetPaneRow.md)|返回指向窗格停靠的 [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)对象。|  
|[CBasePane::GetPaneStyle](../Topic/CBasePane::GetPaneStyle.md)|返回窗格样式。|  
|[CBasePane::GetParentDockSite](../Topic/CBasePane::GetParentDockSite.md)|返回指向父停靠站点。|  
|[CBasePane::GetParentMiniFrame](../Topic/CBasePane::GetParentMiniFrame.md)|返回指向父和框架窗口。|  
|[CBasePane::GetParentTabbedPane](../Topic/CBasePane::GetParentTabbedPane.md)|返回指向父选项卡式窗格。|  
|[CBasePane::GetParentTabWnd](../Topic/CBasePane::GetParentTabWnd.md)|返回指向是在选项卡中的父窗口。|  
|[CBasePane::GetRecentVisibleState](../Topic/CBasePane::GetRecentVisibleState.md)|在窗格中，从存档时，已还原框架调用此方法。|  
|[CBasePane::HideInPrintPreviewMode](../Topic/CBasePane::HideInPrintPreviewMode.md)|指定窗格是否在打印预览隐藏。|  
|[CBasePane::InsertPane](../Topic/CBasePane::InsertPane.md)|注册了停靠管理器中指定的窗格。|  
|[CBasePane::IsAccessibilityCompatible](../Topic/CBasePane::IsAccessibilityCompatible.md)|指定窗格是否支持Active Accessibility。|  
|[CBasePane::IsAutoHideMode](../Topic/CBasePane::IsAutoHideMode.md)|确定窗格是否在自动隐藏模式。|  
|[CBasePane::IsDialogControl](../Topic/CBasePane::IsDialogControl.md)|指定窗格是否对话框控件。|  
|[CBasePane::IsDocked](../Topic/CBasePane::IsDocked.md)|确定窗格是停靠。|  
|[CBasePane::IsFloating](../Topic/CBasePane::IsFloating.md)|确定窗格是浮动。|  
|[CBasePane::IsHorizontal](../Topic/CBasePane::IsHorizontal.md)|确定窗格是水平停靠。|  
|[CBasePane::IsInFloatingMultiPaneFrameWnd](../Topic/CBasePane::IsInFloatingMultiPaneFrameWnd.md)|指定窗格是否在多窗格框架窗口。|  
|[CBasePane::IsMDITabbed](../Topic/CBasePane::IsMDITabbed.md)|确定窗格是否已添加到MDI子窗口，在选项卡式文档。|  
|[CBasePane::IsPaneVisible](../Topic/CBasePane::IsPaneVisible.md)|指定 `WS_VISIBLE` 标志是否为窗格中设置。|  
|[CBasePane::IsPointNearDockSite](../Topic/CBasePane::IsPointNearDockSite.md)|确定指定的点是否在停靠站点附近。|  
|[CBasePane::IsResizable](../Topic/CBasePane::IsResizable.md)|确定窗格是否可调整大小。|  
|[CBasePane::IsRestoredFromRegistry](../Topic/CBasePane::IsRestoredFromRegistry.md)|确定窗格是从注册表中恢复。|  
|[CBasePane::IsTabbed](../Topic/CBasePane::IsTabbed.md)|确定窗格是在一个选项卡式窗口的选项卡控件插入了。|  
|`CBasePane::IsTooltipTopmost`|内部使用。|  
|[CBasePane::IsVisible](../Topic/CBasePane::IsVisible.md)|确定窗格是否可见。|  
|[CBasePane::LoadState](../Topic/CBasePane::LoadState.md)|从注册表填充窗格状态。|  
|[CBasePane::MoveWindow](../Topic/CBasePane::MoveWindow.md)|移动窗格。|  
|[CBasePane::OnAfterChangeParent](../Topic/CBasePane::OnAfterChangeParent.md)|调用由框架，更改了窗格的父级。|  
|[CBasePane::OnBeforeChangeParent](../Topic/CBasePane::OnBeforeChangeParent.md)|调用由窗格之前的framework更改其父窗口。|  
|[CBasePane::OnDrawCaption](../Topic/CBasePane::OnDrawCaption.md)|在绘制时，框架调用此方法声明中。|  
|[CBasePane::OnMovePaneDivider](../Topic/CBasePane::OnMovePaneDivider.md)|当前不使用此方法。|  
|[CBasePane::OnPaneContextMenu](../Topic/CBasePane::OnPaneContextMenu.md)|调用由结构，在生成具有窗格中列出的菜单。|  
|[CBasePane::OnRemoveFromMiniFrame](../Topic/CBasePane::OnRemoveFromMiniFrame.md)|调用由结构，当窗格从其父mini框架窗口中移除。|  
|[CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md)|`CBasePane` 不使用此方法。|  
|`CBasePane::OnUpdateCmdUI`|内部使用。|  
|[CBasePane::PaneFromPoint](../Topic/CBasePane::PaneFromPoint.md)|返回包含给定的点窗格。|  
|`CBasePane::PreTranslateMessage`|用于使选件类 [CWinApp](../../mfc/reference/cwinapp-class.md) 转换窗口消息，并在调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows功能之前。  （重写 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。）|  
|[CBasePane::RecalcLayout](../Topic/CBasePane::RecalcLayout.md)|`CBasePane` 不使用此方法。|  
|[CBasePane::RemovePaneFromDockManager](../Topic/CBasePane::RemovePaneFromDockManager.md)|注销窗格和在停靠管理器的列表中移除。|  
|[CBasePane::SaveState](../Topic/CBasePane::SaveState.md)|保存窗格的状态对注册表。|  
|[CBasePane::SelectDefaultFont](../Topic/CBasePane::SelectDefaultFont.md)|为特定设备上下文选择默认字体。|  
|`CBasePane::Serialize`|读取或写入此对象从或对存档。  （重写 [CObject::Serialize](../Topic/CObject::Serialize.md)。）|  
|[CBasePane::SetControlBarStyle](../Topic/CBasePane::SetControlBarStyle.md)|设置控件条样式。|  
|[CBasePane::SetDockingMode](../Topic/CBasePane::SetDockingMode.md)|设置窗格的停靠模式。|  
|`CBasePane::SetMDITabbed`|内部使用。|  
|[CBasePane::SetPaneAlignment](../Topic/CBasePane::SetPaneAlignment.md)|设置窗格的对齐方式。|  
|`CBasePane::SetPaneRect`|内部使用。|  
|[CBasePane::SetPaneStyle](../Topic/CBasePane::SetPaneStyle.md)|设置窗格的样式。|  
|`CBasePane::SetRestoredFromRegistry`|内部使用。|  
|[CBasePane::SetWindowPos](../Topic/CBasePane::SetWindowPos.md)|更改窗格的大小、位置和Z顺序。|  
|[CBasePane::ShowPane](../Topic/CBasePane::ShowPane.md)|显示或隐藏窗格。|  
|[CBasePane::StretchPane](../Topic/CBasePane::StretchPane.md)|拉伸窗格水平或垂直。|  
|[CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md)|从其当前停靠的停靠站点、默认滑块或服务器框架窗口移除窗格。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CBasePane::DoPaint](../Topic/CBasePane::DoPaint.md)|填充窗格的背景。|  
  
## 备注  
 如果要创建支持扩展的停靠功能在MFC的窗格选件类，则它必须派生自 `CBasePane` 或从 [CPane Class](../../mfc/reference/cpane-class.md)。  
  
## 自定义提示  
 从其继承的下列自定义提示与 [CBasePane Class](../../mfc/reference/cbasepane-class.md) 和任何选件类:  
  
-   如果您创建一个窗格时，可以向文本应用新样式:  
  
    -   `AFX_CBRS_FLOAT` 使浮动窗格。  
  
    -   `AFX_CBRS_AUTOHIDE` 启动自动隐藏模式。  
  
    -   `AFX_CBRS_CLOSE` 使窗格中关闭\(隐藏）。  
  
     这些是您可以将与按位或运算的标志。  
  
     `CBasePane` 执行以下虚布尔值方法反映了这些标志: [CBasePane::CanBeClosed](../Topic/CBasePane::CanBeClosed.md)，[CBasePane::CanAutoHide](../Topic/CBasePane::CanAutoHide.md)，[CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md)。  您可以重写它们在派生类自定义其行为。  
  
-   可以通过重写的 [CBasePane::CanAcceptPane](../Topic/CBasePane::CanAcceptPane.md)自定义的停靠行为。  排列窗格返回从此方法的 `FALSE` 防止另一个窗格停靠到它。  
  
-   如果要创建不能浮点数，并防止其他窗格停靠在它之前的静态窗格\(类似于OutlookDemo示例中的Outlook栏\)，请将其创建为非浮动并重写 [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md) 返回 `FALSE`。  如果窗格创建的，而不用 `AFX_CBRS_FLOAT` 样式，默认实现返回 `FALSE`。  
  
-   \-1以外，用ID创建所有窗格。  
  
-   若要确定窗格可见性，请使用 [CBasePane::IsVisible](../Topic/CBasePane::IsVisible.md)。  正确它处理可见性状态在选项卡式和自动隐藏模式。  
  
-   如果要创建非浮动可调整大小的窗格中，将创建它，而无需 `AFX_CBRS_FLOAT` 样式并调用 [CFrameWnd::DockControlBar](../Topic/CFrameWnd::DockControlBar.md)。  
  
-   从停靠格式要排除窗格或从其停靠条移除工具栏，请调用 [CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md)。  不要调用此方法窗格上自动隐藏模式或位于选项卡式窗口"选项卡窗格的。  
  
-   如果要浮动或停靠在自动隐藏模式下的窗格，必须调用 [CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md) 和 `FALSE`，当第一个参数，在调用 [CBasePane::FloatPane](../Topic/CBasePane::FloatPane.md) 或 [CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md)之前。  
  
## 示例  
 下面的示例在 `CBasePane` 选件类演示如何使用各种方法。  示例演示如何从 `CFrameWndEx` 选件类检索窗格和如何设置停靠模式、窗格和窗格对齐样式。  代码是从 [Word填充示例](../../top/visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad#2](../../mfc/reference/codesnippet/CPP/cbasepane-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
## 要求  
 **标头:** afxbasepane.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane](../../mfc/reference/cbasepane-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)