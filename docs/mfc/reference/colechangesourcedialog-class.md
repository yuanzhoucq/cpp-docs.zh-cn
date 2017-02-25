---
title: "COleChangeSourceDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleChangeSourceDialog"
  - "OLEUICHANGESOURCE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleChangeSourceDialog class"
  - "对话框, OLE"
  - "OLE Change Source dialog box"
  - "OLE 对话框, Change Source"
  - "OleUIChangeSource structure"
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# COleChangeSourceDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于OLE更改源对话框。  
  
## 语法  
  
```  
class COleChangeSourceDialog : public COleDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleChangeSourceDialog::COleChangeSourceDialog](../Topic/COleChangeSourceDialog::COleChangeSourceDialog.md)|构造 `COleChangeSourceDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleChangeSourceDialog::DoModal](../Topic/COleChangeSourceDialog::DoModal.md)|显示OLE更改源对话框。|  
|[COleChangeSourceDialog::GetDisplayName](../Topic/COleChangeSourceDialog::GetDisplayName.md)|获取完整源代码显示名称。|  
|[COleChangeSourceDialog::GetFileName](../Topic/COleChangeSourceDialog::GetFileName.md)|从数据源名称获取文件名。|  
|[COleChangeSourceDialog::GetFromPrefix](../Topic/COleChangeSourceDialog::GetFromPrefix.md)|获取前面的源的标题。|  
|[COleChangeSourceDialog::GetItemName](../Topic/COleChangeSourceDialog::GetItemName.md)|从数据源名称获取项目名称。|  
|[COleChangeSourceDialog::GetToPrefix](../Topic/COleChangeSourceDialog::GetToPrefix.md)|获取新的源的标题|  
|[COleChangeSourceDialog::IsValidSource](../Topic/COleChangeSourceDialog::IsValidSource.md)|指示该数据源是否有效。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleChangeSourceDialog::m\_cs](../Topic/COleChangeSourceDialog::m_cs.md)|控件的行为的结构。|  
  
## 备注  
 当您要调用此对话框时，请创建选件类 `COleChangeSourceDialog` 对象。  在 `COleChangeSourceDialog` 对象构造后，可以使用 [m\_cs](../Topic/COleChangeSourceDialog::m_cs.md) framework初始化控件值或状态在对话框中。  `m_cs` 机制是类型 [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160)。  有关使用此对话框选件类的更多信息，请参见 [DoModal](../Topic/COleChangeSourceDialog::DoModal.md) 成员函数。  
  
 有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) 结构。  
  
 有关OLE特定对话框的更多信息，请参见文章 [在OLE的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeSourceDialog`  
  
## 要求  
 **Header:** afxodlgs.h  
  
## 请参阅  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)