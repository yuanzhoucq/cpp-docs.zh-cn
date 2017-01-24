---
title: "CDialogEx Class | Microsoft Docs"
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
  - "CDialogEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialogEx class"
  - "CDialogEx::PreTranslateMessage method"
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
caps.latest.revision: 27
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDialogEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CDialogEx`类指定对话框的背景色和背景图像。  
  
## 语法  
  
```  
class CDialogEx : public CDialog  
```  
  
## Members  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDialogEx::CDialogEx](../Topic/CDialogEx::CDialogEx.md)|构造 `CDialogEx` 对象。|  
|`CDialogEx::~CDialogEx`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDialogEx::SetBackgroundColor](../Topic/CDialogEx::SetBackgroundColor.md)|设置对话框的背景色。|  
|[CDialogEx::SetBackgroundImage](../Topic/CDialogEx::SetBackgroundImage.md)|设置对话框的背景图像。|  
  
## 备注  
 若要使用`CDialogEx`类，则从`CDialogEx`类而不是`CDialog`类派生对话框类。  
  
 对话框图像存储在资源文件中。  该框架将自动删除从资源文件加载的任何图像。  若要以编程方式删除当前的背景图像，请调用 [CDialogEx::SetBackgroundImage](../Topic/CDialogEx::SetBackgroundImage.md) 方法或实现 `OnDestroy` 事件处理程序。  当你调用 [CDialogEx::SetBackgroundImage](../Topic/CDialogEx::SetBackgroundImage.md) 方法时，请传入 `HBITMAP` 参数作为图像句柄。  如果`CDialogEx`标记是`m_bAutoDestroyBmp`，`TRUE`对象将取得图像的所有权并将其删除。  
  
 `CDialogEx` 对象可以是 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 对象的父级。  当 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 对象打开时，[CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 对象将调用 `CDialogEx::SetActiveMenu` 方法。  此后，`CDialogEx` 对象将处理任何菜单事件，直到 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 对象关闭。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
## 要求  
 **标头：** afxdialogex.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)   
 [CContextMenuManager Class](../../mfc/reference/ccontextmenumanager-class.md)