---
title: "CMFCRibbonButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonButton class"
ms.assetid: 732e941c-9504-4b83-a691-d18075965d53
caps.latest.revision: 42
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 44
---
# CMFCRibbonButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCRibbonButton` 类实现可放置在功能区栏元素（例如面板、快速访问工具栏和弹出菜单）上的按钮。  
  
## 语法  
  
```  
class CMFCRibbonButton : public CMFCRibbonBaseElement  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonButton::CMFCRibbonButton](../Topic/CMFCRibbonButton::CMFCRibbonButton.md)|构造一个功能区按钮对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonButton::AddSubItem](../Topic/CMFCRibbonButton::AddSubItem.md)|将菜单项添加到与按钮相关联的弹出菜单。|  
|[CMFCRibbonButton::CanBeStretched](../Topic/CMFCRibbonButton::CanBeStretched.md)|（重写 [CMFCRibbonBaseElement::CanBeStretched](../Topic/CMFCRibbonBaseElement::CanBeStretched.md)。）|  
|[CMFCRibbonButton::CleanUpSizes](../Topic/CMFCRibbonButton::CleanUpSizes.md)|（重写 [CMFCRibbonBaseElement::CleanUpSizes](../Topic/CMFCRibbonBaseElement::CleanUpSizes.md)。）|  
|[CMFCRibbonButton::ClosePopupMenu](../Topic/CMFCRibbonButton::ClosePopupMenu.md)|（重写 [CMFCRibbonBaseElement::ClosePopupMenu](../Topic/CMFCRibbonBaseElement::ClosePopupMenu.md)。）|  
|[CMFCRibbonButton::DrawBottomText](../Topic/CMFCRibbonButton::DrawBottomText.md)||  
|[CMFCRibbonButton::DrawImage](../Topic/CMFCRibbonButton::DrawImage.md)|（重写 [CMFCRibbonBaseElement::DrawImage](../Topic/CMFCRibbonBaseElement::DrawImage.md)。）|  
|[CMFCRibbonButton::DrawRibbonText](../Topic/CMFCRibbonButton::DrawRibbonText.md)||  
|[CMFCRibbonButton::FindSubItemIndexByID](../Topic/CMFCRibbonButton::FindSubItemIndexByID.md)|返回与指定的命令 ID 相关联的弹出菜单项的索引。|  
|[CMFCRibbonButton::GetCommandRect](../Topic/CMFCRibbonButton::GetCommandRect.md)||  
|[CMFCRibbonButton::GetCompactSize](../Topic/CMFCRibbonButton::GetCompactSize.md)|返回功能区元素的压缩大小。  （重写 [CMFCRibbonBaseElement::GetCompactSize](../Topic/CMFCRibbonBaseElement::GetCompactSize.md)。）|  
|[CMFCRibbonButton::GetIcon](../Topic/CMFCRibbonButton::GetIcon.md)||  
|[CMFCRibbonButton::GetImageIndex](../Topic/CMFCRibbonButton::GetImageIndex.md)|返回与按钮相关联的图像的索引。|  
|[CMFCRibbonButton::GetImageSize](../Topic/CMFCRibbonButton::GetImageSize.md)|返回功能区元素的图像大小。  （重写 [CMFCRibbonBaseElement::GetImageSize](../Topic/CMFCRibbonBaseElement::GetImageSize.md)。）|  
|[CMFCRibbonButton::GetIntermediateSize](../Topic/CMFCRibbonButton::GetIntermediateSize.md)|返回处于中间状态的功能区元素的大小。  （重写 [CMFCRibbonBaseElement::GetIntermediateSize](../Topic/CMFCRibbonBaseElement::GetIntermediateSize.md)。）|  
|[CMFCRibbonButton::GetMenu](../Topic/CMFCRibbonButton::GetMenu.md)|将一个句柄返回给一个分配给功能区按钮的 Windows 菜单。|  
|[CMFCRibbonButton::GetMenuRect](../Topic/CMFCRibbonButton::GetMenuRect.md)||  
|[CMFCRibbonButton::GetRegularSize](../Topic/CMFCRibbonButton::GetRegularSize.md)|返回功能区元素的常规大小。  （重写 [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)。）|  
|[CMFCRibbonButton::GetSubItems](../Topic/CMFCRibbonButton::GetSubItems.md)||  
|[CMFCRibbonButton::GetTextRowHeight](../Topic/CMFCRibbonButton::GetTextRowHeight.md)||  
|[CMFCRibbonButton::GetToolTipText](../Topic/CMFCRibbonButton::GetToolTipText.md)|返回功能区元素的工具提示文本。  （重写 [CMFCRibbonBaseElement::GetToolTipText](../Topic/CMFCRibbonBaseElement::GetToolTipText.md)。）|  
|[CMFCRibbonButton::HasCompactMode](../Topic/CMFCRibbonButton::HasCompactMode.md)|指定功能区元素是否有压缩模式。  （重写 [CMFCRibbonBaseElement::HasCompactMode](../Topic/CMFCRibbonBaseElement::HasCompactMode.md)。）|  
|[CMFCRibbonButton::HasIntermediateMode](../Topic/CMFCRibbonButton::HasIntermediateMode.md)|指定功能区元素是否有中间模式。  （重写 [CMFCRibbonBaseElement::HasIntermediateMode](../Topic/CMFCRibbonBaseElement::HasIntermediateMode.md)。）|  
|[CMFCRibbonButton::HasLargeMode](../Topic/CMFCRibbonButton::HasLargeMode.md)|确定功能区元素是否有大型模式。  （重写 [CMFCRibbonBaseElement::HasLargeMode](../Topic/CMFCRibbonBaseElement::HasLargeMode.md)。）|  
|[CMFCRibbonButton::HasMenu](../Topic/CMFCRibbonButton::HasMenu.md)|（重写 [CMFCRibbonBaseElement::HasMenu](../Topic/CMFCRibbonBaseElement::HasMenu.md)。）|  
|[CMFCRibbonButton::IsAlwaysDrawBorder](../Topic/CMFCRibbonButton::IsAlwaysDrawBorder.md)||  
|[CMFCRibbonButton::IsAlwaysLargeImage](../Topic/CMFCRibbonButton::IsAlwaysLargeImage.md)|（重写 [CMFCRibbonBaseElement::IsAlwaysLargeImage](../Topic/CMFCRibbonBaseElement::IsAlwaysLargeImage.md)。）|  
|[CMFCRibbonButton::IsApplicationButton](../Topic/CMFCRibbonButton::IsApplicationButton.md)||  
|[CMFCRibbonButton::IsCommandAreaHighlighted](../Topic/CMFCRibbonButton::IsCommandAreaHighlighted.md)||  
|[CMFCRibbonButton::IsDefaultCommand](../Topic/CMFCRibbonButton::IsDefaultCommand.md)|确定是否已启用功能区按钮的默认命令。|  
|[CMFCRibbonButton::IsDefaultPanelButton](../Topic/CMFCRibbonButton::IsDefaultPanelButton.md)||  
|[CMFCRibbonButton::IsDrawTooltipImage](../Topic/CMFCRibbonButton::IsDrawTooltipImage.md)||  
|[CMFCRibbonButton::IsLargeImage](../Topic/CMFCRibbonButton::IsLargeImage.md)||  
|[CMFCRibbonButton::IsMenuAreaHighlighted](../Topic/CMFCRibbonButton::IsMenuAreaHighlighted.md)||  
|[CMFCRibbonButton::IsMenuOnBottom](../Topic/CMFCRibbonButton::IsMenuOnBottom.md)||  
|[CMFCRibbonButton::IsPopupDefaultMenuLook](../Topic/CMFCRibbonButton::IsPopupDefaultMenuLook.md)||  
|[CMFCRibbonButton::IsRightAlignMenu](../Topic/CMFCRibbonButton::IsRightAlignMenu.md)|确定菜单是否为右对齐。|  
|[CMFCRibbonButton::IsSingleLineText](../Topic/CMFCRibbonButton::IsSingleLineText.md)||  
|[CMFCRibbonButton::OnCalcTextSize](../Topic/CMFCRibbonButton::OnCalcTextSize.md)|（重写 [CMFCRibbonBaseElement::OnCalcTextSize](../Topic/CMFCRibbonBaseElement::OnCalcTextSize.md)。）|  
|[CMFCRibbonButton::OnDrawBorder](../Topic/CMFCRibbonButton::OnDrawBorder.md)||  
|[CMFCRibbonButton::OnDraw](../Topic/CMFCRibbonButton::OnDraw.md)|由框架调用以绘制功能区元素。  （重写 [CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md)。）|  
|[CMFCRibbonButton::OnFillBackground](../Topic/CMFCRibbonButton::OnFillBackground.md)||  
|[CMFCRibbonButton::RemoveAllSubItems](../Topic/CMFCRibbonButton::RemoveAllSubItems.md)|从弹出菜单中删除所有菜单项。|  
|[CMFCRibbonButton::RemoveSubItem](../Topic/CMFCRibbonButton::RemoveSubItem.md)|从弹出菜单中删除一个菜单项。|  
|[CMFCRibbonButton::SetACCData](../Topic/CMFCRibbonButton::SetACCData.md)|（重写 [CMFCRibbonBaseElement::SetACCData](../Topic/CMFCRibbonBaseElement::SetACCData.md)。）|  
|[CMFCRibbonButton::SetAlwaysLargeImage](../Topic/CMFCRibbonButton::SetAlwaysLargeImage.md)|指定当用户折叠按钮时，按钮显示大图像还是小图像。|  
|[CMFCRibbonButton::SetDefaultCommand](../Topic/CMFCRibbonButton::SetDefaultCommand.md)|启用功能区按钮的默认命令。|  
|[CMFCRibbonButton::SetDescription](../Topic/CMFCRibbonButton::SetDescription.md)|设置功能区元素的说明。  （重写 [CMFCRibbonBaseElement::SetDescription](../Topic/CMFCRibbonBaseElement::SetDescription.md)。）|  
|[CMFCRibbonButton::SetImageIndex](../Topic/CMFCRibbonButton::SetImageIndex.md)|将索引分配给按钮的图像。|  
|[CMFCRibbonButton::SetMenu](../Topic/CMFCRibbonButton::SetMenu.md)|将弹出菜单分配给功能区按钮。|  
|[CMFCRibbonButton::SetParentCategory](../Topic/CMFCRibbonButton::SetParentCategory.md)|（重写 [CMFCRibbonBaseElement::SetParentCategory](../Topic/CMFCRibbonBaseElement::SetParentCategory.md)。）|  
|[CMFCRibbonButton::SetRightAlignMenu](../Topic/CMFCRibbonButton::SetRightAlignMenu.md)|使弹出菜单与按钮的右侧对齐。|  
|[CMFCRibbonButton::SetText](../Topic/CMFCRibbonButton::SetText.md)|设置功能区元素的文本。  （重写 [CMFCRibbonBaseElement::SetText](../Topic/CMFCRibbonBaseElement::SetText.md)。）|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCRibbonButton::OnClick](../Topic/CMFCRibbonButton::OnClick.md)|当用户单击按钮时，由框架调用。|  
  
## 示例  
 下面的示例演示如何使用 `CMFCRibbonButton` 类中的各种方法。  该示例展示如何构造 `CMFCRibbonButton` 类的对象，将弹出菜单分配给功能区按钮，设置按钮的说明，从弹出菜单中删除一个菜单项，然后使弹出菜单与按钮的边缘右对齐。  
  
 [!code-cpp[NVC_MFC_RibbonApp#7](../../mfc/reference/codesnippet/CPP/cmfcribbonbutton-class_1.cpp)]  
  
## 备注  
 若要在应用程序中使用功能区按钮，请构造按钮对象，并将其添加到相应的功能区[面板](../../mfc/reference/cmfcribbonpanel-class.md)。  
  
```  
CMFCRibbonPanel* pPanel = pCategory->AddPanel (  
    _T("Clipboard"),                       // Panel name  
    m_PanelIcons.ExtractIcon (0));  // Panel icon  
// Create the first button ("Paste"):  
CMFCRibbonButton* pPasteButton =   
    new CMFCRibbonButton (ID_EDIT_PASTE, _T("Paste"), -1, 0);  
// The third parameter (-1) disables small images for button.  
// This button is always displayed with a large image  
// Associate a pop-up menu with the "Paste" button:  
pPasteButton->SetMenu (IDR_CONTEXT_MENU);  
// Add buttons to the panel. These buttons have only small images.  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_CUT, _T("Cut"), 1));  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_COPY, _T("Copy"), 2));  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_PAINT, _T("Paint"), 9));  
```  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
## 要求  
 **标头：**afxribbonbutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)