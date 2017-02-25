---
title: "COleDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDialog class"
  - "对话框, OLE"
  - "OLE 对话框, 基类"
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# COleDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于OLE提供常用功能的到对话框。  
  
## 语法  
  
```  
class COleDialog : public CCommonDialog  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleDialog::GetLastError](../Topic/COleDialog::GetLastError.md)|获取错误代码返回由对话框。|  
  
## 备注  
 Microsoft基础选件类库提供从 `COleDialog`派生的几选件类:  
  
-   [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)  
  
-   [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)  
  
-   [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)  
  
-   [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
-   [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)  
  
-   [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)  
  
-   [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)  
  
-   [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)  
  
-   [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)  
  
 有关OLE特定对话框的更多信息，请参见文章 [在OLE的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `COleDialog`  
  
## 要求  
 **Header:** afxodlgs.h  
  
## 请参阅  
 [CCommonDialog Class](../../mfc/reference/ccommondialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)