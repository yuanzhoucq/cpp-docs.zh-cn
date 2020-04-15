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
ms.openlocfilehash: c31d13e03483f8632f17a526da75ebe8e21bccbf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364570"
---
# <a name="mfc-activex-controls-property-pages"></a>MFC ActiveX 控件：属性页

属性页允许 ActiveX 控件用户查看和更改 ActiveX 控件属性。 这些属性是通过调用控件属性对话框来访问的，该对话框包含一个或多个属性页，这些页面提供用于查看和编辑控件属性的自定义图形界面。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

ActiveX 控件属性页以两种方式显示：

- 调用控件的"属性"谓词 **（OLEIVERB_PROPERTIES**）时，控件将打开一个包含控件属性页的模式属性对话框。

- 容器可以显示其自己的无模式对话框，该对话框显示所选控件的属性页。

属性对话框（下图所示）包括用于显示当前属性页的区域、用于在属性页之间切换的选项卡以及执行常见任务的按钮的集合，如关闭属性页对话框、取消所做的任何更改或立即对 ActiveX 控件应用任何更改。

![Circ3 的“属性”对话框](../mfc/media/vc373i1.gif "Circ3 的“属性”对话框") <br/>
“属性”对话框

本文介绍与在 ActiveX 控件中使用属性页相关的主题。 其中包括:

- [实现 ActiveX 控件的默认属性页](#_core_implementing_the_default_property_page)

- [将控件添加到属性页](#_core_adding_controls_to_a_property_page)

- [自定义 DoDataExchange 功能](#_core_customizing_the_dodataexchange_function)

有关在 ActiveX 控件中使用属性页的详细信息，请参阅以下文章：

- [MFC ActiveX 控件：添加另一自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)

- [MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)

有关在 MFC 应用程序中使用属性表（而不是 ActiveX 控件）的信息，请参阅[属性表](../mfc/property-sheets-mfc.md)。

## <a name="implementing-the-default-property-page"></a><a name="_core_implementing_the_default_property_page"></a>实现默认属性页

如果使用 ActiveX 控件向导创建控件项目，则 ActiveX 控件向导为派生自[COlePropertyPage 类](../mfc/reference/colepropertypage-class.md)的控件提供默认属性页类。 最初，此属性页为空，但您可以将任何对话框控件或控件集添加到其中。 由于 ActiveX 控件向导默认情况下只创建一个属性页类，因此必须使用 类视图创建`COlePropertyPage`其他属性页类（也派生自 ）。 有关此过程的详细信息，请参阅[MFC ActiveX 控件：添加另一个自定义属性页](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)。

实现属性页（本例中为默认值）是一个三步过程：

#### <a name="to-implement-a-property-page"></a>实现属性页

1. 向控件`COlePropertyPage`项目添加派生类。 如果项目是使用 ActiveX 控件向导创建的（如本例），则默认属性页类已存在。

1. 使用对话框编辑器将任何控件添加到属性页模板。

1. `DoDataExchange`自定义`COlePropertyPage`派生类的功能以在属性页控件和 ActiveX 控件之间交换值。

例如，以下过程使用简单的控件（称为"示例"）。 示例是使用 ActiveX 控件向导创建的，并且仅包含库存标题属性。

## <a name="adding-controls-to-a-property-page"></a><a name="_core_adding_controls_to_a_property_page"></a>将控件添加到属性页

#### <a name="to-add-controls-to-a-property-page"></a>向属性页添加控件

1. 打开控制项目后，打开资源视图。

1. 双击 **"对话框**"目录图标。

1. 打开IDD_PROPPAGE_SAMPLE对话框。

   ActiveX 控制向导将项目的名称追加到对话框 ID 的末尾，本例中为示例。

1. 将所选控件从"工具箱"拖放到对话框区域。

1. 在此示例中，文本标签控件"标题 "和具有IDC_CAPTION标识符的编辑框控件就足够了。

1. 单击"在工具栏上**保存**"以保存更改。

现在用户界面已被修改，您需要将编辑框与"标题"属性链接。 这通过编辑`CSamplePropPage::DoDataExchange`函数在以下部分完成。

## <a name="customizing-the-dodataexchange-function"></a><a name="_core_customizing_the_dodataexchange_function"></a>自定义 DoData 交换功能

属性页[CWnd：:DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)函数允许您将属性页值与控件中属性的实际值链接。 要建立链接，必须将相应的属性页字段映射到其各自的控件属性。

这些映射使用属性页**DDP_** 函数实现。 **DDP_** 函数的工作方式与标准 MFC 对话框中使用的**DDX_** 函数类似，但有一个例外。 除了对成员变量的引用外 **，DDP_** 函数采用控件属性的名称。 以下是属性页函数中`DoDataExchange`的典型条目。

[!code-cpp[NVC_MFC_AxUI#31](../mfc/codesnippet/cpp/mfc-activex-controls-property-pages_1.cpp)]

此函数使用`DDP_TEXT`函数将属性页的*m_caption*成员变量与标题关联。

插入属性页控件后，需要使用上述`DDP_Text`函数在属性页控件、IDC_CAPTION 和实际控件属性"Caption"之间建立链接。

[属性页](../mfc/reference/property-pages-mfc.md)可用于其他对话框控件类型，如复选框、单选按钮和列表框。 下表列出了函数**DDP_** 及其用途的整组属性页：

### <a name="property-page-functions"></a>属性页函数

|函数名称|使用此函数链接|
|-------------------|-------------------------------|
|`DDP_CBIndex`|组合框中所选字符串的索引具有控件属性。|
|`DDP_CBString`|组合框中的选定字符串具有控件属性。 所选字符串可以以与属性值相同的字母开头，但不必完全匹配它。|
|`DDP_CBStringExact`|组合框中的选定字符串具有控件属性。 所选字符串和属性的字符串值必须完全匹配。|
|`DDP_Check`|具有控件属性的复选框。|
|`DDP_LBIndex`|具有控件属性的列表框中的选定字符串索引。|
|`DDP_LBString`|具有控件属性的列表框中的选定字符串。 所选字符串可以以与属性值相同的字母开头，但不必完全匹配它。|
|`DDP_LBStringExact`|具有控件属性的列表框中的选定字符串。 所选字符串和属性的字符串值必须完全匹配。|
|`DDP_Radio`|具有控制属性的单选按钮。|
|`DDP_Text`|具有控件属性的文本。|

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)<br/>
[COle属性页类](../mfc/reference/colepropertypage-class.md)
