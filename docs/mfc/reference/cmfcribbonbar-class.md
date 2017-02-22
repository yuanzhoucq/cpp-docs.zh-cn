---
title: "CMFCRibbonBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonBar class"
ms.assetid: a65d06fa-1a28-4cc0-8971-bc9d7c9198fe
caps.latest.revision: 41
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 43
---
# CMFCRibbonBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonBar` 类实现与 Office 2007 中所使用的类似功能区栏。  
  
## 语法  
  
```  
class CMFCRibbonBar : public CPane  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|`CMFCRibbonBar::CMFCRibbonBar`|默认构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonBar::ActivateContextCategory](../Topic/CMFCRibbonBar::ActivateContextCategory.md)|激活已经可见的上下文类别。|  
|[CMFCRibbonBar::AddCategory](../Topic/CMFCRibbonBar::AddCategory.md)|向功能区添加新的功能区类别。|  
|[CMFCRibbonBar::AddContextCategory](../Topic/CMFCRibbonBar::AddContextCategory.md)|添加上下文类别。|  
|[CMFCRibbonBar::AddMainCategory](../Topic/CMFCRibbonBar::AddMainCategory.md)|添加新的主功能区类别。|  
|[CMFCRibbonBar::AddPrintPreviewCategory](../Topic/CMFCRibbonBar::AddPrintPreviewCategory.md)||  
|[CMFCRibbonBar::AddQATOnlyCategory](../Topic/CMFCRibbonBar::AddQATOnlyCategory.md)||  
|[CMFCRibbonBar::AddToTabs](../Topic/CMFCRibbonBar::AddToTabs.md)|将功能区元素添加到功能区栏的右侧。|  
|[CMFCRibbonBar::CreateEx](../Topic/CMFCRibbonBar::CreateEx.md)|创建功能区栏并将其附加到 [CPane](../../mfc/reference/cpane-class.md) 对象。  （重写 [CPane::CreateEx](../Topic/CPane::CreateEx.md)。）|  
|[CMFCRibbonBar::Create](../Topic/CMFCRibbonBar::Create.md)|创建功能区栏控件并将其附加到功能区栏。|  
|[CMFCRibbonBar::DeactivateKeyboardFocus](../Topic/CMFCRibbonBar::DeactivateKeyboardFocus.md)||  
|[CMFCRibbonBar::DrawMenuImage](../Topic/CMFCRibbonBar::DrawMenuImage.md)||  
|[CMFCRibbonBar::DWMCompositionChanged](../Topic/CMFCRibbonBar::DWMCompositionChanged.md)||  
|[CMFCRibbonBar::EnableKeyTips](../Topic/CMFCRibbonBar::EnableKeyTips.md)|启用或禁用功能区控件的键提示。|  
|[CMFCRibbonBar::EnablePrintPreview](../Topic/CMFCRibbonBar::EnablePrintPreview.md)|启用**“打印预览”**选项卡。|  
|[CMFCRibbonBar::EnableToolTips](../Topic/CMFCRibbonBar::EnableToolTips.md)|启用或禁用功能区栏的工具提示或工具提示说明。|  
|[CMFCRibbonBar::FindByData](../Topic/CMFCRibbonBar::FindByData.md)|使用用户指定的数据查找功能区元素。|  
|[CMFCRibbonBar::FindByID](../Topic/CMFCRibbonBar::FindByID.md)|查找具有指定命令 ID 的功能区元素。|  
|[CMFCRibbonBar::FindCategoryIndexByData](../Topic/CMFCRibbonBar::FindCategoryIndexByData.md)|查找包含用户定义数据的功能区类别的索引。|  
|[CMFCRibbonBar::ForceRecalcLayout](../Topic/CMFCRibbonBar::ForceRecalcLayout.md)||  
|[CMFCRibbonBar::GetActiveCategory](../Topic/CMFCRibbonBar::GetActiveCategory.md)|获取指向活动类别的指针。|  
|[CMFCRibbonBar::GetCaptionHeight](../Topic/CMFCRibbonBar::GetCaptionHeight.md)|返回标题高度。  （重写 [CBasePane::GetCaptionHeight](../Topic/CBasePane::GetCaptionHeight.md)。）|  
|[CMFCRibbonBar::GetCategory](../Topic/CMFCRibbonBar::GetCategory.md)|获取指向位于指定索引处的类别的指针。|  
|[CMFCRibbonBar::GetCategoryCount](../Topic/CMFCRibbonBar::GetCategoryCount.md)|获取功能区栏中功能区类别的数目。|  
|[CMFCRibbonBar::GetCategoryHeight](../Topic/CMFCRibbonBar::GetCategoryHeight.md)||  
|[CMFCRibbonBar::GetCategoryIndex](../Topic/CMFCRibbonBar::GetCategoryIndex.md)|返回功能区类别的索引。|  
|[CMFCRibbonBar::GetContextName](../Topic/CMFCRibbonBar::GetContextName.md)|检索通过使用 ID 指定的上下文类别标题的名称。|  
|[CMFCRibbonBar::GetDroppedDown](../Topic/CMFCRibbonBar::GetDroppedDown.md)||  
|[CMFCRibbonBar::GetElementsByID](../Topic/CMFCRibbonBar::GetElementsByID.md)|获取一个数组，该数组包含指向具有指定 ID 的所有功能区元素的指针。|  
|[CMFCRibbonBar::GetApplicationButton](../Topic/CMFCRibbonBar::GetApplicationButton.md)|获取指向功能区按钮的指针。|  
|[CMFCRibbonBar::GetFocused](../Topic/CMFCRibbonBar::GetFocused.md)|返回焦点元素。|  
|[CMFCRibbonBar::GetHideFlags](../Topic/CMFCRibbonBar::GetHideFlags.md)||  
|[CMFCRibbonBar::GetItemIDsList](../Topic/CMFCRibbonBar::GetItemIDsList.md)||  
|[CMFCRibbonBar::GetKeyboardNavigationLevel](../Topic/CMFCRibbonBar::GetKeyboardNavigationLevel.md)||  
|[CMFCRibbonBar::GetKeyboardNavLevelCurrent](../Topic/CMFCRibbonBar::GetKeyboardNavLevelCurrent.md)||  
|[CMFCRibbonBar::GetKeyboardNavLevelParent](../Topic/CMFCRibbonBar::GetKeyboardNavLevelParent.md)||  
|[CMFCRibbonBar::GetMainCategory](../Topic/CMFCRibbonBar::GetMainCategory.md)|返回指向当前选定功能区类别的指针。|  
|[CMFCRibbonBar::GetQATCommandsLocation](../Topic/CMFCRibbonBar::GetQATCommandsLocation.md)||  
|[CMFCRibbonBar::GetQATDroppedDown](../Topic/CMFCRibbonBar::GetQATDroppedDown.md)||  
|[CMFCRibbonBar::GetQuickAccessCommands](../Topic/CMFCRibbonBar::GetQuickAccessCommands.md)|填充列表，该列表包含快速访问工具栏上显示的所有元素的命令 ID。|  
|[CMFCRibbonBar::GetQuickAccessToolbarLocation](../Topic/CMFCRibbonBar::GetQuickAccessToolbarLocation.md)||  
|[CMFCRibbonBar::GetTabTrancateRatio](../Topic/CMFCRibbonBar::GetTabTrancateRatio.md)||  
|[CMFCRibbonBar::GetTooltipFixedWidthLargeImage](../Topic/CMFCRibbonBar::GetTooltipFixedWidthLargeImage.md)||  
|[CMFCRibbonBar::GetTooltipFixedWidthRegular](../Topic/CMFCRibbonBar::GetTooltipFixedWidthRegular.md)||  
|[CMFCRibbonBar::GetVisibleCategoryCount](../Topic/CMFCRibbonBar::GetVisibleCategoryCount.md)||  
|[CMFCRibbonBar::HideAllContextCategories](../Topic/CMFCRibbonBar::HideAllContextCategories.md)|隐藏所有活动的且可见的类别。|  
|[CMFCRibbonBar::HideKeyTips](../Topic/CMFCRibbonBar::HideKeyTips.md)||  
|[CMFCRibbonBar::HitTest](../Topic/CMFCRibbonBar::HitTest.md)|查找一个指针，该指针指向位于功能区栏客户端坐标中指定点的功能区元素。|  
|[CMFCRibbonBar::IsKeyTipEnabled](../Topic/CMFCRibbonBar::IsKeyTipEnabled.md)|确定是否启用键提示。|  
|[CMFCRibbonBar::IsMainRibbonBar](../Topic/CMFCRibbonBar::IsMainRibbonBar.md)||  
|[CMFCRibbonBar::IsPrintPreviewEnabled](../Topic/CMFCRibbonBar::IsPrintPreviewEnabled.md)|确定是否启用**“打印预览”**选项卡。|  
|[CMFCRibbonBar::IsQATEmpty](../Topic/CMFCRibbonBar::IsQATEmpty.md)||  
|[CMFCRibbonBar::IsQuickAccessToolbarOnTop](../Topic/CMFCRibbonBar::IsQuickAccessToolbarOnTop.md)|指定快速访问工具栏是否位于功能区栏上方。|  
|[CMFCRibbonBar::IsReplaceFrameCaption](../Topic/CMFCRibbonBar::IsReplaceFrameCaption.md)|确定功能区栏是替换主框架标题还是添加到框架标题的下方。|  
|[CMFCRibbonBar::IsShowGroupBorder](../Topic/CMFCRibbonBar::IsShowGroupBorder.md)||  
|[CMFCRibbonBar::IsToolTipDescrEnabled](../Topic/CMFCRibbonBar::IsToolTipDescrEnabled.md)|确定是否启用工具提示说明。|  
|[CMFCRibbonBar::IsToolTipEnabled](../Topic/CMFCRibbonBar::IsToolTipEnabled.md)|确定是否禁用工具提示说明。|  
|[CMFCRibbonBar::IsTransparentCaption](../Topic/CMFCRibbonBar::IsTransparentCaption.md)||  
|[CMFCRibbonBar::IsWindows7Look](../Topic/CMFCRibbonBar::IsWindows7Look.md)|指示功能区是否具有 Windows 7 样式的外观（小型矩形应用程序按钮）。|  
|[CMFCRibbonBar::LoadFromResource](../Topic/CMFCRibbonBar::LoadFromResource.md)|已重载。  从应用程序资源加载功能区栏。|  
|[CMFCRibbonBar::OnClickButton](../Topic/CMFCRibbonBar::OnClickButton.md)||  
|[CMFCRibbonBar::OnEditContextMenu](../Topic/CMFCRibbonBar::OnEditContextMenu.md)||  
|[CMFCRibbonBar::OnRTLChanged](../Topic/CMFCRibbonBar::OnRTLChanged.md)|（重写 `CPane::OnRTLChanged`。）|  
|[CMFCRibbonBar::OnSetAccData](../Topic/CMFCRibbonBar::OnSetAccData.md)|（重写 [CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md)。）|  
|[CMFCRibbonBar::OnShowRibbonContextMenu](../Topic/CMFCRibbonBar::OnShowRibbonContextMenu.md)||  
|[CMFCRibbonBar::OnShowRibbonQATMenu](../Topic/CMFCRibbonBar::OnShowRibbonQATMenu.md)||  
|[CMFCRibbonBar::OnSysKeyDown](../Topic/CMFCRibbonBar::OnSysKeyDown.md)||  
|[CMFCRibbonBar::OnSysKeyUp](../Topic/CMFCRibbonBar::OnSysKeyUp.md)||  
|[CMFCRibbonBar::PopTooltip](../Topic/CMFCRibbonBar::PopTooltip.md)||  
|[CMFCRibbonBar::PreTranslateMessage](../Topic/CMFCRibbonBar::PreTranslateMessage.md)|（重写 `CBasePane::PreTranslateMessage`。）|  
|[CMFCRibbonBar::RecalcLayout](../Topic/CMFCRibbonBar::RecalcLayout.md)|（重写 [CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md)。）|  
|[CMFCRibbonBar::RemoveAllCategories](../Topic/CMFCRibbonBar::RemoveAllCategories.md)|从功能区栏删除所有功能区类别。|  
|[CMFCRibbonBar::RemoveAllFromTabs](../Topic/CMFCRibbonBar::RemoveAllFromTabs.md)|从选项卡区域删除所有功能区元素。|  
|[CMFCRibbonBar::RemoveCategory](../Topic/CMFCRibbonBar::RemoveCategory.md)|删除位于指定索引处的功能区类别。|  
|[CMFCRibbonBar::SaveToXMLBuffer](../Topic/CMFCRibbonBar::SaveToXMLBuffer.md)|将功能区栏保存到缓冲区。|  
|[CMFCRibbonBar::SaveToXMLFile](../Topic/CMFCRibbonBar::SaveToXMLFile.md)|将功能区栏保存到 XML 文件。|  
|[CMFCRibbonBar::SetActiveCategory](../Topic/CMFCRibbonBar::SetActiveCategory.md)|将指定功能区类别设置为活动。|  
|[CMFCRibbonBar::SetActiveMDIChild](../Topic/CMFCRibbonBar::SetActiveMDIChild.md)||  
|[CMFCRibbonBar::SetElementKeys](../Topic/CMFCRibbonBar::SetElementKeys.md)|为具有指定命令 ID 的所有功能区元素设置指定键提示。|  
|[CMFCRibbonBar::SetApplicationButton](../Topic/CMFCRibbonBar::SetApplicationButton.md)|向功能区栏分配应用程序功能区按钮。|  
|[CMFCRibbonBar::SetKeyboardNavigationLevel](../Topic/CMFCRibbonBar::SetKeyboardNavigationLevel.md)||  
|[CMFCRibbonBar::SetMaximizeMode](../Topic/CMFCRibbonBar::SetMaximizeMode.md)||  
|[CMFCRibbonBar::SetQuickAccessCommands](../Topic/CMFCRibbonBar::SetQuickAccessCommands.md)|向快速访问工具栏添加一个或多个功能区元素。|  
|[CMFCRibbonBar::SetQuickAccessDefaultState](../Topic/CMFCRibbonBar::SetQuickAccessDefaultState.md)|指定快速访问工具栏的默认状态。|  
|[CMFCRibbonBar::SetQuickAccessToolbarOnTop](../Topic/CMFCRibbonBar::SetQuickAccessToolbarOnTop.md)|将快速访问工具栏 \(QAT\) 定位在功能区栏上方或下方。|  
|[CMFCRibbonBar::SetTooltipFixedWidth](../Topic/CMFCRibbonBar::SetTooltipFixedWidth.md)||  
|[CMFCRibbonBar::SetWindows7Look](../Topic/CMFCRibbonBar::SetWindows7Look.md)|启用\/禁用功能区的 Windows 7 样式的外观（小型矩形应用程序按钮）|  
|[CMFCRibbonBar::ShowCategory](../Topic/CMFCRibbonBar::ShowCategory.md)|显示或隐藏指定的功能区类别。|  
|[CMFCRibbonBar::ShowContextCategories](../Topic/CMFCRibbonBar::ShowContextCategories.md)|显示或隐藏具有指定 ID 的上下文类别。|  
|[CMFCRibbonBar::ShowKeyTips](../Topic/CMFCRibbonBar::ShowKeyTips.md)||  
|[CMFCRibbonBar::ToggleMimimizeState](../Topic/CMFCRibbonBar::ToggleMimimizeState.md)|在最小化和最大化状态之间切换功能区栏。|  
|[CMFCRibbonBar::TranslateChar](../Topic/CMFCRibbonBar::TranslateChar.md)||  
  
## 备注  
 Microsoft 在发布 Microsoft Office 2007 时同时引入了 Office Fluent 功能区。  该功能区栏不仅仅是一个新控件。  它代表了一个新的用户界面范例。  功能区是一个包含一组称为类别的选项卡的窗格。  各类别以逻辑方式拆分为不同的功能区面板，而各面板可包含各种控件和命令按钮。  
  
 功能区栏上显示的元素可进行缩放以实现可用空间的最佳利用。  例如，如果一个功能区面板具有足够的空间来显示其元素，它便成为一个菜单按钮，可在一个弹出菜单上显示子项。  功能区栏的行为方式与静态（非浮点）控件栏一样，并可以停靠在框架顶部。  
  
 你可以使用 `CMFCRibbonStatusBar` 类来实现一个类似于 Office 2007 中所用的状态栏。  一个功能区类别包含（并显示）一组[功能区面板](../../mfc/reference/cmfcribbonpanel-class.md)。  各功能区面板包含一个或多个功能区元素，这些元素派生自 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)。  
  
 有关如何向现有 MFC 应用程序添加功能区栏的信息，请参阅[演练：更新 MFC 自由曲线应用程序](../../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)  
  
## 要求  
 **标头：**afxribbonbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)   
 [CMFCRibbonCategory Class](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonPanel Class](../../mfc/reference/cmfcribbonpanel-class.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [演练：更新 MFC 自由曲线应用程序](../../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)