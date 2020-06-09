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
ms.openlocfilehash: 13e8af5ddb3dd5130c864e42383e3bb9ff23b87b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625426"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>MFC ActiveX 控件：添加常用属性

常用属性不同于自定义属性，因为它们已由类实现 `COleControl` 。 `COleControl`包含支持控件的公共属性的预定义成员函数。 一些常见的属性包括控件的标题以及前景色和背景色。 有关其他常用属性的信息，请参阅本文后面[的添加属性向导支持的常用属性](#_core_stock_properties_supported_by_classwizard)。 常用属性的调度映射条目始终带有 DISP_STOCKPROP 的前缀。

本文介绍如何使用 "添加属性向导" 将 stock 属性（在本例中为 Caption）添加到 ActiveX 控件，并说明生成的代码修改。 主题包括：

- [使用 "添加属性向导" 添加 stock 属性](#_core_using_classwizard_to_add_a_stock_property)

- [为常用属性添加属性向导更改](#_core_classwizard_changes_for_stock_properties)

- ["添加属性向导" 支持的常用属性](#_core_stock_properties_supported_by_classwizard)

- [常用属性和通知](#_core_stock_properties_and_notification)

- [颜色属性](#_core_color_properties)

    > [!NOTE]
    >  Visual Basic 自定义控件通常具有属性，如 Top、Left、Width、Height、Align、Tag、Name、TabIndex、TabStop 和 Parent。 但是，ActiveX 控件容器负责实现这些控件属性，因此 ActiveX 控件不应支持这些属性。

## <a name="using-the-add-property-wizard-to-add-a-stock-property"></a><a name="_core_using_classwizard_to_add_a_stock_property"></a>使用 "添加属性向导" 添加 Stock 属性

添加常用属性比添加自定义属性需要更少的代码，因为对属性的支持由自动处理 `COleControl` 。 下面的过程演示如何将 stock Caption 属性添加到 ActiveX 控件框架，还可用于添加其他常用属性。 将所选的常用属性名称替换为 Caption。

#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>使用 "添加属性向导" 添加 stock Caption 属性

1. 加载控件的项目。

1. 在“类视图”中，展开控件的库节点。

1. 右键单击控件的接口节点（库节点的第二个节点）以打开快捷菜单。

1. 在快捷菜单中，单击 "**添加**"，然后单击 "**添加属性**"。

   这将打开 "[添加属性向导](../ide/names-add-property-wizard.md)"。

1. 在 "**属性名称**" 框中，单击 "**标题**"。

1. 单击“完成”。

## <a name="add-property-wizard-changes-for-stock-properties"></a><a name="_core_classwizard_changes_for_stock_properties"></a>为常用属性添加属性向导更改

由于 `COleControl` 支持常用属性，因此 "添加属性向导" 不会以任何方式更改类声明，而是将属性添加到调度映射。 "添加属性向导" 将以下行添加到控件（位于实现中的调度映射）（）。CPP）文件：

[!code-cpp[NVC_MFC_AxUI#22](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]

将以下行添加到控件的接口说明（。IDL）文件：

[!code-cpp[NVC_MFC_AxUI#23](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]

此行为 Caption 属性分配特定 ID。 请注意，属性可绑定，并将在修改值之前从数据库请求权限。

这使 Caption 属性可用于控件的用户。 若要使用 stock 属性的值，请访问基类的成员变量或成员函数 `COleControl` 。 有关这些成员变量和成员函数的详细信息，请参阅下一节 "添加属性向导" 支持的常用属性。

## <a name="stock-properties-supported-by-the-add-property-wizard"></a><a name="_core_stock_properties_supported_by_classwizard"></a>"添加属性向导" 支持的常用属性

`COleControl`类提供九个常用属性。 您可以使用 "添加属性向导" 添加所需的属性。

|properties|调度映射项|如何访问值|
|--------------|------------------------|-------------------------|
|`Appearance`|DISP_STOCKPROP_APPEARANCE （）|可访问的值 `m_sAppearance` 。|
|`BackColor`|DISP_STOCKPROP_BACKCOLOR （）|可通过调用访问的值 `GetBackColor` 。|
|`BorderStyle`|DISP_STOCKPROP_BORDERSTYLE （）|可访问的值 `m_sBorderStyle` 。|
|`Caption`|DISP_STOCKPROP_CAPTION （）|可通过调用访问的值 `InternalGetText` 。|
|`Enabled`|DISP_STOCKPROP_ENABLED （）|可访问的值 `m_bEnabled` 。|
|`Font`|DISP_STOCKPROP_FONT （）|请参阅[MFC ActiveX 控件：使用字体](mfc-activex-controls-using-fonts.md)进行使用一文。|
|`ForeColor`|DISP_STOCKPROP_FORECOLOR （）|可通过调用访问的值 `GetForeColor` 。|
|`hWnd`|DISP_STOCKPROP_HWND （）|可访问的值 `m_hWnd` 。|
|`Text`|DISP_STOCKPROP_TEXT （）|可通过调用访问的值 `InternalGetText` 。 此属性与相同 `Caption` （属性名称除外）。|
|`ReadyState`|DISP_STOCKPROP_READYSTATE （）|可作为或访问的值 `m_lReadyState``GetReadyState`|

## <a name="stock-properties-and-notification"></a><a name="_core_stock_properties_and_notification"></a>常用属性和通知

大多数常用属性都具有可重写的通知函数。 例如，每当 `BackColor` 属性更改时， `OnBackColorChanged` 都会调用函数（control 类的成员函数）。 默认实现（中为 `COleControl` ）调用 `InvalidateControl` 。 如果要执行其他操作来响应此情况，请重写此函数。

## <a name="color-properties"></a><a name="_core_color_properties"></a>颜色属性

在绘制控件时，可以使用常用 `ForeColor` 和 `BackColor` 属性，或者您自己的自定义颜色属性。 若要使用 color 属性，请调用[COleControl：： TranslateColor](reference/colecontrol-class.md#translatecolor)成员函数。 此函数的参数是 color 属性和可选调色板控点的值。 返回值是可传递给 GDI 函数（如和）的**COLORREF**值 `SetTextColor` `CreateSolidBrush` 。

可以 `ForeColor` `BackColor` 通过分别调用或函数来访问股票和属性的颜色值 `GetForeColor` `GetBackColor` 。

下面的示例演示了在绘制控件时使用这两种颜色属性。 它使用属性将临时**COLORREF**变量和 `CBrush` 对象初始化为 `TranslateColor` ：一个使用 `ForeColor` 属性，另 `BackColor` 一个是使用属性。 `CBrush`然后，使用临时对象绘制控件的矩形，并使用属性设置文本颜色 `ForeColor` 。

[!code-cpp[NVC_MFC_AxUI#24](codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]

## <a name="see-also"></a>另请参阅

[MFC ActiveX 控件](mfc-activex-controls.md)<br/>
[MFC ActiveX 控件：属性](mfc-activex-controls-properties.md)<br/>
[MFC ActiveX 控件：方法](mfc-activex-controls-methods.md)<br/>
[COleControl 类](reference/colecontrol-class.md)
