---
title: "CMFCImageEditorPaletteBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCImageEditorPaletteBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCImageEditorPaletteBar class"
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CMFCImageEditorPaletteBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供调色板栏功能到图像编辑器对话框。  
  
## 语法  
  
```  
class CMFCImageEditorPaletteBar : public CMFCToolBar  
```  
  
## 成员  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCImageEditorPaletteBar::GetRowHeight](../Topic/CMFCImageEditorPaletteBar::GetRowHeight.md)|返回高度工具栏按钮。  （重写 [CMFCToolBar::GetRowHeight](../Topic/CMFCToolBar::GetRowHeight.md)。）|  
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable](../Topic/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable.md)|定位工具栏是否可以显示扩展的边框的按钮。  （重写 [CMFCToolBar::IsButtonExtraSizeAvailable](../Topic/CMFCToolBar::IsButtonExtraSizeAvailable.md)。）|  
  
### 备注  
 此类不适于在您的代码中直接使用。  
  
 框架使用此选件类显示在图像编辑器对话框的一个调色板条。  有关图像编辑器对话框的更多信息，请参见 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)  
  
## 要求  
 **标头:** afximageeditordialog.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)