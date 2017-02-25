---
title: "CMFCToolBarMenuButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarMenuButton class"
ms.assetid: cfa50176-7e4b-4527-9904-86a1b48fc1bc
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CMFCToolBarMenuButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含一个弹出菜单的工具栏按钮。  
  
## 语法  
  
```  
class CMFCToolBarMenuButton : public CMFCToolBarButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarMenuButton::CMFCToolBarMenuButton](../Topic/CMFCToolBarMenuButton::CMFCToolBarMenuButton.md)|构造 `CMFCToolBarMenuButton` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarMenuButton::CompareWith](../Topic/CMFCToolBarMenuButton::CompareWith.md)|此实例与提供的 `CMFCToolBarButton` 对象进行比较。  （重写 [CMFCToolBarButton::CompareWith](../Topic/CMFCToolBarButton::CompareWith.md)。）|  
|[CMFCToolBarMenuButton::CopyFrom](../Topic/CMFCToolBarMenuButton::CopyFrom.md)|复制另一个工具栏按钮的属性设置为当前按钮。  （重写 [CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md)。）|  
|[CMFCToolBarMenuButton::CreateFromMenu](../Topic/CMFCToolBarMenuButton::CreateFromMenu.md)|初始化从Windows菜单句柄的工具栏菜单。|  
|[CMFCToolBarMenuButton::CreateMenu](../Topic/CMFCToolBarMenuButton::CreateMenu.md)|创建包含在工具栏菜单上的命令的一个Windows菜单。  返回的句柄Windows菜单。|  
|[CMFCToolBarMenuButton::CreatePopupMenu](../Topic/CMFCToolBarMenuButton::CreatePopupMenu.md)|创建一个弹出菜单对象\([CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)\)显示工具栏菜单。|  
|[CMFCToolBarMenuButton::EnableQuickCustomize](../Topic/CMFCToolBarMenuButton::EnableQuickCustomize.md)||  
|[CMFCToolBarMenuButton::GetCommands](../Topic/CMFCToolBarMenuButton::GetCommands.md)|允许访问指令列表的只读访问工具栏上的。|  
|[CMFCToolBarMenuButton::GetImageRect](../Topic/CMFCToolBarMenuButton::GetImageRect.md)|检索按钮图像的边框。|  
|[CMFCToolBarMenuButton::GetPaletteRows](../Topic/CMFCToolBarMenuButton::GetPaletteRows.md)|当菜单在"模式时，返回的行数在弹出菜单中的。|  
|[CMFCToolBarMenuButton::GetPopupMenu](../Topic/CMFCToolBarMenuButton::GetPopupMenu.md)|返回指向与按钮的弹出菜单对象。|  
|[CMFCToolBarMenuButton::HasButton](../Topic/CMFCToolBarMenuButton::HasButton.md)||  
|[CMFCToolBarMenuButton::HaveHotBorder](../Topic/CMFCToolBarMenuButton::HaveHotBorder.md)|确定按钮的边框是否显示，当用户选择按钮。  （重写 [CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md)。）|  
|[CMFCToolBarMenuButton::IsBorder](../Topic/CMFCToolBarMenuButton::IsBorder.md)||  
|[CMFCToolBarMenuButton::IsClickedOnMenu](../Topic/CMFCToolBarMenuButton::IsClickedOnMenu.md)||  
|[CMFCToolBarMenuButton::IsDroppedDown](../Topic/CMFCToolBarMenuButton::IsDroppedDown.md)|确定弹出菜单是否显示。|  
|[CMFCToolBarMenuButton::IsEmptyMenuAllowed](../Topic/CMFCToolBarMenuButton::IsEmptyMenuAllowed.md)|调用由框架确定用户是否可以从打开选定菜单项的子菜单。|  
|[CMFCToolBarMenuButton::IsExclusive](../Topic/CMFCToolBarMenuButton::IsExclusive.md)|确定按钮，也就是说，是否在独占模式弹出菜单是否保持打开状态，即使当用户移动到另一个工具栏或按钮的指针。|  
|[CMFCToolBarMenuButton::IsMenuPaletteMode](../Topic/CMFCToolBarMenuButton::IsMenuPaletteMode.md)|确定弹出菜单是否在"模式。|  
|[CMFCToolBarMenuButton::IsQuickMode](../Topic/CMFCToolBarMenuButton::IsQuickMode.md)||  
|[CMFCToolBarMenuButton::IsTearOffMenu](../Topic/CMFCToolBarMenuButton::IsTearOffMenu.md)|确定弹出菜单是否具有拖曳条。|  
|[CMFCToolBarMenuButton::OnAfterCreatePopupMenu](../Topic/CMFCToolBarMenuButton::OnAfterCreatePopupMenu.md)||  
|[CMFCToolBarMenuButton::OnBeforeDrag](../Topic/CMFCToolBarMenuButton::OnBeforeDrag.md)|指定按钮是否可以拖动。  （重写 [CMFCToolBarButton::OnBeforeDrag](../Topic/CMFCToolBarButton::OnBeforeDrag.md)。）|  
|[CMFCToolBarMenuButton::OnCalculateSize](../Topic/CMFCToolBarMenuButton::OnCalculateSize.md)|调用由结构计算该按钮的大小指定的设备上下文和停靠状态的。  （重写 [CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md)。）|  
|[CMFCToolBarMenuButton::OnCancelMode](../Topic/CMFCToolBarMenuButton::OnCancelMode.md)|调用由框架处理 [WM\_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) 消息。  （重写 [CMFCToolBarButton::OnCancelMode](../Topic/CMFCToolBarButton::OnCancelMode.md)。）|  
|[CMFCToolBarMenuButton::OnChangeParentWnd](../Topic/CMFCToolBarMenuButton::OnChangeParentWnd.md)|调用由结构，当按钮插入新工具栏。  （重写 [CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md)。）|  
|[CMFCToolBarMenuButton::OnClick](../Topic/CMFCToolBarMenuButton::OnClick.md)|调用由结构，当用户单击鼠标按钮。  （重写 [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)。）|  
|[CMFCToolBarMenuButton::OnClickMenuItem](../Topic/CMFCToolBarMenuButton::OnClickMenuItem.md)|调用由结构，当用户选择在弹出菜单的项目。|  
|[CMFCToolBarMenuButton::OnContextHelp](../Topic/CMFCToolBarMenuButton::OnContextHelp.md)|调用由结构，当父工具栏处理 `WM_HELPHITTEST` 消息。  （重写 [CMFCToolBarButton::OnContextHelp](../Topic/CMFCToolBarButton::OnContextHelp.md)。）|  
|[CMFCToolBarMenuButton::OnDraw](../Topic/CMFCToolBarMenuButton::OnDraw.md)|使用指定的样式和选项，调用由框架绘制按钮。  （重写 [CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md)。）|  
|[CMFCToolBarMenuButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarMenuButton::OnDrawOnCustomizeList.md)|调用由框架绘制在 **自定义** 对话框的 **命令** 窗格的按钮。  （重写 [CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md)。）|  
|[CMFCToolBarMenuButton::OpenPopupMenu](../Topic/CMFCToolBarMenuButton::OpenPopupMenu.md)|调用由结构，当用户打开弹出菜单。|  
|[CMFCToolBarMenuButton::ResetImageToDefault](../Topic/CMFCToolBarMenuButton::ResetImageToDefault.md)|将设置为默认值与按钮的图像。  （重写 [CMFCToolBarButton::ResetImageToDefault](../Topic/CMFCToolBarButton::ResetImageToDefault.md)。）|  
|[CMFCToolBarMenuButton::SaveBarState](../Topic/CMFCToolBarMenuButton::SaveBarState.md)|保存工具栏按钮的状态。  （重写 [CMFCToolBarButton::SaveBarState](../Topic/CMFCToolBarButton::SaveBarState.md)。）|  
|[CMFCToolBarMenuButton::Serialize](../Topic/CMFCToolBarMenuButton::Serialize.md)|读取存档或写入的此对象到存档。  （重写 [CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md)。）|  
|[CMFCToolBarMenuButton::SetACCData](../Topic/CMFCToolBarMenuButton::SetACCData.md)|填充可访问性数据的提供的 `CAccessibilityData` 对象从工具栏按钮。  （重写 [CMFCToolBarButton::SetACCData](../Topic/CMFCToolBarButton::SetACCData.md)。）|  
|[CMFCToolBarMenuButton::SetMenuOnly](../Topic/CMFCToolBarMenuButton::SetMenuOnly.md)|指定按钮是否可添加到工具栏。|  
|[CMFCToolBarMenuButton::SetMenuPaletteMode](../Topic/CMFCToolBarMenuButton::SetMenuPaletteMode.md)|指定弹出菜单是否在"模式。|  
|[CMFCToolBarMenuButton::SetMessageWnd](../Topic/CMFCToolBarMenuButton::SetMessageWnd.md)||  
|[CMFCToolBarMenuButton::SetRadio](../Topic/CMFCToolBarMenuButton::SetRadio.md)|强制工具栏菜单按钮显示指示的图标选择了。|  
|[CMFCToolBarMenuButton::SetTearOff](../Topic/CMFCToolBarMenuButton::SetTearOff.md)|为弹出菜单指定拖曳条ID。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarMenuButton::DrawDocumentIcon](../Topic/CMFCToolBarMenuButton::DrawDocumentIcon.md)|绘制在菜单按钮的图标。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarMenuButton::m\_bAlwaysCallOwnerDraw](../Topic/CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw.md)|如果 `TRUE`，框架始终调用 [CFrameWndEx::OnDrawMenuImage](../Topic/CFrameWndEx::OnDrawMenuImage.md)，在绘制按钮。|  
  
## 备注  
 `CMFCToolBarMenuButton` 可以显示为菜单、有一个子菜单，按钮执行命令或显示菜单的菜单项，或仅显示菜单的按钮。  通过指定参数确定菜单按钮的行为和外观\(与在构造函数 `CMFCToolbarMenuButton::CMFCToolbarMenuButton`按钮的图像、文本、"菜单句柄和命令ID。  
  
 从 `CMFCToolbarMenuButton` 选件类派生的自定义选件类必须使用 [DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) 宏。  当应用程序关闭时，[DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) 宏生成错误。  
  
## 示例  
 下面的示例演示如何配置 `CMFCToolBarMenuButton` 对象。  代码演示如何指定的下拉菜单中调色板模式以及将创建的拖曳条指定ID，当用户拖动菜单按钮菜单栏时。  此代码段是 [Word填充示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#10](../../mfc/reference/codesnippet/CPP/cmfctoolbarmenubutton-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
## 要求  
 **标头:** afxtoolbarmenubutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)