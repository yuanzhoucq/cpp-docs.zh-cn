---
title: "COleBusyDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleBusyDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleBusyDialog class"
  - "Server Busy dialog box"
  - "Server Not Responding dialog box"
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleBusyDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于OLE服务器未响应或服务器忙对话框。  
  
## 语法  
  
```  
class COleBusyDialog : public COleDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleBusyDialog::COleBusyDialog](../Topic/COleBusyDialog::COleBusyDialog.md)|构造 `COleBusyDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleBusyDialog::DoModal](../Topic/COleBusyDialog::DoModal.md)|显示OLE服务器忙对话框。|  
|[COleBusyDialog::GetSelectionType](../Topic/COleBusyDialog::GetSelectionType.md)|确定在对话框中所做的选定内容。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleBusyDialog::m\_bz](../Topic/COleBusyDialog::m_bz.md)|控件对话框的行为类型 **OLEUIBUSY** 的结构。|  
  
## 备注  
 当您要调用这些对话框时，请创建选件类 `COleBusyDialog` 对象。  在 `COleBusyDialog` 对象构造后，可以使用 [m\_bz](../Topic/COleBusyDialog::m_bz.md) framework初始化控件值或状态在对话框中。  `m_bz` 机制是类型 **OLEUIBUSY**。  有关使用此对话框选件类的更多信息，请参见 [DoModal](../Topic/COleBusyDialog::DoModal.md) 成员函数。  
  
> [!NOTE]
>  应用程序向导生成的容器代码使用此选件类。  
  
 有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUIBUSY](http://msdn.microsoft.com/library/windows/desktop/ms682493) 结构。  
  
 有关OLE特定对话框的更多信息，请参见文章 [在OLE的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleBusyDialog`  
  
## 要求  
 **Header:** afxodlgs.h  
  
## 请参阅  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)