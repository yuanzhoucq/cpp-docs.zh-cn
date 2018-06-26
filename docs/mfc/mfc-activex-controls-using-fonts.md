---
title: MFC ActiveX 控件： 使用字体 |Microsoft 文档
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
ms.openlocfilehash: 7f5d1475412de736970d0ae36a39540121bfbc01
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930710"
---
# <a name="mfc-activex-controls-using-fonts"></a>MFC ActiveX 控件：使用字体
如果 ActiveX 控件显示文本，你可以允许控制用户通过更改字体属性更改的文本外观。 字体属性作为字体对象实现，并可以是两种类型之一： 常用或自定义。 常用字体属性是可以使用添加属性向导添加的 preimplemented 的字体属性。 自定义字体属性不 preimplemented 并控件开发人员确定属性的行为和使用情况。  
  
 本文介绍了以下主题：  
  
-   [使用常用字体属性](#_core_using_the_stock_font_property)  
  
-   [在控件中使用自定义字体属性](#_core_implementing_a_custom_font_property)  
  
##  <a name="_core_using_the_stock_font_property"></a> 使用常用字体属性  
 常用字体属性 preimplemented 由类[COleControl](../mfc/reference/colecontrol-class.md)。 此外，标准的字体属性页也会提供，允许用户更改字体对象，如其名称、 大小和样式的各种属性。  
  
 访问字体对象，通过[GetFont](../mfc/reference/colecontrol-class.md#getfont)， [SetFont](../mfc/reference/colecontrol-class.md#setfont)，和[InternalGetFont](../mfc/reference/colecontrol-class.md#internalgetfont)函数的`COleControl`。 控制用户将访问通过字体对象`GetFont`和`SetFont`与任何其他 Get/Set 属性相同的方式中的函数。 需要从控件内的字体对象访问权限时，使用`InternalGetFont`函数。  
  
 中所述[MFC ActiveX 控件： 属性](../mfc/mfc-activex-controls-properties.md)，添加常用属性是可以方便[添加属性向导](../ide/names-add-property-wizard.md)。 选择字体属性中，并添加属性向导自动将插入到控件的调度映射的常用字体条目。  
  
#### <a name="to-add-the-stock-font-property-using-the-add-property-wizard"></a>若要添加常用字体属性使用添加属性向导  
  
1.  加载控件的项目。  
  
2.  在“类视图”中，展开控件的库节点。  
  
3.  右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。  
  
4.  从快捷菜单中，单击**添加**，然后单击**添加属性**。  
  
     这将打开添加属性向导。  
  
5.  在**属性名称**框中，单击**字体**。  
  
6.  单击 **“完成”**。  
  
 添加属性向导将添加到控件的调度映射，位于控件类实现文件中的以下行：  
  
 [!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_1.cpp)]  
  
 此外，添加属性向导将以下行添加到控件。IDL 文件：  
  
 [!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_2.idl)]  
  
 常用的标题属性是一个文本属性，可以使用的常用字体属性信息绘制一个示例。 向控件添加常用标题属性使用类似于所使用的常用字体属性步骤。  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>若要添加常用标题属性使用添加属性向导  
  
1.  加载控件的项目。  
  
2.  在“类视图”中，展开控件的库节点。  
  
3.  右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。  
  
4.  从快捷菜单中，单击**添加**，然后单击**添加属性**。  
  
     这将打开添加属性向导。  
  
5.  在**属性名称**框中，单击**标题**。  
  
6.  单击 **“完成”**。  
  
 添加属性向导将添加到控件的调度映射，位于控件类实现文件中的以下行：  
  
 [!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_3.cpp)]  
  
##  <a name="_core_modifying_the_ondraw_function"></a> 修改 OnDraw 函数  
 默认实现`OnDraw`Windows 系统字体用于显示控件中的所有文本。 这意味着，你必须修改`OnDraw`通过将字体对象选入设备上下文的代码。 若要执行此操作，调用[COleControl::SelectStockFont](../mfc/reference/colecontrol-class.md#selectstockfont)并传递控件的设备上下文，如下面的示例中所示：  
  
 [!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_4.cpp)]  
  
 后`OnDraw`函数进行了修改，以使用字体对象，控件中的任何文本将显示具有从控件的常用字体属性的特性。  
  
