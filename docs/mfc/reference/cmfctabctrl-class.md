---
title: "CMFCTabCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTabCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTabCtrl class"
  - "CMFCTabCtrl constructor"
  - "CMFCTabCtrl::GetTabFromPoint method"
  - "CMFCTabCtrl::IsPtInTabArea method"
  - "CMFCTabCtrl::MoveTab method"
  - "CMFCTabCtrl::PreTranslateMessage method"
  - "CMFCTabCtrl::RecalcLayout method"
  - "CMFCTabCtrl::SwapTabs method"
ms.assetid: d441385d-2c72-4203-96fa-deae2273da35
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCTabCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCTabCtrl` 选件类为选项卡控件的功能。  选项卡控件显示有平面或三维选项的可停靠窗口在其顶部或底部。  选项卡显示文本和图像，并能更改颜色，当激活。  
  
## 语法  
  
```  
class CMFCTabCtrl : public CMFCBaseTabCtrl  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCTabCtrl::CMFCTabCtrl`|默认构造函数。|  
|`CMFCTabCtrl::~CMFCTabCtrl`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCTabCtrl::ActivateMDITab](../Topic/CMFCTabCtrl::ActivateMDITab.md)|显示当前选项卡控件上指定的选项并在该选项的焦点。|  
|[CMFCTabCtrl::AllowDestroyEmptyTabbedPane](../Topic/CMFCTabCtrl::AllowDestroyEmptyTabbedPane.md)||  
|[CMFCTabCtrl::AutoSizeWindow](../Topic/CMFCTabCtrl::AutoSizeWindow.md)|指定框架是否调整所有选项卡控件窗口的工作区，在选项卡控件中的用户界面元素。|  
|[CMFCTabCtrl::CalcRectEdit](../Topic/CMFCTabCtrl::CalcRectEdit.md)|deflate指定的选项区域的大小。  （重写 `CMFCBaseTabCtrl::CalcRectEdit`。）|  
|[CMFCTabCtrl::Create](../Topic/CMFCTabCtrl::Create.md)|创建选项卡控件并将它附加到 `CMFCTabCtrl` 对象。|  
|`CMFCTabCtrl::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CMFCTabCtrl::EnableActiveTabCloseButton](../Topic/CMFCTabCtrl::EnableActiveTabCloseButton.md)|显示或隐藏"关闭"按钮\(**x**\)在活动选项卡。|  
|[CMFCTabCtrl::EnableInPlaceEdit](../Topic/CMFCTabCtrl::EnableInPlaceEdit.md)|启用或禁用可编辑的选项卡标签。  （重写 [CMFCBaseTabCtrl::EnableInPlaceEdit](../Topic/CMFCBaseTabCtrl::EnableInPlaceEdit.md)。）|  
|[CMFCTabCtrl::EnableTabDocumentsMenu](../Topic/CMFCTabCtrl::EnableTabDocumentsMenu.md)|替换将与按钮的窗口"选项卡打开选项卡式窗口菜单的两个按钮。|  
|[CMFCTabCtrl::EnsureVisible](../Topic/CMFCTabCtrl::EnsureVisible.md)|确保选项可见。|  
|[CMFCTabCtrl::GetDocumentIcon](../Topic/CMFCTabCtrl::GetDocumentIcon.md)|检索与在选项卡式窗口的弹出菜单的选项卡符号。|  
|[CMFCTabCtrl::GetFirstVisibleTabNum](../Topic/CMFCTabCtrl::GetFirstVisibleTabNum.md)|检索会显示在当前选项卡控件第一个选项的索引。|  
|[CMFCTabCtrl::GetResizeMode](../Topic/CMFCTabCtrl::GetResizeMode.md)|检索指定的值当前选项卡控件如何调整大小。|  
|[CMFCTabCtrl::GetScrollBar](../Topic/CMFCTabCtrl::GetScrollBar.md)|检索指向与选项卡控件的滚动条对象。|  
|[CMFCTabCtrl::GetTabArea](../Topic/CMFCTabCtrl::GetTabArea.md)|检索选项卡标签区域的边框在选项卡控件的顶部或底部。  （重写 [CMFCBaseTabCtrl::GetTabArea](../Topic/CMFCBaseTabCtrl::GetTabArea.md)。）|  
|`CMFCTabCtrl::GetTabFromPoint`|检索包含指定的点的选项。  （重写 [CMFCBaseTabCtrl::GetTabFromPoint](../Topic/CMFCBaseTabCtrl::GetTabFromPoint.md)。）|  
|[CMFCTabCtrl::GetTabMaxWidth](../Topic/CMFCTabCtrl::GetTabMaxWidth.md)|检索选项的最大宽度。|  
|[CMFCTabCtrl::GetTabsHeight](../Topic/CMFCTabCtrl::GetTabsHeight.md)|检索当前选项卡控件的选项范围的高度。|  
|[CMFCTabCtrl::GetTabsRect](../Topic/CMFCTabCtrl::GetTabsRect.md)|检索限制当前选项卡控件的制表符大小的矩形。  （重写 [CMFCBaseTabCtrl::GetTabsRect](../Topic/CMFCBaseTabCtrl::GetTabsRect.md)。）|  
|`CMFCTabCtrl::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCTabCtrl::GetWndArea](../Topic/CMFCTabCtrl::GetWndArea.md)|检索当前选项卡控件的客户端范围的边界。|  
|[CMFCTabCtrl::HideActiveWindowHorzScrollBar](../Topic/CMFCTabCtrl::HideActiveWindowHorzScrollBar.md)|隐藏水平滚动条，如果有，活动窗口。|  
|[CMFCTabCtrl::HideInactiveWindow](../Topic/CMFCTabCtrl::HideInactiveWindow.md)|指定框架是否显示非活动选项卡控件窗口。|  
|[CMFCTabCtrl::HideNoTabs](../Topic/CMFCTabCtrl::HideNoTabs.md)|;如果没有显示选项，启用或禁用选项绘制区域。|  
|[CMFCTabCtrl::HideSingleTab](../Topic/CMFCTabCtrl::HideSingleTab.md)|当有一个选项卡式窗口时，启用或禁用绘制选项。  （重写 [CMFCBaseTabCtrl::HideSingleTab](../Topic/CMFCBaseTabCtrl::HideSingleTab.md)。）|  
|[CMFCTabCtrl::IsActiveInMDITabGroup](../Topic/CMFCTabCtrl::IsActiveInMDITabGroup.md)|指示可选控件的当前选择是在多个的有效选项文档界面选项卡组。|  
|[CMFCTabCtrl::IsActiveTabBoldFont](../Topic/CMFCTabCtrl::IsActiveTabBoldFont.md)|指示活动选项卡上的文本使用用粗体，是否显示。|  
|[CMFCTabCtrl::IsActiveTabCloseButton](../Topic/CMFCTabCtrl::IsActiveTabCloseButton.md)|指示关闭"按钮\(**x**\)是否位于有效的选项区域的右上角显示。|  
|[CMFCTabCtrl::IsDrawFrame](../Topic/CMFCTabCtrl::IsDrawFrame.md)|指示选项卡式窗口是否在嵌入式窗格周围绘制帧矩形。|  
|[CMFCTabCtrl::IsFlatFrame](../Topic/CMFCTabCtrl::IsFlatFrame.md)|指示在选项卡区域画出的帧是否为平面或三维。|  
|[CMFCTabCtrl::IsFlatTab](../Topic/CMFCTabCtrl::IsFlatTab.md)|指示是否选项的外观在当前选项卡控件上保持不变。|  
|[CMFCTabCtrl::IsLeftRightRounded](../Topic/CMFCTabCtrl::IsLeftRightRounded.md)|指示一个选项的左右侧的外观在当前选项卡控件是否被舍入。|  
|[CMFCTabCtrl::IsMDITabGroup](../Topic/CMFCTabCtrl::IsMDITabGroup.md)|指示当前选项卡控件是否在多文档界面\(mdi\)窗口的工作区包含。|  
|[CMFCTabCtrl::IsOneNoteStyle](../Topic/CMFCTabCtrl::IsOneNoteStyle.md)|指示当前选项卡控件是否显示如果Microsoft OneNote样式。|  
|`CMFCTabCtrl::IsPtInTabArea`|确定一个点是否位于可选区域内。  （重写 [CMFCBaseTabCtrl::IsPtInTabArea](../Topic/CMFCBaseTabCtrl::IsPtInTabArea.md)。）|  
|[CMFCTabCtrl::IsSharedScroll](../Topic/CMFCTabCtrl::IsSharedScroll.md)|指示当前选项卡控件是否有可以移动其选项作为组滚动条。|  
|[CMFCTabCtrl::IsTabDocumentsMenu](../Topic/CMFCTabCtrl::IsTabDocumentsMenu.md)|指示可选控制是否显示滚动按钮或显示选项卡式窗口菜单的按钮。|  
|[CMFCTabCtrl::IsVS2005Style](../Topic/CMFCTabCtrl::IsVS2005Style.md)|选项指示是否显示如果Visual Studio .NET样式2005。|  
|[CMFCTabCtrl::ModifyTabStyle](../Topic/CMFCTabCtrl::ModifyTabStyle.md)|在当前选项卡控件指定选项外观。|  
|`CMFCTabCtrl::MoveTab`|移动选项移到另一个选项位置。  （重写 [CMFCBaseTabCtrl::MoveTab](../Topic/CMFCBaseTabCtrl::MoveTab.md)。）|  
|[CMFCTabCtrl::OnDragEnter](../Topic/CMFCTabCtrl::OnDragEnter.md)|调用由结构，当光标首先拖动到选项卡控件的窗口。|  
|[CMFCTabCtrl::OnDragOver](../Topic/CMFCTabCtrl::OnDragOver.md)|调用由框架在拖动操作过程中，当鼠标移动在放置目标窗口上。  （重写 [CMFCBaseTabCtrl::OnDragOver](../Topic/CMFCBaseTabCtrl::OnDragOver.md)。）|  
|[CMFCTabCtrl::OnShowTabDocumentsMenu](../Topic/CMFCTabCtrl::OnShowTabDocumentsMenu.md)|显示选项卡式窗口的弹出菜单，等待，直到用户选择一个选项，并使选定的选项有效选项。|  
|`CMFCTabCtrl::PreTranslateMessage`|在将调度到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows功能之前，将windows消息。  （重写 [CMFCBaseTabCtrl::PreTranslateMessage](../Topic/CMFCBaseTabCtrl::PreTranslateMessage.md)。）|  
|`CMFCTabCtrl::RecalcLayout`|计算选项卡控件的内部格式。  （重写 [CMFCBaseTabCtrl::RecalcLayout](../Topic/CMFCBaseTabCtrl::RecalcLayout.md)。）|  
|[CMFCTabCtrl::SetActiveInMDITabGroup](../Topic/CMFCTabCtrl::SetActiveInMDITabGroup.md)|设置选项卡控件的当前tab为多个的有效选项文档界面选项卡组。|  
|[CMFCTabCtrl::SetActiveTab](../Topic/CMFCTabCtrl::SetActiveTab.md)|激活选项。  （重写 [CMFCBaseTabCtrl::SetActiveTab](../Topic/CMFCBaseTabCtrl::SetActiveTab.md)。）|  
|[CMFCTabCtrl::SetActiveTabBoldFont](../Topic/CMFCTabCtrl::SetActiveTabBoldFont.md)|启用或对于活动选项卡的粗体中禁用使用。|  
|[CMFCTabCtrl::SetDrawFrame](../Topic/CMFCTabCtrl::SetDrawFrame.md)|在嵌入式条边启用或禁用drawinga帧矩形。|  
|[CMFCTabCtrl::SetFlatFrame](../Topic/CMFCTabCtrl::SetFlatFrame.md)|指定是否在选项卡区域周围绘制简单或三维帧。|  
|[CMFCTabCtrl::SetImageList](../Topic/CMFCTabCtrl::SetImageList.md)|指定图像列表。  （重写 [CMFCBaseTabCtrl::SetImageList](../Topic/CMFCBaseTabCtrl::SetImageList.md)。）|  
|[CMFCTabCtrl::SetResizeMode](../Topic/CMFCTabCtrl::SetResizeMode.md)|指定当前选项卡控件如何调整然后重新显示控件。|  
|[CMFCTabCtrl::SetTabMaxWidth](../Topic/CMFCTabCtrl::SetTabMaxWidth.md)|在一个选项卡式窗口指定最大选项宽度。|  
|[CMFCTabCtrl::StopResize](../Topic/CMFCTabCtrl::StopResize.md)|停止当前调整在选项卡控件的操作。|  
|`CMFCTabCtrl::SwapTabs`|交换选项对。  （重写 [CMFCBaseTabCtrl::SwapTabs](../Topic/CMFCBaseTabCtrl::SwapTabs.md)。）|  
|[CMFCTabCtrl::SynchronizeScrollBar](../Topic/CMFCTabCtrl::SynchronizeScrollBar.md)|绘制在显示简单的选项卡上的控件的水平滚动条。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCTabCtrl::m\_bEnableActivate](../Topic/CMFCTabCtrl::m_bEnableActivate.md)|在插入新选项卡并启用时，防止活动视图失去焦点。|  
  
## 备注  
 `CMFCTabCtrl` 选件类支持:  
  
-   选项卡包含三维，平面，并平展具有共享水平滚动条的控件的样式。  
  
-   选项位于顶部或窗口的底部。  
  
-   显示文本、图像或文本和图像的选项。  
  
-   更改颜色的选项，该选项处于活动状态。  
  
-   边框可调整的选项范围的更改。  
  
-   可拆的选项卡式窗口。  
  
 `CMFCTabCtrl` 选件类可用于对话框，但是，供使用停靠与 [!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)] 和 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]的控制条的应用程序。  有关更多信息，请参见 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)。  
  
 按照这些步骤添加可调整大小，该栏停靠在应用程序的可选控件:  
  
1.  创建 [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md) 的一个实例。  
  
2.  调用 [CDockablePane::Create](../Topic/CDockablePane::Create.md)。  
  
3.  使用 [CBaseTabbedPane::AddTab](../Topic/CBaseTabbedPane::AddTab.md) 或 [CMFCBaseTabCtrl::InsertTab](../Topic/CMFCBaseTabCtrl::InsertTab.md) 添加新选项卡。  
  
4.  调用 [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md)，以便当前停靠选项卡控件可以停靠在主框架窗口。  
  
5.  调用 [CFrameWndEx::DockPane](../Topic/CFrameWndEx::DockPane.md) 停靠选项卡式窗口在主框架。  
  
 有关如何创建一个选项卡式窗口作为停靠控件条，请参见 [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md)。  若要使用 `CMFCTabCtrl` 作为非停靠控件，请创建一 `CMFCTabCtrl` 对象并调用 [CMFCTabCtrl::Create](../Topic/CMFCTabCtrl::Create.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)  
  
## 示例  
 下面的示例在 `CMFCTabCtrl` 选件类演示如何使用各种方案配置 `CMFCTabCtrl` 对象。  示例说明如何将选项，显示活动可选的关闭"按钮，启用可编辑的选项卡标签和显示选项卡式窗口标签弹出菜单。  此示例是 [状态COLLECT示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_StateCollection#1](../../mfc/reference/codesnippet/CPP/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection#3](../../mfc/reference/codesnippet/CPP/cmfctabctrl-class_2.cpp)]  
  
## 要求  
 **标头:** afxtabctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)