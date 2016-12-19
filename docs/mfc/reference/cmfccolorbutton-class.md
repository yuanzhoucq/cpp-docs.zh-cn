---
title: "CMFCColorButton Class | Microsoft Docs"
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
  - "CMFCColorButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorButton class"
  - "CMFCColorButton::m_bAltColorDlg data member"
  - "CMFCColorButton::m_bAutoSetFocus data member"
  - "CMFCColorButton::m_Color data member"
  - "CMFCColorButton::m_ColorAutomatic data member"
  - "CMFCColorButton::m_lstDocColors data member"
  - "CMFCColorButton::m_nColumns data member"
  - "CMFCColorButton::m_pPalette data member"
  - "CMFCColorButton::m_pPopup data member"
  - "CMFCColorButton::m_strAutoColorText data member"
  - "CMFCColorButton::m_strDocColorsText data member"
  - "CMFCColorButton::m_strOtherText data member"
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
caps.latest.revision: 34
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCColorButton` 和 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) 选件类一起用来实现颜色选取器控件。  
  
## 语法  
  
```  
class CMFCColorButton : public CMFCButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorButton::CMFCColorButton](../Topic/CMFCColorButton::CMFCColorButton.md)|构造新的 `CMFCColorButton` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorButton::EnableAutomaticButton](../Topic/CMFCColorButton::EnableAutomaticButton.md)|启用和禁用常规的颜色按钮上确定“auto”按钮。  （标准系统自动按钮被标记 **自动**。）|  
|[CMFCColorButton::EnableOtherButton](../Topic/CMFCColorButton::EnableOtherButton.md)|启用和禁用常规的颜色按钮下方的“其他”按钮。  （标准系统“other”按钮被标记 **更多颜色…**。）|  
|[CMFCColorButton::GetAutomaticColor](../Topic/CMFCColorButton::GetAutomaticColor.md)|检索当前自动颜色。|  
|[CMFCColorButton::GetColor](../Topic/CMFCColorButton::GetColor.md)|检索按钮的颜色。|  
|[CMFCColorButton::SetColor](../Topic/CMFCColorButton::SetColor.md)|设置按钮的颜色。|  
|[CMFCColorButton::SetColorName](../Topic/CMFCColorButton::SetColorName.md)|设置颜色名称。|  
|[CMFCColorButton::SetColumnsNumber](../Topic/CMFCColorButton::SetColumnsNumber.md)|设置列数在颜色选取器对话框中。|  
|[CMFCColorButton::SetDocumentColors](../Topic/CMFCColorButton::SetDocumentColors.md)|指定在颜色选取器对话框中显示文档特定颜色的列表。|  
|[CMFCColorButton::SetPalette](../Topic/CMFCColorButton::SetPalette.md)|指定条件显示颜色调色板。|  
|[CMFCColorButton::SizeToContent](../Topic/CMFCColorButton::SizeToContent.md)|基于其文本和图像大小更改按钮控件的大小。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorButton::IsDrawXPTheme](../Topic/CMFCColorButton::IsDrawXPTheme.md)|指示当前颜色按钮是否在Windows XP视觉样式显示。|  
|[CMFCColorButton::OnDraw](../Topic/CMFCColorButton::OnDraw.md)|调用由结构显示按钮的图像。|  
|[CMFCColorButton::OnDrawBorder](../Topic/CMFCColorButton::OnDrawBorder.md)|调用由结构显示按钮的边框。|  
|[CMFCColorButton::OnDrawFocusRect](../Topic/CMFCColorButton::OnDrawFocusRect.md)|调用由结构显示焦点矩形，当按钮具有焦点。|  
|[CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md)|调用由结构，当颜色选取器将显示对话框。|  
|[CMFCColorButton::RebuildPalette](../Topic/CMFCColorButton::RebuildPalette.md)|初始化 `m_pPalette` 保护的数据成员添加到指定的调色板或默认系统调色板。|  
|[CMFCColorButton::UpdateColor](../Topic/CMFCColorButton::UpdateColor.md)|调用由结构，当用户选择一种颜色从颜色选择器对话框的调色板。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|`m_bAltColorDlg`|一个布尔值。  如果 `TRUE`，框架显示 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) 颜色对话框，而 *另一个* 按钮单击，或者，如果 `FALSE`，系统颜色对话框。  默认值为 `TRUE`。  有关更多信息，请参见 [CMFCColorButton::EnableOtherButton](../Topic/CMFCColorButton::EnableOtherButton.md)。|  
|`m_bAutoSetFocus`|一个布尔值。  如果 `TRUE`，框架将颜色菜单上，当菜单显示，或者，如果 `FALSE`，不更改焦点。  默认值为 `TRUE`。|  
|[CMFCColorButton::m\_bEnabledInCustomizeMode](../Topic/CMFCColorButton::m_bEnabledInCustomizeMode.md)|指示自定义模式是否为颜色按钮启动。|  
|`m_Color`|[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值。  包含当前选定的颜色。|  
|`m_ColorAutomatic`|[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值。  包含当前选定的默认颜色。|  
|`m_Colors`|[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值 [CArray](../../mfc/reference/carray-class.md)。  包含当前可用的颜色。|  
|`m_lstDocColors`|[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) 值 [CList](../../mfc/reference/clist-class.md)。  包含当前文件颜色。|  
|`m_nColumns`|一个 Integer。  在颜色网格包含列数显示在颜色选择菜单上的。|  
|`m_pPalette`|为 [CPalette](../../mfc/reference/cpalette-class.md)的指针。  包含可在当前颜色选择菜单的颜色。|  
|`m_pPopup`|为 [CMFCColorPopupMenu Class](../../mfc/reference/cmfccolorpopupmenu-class.md) 对象的指针。  显示的颜色选择菜单，当您单击按钮颜色。|  
|`m_strAutoColorText`|一个字符串。  “auto”按钮的标签在颜色选择菜单上的。|  
|`m_strDocColorsText`|一个字符串。  按钮的标签中显示文档的颜色选择菜单的颜色。|  
|`m_strOtherText`|一个字符串。  “另一个”按钮的标签在颜色选择菜单上的。|  
  
## 备注  
 默认情况下，`CMFCColorButton` 选件类的行为就如同打开颜色选择器对话框的普通按钮。  颜色选择器对话框包含演示自定义颜色选取器的数组小的颜色按钮和“other”按钮。  （标准系统“other”按钮被标记 **更多颜色…**。）当用户选择一个新的颜色时，`CMFCColorButton` 对象反映更改并显示选定的颜色。  
  
 使用 **类向导** 工具和对话框模板，创建颜色按钮控件直接在代码中，或。  如果直接创建颜色按钮控件中，添加一个 `CMFCColorButton` 变量到您的应用程序，然后调用 `CMFCColorButton` 对象的构造函数和 `Create` 方法。  如果使用 **类向导**，添加一个 `CButton` 变量到您的应用程序，从 `CButton` 然后将变量的类型。`CMFCColorButton`。  
  
 颜色选择器对话框\([CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)\)。[CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md) 方法显示，当框架调用 `OnLButtonDown` 事件处理程序时。  [CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md) 可以重写方法以支持自定义颜色选择。  
  
 `CMFCColorButton` 对象通知其父颜色通过将其发送 `WM_COMMAND | BN_CLICKED` 通知更改。  父使用 [CMFCColorButton::GetColor](../Topic/CMFCColorButton::GetColor.md) 方法检索当前颜色。  
  
## 示例  
 通过在 `CMFCColorButton` 选件类，中的各种方法下面的示例演示如何配置颜色按钮。  方法设置颜色按钮及其列数的颜色，从而自动和其他按钮。  此示例是 [状态栏演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/CPP/cmfccolorbutton-class_1.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/CPP/cmfccolorbutton-class_2.cpp)]  
  
## 要求  
 **标头:** afxcolorbutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md)   
 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [CPalette Class](../../mfc/reference/cpalette-class.md)   
 [CArray Class](../../mfc/reference/carray-class.md)   
 [CList Class](../../mfc/reference/clist-class.md)   
 [CString](../../atl-mfc-shared/reference/cstringt-class.md)