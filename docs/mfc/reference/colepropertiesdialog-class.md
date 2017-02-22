---
title: "COlePropertiesDialog Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COlePropertiesDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COlePropertiesDialog class"
  - "对话框, OLE"
  - "Object Properties dialog box"
  - "OLE 文档, 修改属性"
  - "OLE Object Properties dialog box"
  - "属性页, OLE"
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COlePropertiesDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装Windows通用OLE对象属性对话框。  
  
## 语法  
  
```  
  
class COlePropertiesDialog : public COleDialog  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COlePropertiesDialog::COlePropertiesDialog](../Topic/COlePropertiesDialog::COlePropertiesDialog.md)|构造 `COlePropertiesDialog` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COlePropertiesDialog::DoModal](../Topic/COlePropertiesDialog::DoModal.md)|显示对话框以及允许用户进行选择。|  
|[COlePropertiesDialog::OnApplyScale](../Topic/COlePropertiesDialog::OnApplyScale.md)|调用由框架，则此项目的缩放已更改。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COlePropertiesDialog::m\_gp](../Topic/COlePropertiesDialog::m_gp.md)|用于初始化框架 `COlePropertiesDialog` 对象的“常规”页。|  
|[COlePropertiesDialog::m\_lp](../Topic/COlePropertiesDialog::m_lp.md)|用于初始化框架 `COlePropertiesDialog` 对象的“链接”页。|  
|[COlePropertiesDialog::m\_op](../Topic/COlePropertiesDialog::m_op.md)|用于初始化框架 `COlePropertiesDialog` 对象。|  
|[COlePropertiesDialog::m\_psh](../Topic/COlePropertiesDialog::m_psh.md)|使用的结构中添加其他自定义属性页。|  
|[COlePropertiesDialog::m\_vp](../Topic/COlePropertiesDialog::m_vp.md)|用于的结构自定义 `COlePropertiesDialog` 对象的“视图”页。|  
  
## 备注  
 通用OLE对象属性对话框提供一种简便方法显示，并修改OLE的属性文档项目的某些符合Windows标准。  （如果项目被链接\)，这些属性包括，除了其他模板之外，有关文档项表示文件的显示图标和图像缩放的信息，有关项目链接的选项卡和信息。  
  
 使用 `COlePropertiesDialog` 构造函数，若要使用 `COlePropertiesDialog` 对象，请首先创建对象。  在对话框中构造完成后，调用 `DoModal` 成员函数显示对话框并允许用户修改项目的所有属性。  `DoModal` 返回用户是否选择了“确定” \(**IDOK**\) 或移除 \(**IDCANCEL**\) 按钮。  除"和"取消"按钮外，还有应用按钮。  当用户选择时将应用，所做的任何更改到文档项目的属性会应用于该项目，并自动更新其图像，但是，保持有效。  
  
 [m\_psh](../Topic/COlePropertiesDialog::m_psh.md) 数据成员是指向 **PROPSHEETHEADER** 结构，因此，您不会显式在许多情况下需要访问它。  例外情况是您需要在默认常规、视图和链接页以外的其他属性页。  在这种情况下，可以修改 `m_psh` 数据成员在调用 `DoModal` 成员函数之前将您的自定义页。  
  
 有关OLE对话框的更多信息，请参见文章 [在OLE的对话框](../../mfc/dialog-boxes-in-ole.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePropertiesDialog`  
  
## 要求  
 **Header:** afxodlgs.h  
  
## 请参阅  
 [MFC CIRC示例](../../top/visual-cpp-samples.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDialog Class](../../mfc/reference/coledialog-class.md)   
 [CPropertyPage Class](../../mfc/reference/cpropertypage-class.md)