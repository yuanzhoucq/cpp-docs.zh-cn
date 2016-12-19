---
title: "COleUpdateDialog Class | Microsoft Docs"
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
  - "COleUpdateDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleUpdateDialog class"
  - "链接 [C++], 更新"
  - "OLE 对话框, Edit Link"
  - "OLE link updating"
  - "Update dialog"
  - "updating OLE links"
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleUpdateDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于OLE的一种特例编辑链接对话框，应使用，当需要更新在文档中仅存在于链接的或嵌入对象。  
  
## 语法  
  
```  
class COleUpdateDialog : public COleLinksDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleUpdateDialog::COleUpdateDialog](../Topic/COleUpdateDialog::COleUpdateDialog.md)|构造 `COleUpdateDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleUpdateDialog::DoModal](../Topic/COleUpdateDialog::DoModal.md)|在更新模式下显示 **编辑链接** 对话框。|  
  
## 备注  
 有关OLE特定对话框的更多信息，请参见文章 [在OLE的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
 `COleUpdateDialog`  
  
## 要求  
 **Header:** afxodlgs.h  
  
## 请参阅  
 [MFC示例OCLIENT](../../top/visual-cpp-samples.md)   
 [COleLinksDialog Class](../../mfc/reference/colelinksdialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleLinksDialog Class](../../mfc/reference/colelinksdialog-class.md)