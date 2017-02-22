---
title: "CPropertySheet Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPropertySheet"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPropertySheet class"
  - "对话框, 选项卡"
  - "属性表, CPropertySheet class"
  - "选项卡对话框"
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CPropertySheet Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示属性表，也称为"选项"对话框。  
  
## 语法  
  
```  
class CPropertySheet : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPropertySheet::CPropertySheet](../Topic/CPropertySheet::CPropertySheet.md)|构造 `CPropertySheet` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPropertySheet::AddPage](../Topic/CPropertySheet::AddPage.md)|页添加到特性表。|  
|[CPropertySheet::Construct](../Topic/CPropertySheet::Construct.md)|构造 `CPropertySheet` 对象。|  
|[CPropertySheet::Create](../Topic/CPropertySheet::Create.md)|显示非模式属性表。|  
|[CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md)|显示一个模式属性表。|  
|[CPropertySheet::EnableStackedTabs](../Topic/CPropertySheet::EnableStackedTabs.md)|指示属性表是否使用堆叠或滚动选项。|  
|[CPropertySheet::EndDialog](../Topic/CPropertySheet::EndDialog.md)|停止属性表。|  
|[CPropertySheet::GetActiveIndex](../Topic/CPropertySheet::GetActiveIndex.md)|检索属性表的事件页的索引。|  
|[CPropertySheet::GetActivePage](../Topic/CPropertySheet::GetActivePage.md)|返回页事件对象。|  
|[CPropertySheet::GetPage](../Topic/CPropertySheet::GetPage.md)|检索指向指定的页。|  
|[CPropertySheet::GetPageCount](../Topic/CPropertySheet::GetPageCount.md)|检索页的数量在属性表的。|  
|[CPropertySheet::GetPageIndex](../Topic/CPropertySheet::GetPageIndex.md)|检索属性表的指定页的索引。|  
|[CPropertySheet::GetTabControl](../Topic/CPropertySheet::GetTabControl.md)|检索指向选项卡控件。|  
|[CPropertySheet::MapDialogRect](../Topic/CPropertySheet::MapDialogRect.md)|将矩形的对话框单位转换为屏幕单元。|  
|[CPropertySheet::OnInitDialog](../Topic/CPropertySheet::OnInitDialog.md)|扩充属性表初始化的重写。|  
|[CPropertySheet::PressButton](../Topic/CPropertySheet::PressButton.md)|模拟指定的按钮选择在属性表的。|  
|[CPropertySheet::RemovePage](../Topic/CPropertySheet::RemovePage.md)|从属性表中移除页。|  
|[CPropertySheet::SetActivePage](../Topic/CPropertySheet::SetActivePage.md)|以编程方式设置页事件对象。|  
|[CPropertySheet::SetFinishText](../Topic/CPropertySheet::SetFinishText.md)|设置完成按钮的文本。|  
|[CPropertySheet::SetTitle](../Topic/CPropertySheet::SetTitle.md)|设置属性表的说明。|  
|[CPropertySheet::SetWizardButtons](../Topic/CPropertySheet::SetWizardButtons.md)|启用向导按钮。|  
|[CPropertySheet::SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md)|启动向导模式。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPropertySheet::m\_psh](../Topic/CPropertySheet::m_psh.md)|Windows [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) 结构。  提供对基本的属性表参数。|  
  
## 备注  
 属性表包括 `CPropertySheet` 对象和一个或多 [CPropertyPage](../../mfc/reference/cpropertypage-class.md) 对象。  框架显示属性表为具有的窗口包含当前选定的页的设置选项卡索引和区域。  通过使用相应的选项，用户导航到特定页。  
  
 `CPropertySheet` 提供了在 [!INCLUDE[Win98](../../mfc/reference/includes/win98_md.md)] 和Windows NT引入的展开的 [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) framework支持2000。  结构包含使用“水印” background位图，支持的其他标志和成员。  
  
 若要自动显示这些新图像中的属性表对象，请将位图和调色板图像的有效值在调用 [CPropertySheet::Construct](../Topic/CPropertySheet::Construct.md) 或 [CPropertySheet::CPropertySheet](../Topic/CPropertySheet::CPropertySheet.md)。  
  
 即使 `CPropertySheet` 从 [CDialog](../../mfc/reference/cdialog-class.md)未派生，管理 `CPropertySheet` 对象是与托管 `CDialog` 对象。  例如，特性表的创建需要两部分:构造调用构造函数，然后调用一个模式属性表的非模式属性表的 [DoModal](../Topic/CPropertySheet::DoModal.md) 或 [创建](../Topic/CPropertySheet::Create.md)。  `CPropertySheet` 具有构造函数的两种类型: [CPropertySheet::Construct](../Topic/CPropertySheet::Construct.md) 和 [CPropertySheet::CPropertySheet](../Topic/CPropertySheet::CPropertySheet.md)。  
  
 当构造 `CPropertySheet` 对象时，某些 [窗口样式](../../mfc/reference/window-styles.md) 可能导致首次异常发生。  在页中创建之前，会产生尝试用个系统更改属性表的样式。  若要避免此异常，请确保将以下样式，当您创建 `CPropertySheet`时:  
  
-   DS\_3DLOOK  
  
-   DS\_CONTROL  
  
-   WS\_CHILD  
  
-   WS\_TABSTOP  
  
 以下样式是可选的和不会导致首次异常:  
  
-   DS\_SHELLFONT  
  
-   DS\_LOCALEDIT  
  
-   WS\_CLIPCHILDREN  
  
 所有其他 `Window Styles` 禁止，您不应启用它们。  
  
 在 `CPropertySheet` 对象和外部对象之间交换数据类似于 `CDialog` 对象交换数据。  重要差别在于属性表的设置通常是 `CPropertyPage` 对象的成员变量而不是 `CPropertySheet` 对象。  
  
 可以创建一个名为"选项"对话框的类型，包括使用属性页序列的一个属性表通过操作步骤或者用户，如一组计算机或创建简讯。  在一个向导类型的选项"对话框中，属性页没有选项，因此，只有一个属性页次可见。  此外，而不是 **好** 和 **现在应用** 按钮，一个向导类型的选项"对话框具有一个 **返回** 按钮、一个 **接下来** 或 **完成** 按钮、一个 **取消** 按钮和一个 **帮助** 按钮。  
  
 若要创建一个向导类型的对话框，请按照您应在执行创建标准属性表的相同步骤，但是，调用 [SetWizardMode](../Topic/CPropertySheet::SetWizardMode.md)，在调用 [DoModal](../Topic/CPropertySheet::DoModal.md)之前。  若要启用向导按钮，请调用 [SetWizardButtons](../Topic/CPropertySheet::SetWizardButtons.md)，使用标志自定义其功能和外观。  该用户执行到向导的最后一页后，操作若要启用 **完成** 按钮，请调用 [SetFinishText](../Topic/CPropertySheet::SetFinishText.md)。  
  
 有关如何使用 `CPropertySheet` 对象的更多信息，请参见文章 [属性表和属性页](../../mfc/property-sheets-and-property-pages-in-mfc.md)。  此外，请参见知识库文章Q146916:HOWTO:在标准按钮和文章Q300606创建无模式CPropertySheet:HOWTO:设计一个可调整大小的MFC属性表。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPropertySheet`  
  
## 要求  
 **标头:** afxdlgs.h  
  
## 请参阅  
 [MFC示例CMNCTRL1](../../top/visual-cpp-samples.md)   
 [MFC示例CMNCTRL2](../../top/visual-cpp-samples.md)   
 [MFC示例PROPDLG](../../top/visual-cpp-samples.md)   
 [MFC SNAPVW示例](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)