---
title: MFC ActiveX 控件： 使用字体 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnFontChanged
- HeadingFont
- InternalFont
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b14adec8d601778e255ae7e4242fc552fc820e64
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396696"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC ActiveX 控件：使用字体

如果 ActiveX 控件显示的文本，可以允许控制用户可以通过更改字体属性更改文本外观。 字体属性实现为字体对象和可以是两种类型之一： 股票或自定义。 常用字体属性是可以使用添加属性向导添加的 preimplemented 的字体属性。 不 preimplemented 自定义字体属性和控件开发人员确定该属性的行为和使用情况。

本文介绍了以下主题：

- [使用常用字体属性](#_core_using_the_stock_font_property)

- [在您的控件中使用自定义字体属性](#_core_implementing_a_custom_font_property)

##  <a name="_core_using_the_stock_font_property"></a> 使用常用字体属性

常用字体属性 preimplemented 由类[COleControl](../mfc/reference/colecontrol-class.md)。 此外，标准的字体属性页是也可用，这样就允许用户更改字体对象，如其名称、 大小和样式的各种属性。

访问通过字体对象[GetFont](../mfc/reference/colecontrol-class.md#getfont)， [SetFont](../mfc/reference/colecontrol-class.md#setfont)，并[InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont)函数的`COleControl`。 控制用户访问字体对象通过`GetFont`和`SetFont`与任何其他 Get/Set 属性相同的方式中的函数。 需要在控件内对字体对象的访问时，请使用`InternalGetFont`函数。

如中所述[MFC ActiveX 控件： 属性](../mfc/mfc-activex-controls-properties.md)，添加常用属性是使用轻松[添加属性向导](../ide/names-add-property-wizard.md)。 选择的字体属性，并添加属性向导自动常用字体将项插入到控件的调度映射。

#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>若要添加使用添加属性向导的堆栈 Font 属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加属性**。

     这将打开添加属性向导。

1. 在中**属性名称**框中，单击**字体**。

1. 单击 **“完成”**。

添加属性向导将以下行添加到控件的调度映射，位于控件类实现文件中：

[!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]

此外，添加属性向导将以下行添加到控件。IDL 文件：

[!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]

常用的标题属性是可以使用常用字体属性信息绘制的文本属性的示例。 向控件添加常用 Caption 属性使用类似于所使用的常用字体属性的步骤。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>若要添加常用的标题属性使用添加属性向导

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加属性**。

     这将打开添加属性向导。

1. 在中**属性名称**框中，单击**标题**。

1. 单击 **“完成”**。

添加属性向导将以下行添加到控件的调度映射，位于控件类实现文件中：

[!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]

##  <a name="_core_modifying_the_ondraw_function"></a> 修改 OnDraw 函数

默认实现`OnDraw`Windows 系统字体用于显示控件中的所有文本。 这意味着，必须修改`OnDraw`由字体对象选入设备上下文的代码。 若要执行此操作，调用[COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont)并传递控件的设备上下文，如下面的示例中所示：

[!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]

之后`OnDraw`函数进行了修改，以使用字体对象，在控件内的任何文本将显示与来自控件的常用字体属性的特征。

##  <a name="_core_using_custom_font_properties_in_your_control"></a> 在您的控件中使用自定义字体属性

除了常用字体属性，ActiveX 控件可以有自定义字体属性。 若要添加自定义字体属性必须：

- 使用添加属性向导来实现自定义的字体属性。

- [处理字体通知](#_core_processing_font_notifications)。

- [实现新的字体通知接口](#_core_implementing_a_new_font_notification_interface)。

###  <a name="_core_implementing_a_custom_font_property"></a> 实现自定义字体属性

若要实现自定义字体属性，您使用添加属性向导以添加该属性，然后将某些修改代码。 以下各节介绍了如何添加自定义`HeadingFont`示例控件的属性。

##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>若要添加使用添加属性向导的自定义字体属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 从快捷菜单中，单击**外**，然后单击**添加属性**。

     这将打开添加属性向导。

1. 在中**属性名称**框中，键入属性的名称。 对于此示例中，使用**HeadingFont**。

1. 对于“实现类型” ，请单击“Get/Set 方法” 。

1. 在中**属性类型**框中，选择**IDispatch** <strong>\*</strong>属性的类型。

1. 单击 **“完成”**。

添加属性向导创建代码以添加`HeadingFont`自定义属性设置为`CSampleCtrl`类和示例。IDL 文件。 因为`HeadingFont`是 Get/Set 属性类型添加属性向导修改`CSampleCtrl`类的调度映射，以包括 DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)宏条目：

[!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]

DISP_PROPERTY_EX 宏将相关联`HeadingFont`与其对应的属性名称`CSampleCtrl`类获取和设置方法，`GetHeadingFont`和`SetHeadingFont`。 此外指定属性值的类型;在此情况下，VT_FONT。

添加属性向导还会在控件头文件中添加声明 (。H） 对于`GetHeadingFont`和`SetHeadingFont`函数并在控件实现文件中添加其函数模板 (。CPP):

[!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]

最后，添加属性向导修改控件。IDL 文件添加的条目`HeadingFont`属性：

[!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]

### <a name="modifications-to-the-control-code"></a>修改控件代码

现在，已添加`HeadingFont`到控件的属性，您必须对控件标头和实现文件，以完全支持新的属性进行一些更改。

控制标头文件中 (。H） 中，添加一个受保护的成员变量的以下声明：

[!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]

在控件实现文件 (。CPP) 中，执行以下操作：

- 初始化*m_fontHeading*控件构造函数中。

     [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]

- 声明静态 FONTDESC 结构包含字体的默认属性。

     [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]

- 在控件中`DoPropExchange`成员函数中，添加对的调用`PX_Font`函数。 这提供了初始化和自定义字体属性的持久性。

     [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]

- 完成实现控件`GetHeadingFont`成员函数。

     [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]

- 完成实现控件`SetHeadingFont`成员函数。

     [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]

- 修改控件`OnDraw`成员函数，以定义一个变量来保存以前选择的字体。

     [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]

- 修改控件`OnDraw`成员函数要通过添加以下代码行字体的地方都要使用的设备上下文中选择自定义字体。

     [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]

- 修改控件`OnDraw`成员函数以返回到设备上下文选择上一字体，通过将以下行添加后使用的字体。

     [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]

在实现自定义的字体属性后，应实现标准的字体属性页，允许控制用户更改控件的当前字体。 若要添加标准的字体属性页的属性页 ID，请 BEGIN_PROPPAGEIDS 宏后插入以下行：

[!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]

你还必须由一个递增 BEGIN_PROPPAGEIDS 宏的计数参数。 下面一行阐释了这一点：

[!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]

在进行这些更改后，重新生成整个项目以合并的其他功能。

###  <a name="_core_processing_font_notifications"></a> 处理字体通知

在大多数情况下该控件需要知道如果字体对象的特征已修改。 每个字体对象都能够通过调用的成员函数发生更改时提供通知`IFontNotification`实现的接口`COleControl`。

如果该控件使用的堆栈 Font 属性，其通知由处理`OnFontChanged`成员函数的`COleControl`。 当你添加自定义字体属性时，可以让它们使用相同的实现。 在上一节中示例中，这通过传递 &*m_xFontNotification*初始化时*m_fontHeading*成员变量。

![实现多个字体对象接口](../mfc/media/vc373q1.gif "vc373q1")实现多个字体对象接口

在上图中实线显示这两个字体对象使用的相同实现`IFontNotification`。 如果你想要区分哪些字体更改，这可能导致问题。

区分控件的字体对象通知的一种方法是创建的单独实现`IFontNotification`控件中每个字体对象接口。 此技术，可通过更新的字符串或字符串，使用最近修改过的字体来优化绘制代码。 以下各节演示如何实现第二个字体属性的单独通知接口所需的步骤。 第二个字体属性被假定为`HeadingFont`已在上一节中添加的属性。

###  <a name="_core_implementing_a_new_font_notification_interface"></a> 实现新的字体通知接口

若要区分两个或多个字体的通知，必须为每个控件中使用的字体实现新的通知接口。 以下部分介绍如何通过修改控制标头和实现文件中实现新的字体通知接口。

### <a name="additions-to-the-header-file"></a>新增内容标头文件

控制标头文件中 (。H） 中，将以下行添加到类声明：

[!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]

这将创建的实现`IPropertyNotifySink`接口调用`HeadingFontNotify`。 此新接口包含一个名为方法`OnChanged`。

### <a name="additions-to-the-implementation-file"></a>在实现文件的新增功能

在初始化 （在控件构造函数） 的标题字体的代码，更改 &*m_xFontNotification*到 &*m_xHeadingFontNotify*。 然后添加以下代码：

[!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]

`AddRef`并`Release`中的方法`IPropertyNotifySink`接口跟踪的 ActiveX 控件对象的引用计数。 当控件获得访问接口指针时，该控件调用`AddRef`递增引用数。 当控件完成的指针时，它将调用`Release`，在大致相同的方式`GlobalFree`可能调用以释放的全局内存块。 在此接口的引用计数变为零，则可以释放接口实现。 在此示例中，`QueryInterface`函数将返回一个指向`IPropertyNotifySink`特定对象上的接口。 此函数允许 ActiveX 控件来查询对象来确定所支持的接口。

到你的项目进行了这些更改后，重新生成项目，并使用测试容器测试接口。 请参阅 [使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md) 了解有关如何访问测试容器的信息。

## <a name="see-also"></a>请参阅

[MFC ActiveX 控件](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：在 ActiveX 控件中使用图片](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)<br/>
[MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)