##  <a name="_core_using_custom_font_properties_in_your_control"></a> 在控件中使用自定义字体属性  
 除了常用字体属性，ActiveX 控件可以包含自定义字体属性。 若要添加自定义字体属性必须：  
  
-   使用添加属性向导来实现自定义的字体属性。  
  
-   [处理字体通知](#_core_processing_font_notifications)。  
  
-   [实现新字体通知接口](#_core_implementing_a_new_font_notification_interface)。  
  
###  <a name="_core_implementing_a_custom_font_property"></a> 实现自定义字体属性  
 若要实现自定义的字体属性，你使用添加属性向导来添加属性，然后对代码的一些修改。 下列各节描述如何添加自定义`HeadingFont`示例控件的属性。  
  
##### <a name="to-add-the-custom-font-property-using-the-add-property-wizard"></a>若要添加使用添加属性向导的自定义字体属性  
  
1.  加载控件的项目。  
  
2.  在“类视图”中，展开控件的库节点。  
  
3.  右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。  
  
4.  从快捷菜单中，单击**添加**，然后单击**添加属性**。  
  
     这将打开添加属性向导。  
  
5.  在**属性名称**框中，键入属性的名称。 对于此示例中，使用**HeadingFont**。  
  
6.  对于“实现类型” ，请单击“Get/Set 方法” 。  
  
7.  在**属性类型**框中，选择**IDispatch\*** 属性的类型。  
  
8.  单击 **“完成”**。  
  
 添加属性向导创建用于添加的代码`HeadingFont`自定义属性`CSampleCtrl`类和示例。IDL 文件。 因为`HeadingFont`是 Get/Set 属性类型，则添加属性向导将修改`CSampleCtrl`类的调度映射，以包括 DISP_PROPERTY_EX_ID[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)宏条目：  
  
 [!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_5.cpp)]  
  
 DISP_PROPERTY_EX 宏将相关联`HeadingFont`与其对应的属性名称`CSampleCtrl`类获取和设置方法，`GetHeadingFont`和`SetHeadingFont`。 此外指定属性值的类型;在此情况下，VT_FONT。  
  
 添加属性向导还会在控件头文件中添加声明 (。H） 为`GetHeadingFont`和`SetHeadingFont`函数，并在控件实现文件中添加其函数模板 (。CPP):  
  
 [!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_6.cpp)]  
  
 最后，添加属性向导修改控件。IDL 文件添加的条目`HeadingFont`属性：  
  
 [!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_7.idl)]  
  
### <a name="modifications-to-the-control-code"></a>对该控件代码做的修改  
 现在，已添加`HeadingFont`到控件的属性，则必须以完全支持新的属性控制标头和实现文件中做一些更改。  
  
 控制标头文件中 (。H） 中，添加的受保护的成员变量的以下声明：  
  
 [!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_8.h)]  
  
 在控件实现文件 (。CPP) 中，执行以下操作：  
  
-   初始化*m_fontHeading*控件构造函数中。  
  
     [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_9.cpp)]  
  
-   声明静态 FONTDESC 结构包含的字体的默认属性。  
  
     [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_10.cpp)]  
  
-   在控件中`DoPropExchange`成员函数中，添加对的调用`PX_Font`函数。 这提供了初始化和自定义字体属性的持久性。  
  
     [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_11.cpp)]  
  
-   完成实现控件`GetHeadingFont`成员函数。  
  
     [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_12.cpp)]  
  
-   完成实现控件`SetHeadingFont`成员函数。  
  
     [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_13.cpp)]  
  
-   修改控件`OnDraw`成员函数定义一个变量以保存以前选定的字体。  
  
     [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_14.cpp)]  
  
