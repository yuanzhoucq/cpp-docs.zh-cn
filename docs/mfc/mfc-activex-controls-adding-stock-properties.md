---
title: MFC ActiveX 控件：添加常用属性
ms.date: 11/04/2016
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
ms.openlocfilehash: 16bdfddf0c028bc6a312767844b38c58c942d56e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364663"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC ActiveX 控件：添加常用属性

股票属性与自定义属性不同，因为它们已由 类`COleControl`实现。 `COleControl`包含支持控件的通用属性的预定义成员函数。 一些常见属性包括控件的标题以及前景和背景颜色。 有关其他股票属性的信息，请参阅本文后面的[添加属性向导支持的股票属性](#_core_stock_properties_supported_by_classwizard)。 股票属性的调度映射条目始终由DISP_STOCKPROP来预定。

本文介绍如何使用添加属性向导将股票属性（本例中为标题）添加到 ActiveX 控件，并解释生成的代码修改。 主题包括：

- [使用添加属性向导添加股票属性](#_core_using_classwizard_to_add_a_stock_property)

- [添加股票属性的属性向导更改](#_core_classwizard_changes_for_stock_properties)

- [添加属性向导支持的股票属性](#_core_stock_properties_supported_by_classwizard)

- [库存属性和通知](#_core_stock_properties_and_notification)

- [颜色属性](#_core_color_properties)

    > [!NOTE]
    >  可视化基本自定义控件通常具有诸如"顶部"、"左侧"、"宽度"、"高度"、"对齐"、"标记"、"名称"、"TabIndex"、"TabStop"和"父级"等属性。 但是，ActiveX 控制容器负责实现这些控制属性，因此 ActiveX 控件不应支持这些属性。

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a>使用"添加属性向导"添加股票属性

添加股票属性需要的代码比添加自定义属性少，因为对属性的支持由 自动处理`COleControl`。 以下过程演示了将股票标题属性添加到 ActiveX 控件框架，还可用于添加其他股票属性。 将所选股票属性名称替换为标题。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>使用添加属性向导添加股票标题属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击"**添加**"，然后单击"**添加属性**"。

   这将打开[添加属性向导](../ide/names-add-property-wizard.md)。

1. 在 **"属性名称"** 框中，单击 **"标题**"。

1. 单击“完成”  。

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a>添加股票属性的属性向导更改

由于`COleControl`支持股票属性，因此添加属性向导不会以任何方式更改类声明;因此，不会更改类声明。它将属性添加到调度映射。 "添加属性向导"将以下行添加到位于实现 （的控件的调度映射中）。CPP） 文件：

[!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

以下行将添加到控件的接口说明 （。IDL） 文件：

[!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

此行为标题属性分配特定 ID。 请注意，该属性是可绑定的，将在修改值之前从数据库请求权限。

这使标题属性可供控件的用户使用。 要使用 stock 属性的值，请使用`COleControl`基类的成员变量或成员函数。 有关这些成员变量和成员函数的详细信息，请参阅下一节"添加属性向导支持的股票属性"。

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a>添加属性向导支持的股票属性

该`COleControl`类提供九个股票属性。 您可以使用"添加属性向导"添加所需的属性。

|Property|调度映射条目|如何访问值|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE）|值可访问`m_sAppearance`为 。|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR）|可通过调用`GetBackColor`访问的值。|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE）|值可访问`m_sBorderStyle`为 。|
|`Caption`|DISP_STOCKPROP_CAPTION）|可通过调用`InternalGetText`访问的值。|
|`Enabled`|DISP_STOCKPROP_ENABLED）|值可访问`m_bEnabled`为 。|
|`Font`|DISP_STOCKPROP_FONT（ ）|请参阅文章[MFC ActiveX 控件：使用字体](../mfc/mfc-activex-controls-using-fonts.md)进行使用。|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR）|可通过调用`GetForeColor`访问的值。|
|`hWnd`|DISP_STOCKPROP_HWND）|值可访问`m_hWnd`为 。|
|`Text`|DISP_STOCKPROP_TEXT）|可通过调用`InternalGetText`访问的值。 此属性与`Caption`相同，属性名称除外。|
|`ReadyState`|DISP_STOCKPROP_READYSTATE（）|值可访问`m_lReadyState`于 或`GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a>股票属性和通知

大多数股票属性具有可以重写的通知函数。 例如，每当更改`BackColor`属性时，`OnBackColorChanged`都会调用函数（控件类的成员函数）。 默认实现 （在`COleControl`）`InvalidateControl`调用 。 如果要针对此情况执行其他操作，请重写此函数。

## <a name="color-properties"></a><a name="_core_color_properties"></a>颜色属性

绘制控件时，可以使用`ForeColor`股票`BackColor`和属性或您自己的自定义颜色属性。 要使用颜色属性，请调用[COleControl：：翻译颜色](../mfc/reference/colecontrol-class.md#translatecolor)成员函数。 此函数的参数是颜色属性的值和可选的调色板句柄。 返回值是一个**COLORREF**值，可以传递给 GDI 函数，`SetTextColor`如`CreateSolidBrush`和 。

`ForeColor`通过分别调用 或`BackColor``GetForeColor``GetBackColor`函数来访问股票和属性的颜色值。

下面的示例演示了在绘制控件时使用这两个颜色属性。 它初始化临时的**COLORREF**变量和`CBrush`一个对象，`TranslateColor`其中一个使用`ForeColor`属性调用 ，另`BackColor`一个使用 属性。 然后，`CBrush`临时对象用于绘制控件的矩形，并使用 属性`ForeColor`设置文本颜色。

[!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 活动X控制](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：属性](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl 类](../mfc/reference/colecontrol-class.md)
