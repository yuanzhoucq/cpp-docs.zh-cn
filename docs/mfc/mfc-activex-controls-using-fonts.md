---
title: "MFC ActiveX 控件：使用字体 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnFontChanged"
  - "HeadingFont"
  - "InternalFont"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字体, ActiveX 控件"
  - "GetFont 方法"
  - "HeadingFont 属性"
  - "InternalFont 方法"
  - "IPropertyNotifySink 类"
  - "MFC ActiveX 控件, 字体"
  - "通知, MFC ActiveX 控件字体"
  - "OnDraw 方法, MFC ActiveX 控件"
  - "OnFontChanged 方法"
  - "SelectStockFont 方法"
  - "SetFont 方法"
  - "常用字体属性"
ms.assetid: 7c51d602-3f5a-481d-84d1-a5d8a3a71761
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控件：使用字体
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果 ActiveX 控件显示文本，您可以让用户控件通过更改字体属性更改文本的外观。  字体属性实现为字体对象，可以为以下两种类型之一：常用或自定义。  常用字体属性是使用添加属性向导"可以将 preimplemented 的字体属性。  自定义字体属性不 preimplemented，控件开发人员确定的行为属性和用法。  
  
 本文涵盖以下主题：  
  
-   [使用栈字体属性](#_core_using_the_stock_font_property)  
  
-   [使用控件中自定义字体属性](#_core_implementing_a_custom_font_property)  
  
##  <a name="_core_using_the_stock_font_property"></a> 使用栈字体属性  
 常用字体属性由类 preimplemented [COleControl](../mfc/reference/colecontrol-class.md)。  此外，标准字体属性可用，页还允许用户更改字体对象的各种特征，例如文件的名称、大小和样式。  
  
 通过 [GetFont](../Topic/COleControl::GetFont.md)、[SetFont](../Topic/COleControl::SetFont.md)和 `COleControl`的函数 [InternalGetFont](../Topic/COleControl::InternalGetFont.md) 字体访问对象。  控件用户通过 `GetFont` 将访问字体对象，并且使用与其他任何相同的 `SetFont` 函数获取\/设置属性。  当对字体对象的访问权。需要控件中时，请使用 `InternalGetFont` 函数。  
  
 如 [MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)所述，将库存属性对 [添加属性向导](../ide/names-add-property-wizard.md)非常容易。  您选择字体属性，并且，添加属性向导自动插入常用字体输入控件的计划映射。  
  
#### 使用"添加属性向导，将库存 Font 属性  
  
1.  加载控件项目。  
  
2.  在类视图中，展开控件的库节点。  
  
3.  右击控件的接口节点 \(库节点的第二个节点\) ，打开快捷菜单。  
  
4.  从快捷菜单中，单击**“添加”**，然后单击**“添加属性”**。  
  
     这会打开 添加属性向导。  
  
5.  在 **属性名** 框中，单击 **字体**。  
  
6.  单击**“完成”**。  
  
 添加属性向导以下行添加到的控件映射计划，位于控件类实现文件：  
  
 [!code-cpp[NVC_MFC_AxFont#1](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_1.cpp)]  
  
 此外，添加属性向导以下行添加到 .idl 控件文件：  
  
 [!code-cpp[NVC_MFC_AxFont#2](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_2.idl)]  
  
 股票的 caption 属性是使用常用字体属性信息，可以绘制文本属性的示例。  添加股票标题属性绑定到控件使用单步执行类似于用于常用字体属性的那些开关。  
  
#### 使用"添加属性向导，将库存 caption 属性  
  
1.  加载控件项目。  
  
2.  在类视图中，展开控件的库节点。  
  
3.  右击控件的接口节点 \(库节点的第二个节点\) ，打开快捷菜单。  
  
4.  从快捷菜单中，单击**“添加”**，然后单击**“添加属性”**。  
  
     这会打开 添加属性向导。  
  
5.  在 **属性名** 框中，单击 **标题**。  
  
6.  单击**“完成”**。  
  
 添加属性向导以下行添加到的控件映射计划，位于控件类实现文件：  
  
 [!code-cpp[NVC_MFC_AxFont#3](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_3.cpp)]  
  
##  <a name="_core_modifying_the_ondraw_function"></a> 修改 OnDraw 函数  
 `OnDraw` 的默认实现。显示的所有文本使用 Windows 系统字体。控件。  这意味着您必须通过修改 `OnDraw` 对象选择字体代码到设备上下文。  如下例所示，若要执行此操作，请调用 [COleControl::SelectStockFont](../Topic/COleControl::SelectStockFont.md) 并传入控件的设备上下文，例如：  
  
 [!code-cpp[NVC_MFC_AxFont#4](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_4.cpp)]  
  
 在修改了 `OnDraw` 函数使用字体对象后，控件内的所有文本显示与股票控制字体属性的特性。  
  
##  <a name="_core_using_custom_font_properties_in_your_control"></a> 使用控件中自定义字体属性  
 除了常用字体属性，ActiveX 控件可以具有自定义字体属性。  若要添加自定义字体属性必须：  
  
-   使用添加属性向导实现自定义字体属性。  
  
-   [通知处理字体](#_core_processing_font_notifications)。  
  
-   [实现一个新字体通知接口](#_core_implementing_a_new_font_notification_interface)。  
  
###  <a name="_core_implementing_a_custom_font_property"></a> 实现自定义字体属性  
 若要实现自定义字体属性，则使用将属性添加属性向导然后对代码进行一些修改。  以下各节描述如何将自定义 `HeadingFont` 的示例属性设置为控件。  
  
##### 使用"添加属性向导，Font 添加自定义属性  
  
1.  加载控件项目。  
  
2.  在类视图中，展开控件的库节点。  
  
3.  右击控件的接口节点 \(库节点的第二个节点\) ，打开快捷菜单。  
  
4.  从快捷菜单中，单击**“添加”**，然后单击**“添加属性”**。  
  
     这会打开 添加属性向导。  
  
5.  在“属性名称”框中，键入新属性的名称。  对于此示例，使用 **HeadingFont**。  
  
6.  对于 **Implementation Type**，单击 **Get\/Set Methods**。  
  
7.  在 **属性类型** 框，为属性类型选择 **IDispatch\***。  
  
8.  单击**“完成”**。  
  
 添加属性向导创建代码添加 `HeadingFont` 自定义属性。`CSampleCtrl` 类和 SAMPLE.IDL 文件。  由于 `HeadingFont` 是 get\/set 特性类型，"添加属性向导"中修改 `CSampleCtrl` 类计划映射以包含 `DISP_PROPERTY_EX_ID`[DISP\_PROPERTY\_EX](../Topic/DISP_PROPERTY_EX.md) 宏 Enter:  
  
 [!code-cpp[NVC_MFC_AxFont#5](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_5.cpp)]  
  
 `DISP_PROPERTY_EX` 宏与 `HeadingFont` 属性名与其对应的 `CSampleCtrl` 类获取和设置方法，`GetHeadingFont` 和 `SetHeadingFont`。  属性值类型还指定；在此例中，**VT\_FONT**。  
  
 添加属性向导还添加到控件标头文件的声明 \(。`GetHeadingFont` 和 `SetHeadingFont`。\) H 函数并将它们在控件实现文件 \(.cpp\) 的函数模板：  
  
 [!code-cpp[NVC_MFC_AxFont#6](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_6.cpp)]  
  
 最后，添加属性向导通过将 `HeadingFont` 属性的项添加修改控件 .idl 文件：  
  
 [!code-cpp[NVC_MFC_AxFont#7](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_7.idl)]  
  
### 修改控件代码  
 既然已经添加了 `HeadingFont` 属性添加控件，必须对控件标题和实现文件的某些更改完全支持新的属性。  
  
 在头 \(控件文件。H\)，添加受保护成员变量中的下列声明：  
  
 [!code-cpp[NVC_MFC_AxFont#8](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_8.h)]  
  
 在控件实现文件 \(.cpp\) 中，执行以下操作：  
  
-   初始化放到控件构造函数的 `m_fontHeading`。  
  
     [!code-cpp[NVC_MFC_AxFont#9](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_9.cpp)]  
  
-   声明包含字体的默认特性的静态 **FONTDESC** 结构。  
  
     [!code-cpp[NVC_MFC_AxFont#10](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_10.cpp)]  
  
-   在控件 `DoPropExchange` 成员函数中，添加一个调用 `PX_Font` 函数。  对于自定义字体属性提供初始化和持久性。  
  
     [!code-cpp[NVC_MFC_AxFont#11](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_11.cpp)]  
  
-   在控件上实现 `GetHeadingFont` 成员函数中完成。  
  
     [!code-cpp[NVC_MFC_AxFont#12](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_12.cpp)]  
  
-   在控件上实现 `SetHeadingFont` 成员函数中完成。  
  
     [!code-cpp[NVC_MFC_AxFont#13](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_13.cpp)]  
  
-   修改控件 `OnDraw` 成员函数定义变量持有以前选定的字体。  
  
     [!code-cpp[NVC_MFC_AxFont#14](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_14.cpp)]  
  
-   修改控件 `OnDraw` 成员函数选择该自定义字体到设备上下文通过添加以下行，在何处使用字体。  
  
     [!code-cpp[NVC_MFC_AxFont#15](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_15.cpp)]  
  
-   修改控件 `OnDraw` 成员函数前选择字体回设备上下文通过添加下面的行，则使用后字体。  
  
     [!code-cpp[NVC_MFC_AxFont#16](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_16.cpp)]  
  
 在自定义字体属性实现后，应实现标准字体属性页，使用户控件更改当前控件的字体。  若要将标准字体属性页的页属性 ID，在 `BEGIN_PROPPAGEIDS` 宏后插入下面的行：  
  
 [!code-cpp[NVC_MFC_AxFont#17](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_17.cpp)]  
  
 还必须增加 `BEGIN_PROPPAGEIDS` 宏的参数的计数。  下面的代码行阐释这一点：  
  
 [!code-cpp[NVC_MFC_AxFont#18](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_18.cpp)]  
  
 在进行这些更改后，重新生成整个项目合并其他功能。  
  
###  <a name="_core_processing_font_notifications"></a> 通知处理字体。  
 在许多情况下需要知道何时修改了字体对象的特性。  字体提供每个对象获得通知，则通过调用 **IFontNotification** 接口的成员函数更改时，实现由 `COleControl`。  
  
 如果控件使用常用字体属性，则其通知由 `COleControl`的 `OnFontChanged` 成员函数处理。  当您将自定义字体添加属性时，可以让它们使用的实现。  在上一节的示例中，这是通过 &传递**m\_xFontNotification** 完成，在初始化 **m\_fontHeading** 成员变量时。  
  
 ![实现多个字体对象接口](../mfc/media/vc373q1.png "vc373Q1")  
实现多个字体对象接口  
  
 在上图显示的实线这两种字体对象使用 **IFontNotification**的实现。  这很可能会造成问题，则字体的更改要区分。  
  
 一种区分控件的字体。对象通知之间要创建 **IFontNotification** 接口的一个单独实现各个字体对象中控件。  此技术可以通过只更新字符串描述代码优化或字符串，则使用。修改新的字体。  下面的节演示的必要步骤实现第二个字体属性通知的接口。  第二个字体属性。假定是在上一节中添加的 `HeadingFont` 属性。  
  
###  <a name="_core_implementing_a_new_font_notification_interface"></a> 实现一个新字体通知接口。  
 若要区分两个或多个字体的通知之间，必须为在控件的每个字体实现新通知的接口。  下面的部分介绍如何通过修改控件标题和实现文件实现一个新字体通知接口。  
  
### 为头文件添加  
 在头 \(控件文件。H\)，下面一行添加到类声明：  
  
 [!code-cpp[NVC_MFC_AxFont#19](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_19.h)]  
  
 创建 `IPropertyNotifySink` interface called `HeadingFontNotify` 接口的实现要求。  此新接口包含一个名为 `OnChanged`的方法。  
  
### 该实现中添加文件  
 标题的字体在初始化代码 \(在控件构造函数\) 中，将 `&m_xFontNotification` 更改为 `&m_xHeadingFontNotify`。  添加下列代码：  
  
 [!code-cpp[NVC_MFC_AxFont#20](../mfc/codesnippet/CPP/mfc-activex-controls-using-fonts_20.cpp)]  
  
 在 `IPropertyNotifySink` 接口的 `AddRef` 和 `Release` 方法记录 ActiveX 控件对象的引用计数。  如果控件获得对接口指针的访问权限时，控件调用 `AddRef` 递增引用计数。  在控件完成对指针时，它将调用 `Release`，在类似情况下释放 **GlobalFree** 可能会调用一种全局存储区。  在此接口的引用计数转到零时，接口实现中释放。  在此示例中，`QueryInterface` 函数返回指向在特定对象的 `IPropertyNotifySink` 接口。  此函数使 ActiveX 控件查询对象确定它支持哪些界面。  
  
 在这些更改对项目后，请重新生成项目并使用测试容器测试接口。  有关如何访问测试容器的信息，请参见[用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件：在 ActiveX 控件中使用图片](../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md)   
 [MFC ActiveX 控件：使用常用属性页](../mfc/mfc-activex-controls-using-stock-property-pages.md)