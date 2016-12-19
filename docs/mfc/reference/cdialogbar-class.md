---
title: "CDialogBar Class | Microsoft Docs"
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
  - "CDialogBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialogBar class"
  - "dialog bars, Windows modeless dialog box"
  - "对话框, 无模式"
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDialogBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供了Windows无模式对话框的功能在控件条。  
  
## 语法  
  
```  
class CDialogBar : public CControlBar  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDialogBar::CDialogBar](../Topic/CDialogBar::CDialogBar.md)|构造 `CDialogBar` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDialogBar::Create](../Topic/CDialogBar::Create.md)|创建一个Windows对话栏并将它附加到 `CDialogBar` 对象。|  
  
## 备注  
 对话栏类似于对话框因为它包含用户可以使用tab键移动之间的标准Windows控件。  另一相似之处是您在其中创建对话框模板表示对话栏。  
  
 创建和使用对话栏类似于创建和使用 `CFormView` 对象。  首先，使用 [对话框编辑器](../../mfc/dialog-editor.md) 定义与该样式 **WS\_CHILD** 而不会影响其他样式的一个对话框模板。  模板不能具有该样式 **WS\_VISIBLE**。  在应用程序代码中，调用构造函数构造 `CDialogBar` 对象，然后调用 **Create** 创建对话栏窗口并将其附加到 `CDialogBar` 对象。  
  
 有关 `CDialogBar`的更多信息，请参见文章 [对话栏](../../mfc/dialog-bars.md) 和 [技术说明31](../../mfc/tn031-control-bars.md)，控制条。  
  
> [!NOTE]
>  在当前版本中，`CDialogBar` 对象不能承载Windows窗体控件。  有关Windows在Visual C\+\+的windows窗体控件的更多信息，请参见 [在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CDialogBar`  
  
## 要求  
 **Header:** afxext.h  
  
## 请参阅  
 [MFC示例CTRLBARS](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFormView Class](../../mfc/reference/cformview-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)