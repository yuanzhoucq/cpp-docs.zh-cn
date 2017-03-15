---
title: "MFC ActiveX 控件：属性页 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPropertyPageDialog 类"
  - "DDP_ 函数"
  - "DoDataExchange 方法"
  - "MFC ActiveX 控件, 属性"
  - "MFC ActiveX 控件, 属性页"
  - "OLEIVERB_PROPERTIES"
  - "属性页, MFC ActiveX 控件"
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# MFC ActiveX 控件：属性页
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

属性页允许 ActiveX 控件用户查看和更改 ActiveX 控件属性。  这些属性通过调用控件属性对话框访问，该对话框包含一个或多个属性页，属性页提供用于查看和编辑控件属性的自定义图形界面。  
  
 ActiveX 控件的属性页以两种方式显示：  
  
-   当控件的属性谓词 \(**OLEIVERB\_PROPERTIES**\) 被调用时，控件打开包含控件属性页的模式属性对话框。  
  
-   容器中显示选定控件的属性页自身的无模式对话框。  
  
 属性对话框 \(见下图说明\) 包含显示当前属性页、在属性页之间切换的标签、执行常规任务按钮集合（如关闭属性页对话框、取消任何更改、立即应用更改于 ActiveX 控件）的区域。  
  
 ![Circ3 的“属性”对话框](../mfc/media/vc373i1.png "vc373I1")  
属性对话框  
  
 本文包含与在ActiveX 控件中使用属性页有关的主题。  这些元素包括：  
  
-   [实现 ActiveX 控件的默认属性页](#_core_implementing_the_default_property_page)  
  
-   [将控件添加到属性页](#_core_adding_controls_to_a_property_page)  
  
-   [自定义 DoDataExchange 函数](#_core_customizing_the_dodataexchange_function)  
  
 有关在 ActiveX 控件使用属性页的详细息，请参见下列文章：  
  
-   [MFC ActiveX 控件：添加另一自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 有关在MFC 应用程序使用属性表而不是ActiveX 控件的信息，请参见 [属性表](../mfc/property-sheets-mfc.md)。  
  
##  <a name="_core_implementing_the_default_property_page"></a> 实现默认属性页  
 如果使用 ActiveX 控件向导创建窗体项目，ActiveX 控件向导可从 [COlePropertyPage Class](../mfc/reference/colepropertypage-class.md)派生的控件提供默认属性页类。  最初，该属性页是空白，但可以添加任何对话框控件或一组控件。  由于默认情况下 ActiveX 控件向导仅创建属性页类 \(也从派生自`COlePropertyPage`\)，必须使用类视图创建额外的属性页类。  有关此过程的更多信息，请参见[MFC ActiveX 控件：添加另一自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)。  
  
 实现属性页 \(在这种情况下，默认值\) 具有三步过程：  
  
#### 实现属性页  
  
1.  向该控件项目添加`COlePropertyPage`\-派生类。  如果项目是使用 ActiveX 控件向导 \(如本例\)创建的，默认属性页类已经存在。  
  
2.  使用对话框编辑器添加所有控件与属性页模板。  
  
3.  自定义 `COlePropertyPage`的 `DoDataExchange` 函数 \- 在属性页控件和 ActiveX 控件之间交换派生类的值。  
  
 为了进行演示，下面过程使用一个简单控件 \(名为“示例”。\)  使用创建 ActiveX 控件向导创建实例，示例中只包含股票标题属性。  
  
##  <a name="_core_adding_controls_to_a_property_page"></a> 将控件添加到属性页  
  
#### 将控件添加到属性页  
  
1.  打开控件的项目后，请打开资源视图。  
  
2.  双击 **对话框** 目录图标。  
  
3.  打开 **IDD\_PROPPAGE\_SAMPLE** 对话框。  
  
     ActiveX 控件向导追加项目名称到对话框 ID 的结尾，在这种情况下的示例。  
  
4.  将从工具箱选择的控件拖到对话框区域。  
  
5.  在本示例中，文本标签控件“标题：”并带有 **IDC\_CAPTION** 标识符的编辑框控件即可。  
  
6.  在工具栏上，单击 **保存**，以保存更改。  
  
 既然已修改用户界面，则需要链接具有标题属性的编辑框。  这在以下部分完成通过编辑 `CSamplePropPage::DoDataExchange` 函数。  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a> 自定义 DoDataExchange 函数  
 属性页 [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md)函数允许在控件中链接实际属性值的属性页。  若要建立链接，必须映射相应属性页字段到各自控件属性。  
  
 使用属性页 **DDP\_** 函数实现以下映射。  **DDP\_** 函数的工作方式与在标准 MFC 对话框的 **DDX\_** 函数相似，但有一个例外。  除了对成员变量的引用之外，**DDP\_** 函数采用控件属性的名称。  以下是 `DoDataExchange` 函数的典型属性页。  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/CPP/mfc-activex-controls-property-pages_1.cpp)]  
  
 使用 `DDP_TEXT` 函数，此函数把`m_caption` 成员变量的属性页与标题联系起来。  
  
 在将属性页控件插入后，需要按如上所述使用 **DDP\_Text** 函数在属性页控件、 `IDC_CAPTION`和实际控件属性、标题之间建立链接，。  
  
 [属性页](../mfc/reference/property-pages-mfc.md)对其他对话框控件类型可用，如复选框、单选按钮和列表框。  下表列出整组属性页 **DDP\_** 函数及其用途：  
  
### 属性页函数  
  
|函数名|使用此函数链接|  
|---------|-------------|  
|`DDP_CBIndex`|一组合框中控件属性的选定字符串索引。|  
|`DDP_CBString`|一组合框中控件属性的选定字符串。  选中的字符串可以以相同的字母开头，如属性值，但不需要完全匹配它。|  
|`DDP_CBStringExact`|一组合框中控件属性的选定字符串。  选定的字符串和属性字符串值必须完全匹配。|  
|`DDP_Check`|具有控件属性的复选框。|  
|`DDP_LBIndex`|一列表框中控件属性的选定字符串。|  
|`DDP_LBString`|一列表框中控件属性的选定字符串。  选中的字符串可以以相同的字母开头，如属性值，但不需要完全匹配它。|  
|`DDP_LBStringExact`|一列表框中控件属性的选定字符串。  选定的字符串和属性字符串值必须完全匹配。|  
|`DDP_Radio`|设置控件属性的一个单选按钮。|  
|**DDP\_Text**|控件属性的文本。|  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [COlePropertyPage Class](../mfc/reference/colepropertypage-class.md)