---
title: "MFC ActiveX 控件： 属性页 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dde35df301c34a6c3a29c48d5ad145681b64a72e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-property-pages"></a>MFC ActiveX 控件：属性页
属性页允许 ActiveX 控件的用户查看和更改 ActiveX 控件属性。 通过调用控件的属性对话框中，其中包含一个或多个属性页可以用于查看和编辑控件属性提供自定义的图形界面访问这些属性。  
  
 ActiveX 控件属性页显示以下两种方式：  
  
-   当控件的属性谓词 (**OLEIVERB_PROPERTIES**) 是调用，控件打开一个模式属性对话框中，包含控件的属性页。  
  
-   容器可以显示显示所选控件的属性页自己无模式对话框。  
  
 （下图中所示） 的属性对话框包含用于显示当前的属性页中，为属性页的按钮执行常见任务，如关闭属性页对话框中，集合之间切换的选项卡的区域取消任何做的更改，或立即将任何更改应用到 ActiveX 控件。  
  
 ![Circ3 的属性对话框](../mfc/media/vc373i1.gif "vc373i1")  
属性对话框中  
  
 本文介绍如何与 ActiveX 控件中使用属性页相关的主题。 这些方法包括：  
  
-   [实现 ActiveX 控件的默认属性页](#_core_implementing_the_default_property_page)  
  
-   [将控件添加到属性页](#_core_adding_controls_to_a_property_page)  
  
-   [自定义 DoDataExchange 函数](#_core_customizing_the_dodataexchange_function)  
  
 在 ActiveX 控件中使用属性页的详细信息，请参阅以下文章：  
  
-   [MFC ActiveX 控件：添加另一自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
-   [MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
 有关使用属性表以外 ActiveX 控件的 MFC 应用程序中的信息，请参阅[属性表](../mfc/property-sheets-mfc.md)。  
  
##  <a name="_core_implementing_the_default_property_page"></a>实现的默认属性页  
 如果你使用 ActiveX 控件向导创建控件项目，则 ActiveX 控件向导提供的默认属性页类派生的控件[COlePropertyPage 类](../mfc/reference/colepropertypage-class.md)。 最初，此属性页为空白，但你可以向其添加任何对话框控件或组控件。 因为 ActiveX 控件向导默认情况下，其他属性页类创建只有一个属性页类 (还派生自`COlePropertyPage`) 必须使用类视图创建。 有关此过程的详细信息，请参阅[MFC ActiveX 控件： 添加另一个自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)。  
  
 实现属性页 （在此情况下，默认值） 是一个三步骤过程：  
  
#### <a name="to-implement-a-property-page"></a>若要实现的属性页  
  
1.  添加`COlePropertyPage`-向控件项目派生类。 如果项目使用 （如下所示这种情况下） ActiveX 控件向导创建的默认属性页类已存在。  
  
2.  使用对话框编辑器将任何控件添加到属性页模板。  
  
3.  自定义`DoDataExchange`函数`COlePropertyPage`-派生类来交换的属性页控件和 ActiveX 控件之间的值。  
  
 例如目的，以下过程使用简单控件 （名为"Sample"）。 示例使用 ActiveX 控件向导创建，并包含仅常用的标题属性。  
  
##  <a name="_core_adding_controls_to_a_property_page"></a>将控件添加到属性页  
  
#### <a name="to-add-controls-to-a-property-page"></a>将控件添加到属性页  
  
1.  打开控件项目后，打开资源视图。  
  
2.  双击**对话框**directory 图标。  
  
3.  打开**IDD_PROPPAGE_SAMPLE**对话框。  
  
     ActiveX 控件向导将项目名称追加到对话框 ID，在这种情况下，示例末尾。  
  
4.  拖放所选的控件从工具箱中拖放到对话框框区域。  
  
5.  例如，文本标签控件"标题:"和具有的编辑框控件**IDC_CAPTION**标识符已经足够。  
  
6.  单击**保存**在工具栏上，以保存所做的更改。  
  
 现在，已修改的用户界面，你需要链接具有标题属性的编辑框。 这通过下列部分中编辑`CSamplePropPage::DoDataExchange`函数。  
  
##  <a name="_core_customizing_the_dodataexchange_function"></a>自定义 DoDataExchange 函数  
 属性页[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)函数使你可以链接属性页值与实际值的控件中的属性。 若要建立链接，必须将相应的属性页字段映射到其各自的控件属性。  
  
 这些映射使用属性页来实现**DDP_**函数。 **DDP_**函数工作方式与类似**DDX_**函数使用在标准 MFC 对话框中，有一个例外。 除了对成员变量，引用**DDP_**函数采用的控件属性的名称。 以下是中的典型项`DoDataExchange`函数为属性页。  
  
 [!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]  
  
 此函数将相关联的属性页`m_caption`标题为成员变量使用`DDP_TEXT`函数。  
  
 插入的属性页控件后，你需要建立属性页上控件之间的链接`IDC_CAPTION`，和的实际控件属性，标题，使用**DDP_Text**函数上文所述。  
  
 [属性页](../mfc/reference/property-pages-mfc.md)可用于其他对话框控件类型，如复选框、 单选按钮和列表框。 下表列出了属性页的整个集**DDP_**函数和它们的用途：  
  
### <a name="property-page-functions"></a>属性页函数  
  
|功能名称|使用此函数来链接|  
|-------------------|-------------------------------|  
|`DDP_CBIndex`|与控件属性的组合框中选定的字符串的索引。|  
|`DDP_CBString`|与控件属性的组合框中选定的字符串。 所选的字符串可以以属性的值相同的字母开头，但需要完全匹配它。|  
|`DDP_CBStringExact`|与控件属性的组合框中选定的字符串。 所选的字符串，该属性的字符串值必须完全匹配。|  
|`DDP_Check`|具有的控件属性的复选框。|  
|`DDP_LBIndex`|中的控件属性在列表框中选定的字符串的索引。|  
|`DDP_LBString`|中的控件属性在列表框中的所选的字符串。 所选的字符串可以以属性的值相同的字母开头，但需要完全匹配它。|  
|`DDP_LBStringExact`|中的控件属性在列表框中的所选的字符串。 所选的字符串，该属性的字符串值必须完全匹配。|  
|`DDP_Radio`|一个具有的控件属性的单选按钮。|  
|**DDP_Text**|与控件属性的文本。|  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [COlePropertyPage 类](../mfc/reference/colepropertypage-class.md)
