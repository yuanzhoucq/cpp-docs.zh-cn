---
title: "CMFCRibbonGallery Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonGallery"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonGallery class"
ms.assetid: 9734c9c9-981c-4b3f-8c59-264fd41811b4
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CMFCRibbonGallery Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现Office 2007样式功能区库。  
  
## 语法  
  
```  
class CMFCRibbonGallery : public CMFCRibbonButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonGallery::CMFCRibbonGallery](../Topic/CMFCRibbonGallery::CMFCRibbonGallery.md)|构造和初始化 `CMFCRibbonGallery` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonGallery::AddGroup](../Topic/CMFCRibbonGallery::AddGroup.md)|添加新组到该库。|  
|[CMFCRibbonGallery::AddSubItem](../Topic/CMFCRibbonGallery::AddSubItem.md)|添加新菜单项添加到下拉菜单。|  
|[CMFCRibbonGallery::Clear](../Topic/CMFCRibbonGallery::Clear.md)|清除该目录该库。|  
|[CMFCRibbonGallery::EnableMenuResize](../Topic/CMFCRibbonGallery::EnableMenuResize.md)|启用或禁用调整菜单面板。|  
|[CMFCRibbonGallery::EnableMenuSideBar](../Topic/CMFCRibbonGallery::EnableMenuSideBar.md)|在该弹出菜单左侧启用或禁用该栏。|  
|[CMFCRibbonGallery::GetCompactSize](../Topic/CMFCRibbonGallery::GetCompactSize.md)|（重写 [CMFCRibbonButton::GetCompactSize](../Topic/CMFCRibbonButton::GetCompactSize.md)。）|  
|[CMFCRibbonGallery::GetDroppedDown](../Topic/CMFCRibbonGallery::GetDroppedDown.md)|（重写 [CMFCRibbonBaseElement::GetDroppedDown](../Topic/CMFCRibbonBaseElement::GetDroppedDown.md)。）|  
|[CMFCRibbonGallery::GetGroupName](../Topic/CMFCRibbonGallery::GetGroupName.md)|返回位于指定索引处的组的名称。|  
|[CMFCRibbonGallery::GetGroupOffset](../Topic/CMFCRibbonGallery::GetGroupOffset.md)||  
|[CMFCRibbonGallery::GetIconsInRow](../Topic/CMFCRibbonGallery::GetIconsInRow.md)|顺序返回项的数目功能区库。|  
|[CMFCRibbonGallery::GetItemToolTip](../Topic/CMFCRibbonGallery::GetItemToolTip.md)|返回与该库的项目的工具提示文本。|  
|[CMFCRibbonGallery::GetLastSelectedItem](../Topic/CMFCRibbonGallery::GetLastSelectedItem.md)|返回最后一项的索引在用户选择的库中。|  
|[CMFCRibbonGallery::GetPaletteID](../Topic/CMFCRibbonGallery::GetPaletteID.md)|返回当前库的命令ID。|  
|[CMFCRibbonGallery::GetRegularSize](../Topic/CMFCRibbonGallery::GetRegularSize.md)|（重写 [CMFCRibbonButton::GetRegularSize](../Topic/CMFCRibbonButton::GetRegularSize.md)。）|  
|[CMFCRibbonGallery::GetSelectedItem](../Topic/CMFCRibbonGallery::GetSelectedItem.md)||  
|[CMFCRibbonGallery::HasMenu](../Topic/CMFCRibbonGallery::HasMenu.md)|（重写 [CMFCRibbonButton::HasMenu](../Topic/CMFCRibbonButton::HasMenu.md)。）|  
|[CMFCRibbonGallery::IsButtonMode](../Topic/CMFCRibbonGallery::IsButtonMode.md)|指定该库是否在库包含按钮。|  
|[CMFCRibbonGallery::IsMenuResizeEnabled](../Topic/CMFCRibbonGallery::IsMenuResizeEnabled.md)|指定调整大小的菜单是否启用或禁用。|  
|[CMFCRibbonGallery::IsMenuResizeVertical](../Topic/CMFCRibbonGallery::IsMenuResizeVertical.md)||  
|[CMFCRibbonGallery::IsMenuSideBar](../Topic/CMFCRibbonGallery::IsMenuSideBar.md)|指定该栏是否启用或禁用。|  
|[CMFCRibbonGallery::OnAfterChangeRect](../Topic/CMFCRibbonGallery::OnAfterChangeRect.md)|（重写 `CMFCRibbonButton::OnAfterChangeRect`。）|  
|[CMFCRibbonGallery::OnDraw](../Topic/CMFCRibbonGallery::OnDraw.md)|（重写 [CMFCRibbonButton::OnDraw](../Topic/CMFCRibbonButton::OnDraw.md)。）|  
|[CMFCRibbonGallery::OnEnable](../Topic/CMFCRibbonGallery::OnEnable.md)|（重写 `CMFCRibbonBaseElement::OnEnable`。）|  
|[CMFCRibbonGallery::OnRTLChanged](../Topic/CMFCRibbonGallery::OnRTLChanged.md)|（重写 [CMFCRibbonBaseElement::OnRTLChanged](../Topic/CMFCRibbonBaseElement::OnRTLChanged.md)。）|  
|[CMFCRibbonGallery::RedrawIcons](../Topic/CMFCRibbonGallery::RedrawIcons.md)|重绘该库。|  
|[CMFCRibbonGallery::RemoveItemToolTips](../Topic/CMFCRibbonGallery::RemoveItemToolTips.md)|从某个库中的所有项目中移除工具提示。|  
|[CMFCRibbonGallery::SelectItem](../Topic/CMFCRibbonGallery::SelectItem.md)||  
|[CMFCRibbonGallery::SetACCData](../Topic/CMFCRibbonGallery::SetACCData.md)|（重写 [CMFCRibbonButton::SetACCData](../Topic/CMFCRibbonButton::SetACCData.md)。）|  
|[CMFCRibbonGallery::SetButtonMode](../Topic/CMFCRibbonGallery::SetButtonMode.md)|指定是否显示了功能区库作为一个下拉式按钮或作为一个调色板直接在功能区。|  
|[CMFCRibbonGallery::SetGroupName](../Topic/CMFCRibbonGallery::SetGroupName.md)|设置组的名称。|  
|[CMFCRibbonGallery::SetIconsInRow](../Topic/CMFCRibbonGallery::SetIconsInRow.md)|定义项的数目每在库中的行。|  
|[CMFCRibbonGallery::SetItemToolTip](../Topic/CMFCRibbonGallery::SetItemToolTip.md)|设置一个项目的工具提示文本在该库。|  
|[CMFCRibbonGallery::SetPalette](../Topic/CMFCRibbonGallery::SetPalette.md)|附加调色板到功能区库。|  
|[CMFCRibbonGallery::SetPaletteID](../Topic/CMFCRibbonGallery::SetPaletteID.md)|定义在 `WM_COMMAND` 消息发送的命令ID，当库项目选中时。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonGallery::OnDrawPaletteIcon](../Topic/CMFCRibbonGallery::OnDrawPaletteIcon.md)|调用由结构，在绘制库图标。|  
  
## 备注  
 库按钮行为与标准菜单按钮，但它显示库，当用户打开它。  当您在中选择库项目时，框架与按钮的命令ID一起发送 `WM_COMMAND` 信息。  在处理消息，应调用 [CMFCRibbonGallery::GetLastSelectedItem](../Topic/CMFCRibbonGallery::GetLastSelectedItem.md) 确定哪个项目从该库中选择。  
  
## 示例  
 下面的示例在 `CMFCRibbonGallery` 选件类演示如何使用各种方案配置 `CMFCRibbonGallery` 对象。  示例的名称说明如何指定项的数目每一行，启用调整菜单面板，在弹出菜单左侧启用栏和显示了功能区库如调色板直接在功能区栏。  此代码段是 [绘制客户端示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#6](../../mfc/reference/codesnippet/CPP/cmfcribbongallery-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md) [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
## 要求  
 **标头:** afxRibbonPaletteGallery.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonGalleryMenuButton Class](../../mfc/reference/cmfcribbongallerymenubutton-class.md)