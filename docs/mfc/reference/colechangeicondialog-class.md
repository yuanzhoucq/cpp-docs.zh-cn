---
title: "COleChangeIconDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleChangeIconDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Change Icon dialog box"
  - "COleChangeIconDialog class"
  - "对话框, OLE"
  - "OLE Change Icon dialog box"
  - "OLE 对话框, Change Icon"
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleChangeIconDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于OLE更改图标对话框。  
  
## 语法  
  
```  
class COleChangeIconDialog : public COleDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleChangeIconDialog::COleChangeIconDialog](../Topic/COleChangeIconDialog::COleChangeIconDialog.md)|构造 `COleChangeIconDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleChangeIconDialog::DoChangeIcon](../Topic/COleChangeIconDialog::DoChangeIcon.md)|执行在对话框中指定的更改。|  
|[COleChangeIconDialog::DoModal](../Topic/COleChangeIconDialog::DoModal.md)|显示OLE 2更改图标对话框。|  
|[COleChangeIconDialog::GetIconicMetafile](../Topic/COleChangeIconDialog::GetIconicMetafile.md)|具有处理该图元文件与此项目的图标样式的窗体。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleChangeIconDialog::m\_ci](../Topic/COleChangeIconDialog::m_ci.md)|控件的行为的结构。|  
  
## 备注  
 当您要调用此对话框时，请创建选件类 `COleChangeIconDialog` 对象。  在 `COleChangeIconDialog` 对象构造后，可以使用 [m\_ci](../Topic/COleChangeIconDialog::m_ci.md) framework初始化控件值或状态在对话框中。  `m_ci` 机制是类型 **OLEUICHANGEICON**。  有关使用此对话框选件类的更多信息，请参见 [DoModal](../Topic/COleChangeIconDialog::DoModal.md) 成员函数。  
  
 有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) 结构。  
  
 有关OLE特定对话框的更多信息，请参见文章 [在OLE的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeIconDialog`  
  
## 要求  
 **Header:** afxodlgs.h  
  
## 请参阅  
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)