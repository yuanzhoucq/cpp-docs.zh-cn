---
title: "CPropertyPage Class | Microsoft Docs"
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
  - "CPropertyPage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPropertyPage class"
  - "对话框, 选项卡"
  - "属性页, CPropertyPage class"
  - "选项卡对话框"
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
caps.latest.revision: 25
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPropertyPage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示属性表的各个页，也称为"选项"对话框。  
  
## 语法  
  
```  
class CPropertyPage : public CDialog  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPropertyPage::CPropertyPage](../Topic/CPropertyPage::CPropertyPage.md)|构造 `CPropertyPage` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPropertyPage::CancelToClose](../Topic/CPropertyPage::CancelToClose.md)|更改"确定"按钮将关闭，并且在一个模式属性表的页的上一个不可恢复的更改后禁用取消按钮。|  
|[CPropertyPage::Construct](../Topic/CPropertyPage::Construct.md)|构造 `CPropertyPage` 对象。  请使用 `Construct`，如果要指定自己的参数在运行时，或者，如果您使用数组。|  
|[CPropertyPage::GetPSP](../Topic/CPropertyPage::GetPSP.md)|检索Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) 结构与 `CPropertyPage` 对象。|  
|[CPropertyPage::OnApply](../Topic/CPropertyPage::OnApply.md)|调用由框架，当应用现在按时单击。|  
|[CPropertyPage::OnCancel](../Topic/CPropertyPage::OnCancel.md)|调用由结构，当单击"取消"按钮。|  
|[CPropertyPage::OnKillActive](../Topic/CPropertyPage::OnKillActive.md)|调用由结构，在当前页不再是事件页。  在此执行数据验证。|  
|[CPropertyPage::OnOK](../Topic/CPropertyPage::OnOK.md)|调用由框架，当"，现在期间应用或关闭键单击。|  
|[CPropertyPage::OnQueryCancel](../Topic/CPropertyPage::OnQueryCancel.md)|调用由框架，当单击"取消"按钮时和在该取消之前的。|  
|[CPropertyPage::OnReset](../Topic/CPropertyPage::OnReset.md)|调用由结构，当单击"取消"按钮。|  
|[CPropertyPage::OnSetActive](../Topic/CPropertyPage::OnSetActive.md)|调用由结构，当页发出事件页。|  
|[CPropertyPage::OnWizardBack](../Topic/CPropertyPage::OnWizardBack.md)|调用由结构，当后退按钮单击，在使用一个向导类型的属性表时。|  
|[CPropertyPage::OnWizardFinish](../Topic/CPropertyPage::OnWizardFinish.md)|调用由结构，在完成单击按钮，在使用一个向导类型的属性表时。|  
|[CPropertyPage::OnWizardNext](../Topic/CPropertyPage::OnWizardNext.md)|调用由结构，在下一个按钮单击，在使用一个向导类型的属性表时。|  
|[CPropertyPage::QuerySiblings](../Topic/CPropertyPage::QuerySiblings.md)|向前到特性表中的每页的消息。|  
|[CPropertyPage::SetModified](../Topic/CPropertyPage::SetModified.md)|调用激活或停用应用现在请按。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPropertyPage::m\_psp](../Topic/CPropertyPage::m_psp.md)|Windows [PROPSHEETPAGE](http://msdn.microsoft.com/library/windows/desktop/bb774548) 结构。  提供对基本属性页参数。|  
  
## 备注  
 与标准对话框，从每页的 `CPropertyPage` 派生选件类中的属性表。  若要使用 `CPropertyPage`派生的对象，请首先创建一 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) 对象，然后创建在属性表中的每页的对象。  调用每页的 [CPropertySheet::AddPage](../Topic/CPropertySheet::AddPage.md) 在页上，通过调用一个模式属性表的 [CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md) 然后显示非模式属性表的属性表或 [CPropertySheet::Create](../Topic/CPropertySheet::Create.md)。  
  
 可以创建一个名为"选项"对话框的类型，包括使用属性页序列的一个属性表通过操作步骤或者用户，如一组计算机或创建简讯。  在一个向导类型的选项"对话框中，属性页没有选项，因此，只有一个属性页次可见。  此外，而不是拥有良好和现在将应用按钮，一个向导类型的选项"对话框具有一个后退按钮，下列或完成按钮和"取消"按钮。  
  
 有关建立作为向导的一个属性表的更多信息，请参见 [CPropertySheet::SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md)。  有关使用 `CPropertyPage` 对象的更多信息，请参见文章 [属性表和属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CPropertyPage`  
  
## 要求  
 **Header:** afxdlgs.h  
  
## 请参阅  
 [MFC示例CMNCTRL1](../../top/visual-cpp-samples.md)   
 [MFC示例CMNCTRL2](../../top/visual-cpp-samples.md)   
 [MFC示例PROPDLG](../../top/visual-cpp-samples.md)   
 [MFC SNAPVW示例](../../top/visual-cpp-samples.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CPropertySheet Class](../../mfc/reference/cpropertysheet-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)   
 [CPropertySheet::SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md)