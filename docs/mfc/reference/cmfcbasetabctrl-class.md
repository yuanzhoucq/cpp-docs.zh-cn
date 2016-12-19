---
title: "CMFCBaseTabCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCBaseTabCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCBaseTabCtrl class"
ms.assetid: 7270c55f-6f6e-4dd2-b0d2-291afeac3882
caps.latest.revision: 41
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCBaseTabCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现选项卡式窗口的基本功能。  
  
## 语法  
  
```  
class CMFCBaseTabCtrl : public CWnd  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCBaseTabCtrl::AddIcon](../Topic/CMFCBaseTabCtrl::AddIcon.md)||  
|[CMFCBaseTabCtrl::AddTab](../Topic/CMFCBaseTabCtrl::AddTab.md)|向选项卡式窗口添加新选项卡。|  
|[CMFCBaseTabCtrl::ApplyRestoredTabInfo](../Topic/CMFCBaseTabCtrl::ApplyRestoredTabInfo.md)||  
|[CMFCBaseTabCtrl::AutoDestroyWindow](../Topic/CMFCBaseTabCtrl::AutoDestroyWindow.md)||  
|[CMFCBaseTabCtrl::CalcRectEdit](../Topic/CMFCBaseTabCtrl::CalcRectEdit.md)||  
|[CMFCBaseTabCtrl::CleanUp](../Topic/CMFCBaseTabCtrl::CleanUp.md)||  
|[CMFCBaseTabCtrl::ClearImageList](../Topic/CMFCBaseTabCtrl::ClearImageList.md)||  
|[CMFCBaseTabCtrl::DetachTab](../Topic/CMFCBaseTabCtrl::DetachTab.md)|从选项卡式窗口分离选项卡。|  
|[CMFCBaseTabCtrl::EnableActivateLastActive](../Topic/CMFCBaseTabCtrl::EnableActivateLastActive.md)||  
|[CMFCBaseTabCtrl::EnableAutoColor](../Topic/CMFCBaseTabCtrl::EnableAutoColor.md)|启用或禁用自动选项卡着色。|  
|[CMFCBaseTabCtrl::EnableCustomToolTips](../Topic/CMFCBaseTabCtrl::EnableCustomToolTips.md)|启用或禁用选项卡的自定义工具提示。|  
|[CMFCBaseTabCtrl::EnableInPlaceEdit](../Topic/CMFCBaseTabCtrl::EnableInPlaceEdit.md)|启用或禁用直接编辑选项卡标签。|  
|[CMFCBaseTabCtrl::EnableTabDetach](../Topic/CMFCBaseTabCtrl::EnableTabDetach.md)|启用可拆分选项卡。|  
|[CMFCBaseTabCtrl::EnableTabSwap](../Topic/CMFCBaseTabCtrl::EnableTabSwap.md)|启用或禁用用户是否可以使用鼠标更改选项卡顺序。|  
|[CMFCBaseTabCtrl::EnsureVisible](../Topic/CMFCBaseTabCtrl::EnsureVisible.md)|滚动选项卡，直到指定选项卡可见。 如果指定选项卡已经可见，则此方法无效。|  
|[CMFCBaseTabCtrl::EnterDragMode](../Topic/CMFCBaseTabCtrl::EnterDragMode.md)||  
|[CMFCBaseTabCtrl::FindTargetWnd](../Topic/CMFCBaseTabCtrl::FindTargetWnd.md)|返回包含指定点的窗格。|  
|[CMFCBaseTabCtrl::FireChangeActiveTab](../Topic/CMFCBaseTabCtrl::FireChangeActiveTab.md)||  
|[CMFCBaseTabCtrl::FireChangingActiveTab](../Topic/CMFCBaseTabCtrl::FireChangingActiveTab.md)||  
|[CMFCBaseTabCtrl::GetActiveTab](../Topic/CMFCBaseTabCtrl::GetActiveTab.md)|返回活动选项卡的索引。|  
|[CMFCBaseTabCtrl::GetActiveTabColor](../Topic/CMFCBaseTabCtrl::GetActiveTabColor.md)|返回活动选项卡的背景色。|  
|[CMFCBaseTabCtrl::GetActiveTabTextColor](../Topic/CMFCBaseTabCtrl::GetActiveTabTextColor.md)|返回活动选项卡的文本颜色。|  
|[CMFCBaseTabCtrl::GetActiveWnd](../Topic/CMFCBaseTabCtrl::GetActiveWnd.md)|返回指向选项卡控件的活动页面的指针。|  
|[CMFCBaseTabCtrl::GetAutoColors](../Topic/CMFCBaseTabCtrl::GetAutoColors.md)|返回对用于自动着色的颜色数组的引用。|  
|[CMFCBaseTabCtrl::GetFirstVisibleTab](../Topic/CMFCBaseTabCtrl::GetFirstVisibleTab.md)|返回指向第一个可见选项卡的指针。|  
|[CMFCBaseTabCtrl::GetFirstVisibleTabNum](../Topic/CMFCBaseTabCtrl::GetFirstVisibleTabNum.md)||  
|[CMFCBaseTabCtrl::GetHighlightedTab](../Topic/CMFCBaseTabCtrl::GetHighlightedTab.md)|返回当前突出显示的选项卡的索引。|  
|[CMFCBaseTabCtrl::GetImageList](../Topic/CMFCBaseTabCtrl::GetImageList.md)||  
|[CMFCBaseTabCtrl::GetImageSize](../Topic/CMFCBaseTabCtrl::GetImageSize.md)||  
|[CMFCBaseTabCtrl::GetLastVisibleTab](../Topic/CMFCBaseTabCtrl::GetLastVisibleTab.md)||  
|[CMFCBaseTabCtrl::GetLocation](../Topic/CMFCBaseTabCtrl::GetLocation.md)|返回指示相对于选项卡控件定位的选项卡区域的 LOCATION 数据类型的变量。 例如位于顶部或底部。|  
|[CMFCBaseTabCtrl::GetMaxWindowSize](../Topic/CMFCBaseTabCtrl::GetMaxWindowSize.md)||  
|[CMFCBaseTabCtrl::GetTabArea](../Topic/CMFCBaseTabCtrl::GetTabArea.md)|返回选项卡区域在选项卡式窗口中的大小和位置。 使用坐标定义选项卡区域的位置。|  
|[CMFCBaseTabCtrl::GetTabBkColor](../Topic/CMFCBaseTabCtrl::GetTabBkColor.md)|返回指定选项卡的背景色。|  
|[CMFCBaseTabCtrl::GetTabBorderSize](../Topic/CMFCBaseTabCtrl::GetTabBorderSize.md)|返回选项卡控件中选项卡边框的大小。|  
|[CMFCBaseTabCtrl::GetTabByID](../Topic/CMFCBaseTabCtrl::GetTabByID.md)|返回由指定 ID 标识的选项卡的索引。|  
|[CMFCBaseTabCtrl::GetTabCloseButton](../Topic/CMFCBaseTabCtrl::GetTabCloseButton.md)||  
|[CMFCBaseTabCtrl::GetTabFromHwnd](../Topic/CMFCBaseTabCtrl::GetTabFromHwnd.md)|返回包含指定 HWND 对象的选项卡的索引。|  
|[CMFCBaseTabCtrl::GetTabFromPoint](../Topic/CMFCBaseTabCtrl::GetTabFromPoint.md)|返回包含指定点的选项卡。|  
|[CMFCBaseTabCtrl::GetTabFullWidth](../Topic/CMFCBaseTabCtrl::GetTabFullWidth.md)||  
|[CMFCBaseTabCtrl::GetTabHicon](../Topic/CMFCBaseTabCtrl::GetTabHicon.md)|返回与指定选项卡关联的图标。|  
|[CMFCBaseTabCtrl::GetTabID](../Topic/CMFCBaseTabCtrl::GetTabID.md)|使用选项卡索引返回选项卡 ID。|  
|[CMFCBaseTabCtrl::GetTabIcon](../Topic/CMFCBaseTabCtrl::GetTabIcon.md)|返回指定选项卡的图标 ID。|  
|[CMFCBaseTabCtrl::GetTabLabel](../Topic/CMFCBaseTabCtrl::GetTabLabel.md)|返回指定选项卡的文本。|  
|[CMFCBaseTabCtrl::GetTabRect](../Topic/CMFCBaseTabCtrl::GetTabRect.md)|检索指定选项卡的大小和位置。|  
|[CMFCBaseTabCtrl::GetTabsHeight](../Topic/CMFCBaseTabCtrl::GetTabsHeight.md)||  
|[CMFCBaseTabCtrl::GetTabsRect](../Topic/CMFCBaseTabCtrl::GetTabsRect.md)||  
|[CMFCBaseTabCtrl::GetTabTextColor](../Topic/CMFCBaseTabCtrl::GetTabTextColor.md)|返回指定选项卡的文本颜色。|  
|[CMFCBaseTabCtrl::GetTabWnd](../Topic/CMFCBaseTabCtrl::GetTabWnd.md)|返回指向驻留在指定选项卡页上的窗格的指针。|  
|[CMFCBaseTabCtrl::GetTabWndNoWrapper](../Topic/CMFCBaseTabCtrl::GetTabWndNoWrapper.md)|返回指向驻留在指定选项卡页上的控件的直接指针，即使该控件具有包装。|  
|[CMFCBaseTabCtrl::GetTabsNum](../Topic/CMFCBaseTabCtrl::GetTabsNum.md)|返回选项卡控件中包含的选项卡的数目。|  
|[CMFCBaseTabCtrl::GetToolTipCtrl](../Topic/CMFCBaseTabCtrl::GetToolTipCtrl.md)|返回对与 `CMFCBaseTabCtrl` 对象关联的工具提示控件的引用。|  
|[CMFCBaseTabCtrl::GetVisibleTabsNum](../Topic/CMFCBaseTabCtrl::GetVisibleTabsNum.md)|返回可见选项卡的数目。|  
|[CMFCBaseTabCtrl::HasImage](../Topic/CMFCBaseTabCtrl::HasImage.md)||  
|[CMFCBaseTabCtrl::HideSingleTab](../Topic/CMFCBaseTabCtrl::HideSingleTab.md)|设置隐藏窗口选项卡的选项，但仅当选项卡式窗口只显示一个可见选项卡时设置。|  
|[CMFCBaseTabCtrl::InsertTab](../Topic/CMFCBaseTabCtrl::InsertTab.md)|插入新选项卡。|  
|[CMFCBaseTabCtrl::InvalidateTab](../Topic/CMFCBaseTabCtrl::InvalidateTab.md)||  
|[CMFCBaseTabCtrl::IsActiveTabCloseButton](../Topic/CMFCBaseTabCtrl::IsActiveTabCloseButton.md)||  
|[CMFCBaseTabCtrl::IsAutoColor](../Topic/CMFCBaseTabCtrl::IsAutoColor.md)|返回一个值，用于指示选项卡式窗口是否处于自动配色模式。|  
|[CMFCBaseTabCtrl::IsAutoDestroyWindow](../Topic/CMFCBaseTabCtrl::IsAutoDestroyWindow.md)||  
|[CMFCBaseTabCtrl::IsColored](../Topic/CMFCBaseTabCtrl::IsColored.md)||  
|[CMFCBaseTabCtrl::IsDialogControl](../Topic/CMFCBaseTabCtrl::IsDialogControl.md)||  
|[CMFCBaseTabCtrl::IsDrawNoPrefix](../Topic/CMFCBaseTabCtrl::IsDrawNoPrefix.md)||  
|[CMFCBaseTabCtrl::IsFlatFrame](../Topic/CMFCBaseTabCtrl::IsFlatFrame.md)|返回一个值，用于指示选项卡区域的框架是平面的还是 3D 的。|  
|[CMFCBaseTabCtrl::IsFlatTab](../Topic/CMFCBaseTabCtrl::IsFlatTab.md)||  
|[CMFCBaseTabCtrl::IsHideSingleTab](../Topic/CMFCBaseTabCtrl::IsHideSingleTab.md)|返回一个值，用于指示选项卡控件是否配置为隐藏选项卡，但仅当选项卡式窗口只具有一个可见选项卡时设置。|  
|[CMFCBaseTabCtrl::IsIconAdded](../Topic/CMFCBaseTabCtrl::IsIconAdded.md)||  
|[CMFCBaseTabCtrl::IsInPlaceEdit](../Topic/CMFCBaseTabCtrl::IsInPlaceEdit.md)|指示用户是否可以修改选项卡上的标签。|  
|[CMFCBaseTabCtrl::IsLeftRightRounded](../Topic/CMFCBaseTabCtrl::IsLeftRightRounded.md)||  
|[CMFCBaseTabCtrl::IsMDITab](../Topic/CMFCBaseTabCtrl::IsMDITab.md)||  
|[CMFCBaseTabCtrl::IsOneNoteStyle](../Topic/CMFCBaseTabCtrl::IsOneNoteStyle.md)|指示选项卡式窗口是否以 Microsoft OneNote 样式显示选项卡。|  
|[CMFCBaseTabCtrl::IsPtInTabArea](../Topic/CMFCBaseTabCtrl::IsPtInTabArea.md)|检查选项卡区域中是否存在指定的点。|  
|[CMFCBaseTabCtrl::IsTabCloseButtonHighlighted](../Topic/CMFCBaseTabCtrl::IsTabCloseButtonHighlighted.md)||  
|[CMFCBaseTabCtrl::IsTabCloseButtonPressed](../Topic/CMFCBaseTabCtrl::IsTabCloseButtonPressed.md)||  
|[CMFCBaseTabCtrl::IsTabDetachable](../Topic/CMFCBaseTabCtrl::IsTabDetachable.md)|指示选项卡是否可拆分。|  
|[CMFCBaseTabCtrl::IsTabIconOnly](../Topic/CMFCBaseTabCtrl::IsTabIconOnly.md)|指示选项卡是否显示图标而不显示标签。|  
|[CMFCBaseTabCtrl::IsTabSwapEnabled](../Topic/CMFCBaseTabCtrl::IsTabSwapEnabled.md)|指示用户是否可以通过拖动选项卡来更改选项卡位置。|  
|[CMFCBaseTabCtrl::IsTabVisible](../Topic/CMFCBaseTabCtrl::IsTabVisible.md)|指示指定选项卡是否可见。|  
|[CMFCBaseTabCtrl::IsVS2005Style](../Topic/CMFCBaseTabCtrl::IsVS2005Style.md)||  
|[CMFCBaseTabCtrl::MoveTab](../Topic/CMFCBaseTabCtrl::MoveTab.md)||  
|[CMFCBaseTabCtrl::OnChangeTabs](../Topic/CMFCBaseTabCtrl::OnChangeTabs.md)|选项卡数量更改时由框架调用。|  
|[CMFCBaseTabCtrl::OnDragEnter](../Topic/CMFCBaseTabCtrl::OnDragEnter.md)||  
|[CMFCBaseTabCtrl::OnDragLeave](../Topic/CMFCBaseTabCtrl::OnDragLeave.md)||  
|[CMFCBaseTabCtrl::OnDragOver](../Topic/CMFCBaseTabCtrl::OnDragOver.md)||  
|[CMFCBaseTabCtrl::OnDrop](../Topic/CMFCBaseTabCtrl::OnDrop.md)||  
|[CMFCBaseTabCtrl::OnRenameTab](../Topic/CMFCBaseTabCtrl::OnRenameTab.md)||  
|[CMFCBaseTabCtrl::PreTranslateMessage](../Topic/CMFCBaseTabCtrl::PreTranslateMessage.md)|在将窗口消息发送到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数之前，由 [CWinApp](../../mfc/reference/cwinapp-class.md) 类用于对此消息进行转换。 （重写 [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)。）|  
|[CMFCBaseTabCtrl::RecalcLayout](../Topic/CMFCBaseTabCtrl::RecalcLayout.md)|重新计算选项卡式窗口的内部布局。|  
|[CMFCBaseTabCtrl::RemoveAllTabs](../Topic/CMFCBaseTabCtrl::RemoveAllTabs.md)|从选项卡式窗口中移除所有选项卡。|  
|[CMFCBaseTabCtrl::RemoveTab](../Topic/CMFCBaseTabCtrl::RemoveTab.md)|从选项卡式窗口中移除一个选项卡。|  
|[CMFCBaseTabCtrl::RenameTab](../Topic/CMFCBaseTabCtrl::RenameTab.md)||  
|[CMFCBaseTabCtrl::ResetImageList](../Topic/CMFCBaseTabCtrl::ResetImageList.md)|重置附加到选项卡式窗口的图像列表。|  
|[CMFCBaseTabCtrl::Serialize](../Topic/CMFCBaseTabCtrl::Serialize.md)|从存档读取该对象或将该对象写入存档。 （重写 [CObject::Serialize](../Topic/CObject::Serialize.md)。）|  
|[CMFCBaseTabCtrl::SetActiveTab](../Topic/CMFCBaseTabCtrl::SetActiveTab.md)|激活选项卡。|  
|[CMFCBaseTabCtrl::SetActiveTabColor](../Topic/CMFCBaseTabCtrl::SetActiveTabColor.md)|设置当前活动选项卡的背景色。|  
|[CMFCBaseTabCtrl::SetActiveTabTextColor](../Topic/CMFCBaseTabCtrl::SetActiveTabTextColor.md)|设置活动选项卡的文本颜色。|  
|[CMFCBaseTabCtrl::SetAutoColors](../Topic/CMFCBaseTabCtrl::SetAutoColors.md)|设置应用到自动配色模式中的选项卡控件颜色。|  
|[CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../Topic/CMFCBaseTabCtrl::SetDockingBarWrapperRTC.md)|设置用于非派生自 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 的任意对象的包装类。|  
|[CMFCBaseTabCtrl::SetDrawNoPrefix](../Topic/CMFCBaseTabCtrl::SetDrawNoPrefix.md)|启用和禁用绘制选项卡标签时前缀字符的处理。|  
|[CMFCBaseTabCtrl::SetImageList](../Topic/CMFCBaseTabCtrl::SetImageList.md)|设置图标图像列表。|  
|[CMFCBaseTabCtrl::SetLocation](../Topic/CMFCBaseTabCtrl::SetLocation.md)||  
|[CMFCBaseTabCtrl::SetTabBkColor](../Topic/CMFCBaseTabCtrl::SetTabBkColor.md)|设置指定选项卡的背景色。|  
|[CMFCBaseTabCtrl::SetTabBorderSize](../Topic/CMFCBaseTabCtrl::SetTabBorderSize.md)|设置新的选项卡边框大小。|  
|[CMFCBaseTabCtrl::SetTabHicon](../Topic/CMFCBaseTabCtrl::SetTabHicon.md)|设置选项卡图标。|  
|[CMFCBaseTabCtrl::SetTabIcon](../Topic/CMFCBaseTabCtrl::SetTabIcon.md)|设置选项卡图标 ID。|  
|[CMFCBaseTabCtrl::SetTabIconOnly](../Topic/CMFCBaseTabCtrl::SetTabIconOnly.md)|为指定选项卡启用和禁用“仅图标”模式。|  
|[CMFCBaseTabCtrl::SetTabLabel](../Topic/CMFCBaseTabCtrl::SetTabLabel.md)|将选项卡标签设置为等于指定的字符串值。|  
|[CMFCBaseTabCtrl::SetTabsHeight](../Topic/CMFCBaseTabCtrl::SetTabsHeight.md)||  
|[CMFCBaseTabCtrl::SetTabTextColor](../Topic/CMFCBaseTabCtrl::SetTabTextColor.md)|为指定选项卡设置文本颜色。|  
|[CMFCBaseTabCtrl::SetTabsOrder](../Topic/CMFCBaseTabCtrl::SetTabsOrder.md)|按照指定的顺序排列选项卡。|  
|[CMFCBaseTabCtrl::ShowTab](../Topic/CMFCBaseTabCtrl::ShowTab.md)|显示或隐藏指定的选项卡。|  
|[CMFCBaseTabCtrl::StartRenameTab](../Topic/CMFCBaseTabCtrl::StartRenameTab.md)||  
|[CMFCBaseTabCtrl::SwapTabs](../Topic/CMFCBaseTabCtrl::SwapTabs.md)||  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCBaseTabCtrl::CreateWrapper](../Topic/CMFCBaseTabCtrl::CreateWrapper.md)|为派生自 [CWnd](../../mfc/reference/cwnd-class.md)（后者不派生自 `CDockablePane`）的对象创建包装。 若要停靠 `CMFCBaseTabCtrl` 对象，则每个嵌入的控件必须具有停靠包装或派生自 `CDockablePane`。<br /><br /> 通过使用 `SetDockingBayWrapperRTC` 设置包装的类。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCBaseTabCtrl::m\_bActivateTabOnRightClick](../Topic/CMFCBaseTabCtrl::m_bActivateTabOnRightClick.md)|指定是通过单击鼠标左键还是单击鼠标右键来选择选项卡。|  
|[CMFCBaseTabCtrl::m\_bAutoDestroyWindow](../Topic/CMFCBaseTabCtrl::m_bAutoDestroyWindow.md)|指定是否自动销毁选项卡中包含的窗格。|  
  
## 备注  
 `CMFCBaseTabCtrl` 类是抽象类。 因此，不能将它实例化。 若要创建选项卡式窗口，则必须从 `CMFCBaseTabCtrl` 派生类。 MFC 库包含一些派生的类示例，其中两个是 [CMFCTabCtrl Class](../../mfc/reference/cmfctabctrl-class.md) 和 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)。  
  
 从 [!INCLUDE[vs_dev14](../../ide/includes/vs_dev14_md.md)] 开始，此类支持 Microsoft Active Accessibility。  
  
## 自定义提示  
 以下提示适用于 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md) 和从其继承的任何类：  
  
-   如果启用可拆分选项卡，请勿保留指向选项卡式窗口的指针。 这些可拆分选项卡可以动态创建和销毁。 因此，指针可能会变为无效。  
  
-   可以配置选项卡控件，使用户可以通过使用鼠标动态移动选项卡控件上的选项卡。 此功能已内置于 `CMFCBaseTabCtrl` 类。 调用 [CMFCBaseTabCtrl::EnableTabSwap](../Topic/CMFCBaseTabCtrl::EnableTabSwap.md) 可启用它。  
  
-   默认情况下，将选项卡添加到选项卡控件时，选项卡是可拆分的。 还可以使用 [CMFCBaseTabCtrl::AddTab](../Topic/CMFCBaseTabCtrl::AddTab.md) 来添加非可拆分的选项卡。 如果将 `bDetachable` 参数设置为 `FALSE`，则选项卡将不可拆分。 还可调用 [CMFCBaseTabCtrl::EnableTabDetach](../Topic/CMFCBaseTabCtrl::EnableTabDetach.md) 方法来更改选项卡是否可拆分。  
  
-   从 [CWnd 类](../../mfc/reference/cwnd-class.md)派生的对象可置于可停靠控件条或可停靠选项卡上。 要停靠整个控件，则必须使 `CWnd` 对象可停靠。 MFC 使用一个包装类实现此目的。 此包装类是 [CDockablePaneAdapter Class](../../mfc/reference/cdockablepaneadapter-class.md)。 添加到可停靠控件条或可停靠选项卡上的任何 `CWnd` 对象将被包装到 `CDockablePaneAdapter` 对象中。 可以通过将 `CMFCBaseTablCtrl` 对象的 `m_bEnableWrapping` 参数设置为 `FALSE` 来禁用自动包装。 还可以使用 [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../Topic/CMFCBaseTabCtrl::SetDockingBarWrapperRTC.md) 方法来更改应用程序将用作包装器的类。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
## 要求  
 **标头：**afxbasetabctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl Class](../../mfc/reference/cmfctabctrl-class.md)   
 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)