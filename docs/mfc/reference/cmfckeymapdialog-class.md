---
title: "CMFCKeyMapDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCKeyMapDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCKeyMapDialog class"
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCKeyMapDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCKeyMapDialog` 选件类支持控制该映射命令将键盘上的键。  
  
## 语法  
  
```  
class CMFCKeyMapDialog : public CDialogEx  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCKeyMapDialog::CMFCKeyMapDialog](../Topic/CMFCKeyMapDialog::CMFCKeyMapDialog.md)|构造 `CMFCKeyMapDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCKeyMapDialog::DoModal](../Topic/CMFCKeyMapDialog::DoModal.md)|显示映射对话框的键盘。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCKeyMapDialog::FormatItem](../Topic/CMFCKeyMapDialog::FormatItem.md)|调用由框架生成描述一个键映射的字符串。  默认情况下，该字符串包含命令名、热键和使用热键说明。|  
|[CMFCKeyMapDialog::GetCommandKeys](../Topic/CMFCKeyMapDialog::GetCommandKeys.md)|检索包含热键列表与该指定的命令的字符串。|  
|[CMFCKeyMapDialog::OnInsertItem](../Topic/CMFCKeyMapDialog::OnInsertItem.md)|调用由框架，在新项插入到内部列表之前支持映射控件的键盘的控件。|  
|[CMFCKeyMapDialog::OnPrintHeader](../Topic/CMFCKeyMapDialog::OnPrintHeader.md)|调用由框架打印键盘映射的标头在新页。|  
|[CMFCKeyMapDialog::OnPrintItem](../Topic/CMFCKeyMapDialog::OnPrintItem.md)|调用由框架打印映射项的键盘。|  
|[CMFCKeyMapDialog::OnSetColumns](../Topic/CMFCKeyMapDialog::OnSetColumns.md)|调用由框架设置列的标题在内部列表中支持映射控件的键盘的控件。|  
|[CMFCKeyMapDialog::PrintKeyMap](../Topic/CMFCKeyMapDialog::PrintKeyMap.md)|调用由结构，当用户单击 **打印** 按钮。|  
|[CMFCKeyMapDialog::SetColumnsWidth](../Topic/CMFCKeyMapDialog::SetColumnsWidth.md)|调用由框架将列的宽度在内部的列表中支持映射控件的键盘的控件。|  
  
## 备注  
 使用 `CMFCKeyMapDialog` 选件类实现映射对话框的可调整大小的键盘。  对话框使用一个列表视图控件显示键盘快捷键及其关联的命令。  
  
 若要使用 `CMFCKeyMapDialog` 选件类在应用程序中，通过在指向主框架窗口作为参数传递给 `CMFCKeyMapDialog` 构造函数。  然后调用 `DoModal` 方法启动一个模式对话框。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)  
  
## 要求  
 **标头:** afxkeymapdialog.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md)