---
title: MFC ActiveX 控件： 属性页 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19dc08fc29de4affaea987025a2bc8b92bc56460
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079852"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC ActiveX 控件：属性页

属性页允许 ActiveX 控件用户可以查看和更改 ActiveX 控件属性。 通过调用控件的属性对话框中，其中包含一个或多个属性页提供用于查看和编辑控件属性的自定义的图形界面访问这些属性。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 本文将取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

ActiveX 控件属性页会显示在两种方法：

- 当控件的属性谓词 (**OLEIVERB_PROPERTIES**) 是调用，该控件将打开包含控件的属性页的模式属性对话框。

- 容器可以显示其自身显示所选控件的属性页无模式对话框。

属性对话框 （如下图中所示） 包含用于显示当前的属性页上，为属性页和一组执行常见任务，例如关闭属性页对话框中，按钮之间切换选项卡区域正在取消任何更改，或立即应用到 ActiveX 控件的所有更改。

![Circ3 属性对话框](../mfc/media/vc373i1.gif "vc373i1")属性对话框

本文介绍如何与 ActiveX 控件中使用属性页相关的主题。 这些方法包括：

- [实现 ActiveX 控件的默认属性页](#_core_implementing_the_default_property_page)

- [将控件添加到属性页](#_core_adding_controls_to_a_property_page)

- [自定义 DoDataExchange 函数](#_core_customizing_the_dodataexchange_function)

使用 ActiveX 控件中的属性页面的详细信息，请参阅以下文章：

- [MFC ActiveX 控件：添加另一自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)

以外的 ActiveX 控件的 MFC 应用程序中使用属性表的信息，请参阅[属性表](../mfc/property-sheets-mfc.md)。

##  <a name="_core_implementing_the_default_property_page"></a> 实现默认属性页

如果使用 ActiveX 控件向导创建控件项目，ActiveX 控件向导提供默认属性页类，该控件派生自[COlePropertyPage 类](../mfc/reference/colepropertypage-class.md)。 最初，此属性页为空，但您可以向其中添加任何对话框控件或一组控件。 因为 ActiveX 控件向导默认情况下，附加属性页类将创建只有一个属性页类 (也派生自`COlePropertyPage`) 必须使用类视图创建。 此过程的详细信息，请参阅[MFC ActiveX 控件： 添加另一个自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)。

实现属性页 （在此情况下，默认值） 是一个三步骤过程：

#### <a name="to-implement-a-property-page"></a>若要实现的属性页

1. 添加`COlePropertyPage`的派生类向控件项目。 如果项目使用 （如在此用例） ActiveX 控件向导创建的默认属性页类已存在。

1. 使用对话框编辑器将任何控件添加到属性页模板。

1. 自定义`DoDataExchange`函数的`COlePropertyPage`的派生类来交换属性页控件和 ActiveX 控件之间的值。

例如目的，以下过程使用简单的控件 （名为"Sample"）。 示例使用 ActiveX 控件向导创建的并包含只股票的 Caption 属性。

##  <a name="_core_adding_controls_to_a_property_page"></a> 将控件添加到属性页

#### <a name="to-add-controls-to-a-property-page"></a>若要将控件添加到属性页

1. 打开控件项目，打开资源视图。

1. 双击**对话框**directory 图标。

1. 打开 IDD_PROPPAGE_SAMPLE 对话框。

   ActiveX 控件向导的对话框 ID，在这种情况下，示例末尾追加的项目的名称。

1. 拖放所选的控件从工具箱拖动到对话框框区域。

1. 对于此示例中，文本标签控件"标题:"和 IDC_CAPTION 标识符的编辑框控件已足够。

1. 单击**保存**工具栏，保存所做的更改。

现在，已修改的用户界面，您需要链接与 Caption 属性的编辑框。 这是在以下部分通过编辑`CSamplePropPage::DoDataExchange`函数。

##  <a name="_core_customizing_the_dodataexchange_function"></a> 自定义 DoDataExchange 函数

属性页[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)功能，您可以将控件中的属性的实际值的属性页值链接。 若要建立链接，必须将相应的属性页字段映射到其各自的控件属性中。

这些映射使用属性页来实现**DDP_** 函数。 **DDP_** 函数的工作方式类似**DDX_** 函数使用在标准 MFC 对话框中，有一个例外。 除了对成员变量的引用**DDP_** 函数采用的控件属性的名称。 以下是中的典型项`DoDataExchange`属性页的函数。

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

此函数将属性页的相关联*m_caption*标题为成员变量使用`DDP_TEXT`函数。

插入属性页控件后，需要建立属性页控件、 IDC_CAPTION 与实际控件属性之间的链接标题使用`DDP_Text`函数如上文所述。

[属性页](../mfc/reference/property-pages-mfc.md)可用于其他对话框控件类型，如复选框、 单选按钮和列表框。 下表列出了属性页整组**DDP_** 函数和它们的用途：

### <a name="property-page-functions"></a>属性页函数

|功能名称|使用此函数将链接|
|-------------------|-------------------------------|
|`DDP_CBIndex`|与控件属性的组合框中的所选的字符串的索引。|
|`DDP_CBString`|与控件属性的组合框中所选的字符串。 所选的字符串可以以属性的值相同的字母开头，但需要完全匹配它。|
|`DDP_CBStringExact`|与控件属性的组合框中所选的字符串。 所选的字符串和属性的字符串值必须完全匹配。|
|`DDP_Check`|与控件属性的复选框。|
|`DDP_LBIndex`|与控件属性的列表框中的所选的字符串的索引。|
|`DDP_LBString`|与控件属性的列表框中所选的字符串。 所选的字符串可以以属性的值相同的字母开头，但需要完全匹配它。|
|`DDP_LBStringExact`|与控件属性的列表框中所选的字符串。 所选的字符串和属性的字符串值必须完全匹配。|
|`DDP_Radio`|与控件属性的单选按钮。|
|`DDP_Text`|与控件属性的文本。|

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[COlePropertyPage 类](../mfc/reference/colepropertypage-class.md)
