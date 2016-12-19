---
title: "CMFCToolBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBar class"
ms.assetid: e7679c01-fb94-44c0-98c6-3af955292fb5
caps.latest.revision: 48
caps.handback.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCToolBar` 选件类类似于 [CToolBar Class](../../mfc/reference/ctoolbar-class.md)，但是，提供用户界面功能附加支持。  其中包括简单的工具栏、工具栏有快捷图像的，大图标、寻呼机按钮、锁定的工具栏、rebar控件、文本在图像下，背景图像和选项卡式工具栏。  `CMFCToolBar` 选件类还包含内置为工具栏的用户可自定义的支持，并菜单、拖放到工具栏和菜单之间，组合框按钮，编辑框按钮、颜色选取器和汇总按钮。  
  
## 语法  
  
```  
class CMFCToolBar : public CMFCBaseToolBar  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCToolBar::CMFCToolBar`|默认构造函数。|  
|`CMFCToolBar::~CMFCToolBar`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBar::AddBasicCommand](../Topic/CMFCToolBar::AddBasicCommand.md)|添加一个菜单命令添加到始终显示命令的列表，当用户打开菜单中。|  
|[CMFCToolBar::AddCommandUsage](../Topic/CMFCToolBar::AddCommandUsage.md)|由一个递增的方式与该特定命令的计数器。|  
|[CMFCToolBar::AddToolBarForImageCollection](../Topic/CMFCToolBar::AddToolBarForImageCollection.md)|从用户界面资源将图像添加到图像的集合在应用程序中。|  
|[CMFCToolBar::AdjustLayout](../Topic/CMFCToolBar::AdjustLayout.md)|计算工具栏的大小和位置。  （重写 [CBasePane::AdjustLayout](../Topic/CBasePane::AdjustLayout.md)）。|  
|[CMFCToolBar::AdjustSize](../Topic/CMFCToolBar::AdjustSize.md)|计算工具栏的大小。|  
|[CMFCToolBar::AllowChangeTextLabels](../Topic/CMFCToolBar::AllowChangeTextLabels.md)|指定文本标签是否可以显示在工具栏按钮的图像下。|  
|[CMFCToolBar::AreTextLabels](../Topic/CMFCToolBar::AreTextLabels.md)|指定在图像下面的文本标签是否在工具栏按钮当前显示。|  
|[CMFCToolBar::AutoGrayInactiveImages](../Topic/CMFCToolBar::AutoGrayInactiveImages.md)|启用或禁用非活动按钮图像的自动生成功能。|  
|[CMFCToolBar::ButtonToIndex](../Topic/CMFCToolBar::ButtonToIndex.md)|返回指定的 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md) 对象的索引此工具栏上的。|  
|[CMFCToolBar::CalcFixedLayout](../Topic/CMFCToolBar::CalcFixedLayout.md)|计算工具栏的水平大小。  （重写 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)。）|  
|[CMFCToolBar::CalcSize](../Topic/CMFCToolBar::CalcSize.md)|调用由框架作为布局计算过程的一部分。  （重写 [CPane::CalcSize](../Topic/CPane::CalcSize.md)。）|  
|[CMFCToolBar::CanHandleSiblings](../Topic/CMFCToolBar::CanHandleSiblings.md)|确定工具栏和同级是否在同一窗格中确定。|  
|[CMFCToolBar::CleanUpImages](../Topic/CMFCToolBar::CleanUpImages.md)|释放为工具栏图像分配的系统资源。|  
|[CMFCToolBar::CleanUpLockedImages](../Topic/CMFCToolBar::CleanUpLockedImages.md)|释放为锁定的工具栏图像分配的系统资源。|  
|[CMFCToolBar::CanBeClosed](../Topic/CMFCToolBar::CanBeClosed.md)|指定用户是否可以关闭工具栏。  （重写 [CBasePane::CanBeClosed](../Topic/CBasePane::CanBeClosed.md)。）|  
|[CMFCToolBar::CanBeRestored](../Topic/CMFCToolBar::CanBeRestored.md)|确定系统是否能还原工具栏到其原始状态在自定义项之后。|  
|[CMFCToolBar::CanFocus](../Topic/CMFCToolBar::CanFocus.md)|指定窗格是否可以接收焦点。  （重写 [CBasePane::CanFocus](../Topic/CBasePane::CanFocus.md)。）|  
|[CMFCToolBar::CanHandleSiblings](../Topic/CMFCToolBar::CanHandleSiblings.md)|确定工具栏和同级是否在同一窗格中确定。|  
|[CMFCToolBar::CommandToIndex](../Topic/CMFCToolBar::CommandToIndex.md)|返回按钮的索引工具栏上的具有指定的命令ID的.|  
|[CMFCToolBar::Create](../Topic/CMFCToolBar::Create.md)|创建一个 `CMFCToolBar` 对象。|  
|[CMFCToolBar::CreateEx](../Topic/CMFCToolBar::CreateEx.md)|创建使用附加样式的选项卡中 `CMFCToolBar` 对象，如大图标。|  
|[CMFCToolBar::Deactivate](../Topic/CMFCToolBar::Deactivate.md)|停用工具栏。|  
|[CMFCToolBar::EnableCustomizeButton](../Topic/CMFCToolBar::EnableCustomizeButton.md)|启用或禁用显示在工具栏的末尾的 **添加或移除按钮**按钮。|  
|[CMFCToolBar::EnableDocking](../Topic/CMFCToolBar::EnableDocking.md)|启用窗格的停靠到主框架。  （重写 [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md)。）|  
|[CMFCToolBar::EnableLargeIcons](../Topic/CMFCToolBar::EnableLargeIcons.md)|启用或禁用了工具栏按钮的大图标。|  
|[CMFCToolBar::EnableQuickCustomization](../Topic/CMFCToolBar::EnableQuickCustomization.md)|启用或禁用工具栏的快速自定义项，以便用户可以按 **Alt** 键和按钮拖动到新位置。|  
|[CMFCToolBar::EnableReflections](../Topic/CMFCToolBar::EnableReflections.md)|启用或禁用命令反射。|  
|[CMFCToolBar::EnableTextLabels](../Topic/CMFCToolBar::EnableTextLabels.md)|启用或禁用文本标签在工具栏按钮图像下。|  
|[CMFCToolBar::FromHandlePermanent](../Topic/CMFCToolBar::FromHandlePermanent.md)|检索指向包含特定窗口句柄的 `CMFCToolBar` 对象。|  
|[CMFCToolBar::GetAllButtons](../Topic/CMFCToolBar::GetAllButtons.md)|返回只读列表工具栏中的按钮。|  
|[CMFCToolBar::GetAllToolbars](../Topic/CMFCToolBar::GetAllToolbars.md)|返回只读列表在应用程序的所有工具栏。|  
|[CMFCToolBar::GetBasicCommands](../Topic/CMFCToolBar::GetBasicCommands.md)|返回只读在应用程序定义列表的基本命令。|  
|[CMFCToolBar::GetButton](../Topic/CMFCToolBar::GetButton.md)|返回指向具有指定的工具栏按钮索引的 `CMFCToolBarButton` 对象。|  
|[CMFCToolBar::GetButtonInfo](../Topic/CMFCToolBar::GetButtonInfo.md)|返回按钮的命令ID、样式和图像索引在指定的索引。|  
|[CMFCToolBar::GetButtonSize](../Topic/CMFCToolBar::GetButtonSize.md)|返回维度工具栏上的每个按钮。|  
|[CMFCToolBar::GetButtonStyle](../Topic/CMFCToolBar::GetButtonStyle.md)|返回位于指定索引处的工具栏按钮的当前样式。|  
|[CMFCToolBar::GetButtonText](../Topic/CMFCToolBar::GetButtonText.md)|返回具有指定的索引按钮的文本标签。|  
|[CMFCToolBar::GetColdImages](../Topic/CMFCToolBar::GetColdImages.md)|返回指向冷工具栏按钮图像的集合在应用程序中。|  
|[CMFCToolBar::GetColumnWidth](../Topic/CMFCToolBar::GetColumnWidth.md)|返回工具栏按钮的宽度。|  
|[CMFCToolBar::GetCommandButtons](../Topic/CMFCToolBar::GetCommandButtons.md)|返回具有从所有工具栏中指定的命令ID在应用程序按钮的列表。|  
|[CMFCToolBar::GetCount](../Topic/CMFCToolBar::GetCount.md)|返回按钮和分隔符数在工具栏。|  
|[CMFCToolBar::GetCustomizeButton](../Topic/CMFCToolBar::GetCustomizeButton.md)|检索指向与工具栏的 `CMFCCustomizeButton` 对象。|  
|[CMFCToolBar::GetDefaultImage](../Topic/CMFCToolBar::GetDefaultImage.md)|返回默认图像的索引一个工具栏按钮的具有指定的命令ID的.|  
|[CMFCToolBar::GetDisabledImages](../Topic/CMFCToolBar::GetDisabledImages.md)|返回指向的指针为禁用工具栏按钮使用应用程序图像的集合。|  
|[CMFCToolBar::GetDisabledMenuImages](../Topic/CMFCToolBar::GetDisabledMenuImages.md)|返回指向的指针为禁用菜单按钮使用应用程序图像的集合。|  
|[CMFCToolBar::GetDroppedDownMenu](../Topic/CMFCToolBar::GetDroppedDownMenu.md)|检索指向当前显示其子菜单的菜单按钮对象。|  
|[CMFCToolBar::GetGrayDisabledButtons](../Topic/CMFCToolBar::GetGrayDisabledButtons.md)|指定禁用按钮的图像是否是普通按钮图像的灰显的版本或将禁用按钮图像的集合。|  
|[CMFCToolBar::GetHighlightedButton](../Topic/CMFCToolBar::GetHighlightedButton.md)|返回指向当前显示的工具栏按钮。|  
|[CMFCToolBar::GetHotBorder](../Topic/CMFCToolBar::GetHotBorder.md)|确定工具栏按钮是否快捷跟踪。|  
|[CMFCToolBar::GetHotTextColor](../Topic/CMFCToolBar::GetHotTextColor.md)|返回所示的工具栏按钮的文本颜色。|  
|[CMFCToolBar::GetHwndLastFocus](../Topic/CMFCToolBar::GetHwndLastFocus.md)|将处理返回给具有输入焦点的窗口，请在工具栏上。|  
|[CMFCToolBar::GetIgnoreSetText](../Topic/CMFCToolBar::GetIgnoreSetText.md)|指定是否调用将按钮标签被忽略。|  
|[CMFCToolBar::GetImageSize](../Topic/CMFCToolBar::GetImageSize.md)|返回工具栏按钮图像的当前范围。|  
|[CMFCToolBar::GetImages](../Topic/CMFCToolBar::GetImages.md)|返回指向在应用程序的默认按钮图像的集合。|  
|[CMFCToolBar::GetImagesOffset](../Topic/CMFCToolBar::GetImagesOffset.md)|返回用于的索引偏移量查找此工具栏的工具栏按钮图像在全局列表工具栏按钮图像。|  
|[CMFCToolBar::GetInvalidateItemRect](../Topic/CMFCToolBar::GetInvalidateItemRect.md)|检索必须为给定索引的按钮重绘工作区的区域。|  
|[CMFCToolBar::GetItemID](../Topic/CMFCToolBar::GetItemID.md)|返回工具栏按钮的命令ID在指定的索引。|  
|[CMFCToolBar::GetItemRect](../Topic/CMFCToolBar::GetItemRect.md)|返回按钮的边框在指定的索引。|  
|[CMFCToolBar::GetLargeColdImages](../Topic/CMFCToolBar::GetLargeColdImages.md)|返回指向用冷工具栏按钮图像的集合在应用程序中。|  
|[CMFCToolBar::GetLargeDisabledImages](../Topic/CMFCToolBar::GetLargeDisabledImages.md)|返回指向用禁用工具栏按钮图像的集合在应用程序中。|  
|[CMFCToolBar::GetLargeImages](../Topic/CMFCToolBar::GetLargeImages.md)|返回指向用工具栏按钮图像的集合在应用程序中。|  
|[CMFCToolBar::GetLockedColdImages](../Topic/CMFCToolBar::GetLockedColdImages.md)|返回指向锁定的冷图像的集合工具栏上的。|  
|[CMFCToolBar::GetLockedDisabledImages](../Topic/CMFCToolBar::GetLockedDisabledImages.md)|返回指向锁定的禁用图像的集合工具栏上的。|  
|[CMFCToolBar::GetLockedImages](../Topic/CMFCToolBar::GetLockedImages.md)|返回指向锁定的按钮图像的集合工具栏上的。|  
|[CMFCToolBar::GetLockedImageSize](../Topic/CMFCToolBar::GetLockedImageSize.md)|返回锁定的工具栏图像的默认大小。|  
|[CMFCToolBar::GetLockedMenuImages](../Topic/CMFCToolBar::GetLockedMenuImages.md)|返回指向锁定的工具栏菜单图像的集合工具栏上的。|  
|[CMFCToolBar::GetMenuButtonSize](../Topic/CMFCToolBar::GetMenuButtonSize.md)|返回菜单按钮的大小在应用程序中。|  
|[CMFCToolBar::GetMenuImageSize](../Topic/CMFCToolBar::GetMenuImageSize.md)|返回菜单在应用程序中按钮的图像的大小。|  
|[CMFCToolBar::GetMenuImages](../Topic/CMFCToolBar::GetMenuImages.md)|返回指向菜单在应用程序的按钮图像的集合。|  
|[CMFCToolBar::GetOrigButtons](../Topic/CMFCToolBar::GetOrigButtons.md)|检索工具栏的非自定义按钮的集合。|  
|[CMFCToolBar::GetOrigResetButtons](../Topic/CMFCToolBar::GetOrigResetButtons.md)|检索工具栏的非自定义的重置按钮的集合。|  
|[CMFCToolBar::GetResourceID](../Topic/CMFCToolBar::GetResourceID.md)|检索工具栏的资源ID。|  
|[CMFCToolBar::GetRouteCommandsViaFrame](../Topic/CMFCToolBar::GetRouteCommandsViaFrame.md)|确定哪个对象、父级框架或所有者，将命令发送到工具栏。|  
|[CMFCToolBar::GetRowHeight](../Topic/CMFCToolBar::GetRowHeight.md)|返回高度工具栏按钮。|  
|[CMFCToolBar::GetShowTooltips](../Topic/CMFCToolBar::GetShowTooltips.md)|指定工具提示是否为工具栏按钮显示。|  
|[CMFCToolBar::GetSiblingToolBar](../Topic/CMFCToolBar::GetSiblingToolBar.md)|检索工具栏的同级节点。|  
|[CMFCToolBar::GetUserImages](../Topic/CMFCToolBar::GetUserImages.md)|返回指向用户定义的工具栏按钮图像的集合在应用程序中。|  
|[CMFCToolBar::HitTest](../Topic/CMFCToolBar::HitTest.md)|返回驻留在指定的位置工具栏按钮的索引。|  
|[CMFCToolBar::InsertButton](../Topic/CMFCToolBar::InsertButton.md)|插入按钮添加到工具栏中的。|  
|[CMFCToolBar::InsertSeparator](../Topic/CMFCToolBar::InsertSeparator.md)|插入分隔符到工具栏中的。|  
|[CMFCToolBar::InvalidateButton](../Topic/CMFCToolBar::InvalidateButton.md)|无效存在中提供的索引工具栏按钮的工作区。|  
|[CMFCToolBar::IsAddRemoveQuickCustomize](../Topic/CMFCToolBar::IsAddRemoveQuickCustomize.md)|确定用户使用 **自定义** 菜单选项，则可以添加或移除工具栏按钮。|  
|[CMFCToolBar::IsAltCustomizeMode](../Topic/CMFCToolBar::IsAltCustomizeMode.md)|指定 *快速自定义* 是否在拖动按钮。|  
|[CMFCToolBar::IsAutoGrayInactiveImages](../Topic/CMFCToolBar::IsAutoGrayInactiveImages.md)|指定非活动\(未显示\)按钮图像的自动生成是否启用。|  
|[CMFCToolBar::IsBasicCommand](../Topic/CMFCToolBar::IsBasicCommand.md)|确定命令是否可以在基本命令列表。|  
|[CMFCToolBar::IsButtonExtraSizeAvailable](../Topic/CMFCToolBar::IsButtonExtraSizeAvailable.md)|定位工具栏是否可以显示扩展的边框的按钮。|  
|[CMFCToolBar::IsButtonHighlighted](../Topic/CMFCToolBar::IsButtonHighlighted.md)|确定工具栏上的按钮是否显示。|  
|[CMFCToolBar::IsCommandPermitted](../Topic/CMFCToolBar::IsCommandPermitted.md)|确定是否允许命令。|  
|[CMFCToolBar::IsCommandRarelyUsed](../Topic/CMFCToolBar::IsCommandRarelyUsed.md)|确定是否很少使用命令\(请参见 [CMFCToolBar::SetCommandUsageOptions](../Topic/CMFCToolBar::SetCommandUsageOptions.md)）。|  
|[CMFCToolBar::IsCustomizeMode](../Topic/CMFCToolBar::IsCustomizeMode.md)|指定工具栏结构是否在自定义模式。|  
|[CMFCToolBar::IsDragButton](../Topic/CMFCToolBar::IsDragButton.md)|确定工具栏按钮是否已拖动。|  
|[CMFCToolBar::IsExistCustomizeButton](../Topic/CMFCToolBar::IsExistCustomizeButton.md)|定位工具栏是否包含 **自定义** 按钮。|  
|[CMFCToolBar::IsFloating](../Topic/CMFCToolBar::IsFloating.md)|确定是否浮动工具栏。|  
|[CMFCToolBar::IsLargeIcons](../Topic/CMFCToolBar::IsLargeIcons.md)|指定在应用程序的工具栏当前是否显示大图标。|  
|[CMFCToolBar::IsLastCommandFromButton](../Topic/CMFCToolBar::IsLastCommandFromButton.md)|确定该最近执行的命令是否从指定的工具栏按钮发送了。|  
|[CMFCToolBar::IsLocked](../Topic/CMFCToolBar::IsLocked.md)|定位工具栏是否锁定。|  
|[CMFCToolBar::IsOneRowWithSibling](../Topic/CMFCToolBar::IsOneRowWithSibling.md)|确定工具栏和同级工具栏是否在同一行确定。|  
|[CMFCToolBar::IsUserDefined](../Topic/CMFCToolBar::IsUserDefined.md)|指定工具栏是否是用户定义的。|  
|[CMFCToolBar::LoadBitmap](../Topic/CMFCToolBar::LoadBitmap.md)|从应用程序资源加载工具栏图像。|  
|[CMFCToolBar::LoadBitmapEx](../Topic/CMFCToolBar::LoadBitmapEx.md)|从应用程序资源加载工具栏图像。  包括大图像。|  
|[CMFCToolBar::LoadParameters](../Topic/CMFCToolBar::LoadParameters.md)|从Windows注册表加载全局工具栏选项。|  
|[CMFCToolBar::LoadState](../Topic/CMFCToolBar::LoadState.md)|从Windows注册表加载toolbar状态信息。  （重写 [CPane::LoadState](../Topic/CPane::LoadState.md)。）|  
|[CMFCToolBar::LoadToolBar](../Topic/CMFCToolBar::LoadToolBar.md)|从应用程序资源加载工具栏。|  
|[CMFCToolBar::LoadToolBarEx](../Topic/CMFCToolBar::LoadToolBarEx.md)|从应用程序资源加载工具栏使用 `CMFCToolBarInfo` 帮助器选件您的应用程序用图像。|  
|[CMFCToolBar::OnChangeHot](../Topic/CMFCToolBar::OnChangeHot.md)|调用由结构，当用户选择工具栏上的按钮。|  
|[CMFCToolBar::OnFillBackground](../Topic/CMFCToolBar::OnFillBackground.md)|调用从 [CBasePane::DoPaint](../Topic/CBasePane::DoPaint.md) 的framework加载工具栏背景。|  
|[CMFCToolBar::OnReset](../Topic/CMFCToolBar::OnReset.md)|工具栏还原到其原始状态。|  
|[CMFCToolBar::OnSetAccData](../Topic/CMFCToolBar::OnSetAccData.md)|（重写 [CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md)。）|  
|[CMFCToolBar::OnSetDefaultButtonText](../Topic/CMFCToolBar::OnSetDefaultButtonText.md)|还原工具栏按钮的文本设置其默认状态。|  
|`CMFCToolBar::OnUpdateCmdUI`|内部使用。|  
|[CMFCToolBar::RemoveAllButtons](../Topic/CMFCToolBar::RemoveAllButtons.md)|从工具栏中移除所有按钮。|  
|[CMFCToolBar::RemoveButton](../Topic/CMFCToolBar::RemoveButton.md)|移除按钮具有指定的索引从工具栏。|  
|[CMFCToolBar::RemoveStateFromRegistry](../Topic/CMFCToolBar::RemoveStateFromRegistry.md)|从Windows注册表删除工具栏的状态信息。|  
|[CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)|用另一个工具栏按钮替换的工具栏按钮。|  
|[CMFCToolBar::ResetAll](../Topic/CMFCToolBar::ResetAll.md)|还原所有工具栏到其原始状态。|  
|[CMFCToolBar::ResetAllImages](../Topic/CMFCToolBar::ResetAllImages.md)|清除在应用程序的所有工具栏图像集合。|  
|[CMFCToolBar::RestoreOriginalState](../Topic/CMFCToolBar::RestoreOriginalState.md)|还原工具栏的原始状态。|  
|[CMFCToolBar::SaveState](../Topic/CMFCToolBar::SaveState.md)|保存工具栏的状态信息在Windows注册表。  （重写 [CPane::SaveState](../Topic/CPane::SaveState.md)。）|  
|`CMFCToolBar::Serialize`|（重写 `CBasePane::Serialize`。）|  
|[CMFCToolBar::SetBasicCommands](../Topic/CMFCToolBar::SetBasicCommands.md)|设置始终显示命令的列表，当用户打开菜单中。|  
|[CMFCToolBar::SetButtonInfo](../Topic/CMFCToolBar::SetButtonInfo.md)|设置工具栏按钮的命令ID、样式和图像ID。|  
|[CMFCToolBar::SetButtonStyle](../Topic/CMFCToolBar::SetButtonStyle.md)|设置工具栏按钮的样式在给定索引。|  
|[CMFCToolBar::SetButtonText](../Topic/CMFCToolBar::SetButtonText.md)|设置工具栏按钮的文本标签。|  
|[CMFCToolBar::SetButtons](../Topic/CMFCToolBar::SetButtons.md)|设置工具栏上的按钮。|  
|[CMFCToolBar::SetCommandUsageOptions](../Topic/CMFCToolBar::SetCommandUsageOptions.md)|在很少使用的命令没有出现在应用程序的菜单，指定。|  
|[CMFCToolBar::SetCustomizeMode](../Topic/CMFCToolBar::SetCustomizeMode.md)|启动或禁用所有工具栏的自定义模式在应用程序。|  
|[CMFCToolBar::SetGrayDisabledButtons](../Topic/CMFCToolBar::SetGrayDisabledButtons.md)|指定在工具栏上禁用按钮是否为灰色，或者禁用图像为禁用的按钮使用。|  
|[CMFCToolBar::SetHeight](../Topic/CMFCToolBar::SetHeight.md)|设置工具栏按钮的高度。|  
|[CMFCToolBar::SetHotBorder](../Topic/CMFCToolBar::SetHotBorder.md)|指定工具栏按钮是否快捷跟踪。|  
|[CMFCToolBar::SetHotTextColor](../Topic/CMFCToolBar::SetHotTextColor.md)|设置快捷工具栏按钮的文本颜色。|  
|[CMFCToolBar::SetLargeIcons](../Topic/CMFCToolBar::SetLargeIcons.md)|指定工具栏按钮是否显示大图标。|  
|[CMFCToolBar::SetLockedSizes](../Topic/CMFCToolBar::SetLockedSizes.md)|设置锁定的按钮的大小与工具栏上的锁定的图像。|  
|[CMFCToolBar::SetMenuSizes](../Topic/CMFCToolBar::SetMenuSizes.md)|设置工具栏菜单按钮及其图像的大小。|  
|[CMFCToolBar::SetNonPermittedCommands](../Topic/CMFCToolBar::SetNonPermittedCommands.md)|设置用户无法执行命令的列表。|  
|[CMFCToolBar::SetOneRowWithSibling](../Topic/CMFCToolBar::SetOneRowWithSibling.md)|在同一行上定位工具栏及其同级。|  
|[CMFCToolBar::SetPermament](../Topic/CMFCToolBar::SetPermament.md)|指定用户是否可以关闭工具栏。|  
|[CMFCToolBar::SetRouteCommandsViaFrame](../Topic/CMFCToolBar::SetRouteCommandsViaFrame.md)|指定父框架或所有者是否将命令发送到工具栏。|  
|[CMFCToolBar::SetShowTooltips](../Topic/CMFCToolBar::SetShowTooltips.md)|指定框架是否显示工具提示。|  
|[CMFCToolBar::SetSiblingToolBar](../Topic/CMFCToolBar::SetSiblingToolBar.md)|指定工具栏的同级节点。|  
|[CMFCToolBar::SetSizes](../Topic/CMFCToolBar::SetSizes.md)|在所有工具栏指定按钮的大小和图像。|  
|[CMFCToolBar::SetToolBarBtnText](../Topic/CMFCToolBar::SetToolBarBtnText.md)|在指定工具栏按钮的属性。|  
|[CMFCToolBar::SetTwoRowsWithSibling](../Topic/CMFCToolBar::SetTwoRowsWithSibling.md)|在单独的行上定位工具栏及其同级。|  
|[CMFCToolBar::SetUserImages](../Topic/CMFCToolBar::SetUserImages.md)|设置用户定义的图像的集合在应用程序中。|  
|[CMFCToolBar::StretchPane](../Topic/CMFCToolBar::StretchPane.md)|拉伸水平或垂直工具栏。（重写 [CBasePane::StretchPane](../Topic/CBasePane::StretchPane.md)。）|  
|[CMFCToolBar::TranslateChar](../Topic/CMFCToolBar::TranslateChar.md)|因此，如果指定的键代码对应于有效的键盘快捷键，执行一个按钮命令。|  
|[CMFCToolBar::UpdateButton](../Topic/CMFCToolBar::UpdateButton.md)|更新指定的按钮的状态。|  
|[CMFCToolBar::WrapToolBar](../Topic/CMFCToolBar::WrapToolBar.md)|重新定位在给定维中的工具栏按钮。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBar::AllowShowOnList](../Topic/CMFCToolBar::AllowShowOnList.md)|定位工具栏是否在 **自定义** 对话框的 **工具栏** 窗格的列表中显示。|  
|[CMFCToolBar::CalcMaxButtonHeight](../Topic/CMFCToolBar::CalcMaxButtonHeight.md)|计算一个按钮的最大高度工具栏上的。|  
|[CMFCToolBar::DoPaint](../Topic/CMFCToolBar::DoPaint.md)|重新绘制一个工具栏。|  
|[CMFCToolBar::DrawButton](../Topic/CMFCToolBar::DrawButton.md)|重新绘制一个工具栏按钮。|  
|[CMFCToolBar::DrawSeparator](../Topic/CMFCToolBar::DrawSeparator.md)|重新绘制在工具栏的分隔符。|  
|[CMFCToolBar::OnUserToolTip](../Topic/CMFCToolBar::OnUserToolTip.md)|调用由结构，当按钮的工具提示将显示。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBar::m\_bDontScaleImages](../Topic/CMFCToolBar::m_bDontScaleImages.md)|在高DPI模式指定是否调用工具栏图像。|  
|[CMFCToolBar::m\_dblLargeImageRatio](../Topic/CMFCToolBar::m_dblLargeImageRatio.md)|指定在尺寸\(高度或宽度\)大图像和维度的比例常规映像之间。|  
  
## 备注  
 若要将 `CMFCToolBar` 对象到应用程序中，请执行以下步骤:  
  
1.  添加一 `CMFCToolBar` 对象向主框架窗口。  
  
2.  在处理主框架窗口时 `WM_CREATE` 消息，请调用 [CMFCToolBar::Create](../Topic/CMFCToolBar::Create.md) 或 [CMFCToolBar::CreateEx](../Topic/CMFCToolBar::CreateEx.md) 创建工具栏并指定其样式。  
  
3.  调用 [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md) 指定停靠样式。  
  
 使用 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)，插入一个特定按钮，如组合框或下拉式工具栏，保留一个虚拟的按钮在父资源，并替换虚假的按钮在运行时。  有关更多信息，请参见 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。  
  
 `CMFCToolBar` 是MFC库选件类的 [CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md)、 [CMFCPopupMenuBar 类](../../mfc/reference/cmfcpopupmenubar-class.md)和 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)基类。  
  
## 示例  
 下面的示例在 `CMFCToolBar` 选件类演示如何使用各种方法。  此示例演示如何设置工具栏的windows标签的文本，设置边框，设置窗格的样式，从而显示在工具栏的末尾的 **添加或移除按钮** 按钮。  此代码段是 [pocket IE演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_IEDemo#6](../../mfc/reference/codesnippet/CPP/cmfctoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo#8](../../mfc/reference/codesnippet/CPP/cmfctoolbar-class_2.cpp)]  
  
## 要求  
 **标头:** afxtoolbar.h  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCMenuBar Class](../../mfc/reference/cmfcmenubar-class.md)   
 [CMFCPopupMenuBar 类](../../mfc/reference/cmfcpopupmenubar-class.md)   
 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)