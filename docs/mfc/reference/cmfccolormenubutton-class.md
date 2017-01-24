---
title: "CMFCColorMenuButton Class | Microsoft Docs"
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
  - "CMFCColorMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorMenuButton class"
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
caps.latest.revision: 29
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorMenuButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCColorMenuButton` 选件类支持菜单命令或启动颜色选择器对话框的工具栏按钮。  
  
## 语法  
  
```  
class CMFCColorMenuButton : public CMFCToolBarMenuButton  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorMenuButton::CMFCColorMenuButton](../Topic/CMFCColorMenuButton::CMFCColorMenuButton.md)|构造 `CMFCColorMenuButton` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorMenuButton::EnableAutomaticButton](../Topic/CMFCColorMenuButton::EnableAutomaticButton.md)|启用和禁用常规的颜色按钮上确定“auto”按钮。  （标准系统自动按钮被标记 **自动**。）|  
|[CMFCColorMenuButton::EnableDocumentColors](../Topic/CMFCColorMenuButton::EnableDocumentColors.md)|使文档无需特定颜色显示而不是系统颜色。|  
|[CMFCColorMenuButton::EnableOtherButton](../Topic/CMFCColorMenuButton::EnableOtherButton.md)|启用和禁用常规的颜色按钮下方的“其他”按钮。  （标准系统“other”按钮被标记 **更多颜色…**。）|  
|[CMFCColorMenuButton::EnableTearOff](../Topic/CMFCColorMenuButton::EnableTearOff.md)|启用此功能撕下颜色窗格。|  
|[CMFCColorMenuButton::GetAutomaticColor](../Topic/CMFCColorMenuButton::GetAutomaticColor.md)|检索当前自动颜色。|  
|[CMFCColorMenuButton::GetColor](../Topic/CMFCColorMenuButton::GetColor.md)|检索当前按钮的颜色。|  
|[CMFCColorMenuButton::GetColorByCmdID](../Topic/CMFCColorMenuButton::GetColorByCmdID.md)|检索对应于指定的命令ID.的颜色|  
|[CMFCColorMenuButton::OnChangeParentWnd](../Topic/CMFCColorMenuButton::OnChangeParentWnd.md)|调用由结构，当父窗口更改。|  
|[CMFCColorMenuButton::OpenColorDialog](../Topic/CMFCColorMenuButton::OpenColorDialog.md)|打开颜色选择对话框。|  
|[CMFCColorMenuButton::SetColor](../Topic/CMFCColorMenuButton::SetColor.md)|set current color按钮的颜色。|  
|[CMFCColorMenuButton::SetColorByCmdID](../Topic/CMFCColorMenuButton::SetColorByCmdID.md)|设置指定的颜色菜单按钮的颜色。|  
|[CMFCColorMenuButton::SetColorName](../Topic/CMFCColorMenuButton::SetColorName.md)|设置新名称对于指定的颜色。|  
|[CMFCColorMenuButton::SetColumnsNumber](../Topic/CMFCColorMenuButton::SetColumnsNumber.md)|设置由 `CMFCColorBar` 对象显示的列数。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCColorMenuButton::CopyFrom](../Topic/CMFCColorMenuButton::CopyFrom.md)|复制另一个工具栏按钮到当前按钮。|  
|[CMFCColorMenuButton::CreatePopupMenu](../Topic/CMFCColorMenuButton::CreatePopupMenu.md)|创建一个颜色选择器对话框。|  
|[CMFCColorMenuButton::IsEmptyMenuAllowed](../Topic/CMFCColorMenuButton::IsEmptyMenuAllowed.md)|指示空菜单是否支持。|  
|[CMFCColorMenuButton::OnDraw](../Topic/CMFCColorMenuButton::OnDraw.md)|调用框架在按钮的图像。|  
|[CMFCColorMenuButton::OnDrawOnCustomizeList](../Topic/CMFCColorMenuButton::OnDrawOnCustomizeList.md)|调用由结构，在 `CMFCColorMenuButton` 对象在工具栏自定义对话框的列表之前显示。|  
  
## 备注  
 在 `CMFCColorMenuButton` 对象若要替换原始菜单命令或工具栏按钮，请创建 `CMFCColorMenuButton` 对象，并设置所有适当的 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) 样式，然后调用 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md) 选件类的 `ReplaceButton` 方法。  如果自定义工具栏，请调用 [CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md) 方法。  
  
 在处理 [CMFCColorMenuButton::CreatePopupMenu](../Topic/CMFCColorMenuButton::CreatePopupMenu.md) 事件处理程序中，颜色选择器对话框中创建。  事件处理程序有两 `WM_COMMAND` 消息的父级框架。  分配给原始菜单命令或工具栏按钮的 `CMFCColorMenuButton` 对象发送控件ID。  
  
## 示例  
 下面的示例演示如何创建和配置颜色菜单按钮使用各种方法。`CMFCColorMenuButton` 选件类。  在此示例中，`CPalette` 对象首次创建然后用于构造对象 `CMFCColorMenuButton` 选件类。  启用它自动和其他按钮并将其颜色和列号然后配置 `CMFCColorMenuButton` 对象。  此代码是 [Word填充示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/CPP/cmfccolormenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/CPP/cmfccolormenubutton-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
 [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)  
  
## 要求  
 **标头:** afxcolormenubutton.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)   
 [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md)