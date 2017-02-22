---
title: "CMFCTasksPane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTasksPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTasksPane class"
ms.assetid: b456328e-2525-4642-b78b-9edd1a1a7d3f
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCTasksPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 `CMFCTasksPane` 类实现可点击项（任务）的列表。  
  
## 语法  
  
```  
class CMFCTasksPane : public CDockablePane  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCTasksPane::CMFCTasksPane](../Topic/CMFCTasksPane::CMFCTasksPane.md)|构造 `CMFCTasksPane` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCTasksPane::AddGroup](../Topic/CMFCTasksPane::AddGroup.md)|将新任务组添加到任务窗格控件。|  
|[CMFCTasksPane::AddLabel](../Topic/CMFCTasksPane::AddLabel.md)|将新的静态标签添加到指定任务组中。|  
|[CMFCTasksPane::AddMRUFilesList](../Topic/CMFCTasksPane::AddMRUFilesList.md)|将由最近使用的 \(MRU\) 文件列表指定的任务添加到一个组中。|  
|[CMFCTasksPane::AddPage](../Topic/CMFCTasksPane::AddPage.md)|将新页面添加到任务窗格。|  
|[CMFCTasksPane::AddSeparator](../Topic/CMFCTasksPane::AddSeparator.md)||  
|[CMFCTasksPane::AddTask](../Topic/CMFCTasksPane::AddTask.md)|将新任务添加到指定的任务组。|  
|[CMFCTasksPane::AddWindow](../Topic/CMFCTasksPane::AddWindow.md)|将子窗口添加到任务窗格。|  
|[CMFCTasksPane::CollapseAllGroups](../Topic/CMFCTasksPane::CollapseAllGroups.md)||  
|[CMFCTasksPane::CollapseGroup](../Topic/CMFCTasksPane::CollapseGroup.md)|以编程方式折叠组。|  
|[CMFCTasksPane::CreateDefaultMiniframe](../Topic/CMFCTasksPane::CreateDefaultMiniframe.md)|（重写 [CPane::CreateDefaultMiniframe](../Topic/CPane::CreateDefaultMiniframe.md)。）|  
|[CMFCTasksPane::CreateMenu](../Topic/CMFCTasksPane::CreateMenu.md)|由框架调用，以便为**“其他任务窗格”**菜单按钮创建菜单。|  
|[CMFCTasksPane::EnableAnimation](../Topic/CMFCTasksPane::EnableAnimation.md)|启用或禁用折叠或展开任务组时的动画。|  
|[CMFCTasksPane::EnableGroupCollapse](../Topic/CMFCTasksPane::EnableGroupCollapse.md)|指定是否可以折叠任务组。|  
|[CMFCTasksPane::EnableHistoryMenuButtons](../Topic/CMFCTasksPane::EnableHistoryMenuButtons.md)|启用或禁用**“下一步”**和**“上一步”**导航按钮中的下拉菜单。|  
|[CMFCTasksPane::EnableNavigationToolbar](../Topic/CMFCTasksPane::EnableNavigationToolbar.md)|启用或禁用导航工具栏。|  
|[CMFCTasksPane::EnableOffsetCustomControls](../Topic/CMFCTasksPane::EnableOffsetCustomControls.md)||  
|[CMFCTasksPane::EnableScrollButtons](../Topic/CMFCTasksPane::EnableScrollButtons.md)|启用滚动按钮，而不是滚动条。|  
|[CMFCTasksPane::EnableWrapLabels](../Topic/CMFCTasksPane::EnableWrapLabels.md)|启用或禁用标签的自动换行。|  
|[CMFCTasksPane::EnableWrapTasks](../Topic/CMFCTasksPane::EnableWrapTasks.md)|启用或禁用任务的自动换行。|  
|[CMFCTasksPane::GetActivePage](../Topic/CMFCTasksPane::GetActivePage.md)|返回活动页的从零开始的索引。|  
|[CMFCTasksPane::GetGroupCaptionHeight](../Topic/CMFCTasksPane::GetGroupCaptionHeight.md)|返回的组标题的高度。|  
|[CMFCTasksPane::GetGroupCaptionHorzOffset](../Topic/CMFCTasksPane::GetGroupCaptionHorzOffset.md)|返回组标题相对于任务窗格的左边缘和右边缘的当前偏移量。|  
|[CMFCTasksPane::GetGroupCaptionVertOffset](../Topic/CMFCTasksPane::GetGroupCaptionVertOffset.md)|返回组标题相对于任务窗格的上边缘和下边缘的当前偏移量。|  
|[CMFCTasksPane::GetGroupCount](../Topic/CMFCTasksPane::GetGroupCount.md)|返回组的总数。|  
|[CMFCTasksPane::GetGroupLocation](../Topic/CMFCTasksPane::GetGroupLocation.md)|返回给定组的内部组索引。|  
|[CMFCTasksPane::GetGroupVertOffset](../Topic/CMFCTasksPane::GetGroupVertOffset.md)|返回组的垂直偏移量。|  
|[CMFCTasksPane::GetHorzMargin](../Topic/CMFCTasksPane::GetHorzMargin.md)|返回任务窗格和工作区边缘之间的水平间距。|  
|[CMFCTasksPane::GetNextPages](../Topic/CMFCTasksPane::GetNextPages.md)||  
|[CMFCTasksPane::GetPageByGroup](../Topic/CMFCTasksPane::GetPageByGroup.md)|检索指定组的页索引。|  
|[CMFCTasksPane::GetPagesCount](../Topic/CMFCTasksPane::GetPagesCount.md)|返回页数。|  
|[CMFCTasksPane::GetPreviousPages](../Topic/CMFCTasksPane::GetPreviousPages.md)||  
|[CMFCTasksPane::GetScrollBarCtrl](../Topic/CMFCTasksPane::GetScrollBarCtrl.md)|（重写 [CWnd::GetScrollBarCtrl](../Topic/CWnd::GetScrollBarCtrl.md)。）|  
|[CMFCTasksPane::GetTask](../Topic/CMFCTasksPane::GetTask.md)|检索任务。|  
|[CMFCTasksPane::GetTaskCount](../Topic/CMFCTasksPane::GetTaskCount.md)|返回指定组中任务项的数量。|  
|[CMFCTasksPane::GetTaskGroup](../Topic/CMFCTasksPane::GetTaskGroup.md)|返回给定组索引的任务组。|  
|[CMFCTasksPane::GetTaskLocation](../Topic/CMFCTasksPane::GetTaskLocation.md)|返回给定任务的组和索引。|  
|[CMFCTasksPane::GetTasksHorzOffset](../Topic/CMFCTasksPane::GetTasksHorzOffset.md)|返回任务相对于其父组的左边缘和右边缘的水平偏移量。|  
|[CMFCTasksPane::GetTasksIconHorzOffset](../Topic/CMFCTasksPane::GetTasksIconHorzOffset.md)||  
|[CMFCTasksPane::GetTasksIconVertOffset](../Topic/CMFCTasksPane::GetTasksIconVertOffset.md)||  
|[CMFCTasksPane::GetVertMargin](../Topic/CMFCTasksPane::GetVertMargin.md)|返回任务窗格和工作区边缘之间的垂直间距。|  
|[CMFCTasksPane::IsAccessibilityCompatible](../Topic/CMFCTasksPane::IsAccessibilityCompatible.md)|（重写 `CDockablePane::IsAccessibilityCompatible`。）|  
|[CMFCTasksPane::IsAnimationEnabled](../Topic/CMFCTasksPane::IsAnimationEnabled.md)|指示动画是否已启用。|  
|[CMFCTasksPane::IsBackButtonEnabled](../Topic/CMFCTasksPane::IsBackButtonEnabled.md)|指示“返回”按钮是否已启用。|  
|[CMFCTasksPane::IsForwardButtonEnabled](../Topic/CMFCTasksPane::IsForwardButtonEnabled.md)|指示“前进”按钮是否已启用。|  
|[CMFCTasksPane::IsGroupCollapseEnabled](../Topic/CMFCTasksPane::IsGroupCollapseEnabled.md)||  
|[CMFCTasksPane::IsHistoryMenuButtonsEnabled](../Topic/CMFCTasksPane::IsHistoryMenuButtonsEnabled.md)|指示**“下一步”**和**“上一步”**导航按钮是否具有下拉菜单。|  
|[CMFCTasksPane::IsNavigationToolbarEnabled](../Topic/CMFCTasksPane::IsNavigationToolbarEnabled.md)|指示导航工具栏是否已启用。|  
|[CMFCTasksPane::IsToolBox](../Topic/CMFCTasksPane::IsToolBox.md)||  
|[CMFCTasksPane::IsWrapLabelsEnabled](../Topic/CMFCTasksPane::IsWrapLabelsEnabled.md)|指示任务窗格是否在标签中换行。|  
|[CMFCTasksPane::IsWrapTasksEnabled](../Topic/CMFCTasksPane::IsWrapTasksEnabled.md)|指示任务窗格是否在任务中换行。|  
|[CMFCTasksPane::LoadState](../Topic/CMFCTasksPane::LoadState.md)|（重写 [CDockablePane::LoadState](http://msdn.microsoft.com/zh-cn/96110136-4f46-4764-8a76-3b4abaf77917)。）|  
|[CMFCTasksPane::OnCancel](../Topic/CMFCTasksPane::OnCancel.md)||  
|[CMFCTasksPane::OnClickTask](../Topic/CMFCTasksPane::OnClickTask.md)|当用户单击任务窗格中的项时，由框架调用。|  
|[CMFCTasksPane::OnOK](../Topic/CMFCTasksPane::OnOK.md)||  
|[CMFCTasksPane::OnPressBackButton](../Topic/CMFCTasksPane::OnPressBackButton.md)|当用户单击“后退”按钮时，由框架调用。|  
|[CMFCTasksPane::OnPressForwardButton](../Topic/CMFCTasksPane::OnPressForwardButton.md)|当用户单击“前进”导航按钮时，由框架调用。|  
|[CMFCTasksPane::OnPressHomeButton](../Topic/CMFCTasksPane::OnPressHomeButton.md)|当用户单击“主页”导航按钮时，由框架调用|  
|[CMFCTasksPane::OnPressOtherButton](../Topic/CMFCTasksPane::OnPressOtherButton.md)||  
|[CMFCTasksPane::OnSetAccData](../Topic/CMFCTasksPane::OnSetAccData.md)|（重写 [CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md)。）|  
|[CMFCTasksPane::OnUpdateCmdUI](../Topic/CMFCTasksPane::OnUpdateCmdUI.md)|（重写 [CDockablePane::OnUpdateCmdUI](http://msdn.microsoft.com/zh-cn/5dd61606-1c12-40d4-b024-f3839aa5e2e0)。）|  
|[CMFCTasksPane::PreTranslateMessage](../Topic/CMFCTasksPane::PreTranslateMessage.md)|（重写 [CDockablePane::PreTranslateMessage](http://msdn.microsoft.com/zh-cn/49a242cc-b158-400e-9e01-0345ec9c3ffd)。）|  
|[CMFCTasksPane::RecalcLayout](../Topic/CMFCTasksPane::RecalcLayout.md)|（重写 [CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md)。）|  
|[CMFCTasksPane::RemoveAllGroups](../Topic/CMFCTasksPane::RemoveAllGroups.md)|删除指定页上的所有组。|  
|[CMFCTasksPane::RemoveAllPages](../Topic/CMFCTasksPane::RemoveAllPages.md)|从任务窗格中删除所有页，除默认（第一）页除外。|  
|[CMFCTasksPane::RemoveAllTasks](../Topic/CMFCTasksPane::RemoveAllTasks.md)|从组中删除所有任务。|  
|[CMFCTasksPane::RemoveGroup](../Topic/CMFCTasksPane::RemoveGroup.md)|删除组。|  
|[CMFCTasksPane::RemovePage](../Topic/CMFCTasksPane::RemovePage.md)|从任务窗格删除指定页。|  
|[CMFCTasksPane::RemoveTask](../Topic/CMFCTasksPane::RemoveTask.md)|从任务组删除任务。|  
|[CMFCTasksPane::SaveState](../Topic/CMFCTasksPane::SaveState.md)|（重写 [CDockablePane::SaveState](http://msdn.microsoft.com/zh-cn/c5c24249-8d0d-46cb-96d9-9f5c6dc191db)。）|  
|[CMFCTasksPane::Serialize](../Topic/CMFCTasksPane::Serialize.md)|（重写 [CDockablePane::Serialize](http://msdn.microsoft.com/zh-cn/09787e59-e446-4e76-894b-206d303dcfd6)。）|  
|[CMFCTasksPane::SetActivePage](../Topic/CMFCTasksPane::SetActivePage.md)|在任务窗格中激活指定页。|  
|[CMFCTasksPane::SetCaption](../Topic/CMFCTasksPane::SetCaption.md)|设置任务窗格的标题名称。|  
|[CMFCTasksPane::SetGroupCaptionHeight](../Topic/CMFCTasksPane::SetGroupCaptionHeight.md)|设置组标题的高度。|  
|[CMFCTasksPane::SetGroupCaptionHorzOffset](../Topic/CMFCTasksPane::SetGroupCaptionHorzOffset.md)|设置组标题的水平偏移量。|  
|[CMFCTasksPane::SetGroupCaptionVertOffset](../Topic/CMFCTasksPane::SetGroupCaptionVertOffset.md)|设置组标题的垂直偏移量。|  
|[CMFCTasksPane::SetGroupName](../Topic/CMFCTasksPane::SetGroupName.md)|设置组名称。|  
|[CMFCTasksPane::SetGroupTextColor](../Topic/CMFCTasksPane::SetGroupTextColor.md)|设置组标题的文本颜色。|  
|[CMFCTasksPane::SetGroupVertOffset](../Topic/CMFCTasksPane::SetGroupVertOffset.md)|设置组的垂直偏移量。|  
|[CMFCTasksPane::SetHorzMargin](../Topic/CMFCTasksPane::SetHorzMargin.md)|设置任务窗格和工作区边缘之间的水平间距。|  
|[CMFCTasksPane::SetIconsList](../Topic/CMFCTasksPane::SetIconsList.md)|设置与任务关联的图像列表。|  
|[CMFCTasksPane::SetPageCaption](../Topic/CMFCTasksPane::SetPageCaption.md)|设置任务窗格页的标题文本。|  
|[CMFCTasksPane::SetTaskName](../Topic/CMFCTasksPane::SetTaskName.md)|设置任务的名称。|  
|[CMFCTasksPane::SetTasksIconHorzOffset](../Topic/CMFCTasksPane::SetTasksIconHorzOffset.md)||  
|[CMFCTasksPane::SetTasksIconVertOffset](../Topic/CMFCTasksPane::SetTasksIconVertOffset.md)||  
|[CMFCTasksPane::SetTaskTextColor](../Topic/CMFCTasksPane::SetTaskTextColor.md)|设置任务的文本颜色。|  
|[CMFCTasksPane::SetTasksHorzOffset](../Topic/CMFCTasksPane::SetTasksHorzOffset.md)|设置任务相对于其父组的左边缘和右边缘的水平偏移量。|  
|[CMFCTasksPane::SetVertMargin](../Topic/CMFCTasksPane::SetVertMargin.md)|设置任务窗格和工作区边缘之间的垂直间距。|  
|[CMFCTasksPane::SetWindowHeight](../Topic/CMFCTasksPane::SetWindowHeight.md)|设置窗口的高度。|  
|[CMFCTasksPane::ShowCommandMessageString](../Topic/CMFCTasksPane::ShowCommandMessageString.md)||  
|[CMFCTasksPane::ShowTask](../Topic/CMFCTasksPane::ShowTask.md)|显示或隐藏任务。|  
|[CMFCTasksPane::ShowTaskByCmdId](../Topic/CMFCTasksPane::ShowTaskByCmdId.md)|基于任务的命令 ID 显示或隐藏任务。|  
|[CMFCTasksPane::Update](../Topic/CMFCTasksPane::Update.md)|更新属于任务窗格的 GUI 元素。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCTasksPane::OnActivateTasksPanePage](../Topic/CMFCTasksPane::OnActivateTasksPanePage.md)|激活新的任务窗格页时，由框架调用。|  
  
## 备注  
 `CMFCTasksPane` 类实现下列功能：  
  
-   可以对项进行分组，并且每个项分组均可具有关联的标题。  
  
-   可以折叠或展开项分组。  
  
-   可以向任务窗格中的每个项分配一个图标。  
  
-   可将单个项与在用户单击该项时执行的任务 ID 关联。  单击时，`WM_COMMAND` 消息会发送给任务窗格控件的所有者。  
  
 若要在应用程序中使用 `CMFCTasksPane` 控件，请执行以下步骤：  
  
1.  将 `CMFCTasksPane` 对象嵌入主框架窗口类。  
  
2.  处理 `WM_CREATE` 消息时，请调用 `Create` 方法。  可以使用常规 [CControlBar](../../mfc/reference/ccontrolbar-class.md) 样式。  有关详细信息，请参阅`CControlBar::Create`。  
  
3.  调用 [CMFCTasksPane::AddGroup](../Topic/CMFCTasksPane::AddGroup.md) 方法以添加不同的组。  
  
4.  调用 [CMFCTasksPane::AddTask](../Topic/CMFCTasksPane::AddTask.md)、[CMFCTasksPane::AddLabel](../Topic/CMFCTasksPane::AddLabel.md) 或 [CMFCTasksPane::AddMRUFilesList](../Topic/CMFCTasksPane::AddMRUFilesList.md) 成员函数，以便将新的项（任务）添加到每个组。  
  
5.  调用 [CMFCTasksPane::EnableGroupCollapse](../Topic/CMFCTasksPane::EnableGroupCollapse.md) 以指定是否可以折叠项组。  
  
 下图显示了一个典型的任务窗格控件。  第一组是*特殊*组，其标题是较深的颜色。  第三组处于折叠状态。  最后一组与任务窗格的底部对齐且没有标题，而且组中的最后一个任务是一个简单的标签：  
  
 ![任务窗格示例](../../mfc/reference/media/nexttaskpane.png "NextTaskPane")  
  
 可以通过调整各种边距和偏移量来自定义任务窗格的外观。  下图阐明这些变量的含义：  
  
 ![自定义任务组](../../mfc/reference/media/nexttaskgrpcustom.png "NextTaskGrpCustom")  
  
## 示例  
 下面的示例演示如何构造 `CMFCTasksPane` 对象和在 `CMFCTasksPane` 类中使用各种方法。  该示例显示如何启用任务组的折叠、在**“下一步”**和**“上一步”**导航按钮上启用下拉菜单、启用滚动按钮代替滚动条、为标签中的文本启用自动换行、设置任务窗格的标题名称、设置组标题的文本颜色以及设置水平和垂直边距。  
  
 [!code-cpp[NVC_MFC_RibbonApp#28](../../mfc/reference/codesnippet/CPP/cmfctaskspane-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)  
  
## 要求  
 **标头：**afxTasksPane.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCTasksPaneTaskGroup Class](../../mfc/reference/cmfctaskspanetaskgroup-class.md)   
 [CMFCTasksPaneTask Class](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)