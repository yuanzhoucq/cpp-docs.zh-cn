---
title: MFC ActiveX 控件：使用字体
ms.date: 11/19/2018
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
helpviewer_keywords:
- notifications [MFC], MFC ActiveX controls fonts
- OnDraw method, MFC ActiveX controls
- InternalFont method [MFC]
- SetFont method [MFC]
- OnFontChanged method [MFC]
- IPropertyNotifySink class [MFC]
- MFC ActiveX controls [MFC], fonts
- Stock Font property [MFC]
- HeadingFont property [MFC]
- GetFont method [MFC]
- SelectStockFont method [MFC]
- fonts [MFC], ActiveX controls
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
ms.openlocfilehash: 58f387ba6f4d7cdffb3ffc1f7be6f9acde8314f4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618168"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC ActiveX 控件：使用字体

如果 ActiveX 控件显示文本，则可以通过更改字体属性允许控件用户更改文本外观。 字体属性作为字体对象实现，可以为以下两种类型之一： stock 或 custom。 常用字体属性是 preimplemented 可以使用 "添加属性向导" 添加的字体属性。 自定义字体属性不 preimplemented，控件开发人员确定属性的行为和使用情况。

本文涵盖以下主题：

- [使用常用字体属性](#_core_using_the_stock_font_property)

- [在控件中使用自定义字体属性](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>使用常用字体属性

常用字体属性由类[COleControl](reference/colecontrol-class.md)preimplemented。 此外，还提供了标准字体属性页，允许用户更改字体对象的各种属性，如其名称、大小和样式。

通过的[ivsfontandcolorstorage.getfont 错误](reference/colecontrol-class.md#getfont)、 [SetFont](reference/colecontrol-class.md#setfont)和[InternalGetFont](reference/colecontrol-class.md#internalgetfont)函数访问 font 对象 `COleControl` 。 控件用户将通过和函数访问 font 对象 `GetFont` ， `SetFont` 方法与任何其他 Get/Set 属性相同。 如果需要从控件中访问 font 对象，请使用 `InternalGetFont` 函数。

如[MFC ActiveX 控件：属性](mfc-activex-controls-properties.md)中所述，通过 "[添加属性向导](../ide/names-add-property-wizard.md)" 可以轻松添加常用属性。 您可以选择 "字体" 属性，"添加属性向导" 会自动在控件的调度映射中插入常用字体条目。

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>使用 "添加属性向导" 添加常用字体属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加属性**"。

   这将打开 "添加属性向导"。

1. 在 "**属性名称**" 框中，单击 "**字体**"。

1. 单击“完成”。

"添加属性向导" 将以下行添加到控件的调度映射，该映射位于控件类实现文件中：

[!code-cpp[NVC_MFC_AxFont#1](codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

此外，"添加属性向导" 将以下行添加到控件中。IDL 文件：

[!code-cpp[NVC_MFC_AxFont#2](codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

Stock Caption 属性是可以使用常用字体属性信息绘制的文本属性的示例。 将 stock Caption 属性添加到控件所使用的步骤类似于用于常用字体属性的步骤。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>使用 "添加属性向导" 添加 stock Caption 属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加属性**"。

   这将打开 "添加属性向导"。

1. 在 "**属性名称**" 框中，单击 "**标题**"。

1. 单击“完成”。

"添加属性向导" 将以下行添加到控件的调度映射，该映射位于控件类实现文件中：

[!code-cpp[NVC_MFC_AxFont#3](codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>修改 OnDraw 函数

的默认实现对 `OnDraw` 控件中显示的所有文本使用 Windows 系统字体。 这意味着，你必须通过在 `OnDraw` 设备上下文中选择 "字体" 对象来修改代码。 为此，请调用[COleControl：： SelectStockFont](reference/colecontrol-class.md#selectstockfont)并传递控件的设备上下文，如以下示例中所示：

[!code-cpp[NVC_MFC_AxFont#4](codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

在将 `OnDraw` 函数修改为使用 font 对象之后，该控件中的任何文本都将与该控件的常用字体属性中的特征一起显示。

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>在控件中使用自定义字体属性

除了常用字体属性，ActiveX 控件还可以具有自定义字体属性。 若要添加自定义字体属性，必须执行以下操作：

- 使用 "添加属性向导" 实现自定义字体属性。

- [处理字体通知](#_core_processing_font_notifications)。

- [实现新的字体通知接口](#_core_implementing_a_new_font_notification_interface)。

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>实现自定义字体属性

若要实现自定义字体属性，请使用 "添加属性向导" 添加属性，然后对代码进行一些修改。 以下各节介绍如何将自定义 `HeadingFont` 属性添加到示例控件。

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>使用 "添加属性向导" 添加自定义字体属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加属性**"。

   这将打开 "添加属性向导"。

1. 在 "**属性名称**" 框中，键入属性的名称。 对于本示例，请使用**HeadingFont**。

1. 对于“实现类型” ****，请单击“Get/Set 方法” ****。

1. 在 "**属性类型**" 框中**IDispatch** ， <strong>\*</strong> 为该属性的类型选择 "IDispatch"。

1. 单击“完成”。

"添加属性向导" 创建用于将 `HeadingFont` 自定义属性添加到 `CSampleCtrl` 类和示例的代码。IDL 文件。 由于 `HeadingFont` 是 Get/Set 属性类型，因此添加属性向导会修改 `CSampleCtrl` 该类的调度映射，以包括 DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](reference/dispatch-maps.md#disp_property_ex)宏项：

[!code-cpp[NVC_MFC_AxFont#5](codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

DISP_PROPERTY_EX 宏将 `HeadingFont` 属性名称与其相应的 `CSampleCtrl` 类 Get 和 Set 方法（和）相关联 `GetHeadingFont` `SetHeadingFont` 。 还指定属性值的类型;在这种情况下，VT_FONT。

"添加属性向导" 还在控件头文件（）中添加一个声明。H）， `GetHeadingFont` `SetHeadingFont` 并将其函数模板添加到控件实现文件（。CPP）：

[!code-cpp[NVC_MFC_AxFont#6](codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

最后，添加属性向导会修改控件。IDL 文件，方法是为属性添加一个项 `HeadingFont` ：

[!code-cpp[NVC_MFC_AxFont#7](codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>对控制代码的修改

现在您已将属性添加 `HeadingFont` 到控件，您必须对控件标题和实现文件进行一些更改，才能完全支持新属性。

在控件头文件（。H）中，添加受保护成员变量的以下声明：

[!code-cpp[NVC_MFC_AxFont#8](codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

在控件实现文件（。CPP）中，执行以下操作：

- 在控件构造函数中初始化*m_fontHeading* 。

   [!code-cpp[NVC_MFC_AxFont#9](codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- 声明一个包含字体的默认属性的静态 FONTDESC 结构。

   [!code-cpp[NVC_MFC_AxFont#10](codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- 在控件 `DoPropExchange` 成员函数中，添加对函数的调用 `PX_Font` 。 这为自定义字体属性提供了初始化和暂留。

   [!code-cpp[NVC_MFC_AxFont#11](codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- 完成控件 `GetHeadingFont` 成员函数的实现。

   [!code-cpp[NVC_MFC_AxFont#12](codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- 完成控件 `SetHeadingFont` 成员函数的实现。

   [!code-cpp[NVC_MFC_AxFont#13](codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- 修改控件 `OnDraw` 成员函数以定义用于保存之前所选字体的变量。

   [!code-cpp[NVC_MFC_AxFont#14](codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- `OnDraw`通过在要使用字体的任何位置添加以下行，修改控件成员函数以选择自定义字体到设备上下文。

   [!code-cpp[NVC_MFC_AxFont#15](codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- `OnDraw`使用字体后，通过添加以下行来修改控件成员函数以选择将上一种字体改回设备上下文。

   [!code-cpp[NVC_MFC_AxFont#16](codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

实现自定义字体属性后，应实现标准字体属性页，以允许控件用户更改控件的当前字体。 若要添加标准字体属性页的属性页 ID，请在 BEGIN_PROPPAGEIDS 宏后面插入以下行：

[!code-cpp[NVC_MFC_AxFont#17](codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

还必须将 BEGIN_PROPPAGEIDS 宏的计数参数递增1。 下面一行阐释了这一点：

[!code-cpp[NVC_MFC_AxFont#18](codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

进行这些更改后，重新生成整个项目以合并附加功能。

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>处理字体通知

在大多数情况下，控件需要知道何时修改了 font 对象的特征。 每个字体对象都可以在通过调用由实现的接口的成员函数来更改时提供通知 `IFontNotification` `COleControl` 。

如果控件使用 "常用字体" 属性，则其通知由的 `OnFontChanged` 成员函数进行处理 `COleControl` 。 添加自定义字体属性时，可以让它们使用相同的实现。 在上一部分的示例中，这是通过在初始化*m_fontHeading*成员变量时传递 &*m_xFontNotification*来实现的。

![实现多个字体对象接口](../mfc/media/vc373q1.gif "实现多个字体对象接口") <br/>
实现多个字体对象接口

上图中的实线显示两个 font 对象使用的是相同的实现 `IFontNotification` 。 如果希望区分更改了哪些字体，这可能会导致问题。

区分控件的字体对象通知的一种方法是为 `IFontNotification` 控件中的每个字体对象创建单独的接口实现。 此方法允许您通过仅更新使用最近修改的字体的字符串或字符串来优化您的绘图代码。 以下部分说明了为第二个字体属性实现单独的通知接口所需的步骤。 第二个字体属性假定为 `HeadingFont` 上一部分中添加的属性。

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>实现新字体通知界面

若要区分两种或多种字体的通知，必须为控件中使用的每个字体实现新的通知接口。 以下部分介绍如何通过修改控件头和实现文件来实现新的字体通知接口。

### <a name="additions-to-the-header-file"></a>添加到头文件

在控件头文件（。H），将以下行添加到类声明中：

[!code-cpp[NVC_MFC_AxFont#19](codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

这将创建一个名为的接口的实现 `IPropertyNotifySink` `HeadingFontNotify` 。 此新接口包含一个名为的方法 `OnChanged` 。

### <a name="additions-to-the-implementation-file"></a>向实现文件中添加内容

在用于初始化标题字体的代码（在控件构造函数中），将 &*m_xFontNotification*更改为 &*m_xHeadingFontNotify*。 然后，添加以下代码：

[!code-cpp[NVC_MFC_AxFont#20](codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

`AddRef` `Release` 接口中的和方法 `IPropertyNotifySink` 跟踪 ActiveX 控件对象的引用计数。 当控件获取对接口指针的访问权限时，控件将调用 `AddRef` 来递增引用计数。 当控件使用指针完成时，它会调用 `Release` ，其方式与 `GlobalFree` 释放全局内存块的方式几乎相同。 此接口的引用计数变为零时，可以释放接口实现。 在此示例中，该 `QueryInterface` 函数返回指向 `IPropertyNotifySink` 特定对象上的接口的指针。 此函数允许 ActiveX 控件查询对象，以确定它支持的接口。

对项目进行这些更改后，重新生成项目，并使用测试容器测试接口。 请参阅 [使用测试容器测试属性和事件](testing-properties-and-events-with-test-container.md) 了解有关如何访问测试容器的信息。

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：在 ActiveX 控件中使用图片](mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC ActiveX 控件：使用常用属性页](mfc-activex-controls-using-stock-property-pages.md)
