---
title: "CMFCDesktopAlertDialog Class | Microsoft Docs"
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
  - "CMFCDesktopAlertDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDesktopAlertDialog class"
ms.assetid: a53c60aa-9607-485b-b826-ec64962075f6
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDesktopAlertDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

结合使用 `CMFCDesktopAlertDialog` 类和 [CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)以在弹出窗口中显示自定义对话框。  
  
## 语法  
  
```  
class CMFCDesktopAlertDialog : public CDialogEx  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCDesktopAlertDialog::CreateFromParams](../Topic/CMFCDesktopAlertDialog::CreateFromParams.md)||  
|[CMFCDesktopAlertDialog::GetDlgSize](../Topic/CMFCDesktopAlertDialog::GetDlgSize.md)||  
|[CMFCDesktopAlertDialog::HasFocus](../Topic/CMFCDesktopAlertDialog::HasFocus.md)||  
|[CMFCDesktopAlertDialog::PreTranslateMessage](../Topic/CMFCDesktopAlertDialog::PreTranslateMessage.md)|（重写 `CDialogEx::PreTranslateMessage`。）|  
  
### 备注  
 执行以下步骤以在弹出窗口中显示自定义对话框：  
  
1.  从 `CMFCDesktopAlertDialog` 派生一个类。  
  
2.  在项目的资源中创建子对话框模板。  
  
3.  调用具有对话框模板资源 ID 的 [CMFCDesktopAlertWnd::Create](../Topic/CMFCDesktopAlertWnd::Create.md) 以及指向派生类的运行时类信息的指针作为参数。  
  
4.  对自定义对话框进行编程以处理来自托管控件的所有通知，或对托管控件进行编程以直接处理这些通知。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)  
  
## 要求  
 **标头：** afxDesktopAlertDialog.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)   
 [CMFCDesktopAlertWndInfo Class](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [CDialogEx Class](../../mfc/reference/cdialogex-class.md)