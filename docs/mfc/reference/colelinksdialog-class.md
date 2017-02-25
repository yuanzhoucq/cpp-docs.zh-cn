---
title: "COleLinksDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleLinksDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleLinksDialog class"
  - "对话框, OLE"
  - "Edit Links dialog box"
  - "OLE Edit Links dialog box"
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleLinksDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于OLE编辑链接对话框。  
  
## 语法  
  
```  
class COleLinksDialog : public COleDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleLinksDialog::COleLinksDialog](../Topic/COleLinksDialog::COleLinksDialog.md)|构造 `COleLinksDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleLinksDialog::DoModal](../Topic/COleLinksDialog::DoModal.md)|显示OLE编辑链接对话框。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleLinksDialog::m\_el](../Topic/COleLinksDialog::m_el.md)|控件对话框的行为类型 **OLEUIEDITLINKS** 的结构。|  
  
## 备注  
 当您要调用此对话框时，请创建选件类 `COleLinksDialog` 对象。  在 `COleLinksDialog` 对象构造后，可以使用 [m\_el](../Topic/COleLinksDialog::m_el.md) framework初始化控件值或状态在对话框中。  `m_el` 机制是类型 **OLEUIEDITLINKS**。  有关使用此对话框选件类的更多信息，请参见 [DoModal](../Topic/COleLinksDialog::DoModal.md) 成员函数。  
  
> [!NOTE]
>  应用程序向导生成的容器代码使用此选件类。  
  
 有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) 结构。  
  
 有关OLE特定对话框的更多信息，请参见文章 [在OLE的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleLinksDialog`  
  
## 要求  
 **Header:** afxodlgs.h  
  
## 请参阅  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)