---
title: "CMFCRibbonBaseElement Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonBaseElement"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonBaseElement class"
ms.assetid: 419ea91b-5062-44cc-b0a3-f87d29566f62
caps.latest.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 36
---
# CMFCRibbonBaseElement Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonBaseElement` 选件类是可以添加到 [功能区栏](../../mfc/reference/cmfcribbonbar-class.md)的所有元素的基类。  功能区元素的示例是功能区按钮、复选框和功能区组合框。  
  
## 语法  
  
```  
class CMFCRibbonBaseElement : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCRibbonBaseElement`|构造 `CMFCRibbonBaseElement` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonBaseElement::AddToKeyList](../Topic/CMFCRibbonBaseElement::AddToKeyList.md)|添加功能区元素的一keytip的一个数组快捷键提示。|  
|[CMFCRibbonBaseElement::AddToListBox](../Topic/CMFCRibbonBaseElement::AddToListBox.md)|添加一个功能区元素到指定的功能区命令列表框。|  
|[CMFCRibbonBaseElement::CanBeAddedToQuickAccessToolBar](../Topic/CMFCRibbonBaseElement::CanBeAddedToQuickAccessToolBar.md)|指示功能区元素是否可添加到快速访问工具栏。|  
|[CMFCRibbonBaseElement::CanBeCompacted](../Topic/CMFCRibbonBaseElement::CanBeCompacted.md)|指示功能区元素的大小是否可以是精简的。|  
|[CMFCRibbonBaseElement::CanBeStretched](../Topic/CMFCRibbonBaseElement::CanBeStretched.md)|指示功能区元素的高度是否可以垂直添加到功能区行的高度。|  
|[CMFCRibbonBaseElement::CanBeStretchedHorizontally](../Topic/CMFCRibbonBaseElement::CanBeStretchedHorizontally.md)|指示功能区元素的宽度是否可以更改。|  
|[CMFCRibbonBaseElement::CleanUpSizes](../Topic/CMFCRibbonBaseElement::CleanUpSizes.md)|清理功能区元素的尺寸设置。|  
|[CMFCRibbonBaseElement::ClosePopupMenu](../Topic/CMFCRibbonBaseElement::ClosePopupMenu.md)|关闭功能区元素的弹出菜单。|  
|[CMFCRibbonBaseElement::CopyFrom](../Topic/CMFCRibbonBaseElement::CopyFrom.md)|复制指定的 `CMFCRibbonBaseElement` 的状态为当前对象。|  
|[CMFCRibbonBaseElement::DestroyCtrl](../Topic/CMFCRibbonBaseElement::DestroyCtrl.md)|销毁功能区元素。|  
|[CMFCRibbonBaseElement::DrawImage](../Topic/CMFCRibbonBaseElement::DrawImage.md)|绘制功能区元素的图像。|  
|[CMFCRibbonBaseElement::Find](../Topic/CMFCRibbonBaseElement::Find.md)|如果它指向当前对象，返回指定的指针功能区元素。|  
|[CMFCRibbonBaseElement::FindByData](../Topic/CMFCRibbonBaseElement::FindByData.md)|如果它包含指定的数据，检索指向功能区元素。|  
|[CMFCRibbonBaseElement::FindByID](../Topic/CMFCRibbonBaseElement::FindByID.md)|如果该元素是由指定的命令ID.，确定的检索指向功能区元素|  
|[CMFCRibbonBaseElement::FindByOriginal](../Topic/CMFCRibbonBaseElement::FindByOriginal.md)|如果其原始的功能区元素与指定的功能区元素，检索指向功能区元素。|  
|[CMFCRibbonBaseElement::GetCompactSize](../Topic/CMFCRibbonBaseElement::GetCompactSize.md)|返回功能区元素的袖珍型。|  
|[CMFCRibbonBaseElement::GetData](../Topic/CMFCRibbonBaseElement::GetData.md)|检索用户定义的数据与功能区元素。|  
|[CMFCRibbonBaseElement::GetDescription](../Topic/CMFCRibbonBaseElement::GetDescription.md)|返回功能区元素的说明。|  
|[CMFCRibbonBaseElement::GetDroppedDown](../Topic/CMFCRibbonBaseElement::GetDroppedDown.md)|则该弹出菜单放置滚动，检索指向功能区元素。|  
|[CMFCRibbonBaseElement::GetElements](../Topic/CMFCRibbonBaseElement::GetElements.md)|将当前功能区元素添加到指定的数组。|  
|[CMFCRibbonBaseElement::GetElementsByID](../Topic/CMFCRibbonBaseElement::GetElementsByID.md)|如果当前功能区元素包含指定的命令ID.，将当前功能区元素添加到指定的数组|  
|[CMFCRibbonBaseElement::GetHighlighted](../Topic/CMFCRibbonBaseElement::GetHighlighted.md)|则显示，检索指向功能区元素。|  
|[CMFCRibbonBaseElement::GetID](../Topic/CMFCRibbonBaseElement::GetID.md)|返回功能区元素的命令ID。|  
|[CMFCRibbonBaseElement::GetImageSize](../Topic/CMFCRibbonBaseElement::GetImageSize.md)|返回功能区元素的图像大小。|  
|[CMFCRibbonBaseElement::GetIntermediateSize](../Topic/CMFCRibbonBaseElement::GetIntermediateSize.md)|返回功能区元素的大小在其元状态的。|  
|[CMFCRibbonBaseElement::GetKeys](../Topic/CMFCRibbonBaseElement::GetKeys.md)|返回keytip与功能区元素。|  
|[CMFCRibbonBaseElement::GetKeyTipRect](../Topic/CMFCRibbonBaseElement::GetKeyTipRect.md)|检索功能区元素的keytip边界矩形。|  
|[CMFCRibbonBaseElement::GetKeyTipSize](../Topic/CMFCRibbonBaseElement::GetKeyTipSize.md)|检索keytip的文本范围。|  
|[CMFCRibbonBaseElement::GetLocationInGroup](../Topic/CMFCRibbonBaseElement::GetLocationInGroup.md)|功能区上的组中指示功能区元素的显示位置。|  
|[CMFCRibbonBaseElement::GetMenuKeys](../Topic/CMFCRibbonBaseElement::GetMenuKeys.md)|返回会与按钮。|  
|[CMFCRibbonBaseElement::GetNotifyID](../Topic/CMFCRibbonBaseElement::GetNotifyID.md)|检索功能区元素的通知命令ID。|  
|[CMFCRibbonBaseElement::GetOriginal](../Topic/CMFCRibbonBaseElement::GetOriginal.md)|检索原始功能区元素。|  
|[CMFCRibbonBaseElement::GetParentCategory](../Topic/CMFCRibbonBaseElement::GetParentCategory.md)|检索功能区元素的功能区类别。|  
|[CMFCRibbonBaseElement::GetParentPanel](../Topic/CMFCRibbonBaseElement::GetParentPanel.md)|检索包含功能区元素的一个。|  
|[CMFCRibbonBaseElement::GetParentRibbonBar](../Topic/CMFCRibbonBaseElement::GetParentRibbonBar.md)|检索功能区元素的父功能区栏。|  
|[CMFCRibbonBaseElement::GetParentWnd](../Topic/CMFCRibbonBaseElement::GetParentWnd.md)|检索功能区元素的父窗口。|  
|[CMFCRibbonBaseElement::GetPressed](../Topic/CMFCRibbonBaseElement::GetPressed.md)|如果用户当前按下它，检索指向功能区元素。|  
|[CMFCRibbonBaseElement::GetQuickAccessToolBarID](../Topic/CMFCRibbonBaseElement::GetQuickAccessToolBarID.md)|它位于快速访问工具栏，检索功能区元素的命令ID。|  
|[CMFCRibbonBaseElement::GetRect](../Topic/CMFCRibbonBaseElement::GetRect.md)|返回功能区元素的边框。|  
|[CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)|返回功能区元素的常规大小。|  
|[CMFCRibbonBaseElement::GetSize](../Topic/CMFCRibbonBaseElement::GetSize.md)|返回功能区元素的当前范围。|  
|[CMFCRibbonBaseElement::GetText](../Topic/CMFCRibbonBaseElement::GetText.md)|返回文本与功能区元素。|  
|[CMFCRibbonBaseElement::GetToolTipText](../Topic/CMFCRibbonBaseElement::GetToolTipText.md)|返回功能区元素的工具提示文本。|  
|[CMFCRibbonBaseElement::GetTopLevelRibbonBar](../Topic/CMFCRibbonBaseElement::GetTopLevelRibbonBar.md)|检索功能区元素的顶级功能区栏。|  
|[CMFCRibbonBaseElement::HasCompactMode](../Topic/CMFCRibbonBaseElement::HasCompactMode.md)|指定功能区元素是否具有compact模式。|  
|[CMFCRibbonBaseElement::HasFocus](../Topic/CMFCRibbonBaseElement::HasFocus.md)|指示父元素是否具有键盘焦点。|  
|[CMFCRibbonBaseElement::HasIntermediateMode](../Topic/CMFCRibbonBaseElement::HasIntermediateMode.md)|指定功能区元素是否具有中间模式。|  
|[CMFCRibbonBaseElement::HasLargeMode](../Topic/CMFCRibbonBaseElement::HasLargeMode.md)|指定功能区元素是否有大型架构。|  
|[CMFCRibbonBaseElement::HasMenu](../Topic/CMFCRibbonBaseElement::HasMenu.md)|指示功能区元素是否都有菜单。|  
|[CMFCRibbonBaseElement::HitTest](../Topic/CMFCRibbonBaseElement::HitTest.md)|因此，如果指定的点位于它，检索指向功能区元素。|  
|[CMFCRibbonBaseElement::IsAlignByColumn](../Topic/CMFCRibbonBaseElement::IsAlignByColumn.md)|指示功能区元素是垂直对齐与其他功能区元素。|  
|[CMFCRibbonBaseElement::IsAlwaysLargeImage](../Topic/CMFCRibbonBaseElement::IsAlwaysLargeImage.md)|指示区组件图像大小是否始终用。|  
|[CMFCRibbonBaseElement::IsAutoRepeatMode](../Topic/CMFCRibbonBaseElement::IsAutoRepeatMode.md)|指示功能区元素是否在自动重复模式。|  
|[CMFCRibbonBaseElement::IsChecked](../Topic/CMFCRibbonBaseElement::IsChecked.md)|指定功能区元素是否进行检查。|  
|[CMFCRibbonBaseElement::IsCompactMode](../Topic/CMFCRibbonBaseElement::IsCompactMode.md)|指定功能区元素是否在紧凑模式。|  
|[CMFCRibbonBaseElement::IsDefaultMenuLook](../Topic/CMFCRibbonBaseElement::IsDefaultMenuLook.md)||  
|[CMFCRibbonBaseElement::IsDisabled](../Topic/CMFCRibbonBaseElement::IsDisabled.md)|指定功能区元素是否禁用。|  
|[CMFCRibbonBaseElement::IsDroppedDown](../Topic/CMFCRibbonBaseElement::IsDroppedDown.md)|确定功能区元素是否显示一个弹出菜单和下拉。|  
|[CMFCRibbonBaseElement::IsFocused](../Topic/CMFCRibbonBaseElement::IsFocused.md)|指定功能区元素是否具有焦点。|  
|[CMFCRibbonBaseElement::IsGalleryIcon](../Topic/CMFCRibbonBaseElement::IsGalleryIcon.md)|指示功能区元素是否在功能区库包含。|  
|[CMFCRibbonBaseElement::IsHighlighted](../Topic/CMFCRibbonBaseElement::IsHighlighted.md)|指定功能区元素是否显示。|  
|[CMFCRibbonBaseElement::IsIntermediateMode](../Topic/CMFCRibbonBaseElement::IsIntermediateMode.md)|指示功能区元素的当前映像是否是一个中间范围。|  
|[CMFCRibbonBaseElement::IsLargeMode](../Topic/CMFCRibbonBaseElement::IsLargeMode.md)|指示功能区元素的当前映像是否是大型。|  
|[CMFCRibbonBaseElement::IsMenuMode](../Topic/CMFCRibbonBaseElement::IsMenuMode.md)|指示功能区元素是否在菜单包含。|  
|[CMFCRibbonBaseElement::IsPressed](../Topic/CMFCRibbonBaseElement::IsPressed.md)|指示用户是否单击功能区元素。|  
|[CMFCRibbonBaseElement::IsQATMode](../Topic/CMFCRibbonBaseElement::IsQATMode.md)|指示功能区元素是否在快速访问工具栏包含。|  
|[CMFCRibbonBaseElement::IsSeparator](../Topic/CMFCRibbonBaseElement::IsSeparator.md)|指示功能区元素是否显示分隔。|  
|[CMFCRibbonBaseElement::IsShowGroupBorder](../Topic/CMFCRibbonBaseElement::IsShowGroupBorder.md)|指示功能区元素是否以显示一个常见边框的组中包含。|  
|[CMFCRibbonBaseElement::IsShowTooltipOnBottom](../Topic/CMFCRibbonBaseElement::IsShowTooltipOnBottom.md)|指示工具提示是否显示在功能区元素下。|  
|[CMFCRibbonBaseElement::IsTabStop](../Topic/CMFCRibbonBaseElement::IsTabStop.md)|指示功能区元素可以选择是否具有键盘。|  
|[CMFCRibbonBaseElement::IsTextAlwaysOnRight](../Topic/CMFCRibbonBaseElement::IsTextAlwaysOnRight.md)|指示功能区元素的文本是否在右侧显示。|  
|[CMFCRibbonBaseElement::IsVisible](../Topic/CMFCRibbonBaseElement::IsVisible.md)|指示功能区元素是否当前显示。|  
|[CMFCRibbonBaseElement::IsWholeRowHeight](../Topic/CMFCRibbonBaseElement::IsWholeRowHeight.md)|指示功能区元素的显示heigth是否与包含该面板显示功能区的高度。|  
|[CMFCRibbonBaseElement::NotifyCommand](../Topic/CMFCRibbonBaseElement::NotifyCommand.md)|发送一个命令通知到功能区元素的父窗口。|  
|[CMFCRibbonBaseElement::NotifyHighlightListItem](../Topic/CMFCRibbonBaseElement::NotifyHighlightListItem.md)|通知功能区栏的父窗口，当用户显示位于列表的一个功能区元素。|  
|[CMFCRibbonBaseElement::OnAddToQAToolbar](../Topic/CMFCRibbonBaseElement::OnAddToQAToolbar.md)|添加功能区元素到指定的快速访问工具栏。|  
|[CMFCRibbonBaseElement::OnAfterChangeRect](../Topic/CMFCRibbonBaseElement::OnAfterChangeRect.md)|更新功能区元素的工具提示。|  
|[CMFCRibbonBaseElement::OnAutoRepeat](../Topic/CMFCRibbonBaseElement::OnAutoRepeat.md)|更新功能区元素以响应中的用户输入。|  
|[CMFCRibbonBaseElement::OnCalcTextSize](../Topic/CMFCRibbonBaseElement::OnCalcTextSize.md)|计算文本的大小功能区元素的。|  
|[CMFCRibbonBaseElement::OnChangeMenuHighlight](../Topic/CMFCRibbonBaseElement::OnChangeMenuHighlight.md)|调用由结构，当突出显示为位于菜单的功能区元素更改。|  
|[CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md)|调用由框架绘制功能区元素。|  
|[CMFCRibbonBaseElement::OnDrawKeyTip](../Topic/CMFCRibbonBaseElement::OnDrawKeyTip.md)|调用由框架绘制功能区元素的keytip。|  
|[CMFCRibbonBaseElement::OnDrawMenuImage](../Topic/CMFCRibbonBaseElement::OnDrawMenuImage.md)|调用由结构，在绘制功能区元素的菜单图像。|  
|[CMFCRibbonBaseElement::OnDrawOnList](../Topic/CMFCRibbonBaseElement::OnDrawOnList.md)|调用由框架绘制功能区组件命令列表框。|  
|[CMFCRibbonBaseElement::OnKey](../Topic/CMFCRibbonBaseElement::OnKey.md)|调用由框架，当用户按下时keytip和功能区具有焦点的元素。|  
|[CMFCRibbonBaseElement::OnMenuKey](../Topic/CMFCRibbonBaseElement::OnMenuKey.md)||  
|[CMFCRibbonBaseElement::OnRTLChanged](../Topic/CMFCRibbonBaseElement::OnRTLChanged.md)|调用由框架，该布局更改方向。|  
|[CMFCRibbonBaseElement::OnShow](../Topic/CMFCRibbonBaseElement::OnShow.md)|调用由结构显示或隐藏功能区元素。|  
|[CMFCRibbonBaseElement::OnShowPopupMenu](../Topic/CMFCRibbonBaseElement::OnShowPopupMenu.md)|调用由结构，当区组件显示一个弹出菜单。|  
|[CMFCRibbonBaseElement::PostMenuCommand](../Topic/CMFCRibbonBaseElement::PostMenuCommand.md)||  
|[CMFCRibbonBaseElement::Redraw](../Topic/CMFCRibbonBaseElement::Redraw.md)|更新功能区元素的显示。|  
|[CMFCRibbonBaseElement::SetACCData](../Topic/CMFCRibbonBaseElement::SetACCData.md)|用户可以设置数据。功能区元素。|  
|[CMFCRibbonBaseElement::SetCompactMode](../Topic/CMFCRibbonBaseElement::SetCompactMode.md)|设置功能区元素的显示范围。|  
|[CMFCRibbonBaseElement::SetData](../Topic/CMFCRibbonBaseElement::SetData.md)|关联数据项与功能区元素。|  
|[CMFCRibbonBaseElement::SetDefaultMenuLook](../Topic/CMFCRibbonBaseElement::SetDefaultMenuLook.md)||  
|[CMFCRibbonBaseElement::SetDescription](../Topic/CMFCRibbonBaseElement::SetDescription.md)|设置功能区元素的说明。|  
|[CMFCRibbonBaseElement::SetID](../Topic/CMFCRibbonBaseElement::SetID.md)|设置功能区元素的命令ID。|  
|[CMFCRibbonBaseElement::SetInitialMode](../Topic/CMFCRibbonBaseElement::SetInitialMode.md)|设置功能区元素的初始显示范围。|  
|[CMFCRibbonBaseElement::SetKeys](../Topic/CMFCRibbonBaseElement::SetKeys.md)|设置功能区元素的一keytip。|  
|[CMFCRibbonBaseElement::SetOriginal](../Topic/CMFCRibbonBaseElement::SetOriginal.md)|设置功能区元素的原始功能区元素。|  
|[CMFCRibbonBaseElement::SetParentCategory](../Topic/CMFCRibbonBaseElement::SetParentCategory.md)|设置功能区元素的父类别。|  
|[CMFCRibbonBaseElement::SetParentMenu](../Topic/CMFCRibbonBaseElement::SetParentMenu.md)|设置功能区元素的父菜单容器。|  
|[CMFCRibbonBaseElement::SetParentRibbonBar](../Topic/CMFCRibbonBaseElement::SetParentRibbonBar.md)|设置功能区元素的父功能区栏。|  
|[CMFCRibbonBaseElement::SetRect](../Topic/CMFCRibbonBaseElement::SetRect.md)|设置维度他FOT显示功能区元素的矩形。|  
|[CMFCRibbonBaseElement::SetText](../Topic/CMFCRibbonBaseElement::SetText.md)|设置功能区元素的文本。|  
|[CMFCRibbonBaseElement::SetTextAlwaysOnRight](../Topic/CMFCRibbonBaseElement::SetTextAlwaysOnRight.md)|在右侧设置功能区元素的文本中显示。|  
|[CMFCRibbonBaseElement::SetToolTipText](../Topic/CMFCRibbonBaseElement::SetToolTipText.md)|设置功能区元素的工具提示文本。|  
|[CMFCRibbonBaseElement::SetVisible](../Topic/CMFCRibbonBaseElement::SetVisible.md)|设置功能区元素的可见性状态。|  
|[CMFCRibbonBaseElement::StretchHorizontally](../Topic/CMFCRibbonBaseElement::StretchHorizontally.md)|拉伸功能区元素的宽度。|  
|[CMFCRibbonBaseElement::StretchToWholeRow](../Topic/CMFCRibbonBaseElement::StretchToWholeRow.md)|更改功能区元素的公开敏感到指定的行高度。|  
|[CMFCRibbonBaseElement::UpdateTooltipInfo](../Topic/CMFCRibbonBaseElement::UpdateTooltipInfo.md)|使用功能区元素的命令，资源更新工具提示文本。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonBaseElement::OnProcessKey](../Topic/CMFCRibbonBaseElement::OnProcessKey.md)|调用由结构，当用户按一个热键。|  
|[CMFCRibbonBaseElement::OnSetFocus](../Topic/CMFCRibbonBaseElement::OnSetFocus.md)|调用由结构，当功能区元素接收或丢失输入焦点。|  
  
## 备注  
 `CMFCRibbonBaseElement` 选件类定义对所有功能区元素共有的包含命令ID、文本标签、工具提示文本、元素可以限定，的声明和状态的属性\(显示，按下，禁用，选中或拉）。  
  
 功能区元素的图像大小由 `RibbonImageType` 成员定义，可为下列值之一：  
  
-   `RibbonImageLarge`  
  
-   `RibbonImageSmall`  
  
 基于其大小，功能区元素显示一个小或大图像。  
  
## 示例  
 下面的示例在 `CMFCRibbonBaseElement` 选件类演示如何使用各种方法。  该示例演示如何从获取 `CMFCRibbonStatusBar` 选件类的一 `CMFCRibbonBaseElement` 对象，并设置功能区元素的说明，将文本，设置keytip，并将功能区元素的工具提示文本。  此代码段是 [绘制客户端示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#8](../../mfc/reference/codesnippet/CPP/cmfcribbonbaseelement-class_1.cpp)]  
[!code-cpp[NVC_MFC_DrawClient#9](../../mfc/reference/codesnippet/CPP/cmfcribbonbaseelement-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
## 要求  
 **标头:** afxbaseribbonelement.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)