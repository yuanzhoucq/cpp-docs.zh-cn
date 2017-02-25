---
title: "COlePasteSpecialDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COlePasteSpecialDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COlePasteSpecialDialog class"
  - "对话框, Paste Special"
  - "OLE Paste Special dialog box"
  - "Paste Special dialog box"
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COlePasteSpecialDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于OLE粘贴特定的对话框。  
  
## 语法  
  
```  
  
class COlePasteSpecialDialog : public COleDialog  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COlePasteSpecialDialog::COlePasteSpecialDialog](../Topic/COlePasteSpecialDialog::COlePasteSpecialDialog.md)|构造 `COlePasteSpecialDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COlePasteSpecialDialog::AddFormat](../Topic/COlePasteSpecialDialog::AddFormat.md)|添加自定义格式到您的应用程序能粘贴格式的列表。|  
|[COlePasteSpecialDialog::AddLinkEntry](../Topic/COlePasteSpecialDialog::AddLinkEntry.md)|添加新项。支持的剪贴板格式列表。|  
|[COlePasteSpecialDialog::AddStandardFormats](../Topic/COlePasteSpecialDialog::AddStandardFormats.md)|添加 **CF\_BITMAP**，**CF\_DIB**，`CF_METAFILEPICT`，并选择对您的应用程序能粘贴格式的列表 `CF_LINKSOURCE`。|  
|[COlePasteSpecialDialog::CreateItem](../Topic/COlePasteSpecialDialog::CreateItem.md)|使用指定的格式，容器创建项目文档。|  
|[COlePasteSpecialDialog::DoModal](../Topic/COlePasteSpecialDialog::DoModal.md)|显示OLE粘贴特定的对话框。|  
|[COlePasteSpecialDialog::GetDrawAspect](../Topic/COlePasteSpecialDialog::GetDrawAspect.md)|指示是否绘制项目作为图标。|  
|[COlePasteSpecialDialog::GetIconicMetafile](../Topic/COlePasteSpecialDialog::GetIconicMetafile.md)|具有处理该图元文件与此项目的图标样式的窗体。|  
|[COlePasteSpecialDialog::GetPasteIndex](../Topic/COlePasteSpecialDialog::GetPasteIndex.md)|获取由用户选择可用粘贴选项的索引。|  
|[COlePasteSpecialDialog::GetSelectionType](../Topic/COlePasteSpecialDialog::GetSelectionType.md)|获取选定内容的类型中选择。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COlePasteSpecialDialog::m\_ps](../Topic/COlePasteSpecialDialog::m_ps.md)|控件对话框的函数类型 **OLEUIPASTESPECIAL** 的结构。|  
  
## 备注  
 当您要调用此对话框时，请创建选件类 `COlePasteSpecialDialog` 对象。  在 `COlePasteSpecialDialog` 对象构造后，可以使用 [AddFormat](../Topic/COlePasteSpecialDialog::AddFormat.md) 和 [AddStandardFormats](../Topic/COlePasteSpecialDialog::AddStandardFormats.md) 成员函数添加剪贴板格式到对话框。  还可以使用 [m\_ps](../Topic/COlePasteSpecialDialog::m_ps.md) framework初始化控件值或状态在对话框中。  `m_ps` 机制是类型 **OLEUIPASTESPECIAL**。  
  
 有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) 结构。  
  
 有关OLE特定对话框的更多信息，请参见文章 [在OLE的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePasteSpecialDialog`  
  
## 要求  
 **Header:** afxodlgs.h  
  
## 请参阅  
 [MFC示例OCLIENT](../../top/visual-cpp-samples.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)