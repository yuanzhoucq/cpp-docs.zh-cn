---
title: "CMFCPopupMenu Class | Microsoft Docs"
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
  - "CMFCPopupMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPopupMenu class"
ms.assetid: 9555dca1-8c9c-44c9-af72-0659ddad128e
caps.latest.revision: 40
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPopupMenu Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现Windows弹出菜单功能和通过添加功能扩展它例如拖曳菜单和工具提示。  
  
## 语法  
  
```  
class CMFCPopupMenu : public CMiniFrameWnd  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCPopupMenu::CMFCPopupMenu](../Topic/CMFCPopupMenu::CMFCPopupMenu.md)|构造 `CMFCPopupMenu` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCPopupMenu::ActivatePopupMenu](../Topic/CMFCPopupMenu::ActivatePopupMenu.md)||  
|[CMFCPopupMenu::AlwaysShowEmptyToolsEntry](../Topic/CMFCPopupMenu::AlwaysShowEmptyToolsEntry.md)|设置弹出菜单是否启用显示用户定义的工具的空项。|  
|[CMFCPopupMenu::AreAllCommandsShown](../Topic/CMFCPopupMenu::AreAllCommandsShown.md)||  
|[CMFCPopupMenu::CheckArea](../Topic/CMFCPopupMenu::CheckArea.md)|确定一个点的位置相对于弹出菜单。|  
|[CMFCPopupMenu::CloseMenu](../Topic/CMFCPopupMenu::CloseMenu.md)||  
|[CMFCPopupMenu::Create](../Topic/CMFCPopupMenu::Create.md)|创建一个弹出菜单并将它附加到 `CMFCPopupMenu` 对象。|  
|[CMFCPopupMenu::DefaultMouseClickOnClose](../Topic/CMFCPopupMenu::DefaultMouseClickOnClose.md)||  
|[CMFCPopupMenu::EnableMenuLogo](../Topic/CMFCPopupMenu::EnableMenuLogo.md)|初始化弹出菜单的徽标。|  
|[CMFCPopupMenu::EnableMenuSound](../Topic/CMFCPopupMenu::EnableMenuSound.md)|启用菜单声音。|  
|[CMFCPopupMenu::EnableResize](../Topic/CMFCPopupMenu::EnableResize.md)||  
|[CMFCPopupMenu::EnableScrolling](../Topic/CMFCPopupMenu::EnableScrolling.md)||  
|[CMFCPopupMenu::EnableVertResize](../Topic/CMFCPopupMenu::EnableVertResize.md)||  
|[CMFCPopupMenu::FindSubItemByCommand](../Topic/CMFCPopupMenu::FindSubItemByCommand.md)||  
|[CMFCPopupMenu::GetActiveMenu](../Topic/CMFCPopupMenu::GetActiveMenu.md)|返回当前活动的菜单。|  
|[CMFCPopupMenu::GetAnimationSpeed](../Topic/CMFCPopupMenu::GetAnimationSpeed.md)|返回弹出菜单的动画速度。|  
|[CMFCPopupMenu::GetAnimationType](../Topic/CMFCPopupMenu::GetAnimationType.md)|返回弹出菜单动画的当前类型。|  
|[CMFCPopupMenu::GetDropDirection](../Topic/CMFCPopupMenu::GetDropDirection.md)||  
|[CMFCPopupMenu::GetForceMenuFocus](../Topic/CMFCPopupMenu::GetForceMenuFocus.md)|指示焦点是否返回与菜单栏，当弹出菜单显示。|  
|[CMFCPopupMenu::GetForceShadow](../Topic/CMFCPopupMenu::GetForceShadow.md)||  
|[CMFCPopupMenu::GetHMenu](../Topic/CMFCPopupMenu::GetHMenu.md)|返回处理附加菜单资源。|  
|[CMFCPopupMenu::GetMenuBar](../Topic/CMFCPopupMenu::GetMenuBar.md)|返回 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) 嵌入在弹出菜单中。|  
|[CMFCPopupMenu::GetMenuItem](../Topic/CMFCPopupMenu::GetMenuItem.md)|返回指向菜单项位于指定索引处。|  
|[CMFCPopupMenu::GetMenuItemCount](../Topic/CMFCPopupMenu::GetMenuItemCount.md)|返回的项数。一个弹出菜单中的。|  
|[CMFCPopupMenu::GetMessageWnd](../Topic/CMFCPopupMenu::GetMessageWnd.md)|返回指向该结构将弹出菜单消息的窗口。|  
|[CMFCPopupMenu::GetParentArea](../Topic/CMFCPopupMenu::GetParentArea.md)||  
|[CMFCPopupMenu::GetParentButton](../Topic/CMFCPopupMenu::GetParentButton.md)|返回指向父工具栏按钮。|  
|[CMFCPopupMenu::GetParentPopupMenu](../Topic/CMFCPopupMenu::GetParentPopupMenu.md)|返回指向父弹出菜单。|  
|[CMFCPopupMenu::GetParentRibbonElement](../Topic/CMFCPopupMenu::GetParentRibbonElement.md)||  
|[CMFCPopupMenu::GetParentToolBar](../Topic/CMFCPopupMenu::GetParentToolBar.md)|返回指向父工具栏。|  
|[CMFCPopupMenu::GetQuickCustomizeType](../Topic/CMFCPopupMenu::GetQuickCustomizeType.md)||  
|[CMFCPopupMenu::GetSelItem](../Topic/CMFCPopupMenu::GetSelItem.md)|返回指向当前选定的菜单命令。|  
|[CMFCPopupMenu::HasBeenResized](../Topic/CMFCPopupMenu::HasBeenResized.md)||  
|[CMFCPopupMenu::HideRarelyUsedCommands](../Topic/CMFCPopupMenu::HideRarelyUsedCommands.md)|指示弹出菜单是否可以隐藏很少使用的命令。|  
|[CMFCPopupMenu::InCommand](../Topic/CMFCPopupMenu::InCommand.md)||  
|[CMFCPopupMenu::InsertItem](../Topic/CMFCPopupMenu::InsertItem.md)|插入新项添加到指定的位置的弹出菜单中。|  
|[CMFCPopupMenu::InsertSeparator](../Topic/CMFCPopupMenu::InsertSeparator.md)|插入分隔符到指定位置的弹出菜单中。|  
|[CMFCPopupMenu::IsAlwaysClose](../Topic/CMFCPopupMenu::IsAlwaysClose.md)||  
|[CMFCPopupMenu::IsAlwaysShowEmptyToolsEntry](../Topic/CMFCPopupMenu::IsAlwaysShowEmptyToolsEntry.md)||  
|[CMFCPopupMenu::IsCustomizePane](../Topic/CMFCPopupMenu::IsCustomizePane.md)|指示弹出菜单是用作 **QuickCustomizePane**。|  
|[CMFCPopupMenu::IsEscClose](../Topic/CMFCPopupMenu::IsEscClose.md)||  
|[CMFCPopupMenu::IsIdle](../Topic/CMFCPopupMenu::IsIdle.md)|指示弹出菜单当前是否处于空闲状态。|  
|[CMFCPopupMenu::IsMenuSound](../Topic/CMFCPopupMenu::IsMenuSound.md)||  
|[CMFCPopupMenu::IsQuickCustomize](../Topic/CMFCPopupMenu::IsQuickCustomize.md)|确定关联的 [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md) 是否在QuickCustomize模式。|  
|[CMFCPopupMenu::IsResizeble](../Topic/CMFCPopupMenu::IsResizeble.md)||  
|[CMFCPopupMenu::IsRightAlign](../Topic/CMFCPopupMenu::IsRightAlign.md)|指示菜单是否是右对齐或左对齐。|  
|[CMFCPopupMenu::IsScrollable](../Topic/CMFCPopupMenu::IsScrollable.md)||  
|[CMFCPopupMenu::IsSendMenuSelectMsg](../Topic/CMFCPopupMenu::IsSendMenuSelectMsg.md)|指示框架是否通知父帧，当用户选择一个命令从弹出菜单。|  
|[CMFCPopupMenu::IsShown](../Topic/CMFCPopupMenu::IsShown.md)|指示弹出菜单当前是否可见。|  
|[CMFCPopupMenu::MoveTo](../Topic/CMFCPopupMenu::MoveTo.md)||  
|[CMFCPopupMenu::OnCmdMsg](../Topic/CMFCPopupMenu::OnCmdMsg.md)|（重写 `CFrameWnd::OnCmdMsg`。）|  
|[CMFCPopupMenu::PostCommand](../Topic/CMFCPopupMenu::PostCommand.md)||  
|[CMFCPopupMenu::PreTranslateMessage](../Topic/CMFCPopupMenu::PreTranslateMessage.md)|（重写 `CFrameWnd::PreTranslateMessage`。）|  
|[CMFCPopupMenu::RecalcLayout](../Topic/CMFCPopupMenu::RecalcLayout.md)|调用由结构，当标准控件条切换来打开或关闭，或者当框架窗口调整大小。  （重写 [CFrameWnd::RecalcLayout](../Topic/CFrameWnd::RecalcLayout.md)。）|  
|[CMFCPopupMenu::RemoveAllItems](../Topic/CMFCPopupMenu::RemoveAllItems.md)|清除弹出菜单中的所有项目。|  
|[CMFCPopupMenu::RemoveItem](../Topic/CMFCPopupMenu::RemoveItem.md)|从弹出菜单中移除指定的项目。|  
|[CMFCPopupMenu::SaveState](../Topic/CMFCPopupMenu::SaveState.md)||  
|[CMFCPopupMenu::SetAnimationSpeed](../Topic/CMFCPopupMenu::SetAnimationSpeed.md)|设置弹出菜单的动画速度。|  
|[CMFCPopupMenu::SetAnimationType](../Topic/CMFCPopupMenu::SetAnimationType.md)|设置弹出菜单的动画类型。|  
|[CMFCPopupMenu::SetAutoDestroy](../Topic/CMFCPopupMenu::SetAutoDestroy.md)||  
|[CMFCPopupMenu::SetDefaultItem](../Topic/CMFCPopupMenu::SetDefaultItem.md)|设置弹出菜单的默认命令。|  
|[CMFCPopupMenu::SetForceMenuFocus](../Topic/CMFCPopupMenu::SetForceMenuFocus.md)|在弹出菜单显示时，强制输入焦点返回到菜单栏。|  
|[CMFCPopupMenu::SetForceShadow](../Topic/CMFCPopupMenu::SetForceShadow.md)|在弹出菜单在主框架时，会强制该结构绘制菜单阴影效果。|  
|[CMFCPopupMenu::SetMaxWidth](../Topic/CMFCPopupMenu::SetMaxWidth.md)|设置弹出菜单的最大宽度。|  
|[CMFCPopupMenu::SetMessageWnd](../Topic/CMFCPopupMenu::SetMessageWnd.md)||  
|[CMFCPopupMenu::SetParentRibbonElement](../Topic/CMFCPopupMenu::SetParentRibbonElement.md)||  
|[CMFCPopupMenu::SetQuickCustomizeType](../Topic/CMFCPopupMenu::SetQuickCustomizeType.md)||  
|[CMFCPopupMenu::SetQuickMode](../Topic/CMFCPopupMenu::SetQuickMode.md)||  
|[CMFCPopupMenu::SetRightAlign](../Topic/CMFCPopupMenu::SetRightAlign.md)|设置弹出菜单的菜单对齐。|  
|[CMFCPopupMenu::SetSendMenuSelectMsg](../Topic/CMFCPopupMenu::SetSendMenuSelectMsg.md)|设置该标志来控制弹出菜单是否通知它的父框架，当用户选择一个命令时。|  
|[CMFCPopupMenu::ShowAllCommands](../Topic/CMFCPopupMenu::ShowAllCommands.md)|强制弹出菜单显示所有命令。|  
|[CMFCPopupMenu::TriggerResize](../Topic/CMFCPopupMenu::TriggerResize.md)||  
|[CMFCPopupMenu::UpdateAllShadows](../Topic/CMFCPopupMenu::UpdateAllShadows.md)|更新所有已打开的弹出菜单的阴影。|  
|[CMFCPopupMenu::UpdateShadow](../Topic/CMFCPopupMenu::UpdateShadow.md)|更新弹出菜单的阴影。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCPopupMenu::CreateTearOffBar](../Topic/CMFCPopupMenu::CreateTearOffBar.md)||  
|[CMFCPopupMenu::OnChangeHot](../Topic/CMFCPopupMenu::OnChangeHot.md)||  
|[CMFCPopupMenu::OnChooseItem](../Topic/CMFCPopupMenu::OnChooseItem.md)||  
  
### 备注  
 通常，MFC自动创建弹出菜单。  如果您需要手动创建 `CMFCPopupMenu` 对象，请将一个在堆然后调用 [CMFCPopupMenu::Create](../Topic/CMFCPopupMenu::Create.md)。  
  
## 示例  
 下面的示例演示如何配置弹出菜单对象。  在弹出菜单在主框架之外出现，将最大宽度，并将弹出菜单的正确菜单对齐时，该示例演示如何设置徽标和弹出菜单的声音，将动画速度和类型，请绘制菜单阴影效果。  此代码段是 [自定义调用示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_CustomPages#2](../../mfc/reference/codesnippet/CPP/cmfcpopupmenu-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
## 要求  
 **标头:** afxpopupmenu.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenuBar 类](../../mfc/reference/cmfcpopupmenubar-class.md)