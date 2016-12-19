---
title: "CMFCWindowsManagerDialog Class | Microsoft Docs"
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
  - "CMFCWindowsManagerDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCWindowsManagerDialog class"
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCWindowsManagerDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCWindowsManagerDialog` 对象使用户能够管理在MDI应用程序的子窗口。  
  
## 语法  
  
```  
class CMFCWindowsManagerDialog : public CDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](../Topic/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog.md)|构造 `CMFCWindowsManagerDialog` 对象。|  
  
## 备注  
 `CMFCWindowsManagerDialog` 包含MDI中当前打开应用程序的子窗口列表。  使用此对话框，用户可以手动控件MDI子窗口的状态。  
  
 `CMFCWindowsManagerDialog` 嵌入在 [CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)中。  `CMFCWindowsManagerDialog` 不是应手动创建的选件类。  相反，请调用函数，[CMDIFrameWndEx::ShowWindowsDialog](../Topic/CMDIFrameWndEx::ShowWindowsDialog.md)，它将创建并显示一 `CMFCWindowsManagerDialog` 对象。  
  
## 示例  
 下面的示例演示如何通过调用 `CMDIFrameWndEx::ShowWindowsDialog`构造 `CMFCWindowsManagerDialog` 对象。  此代码段是 [Visual Studio演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/CPP/cmfcwindowsmanagerdialog-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)  
  
## 要求  
 **标头:** afxWindowsManagerDialog.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)   
 [CMDIFrameWndEx::ShowWindowsDialog](../Topic/CMDIFrameWndEx::ShowWindowsDialog.md)