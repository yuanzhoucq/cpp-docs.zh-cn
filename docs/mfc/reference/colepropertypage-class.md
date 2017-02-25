---
title: "COlePropertyPage Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COlePropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COlePropertyPage class"
  - "自定义控件 [MFC], 属性"
  - "displaying properties"
  - "OLE property pages"
  - "属性 [C++], 显示"
  - "属性页, OLE"
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# COlePropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于显示自定义控件的属性在图形界面的，与对话框。  
  
## 语法  
  
```  
class AFX_NOVTABLE COlePropertyPage : public CDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COlePropertyPage::COlePropertyPage](../Topic/COlePropertyPage::COlePropertyPage.md)|构造 `COlePropertyPage` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COlePropertyPage::GetControlStatus](../Topic/COlePropertyPage::GetControlStatus.md)|指示用户是否修改了控件的值。|  
|[COlePropertyPage::GetObjectArray](../Topic/COlePropertyPage::GetObjectArray.md)|返回属性页编辑的对象数组。|  
|[COlePropertyPage::GetPageSite](../Topic/COlePropertyPage::GetPageSite.md)|返回指向属性页的 `IPropertyPageSite` 接口。|  
|[COlePropertyPage::IgnoreApply](../Topic/COlePropertyPage::IgnoreApply.md)|确定哪些控件不支持将按钮。|  
|[COlePropertyPage::IsModified](../Topic/COlePropertyPage::IsModified.md)|指示用户是否已修改属性页。|  
|[COlePropertyPage::OnEditProperty](../Topic/COlePropertyPage::OnEditProperty.md)|调用由结构，当用户编辑属性。|  
|[COlePropertyPage::OnHelp](../Topic/COlePropertyPage::OnHelp.md)|调用由结构，当用户调用帮助。|  
|[COlePropertyPage::OnInitDialog](../Topic/COlePropertyPage::OnInitDialog.md)|调用由结构，当属性页初始化。|  
|[COlePropertyPage::OnObjectsChanged](../Topic/COlePropertyPage::OnObjectsChanged.md)|调用由框架，而另一个OLE控件，新的属性，如选择。|  
|[COlePropertyPage::OnSetPageSite](../Topic/COlePropertyPage::OnSetPageSite.md)|调用由结构，当属性框架提供页的网站。|  
|[COlePropertyPage::SetControlStatus](../Topic/COlePropertyPage::SetControlStatus.md)|设置指示用户是否的标志修改了控件的值。|  
|[COlePropertyPage::SetDialogResource](../Topic/COlePropertyPage::SetDialogResource.md)|设置属性页的对话框资源。|  
|[COlePropertyPage::SetHelpInfo](../Topic/COlePropertyPage::SetHelpInfo.md)|设置属性页的简短帮助文本、其帮助文件的名称及其帮助上下文。|  
|[COlePropertyPage::SetModifiedFlag](../Topic/COlePropertyPage::SetModifiedFlag.md)|设置指示用户是否的标志修改了属性页。|  
|[COlePropertyPage::SetPageName](../Topic/COlePropertyPage::SetPageName.md)|设置属性页的名称\(说明）。|  
  
## 备注  
 例如，属性页可以包含允许用户查看和修改控件的声明属性的编辑控件。  
  
 每个自定义或库存控件属性可以具有如果需要可使控件的用户查看当前属性值和修改该值的对话框控件。  
  
 有关使用 `COlePropertyPage`的更多信息，请参见文章 [ActiveX控件:属性页](../../mfc/mfc-activex-controls-property-pages.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `COlePropertyPage`  
  
## 要求  
 **Header:** afxctl.h  
  
## 请参阅  
 [MFC示例CIRC3](../../top/visual-cpp-samples.md)   
 [MFC示例TESTHELP](../../top/visual-cpp-samples.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)