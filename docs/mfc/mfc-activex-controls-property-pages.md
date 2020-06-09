---
title: MFC ActiveX 控件：属性页
ms.date: 11/19/2018
helpviewer_keywords:
- DDP_ functions [MFC]
- MFC ActiveX controls [MFC], properties
- property pages [MFC], MFC ActiveX controls
- DoDataExchange method [MFC]
- OLEIVERB_PROPERTIES
- CPropertyPageDialog class [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 1506f87a-9fd6-4505-8380-0dbc9636230e
ms.openlocfilehash: 3d22085daa503a7c778111718445920f98b98a89
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615444"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC ActiveX 控件：属性页

属性页允许 ActiveX 控件用户查看和更改 ActiveX 控件属性。 可以通过调用 "控件属性" 对话框来访问这些属性，其中包含一个或多个属性页，它们提供自定义的图形界面，可用于查看和编辑控件属性。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关取代 ActiveX 的新式技术的详细信息，请参阅[Activex 控件](activex-controls.md)。

ActiveX 控件属性页以两种方式显示：

- 调用控件的属性谓词（**OLEIVERB_PROPERTIES**）时，控件将打开一个模式属性对话框，其中包含控件的属性页。

- 容器可以显示其自己的无模式对话框，其中显示所选控件的属性页。

"属性" 对话框（如下图所示）包含一个区域，用于显示当前属性页、用于在属性页之间切换的选项卡，以及用于执行常见任务（如关闭属性页对话框、取消所做的任何更改或立即将更改应用到 ActiveX 控件）的按钮的集合。

![Circ3 的“属性”对话框](../mfc/media/vc373i1.gif "Circ3 的“属性”对话框") <br/>
“属性”对话框

本文介绍如何在 ActiveX 控件中使用属性页。 其中包括：

- [实现 ActiveX 控件的默认属性页](#_core_implementing_the_default_property_page)

- [向属性页添加控件](#_core_adding_controls_to_a_property_page)

- [自定义 DoDataExchange 函数](#_core_customizing_the_dodataexchange_function)

有关在 ActiveX 控件中使用属性页的详细信息，请参阅以下文章：

- [MFC ActiveX 控件：添加另一自定义属性页](mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC ActiveX 控件：使用常用属性页](mfc-activex-controls-using-stock-property-pages.md)

有关在 MFC 应用程序中使用 ActiveX 控件之外的属性表的信息，请参阅[属性表](property-sheets-mfc.md)。

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>实现默认属性页

如果使用 ActiveX 控件向导来创建控件项目，ActiveX 控件向导会为从[COlePropertyPage 类](reference/colepropertypage-class.md)派生的控件提供默认属性页类。 最初，此属性页为空白，但您可以向其中添加任何对话框控件或一组控件。 由于 ActiveX 控件向导默认只创建一个属性页类，因此必须使用类视图创建其他属性页类（也派生自 `COlePropertyPage` ）。 有关此过程的详细信息，请参阅[MFC ActiveX 控件：添加另一自定义属性页](mfc-activex-controls-adding-another-custom-property-page.md)。

实现属性页（在本例中为默认值）的过程分为三个步骤：

#### <a name="to-implement-a-property-page"></a>实现属性页

1. 向 `COlePropertyPage` 控件项目添加一个派生类。 如果项目是使用 ActiveX 控件向导创建的（在本例中为），则默认属性页类已经存在。

1. 使用对话框编辑器向属性页模板添加任何控件。

1. 自定义 `DoDataExchange` 派生类的函数， `COlePropertyPage` 以在属性页控件和 ActiveX 控件之间交换值。

例如，以下过程使用简单的控件（名为 "Sample"）。 示例是使用 ActiveX 控件向导创建的，并且只包含 stock Caption 属性。

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>向属性页添加控件

#### <a name="to-add-controls-to-a-property-page"></a>向属性页添加控件

1. 打开控件项目后，打开资源视图。

1. 双击 "**对话框**目录" 图标。

1. 打开 "IDD_PROPPAGE_SAMPLE" 对话框。

   ActiveX 控件向导会将项目名称追加到对话框 ID 的末尾，在本例中为示例。

1. 将所选控件从工具箱拖放到对话框区域。

1. 在此示例中，文本标签控件 "Caption：" 和具有 IDC_CAPTION 标识符的编辑框控件已经足够。

1. 单击工具栏上的 "**保存**" 以保存所做的更改。

由于已修改用户界面，因此需要将编辑框链接到 "标题" 属性。 在下一节中，通过编辑函数来完成此操作 `CSamplePropPage::DoDataExchange` 。

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>自定义 DoDataExchange 函数

属性页[CWnd：:D odataexchange](reference/cwnd-class.md#dodataexchange)函数允许您将属性页值与控件中的属性的实际值进行链接。 若要建立链接，必须将相应的属性页字段映射到其各自的控件属性。

这些映射是使用属性页**DDP_** 函数实现的。 **DDP_** 函数的工作方式与标准 MFC 对话框中使用的**DDX_** 函数相同，但有一个例外。 除了对成员变量的引用外， **DDP_** 函数将采用控件属性的名称。 下面是属性页的函数中的典型条目 `DoDataExchange` 。

[!code-cpp[NVC_MFC_AxUI#31](codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

此函数使用函数将属性页的*m_caption*成员变量与标题相关联 `DDP_TEXT` 。

插入属性页控件后，需要使用上述函数在属性页控件、IDC_CAPTION 和实际控件属性（Caption）之间建立链接 `DDP_Text` 。

[属性页](reference/property-pages-mfc.md)可用于其他对话框控件类型，如复选框、单选按钮和列表框。 下表列出了一组完整的属性页**DDP_** 函数及其用途：

### <a name="property-page-functions"></a>属性页函数

|功能名称|使用此函数链接|
|-------------------|-------------------------------|
|`DDP_CBIndex`|包含控件属性的组合框中所选字符串的索引。|
|`DDP_CBString`|组合框中所选的包含控件属性的字符串。 选定的字符串可以以与属性的值相同的字母开头，但不需要完全匹配。|
|`DDP_CBStringExact`|组合框中所选的包含控件属性的字符串。 所选字符串和属性的字符串值必须完全匹配。|
|`DDP_Check`|具有控件属性的复选框。|
|`DDP_LBIndex`|具有控件属性的列表框中所选字符串的索引。|
|`DDP_LBString`|具有控件属性的列表框中所选的字符串。 选定的字符串可以以与属性的值相同的字母开头，但不需要完全匹配。|
|`DDP_LBStringExact`|具有控件属性的列表框中所选的字符串。 所选字符串和属性的字符串值必须完全匹配。|
|`DDP_Radio`|具有控件属性的单选按钮。|
|`DDP_Text`|具有控件属性的文本。|

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)<br/>
[COlePropertyPage 类](reference/colepropertypage-class.md)
