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
ms.openlocfilehash: c336ec6c29b5478655ca8f19f71378a2b446ac64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358260"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC ActiveX 控件：使用字体

如果 ActiveX 控件显示文本，则可以允许控件用户通过更改字体属性来更改文本外观。 字体属性作为字体对象实现，可以是两种类型之一：股票或自定义。 "库存字体"属性是预先实现的字体属性，您可以使用"添加属性向导"添加这些属性。 自定义字体属性未预先实现，控件开发人员确定属性的行为和使用情况。

本文涵盖以下主题：

- [使用"库存字体"属性](#_core_using_the_stock_font_property)

- [在控件中使用自定义字体属性](#_core_implementing_a_custom_font_property)

## <a name="using-the-stock-font-property"></a><a name="_core_using_the_stock_font_property"></a>使用股票字体属性

股票字体属性由类[COleControl](../mfc/reference/colecontrol-class.md)预先实现。 此外，还提供标准 Font 属性页，允许用户更改字体对象的各种属性，如其名称、大小和样式。

通过[GetFont、SetFont](../mfc/reference/colecontrol-class.md#getfont)和[SetFont](../mfc/reference/colecontrol-class.md#setfont)[的内部 GetFont](../mfc/reference/colecontrol-class.md#internalgetfont)函数访问字体`COleControl`对象。 控件用户将通过`GetFont`和`SetFont`函数以与任何其他 Get/Set 属性相同的方式访问字体对象。 当需要从控件中访问字体对象时，请使用`InternalGetFont`函数。

如[MFC ActiveX 控件：属性中](../mfc/mfc-activex-controls-properties.md)所述，[添加属性向导](../ide/names-add-property-wizard.md)很容易添加股票属性。 选择"字体"属性，添加属性向导会自动将"股票字体"条目插入到控件的调度映射中。

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>使用"添加属性向导"添加股票字体属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加属性**"。

   这将打开"添加属性向导"。

1. 在 **"属性名称"** 框中，单击 **"字体**"。

1. 单击“完成”  。

添加属性向导将以下行添加到位于控件类实现文件中的控件调度映射中：

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

此外，"添加属性向导"将以下行添加到控件 。IDL 文件：

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

股票标题属性是可以使用股票字体属性信息绘制的文本属性的示例。 将股票标题属性添加到控件使用的步骤类似于用于股票字体属性的步骤。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>使用添加属性向导添加股票标题属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加属性**"。

   这将打开"添加属性向导"。

1. 在 **"属性名称"** 框中，单击 **"标题**"。

1. 单击“完成”  。

添加属性向导将以下行添加到位于控件类实现文件中的控件调度映射中：

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

## <a name="modifying-the-ondraw-function"></a><a name="_core_modifying_the_ondraw_function"></a>修改 OnDraw 函数

的`OnDraw`默认实现对控件中显示的所有文本使用 Windows 系统字体。 这意味着您必须通过在设备上下文中选择字体`OnDraw`对象来修改代码。 为此，请致电[COleControl：选择StockFont](../mfc/reference/colecontrol-class.md#selectstockfont)并传递控件的设备上下文，如以下示例所示：

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

修改该`OnDraw`函数以使用字体对象后，控件中的任何文本都显示具有控件的"字体"属性的特征。

## <a name="using-custom-font-properties-in-your-control"></a><a name="_core_using_custom_font_properties_in_your_control"></a>在控件中使用自定义字体属性

除了股票字体属性外，ActiveX 控件还可以具有自定义字体属性。 要添加自定义字体属性，您必须：

- 使用"添加属性向导"实现自定义字体属性。

- [处理字体通知](#_core_processing_font_notifications)。

- [实现新的字体通知界面](#_core_implementing_a_new_font_notification_interface)。

### <a name="implementing-a-custom-font-property"></a><a name="_core_implementing_a_custom_font_property"></a>实现自定义字体属性

要实现自定义 Font 属性，请使用"添加属性向导"添加该属性，然后对代码进行一些修改。 以下各节介绍如何将自定义`HeadingFont`属性添加到示例控件。

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>使用"添加属性向导"添加自定义字体属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加属性**"。

   这将打开"添加属性向导"。

1. 在 **"属性名称"** 框中，键入属性的名称。 在此示例中，请使用**标题字体**。

1. 对于“实现类型” ****，请单击“Get/Set 方法” ****。

1. 在 **"属性类型"** 框中，为属性的类型选择**IDispatch。** <strong>\*</strong>

1. 单击“完成”  。

"添加属性向导"创建代码以将`HeadingFont`自定义属性添加到`CSampleCtrl`类和 SAMPLE。IDL 文件。 由于`HeadingFont`是 Get/Set 属性类型，因此"添加属性向导"`CSampleCtrl`修改类的调度映射以包含[DISP_PROPERTY_EX_IDDISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)宏条目：

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

DISP_PROPERTY_EX`HeadingFont`宏将属性名称与其`CSampleCtrl`相应的类"获取和设置"方法关联，`GetHeadingFont`以及`SetHeadingFont`。 属性值的类型也指定;因此，属性值的类型也指定为属性值。在这种情况下，VT_FONT。

添加属性向导还会在控件标头文件 （中添加声明。H）`GetHeadingFont`的`SetHeadingFont`和 函数，并在控件实现文件 （中添加其函数模板 （。CPP）：

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

最后，"添加属性向导"修改控件。通过添加`HeadingFont`属性的条目来提交 IDL 文件：

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>对控制代码的修改

现在，您已将`HeadingFont`该属性添加到控件中，您必须对控件标头和实现文件进行一些更改，以完全支持新属性。

在控件头文件 （.H），添加受保护成员变量的以下声明：

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

在控件实现文件中 （.CPP），执行以下操作：

- 初始化控件构造函数中的*m_fontHeading。*

   [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- 声明包含字体默认属性的静态 FONTDESC 结构。

   [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- 在控件`DoPropExchange`成员函数中，向函数`PX_Font`添加调用。 这为自定义"字体"属性提供了初始化和持久性。

   [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- 完成实现控制`GetHeadingFont`成员函数。

   [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- 完成实现控制`SetHeadingFont`成员函数。

   [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- 修改控件`OnDraw`成员函数以定义变量以保存以前选定的字体。

   [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- 修改控件`OnDraw`成员函数，通过在使用字体的任意位置添加下一行，将自定义字体添加到设备上下文中。

   [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- 修改控件`OnDraw`成员函数，在使用字体后添加下一行，将以前的字体重新选择回设备上下文。

   [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

实现自定义 Font 属性后，应实现标准字体属性页，允许控件用户更改控件的当前字体。 要添加标准 Font 属性页的属性页 ID，请在BEGIN_PROPPAGEIDS宏后插入以下行：

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

您还必须将BEGIN_PROPPAGEIDS宏的计数参数增加一个。 下面一行阐释了这一点：

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

进行这些更改后，重建整个项目以合并其他功能。

### <a name="processing-font-notifications"></a><a name="_core_processing_font_notifications"></a>处理字体通知

在大多数情况下，控件需要知道字体对象的特征何时被修改。 每个字体对象都能够通过在更改时通过调用由 实现的`IFontNotification``COleControl`接口的成员函数来提供通知。

如果控件使用股票字体属性，则其通知由`OnFontChanged`的成员`COleControl`函数处理。 添加自定义字体属性时，可以让它们使用相同的实现。 在上一节中的示例中，通过在初始化*m_fontHeading*成员变量时传递 *&m_xFontNotification*来实现这一点。

![实现多个字体对象接口](../mfc/media/vc373q1.gif "实现多个字体对象接口") <br/>
实现多个字体对象接口

上图中的实线显示两个字体对象都使用相同的实现`IFontNotification`。 如果要区分更改的字体，可能会导致问题。

区分控件的字体对象通知的一种方法是为控件中的每个字体对象创建`IFontNotification`接口的单独实现。 此技术允许您仅更新使用最近修改的字体的字符串或字符串来优化绘图代码。 以下各节演示了为第二个 Font 属性实现单独的通知接口所需的步骤。 第二个字体属性假定为上一`HeadingFont`节中添加的属性。

### <a name="implementing-a-new-font-notification-interface"></a><a name="_core_implementing_a_new_font_notification_interface"></a>实现新的字体通知界面

要区分两种或两种以上字体的通知，必须为控件中使用的每个字体实现一个新的通知接口。 以下各节介绍如何通过修改控件标头和实现文件来实现新的字体通知界面。

### <a name="additions-to-the-header-file"></a>标题文件的添加

在控件头文件 （.H），向类声明添加以下行：

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

这将创建称为`IPropertyNotifySink``HeadingFontNotify`的接口的实现。 此新接口包含一个称为`OnChanged`的方法。

### <a name="additions-to-the-implementation-file"></a>实现文件的添加

在初始化标题字体的代码（在控件构造函数中），将 *&m_xFontNotification*更改为 *&m_xHeadingFontNotify*。 然后，添加以下代码：

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

接口`AddRef`中的`Release``IPropertyNotifySink`和 方法跟踪 ActiveX 控件对象的引用计数。 当控件获得对接口指针的访问时，控件调用`AddRef`以增加引用计数。 当控件使用指针完成时，它将调用`Release`，其方式与调用以释放全局`GlobalFree`内存块的方式大致相同。 当此接口的引用计数为零时，可以释放接口实现。 在此示例中，`QueryInterface`函数返回指向特定对象上的`IPropertyNotifySink`接口的指针。 此函数允许 ActiveX 控件查询对象以确定它支持哪些接口。

对项目进行这些更改后，重新生成项目并使用测试容器测试接口。 请参阅 [使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md) 了解有关如何访问测试容器的信息。

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：在 ActiveX 控件中使用图片](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)