-   修改控件`OnDraw`成员函数以通过添加以下行字体的地方都要使用选入设备上下文的自定义字体。  
  
     [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_15.cpp)]  
  
-   修改控件`OnDraw`成员函数来选择恢复到的设备上下文的以前的字体，通过将以下行添加后使用的字体。  
  
     [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_16.cpp)]  
  
 在实现自定义的字体属性之后，应实现标准的字体属性页，允许控制用户更改控件的当前字体。 若要添加标准的字体属性页的属性页 ID，请在 BEGIN_PROPPAGEIDS 宏后插入以下行：  
  
 [!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_17.cpp)]  
  
 你还必须由一个递增 BEGIN_PROPPAGEIDS 宏的计数参数。 下面一行阐释了这一点：  
  
 [!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_18.cpp)]  
  
 做出这些更改后，重新生成整个项目以整合的其他功能。  
  
###  <a name="_core_processing_font_notifications"></a> 处理字体通知  
 在大多数情况下在控件需要知道何时已修改的字体对象的特征。 每个字体对象都能够提供通知，如果它通过调用的成员函数更改`IFontNotification`由实现的接口`COleControl`。  
  
 如果该控件使用常用字体属性，其通知由`OnFontChanged`成员函数`COleControl`。 当你添加自定义字体属性时，你可以让它们使用相同的实现。 在上一节中示例中，这通过传递 （& a)*m_xFontNotification*初始化时*m_fontHeading*成员变量。  
  
 ![实现多个字体对象接口](../mfc/media/vc373q1.gif "vc373q1")  
实现多个字体对象接口  
  
 在上图中实线显示这两个字体对象正在使用的相同实现`IFontNotification`。 如果你想要区分哪种字体更改，这会导致问题。  
  
 区分控件的字体对象通知的一种方法是创建的单独实现`IFontNotification`控件中每个字体对象接口。 此技术使你可以通过更新字符串或使用最近修改过的字体的字符串优化绘制代码。 以下部分演示实现第二个字体属性的单独通知接口所必需的步骤。 第二个字体属性被假定为`HeadingFont`已添加上一节中的属性。  
  
###  <a name="_core_implementing_a_new_font_notification_interface"></a> 实现新字体通知接口  
 若要区分两个或多个字体的通知，必须为每个控件中使用的字体实现新的通知接口。 下列各节描述如何通过修改控制标头和实现文件实现新的字体通知接口。  
  
### <a name="additions-to-the-header-file"></a>添加内容到标头文件  
 控制标头文件中 (。H） 中，将以下行添加到类声明：  
  
 [!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_19.h)]  
  
 这将创建的实现`IPropertyNotifySink`接口调用`HeadingFontNotify`。 此新界面包含调用的方法`OnChanged`。  
  
### <a name="additions-to-the-implementation-file"></a>添加内容到实现文件  
 在初始化 （中控件的构造函数） 的标题字体的代码，更改 （& a)*m_xFontNotification*到 （& a)*m_xHeadingFontNotify*。 然后添加以下代码：  
  
 [!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/cpp/mfc-activex-controls-using-fonts_20.cpp)]  
  
 `AddRef`和`Release`中的方法`IPropertyNotifySink`跟踪的接口的 ActiveX 控件对象的引用计数。 该控件时控件获得对接口指针的访问，调用`AddRef`递增引用计数。 当控件完成使用指针时，它将调用`Release`，在大致相同的方式`GlobalFree`可能调用释放全局内存块。 在此接口的引用计数变为零时，则可以释放接口的实现。 在此示例中，`QueryInterface`函数返回一个指向`IPropertyNotifySink`特定对象上的接口。 此函数允许 ActiveX 控件来查询来确定所支持的接口的对象。  
  
 到你的项目进行了这些更改后，重新生成项目，并使用测试容器测试该接口。 请参阅 [使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md) 了解有关如何访问测试容器的信息。  
  
## <a name="see-also"></a>请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件： 在 ActiveX 控件中使用图片](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)   
 [MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)

